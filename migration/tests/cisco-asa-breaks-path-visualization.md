# Cisco ASA breaks Path Visualization

When a TCP-based Path Visualization view displays forwarding loss at a node representing a Cisco ASA firewall, and white nodes or no nodes beyond the Cisco ASA firewall, a possible cause is the ASA's feature set which attempts to prevent TCP SYN floods and similar denial-of-service \(DoS\) attacks. The forwarding loss and missing nodes in Path Visualization can be corrected through the use of the ASA's TCP State Bypass feature.

## Reasons for breaking Path Visualization

The TCP synchronization \(SYN\) packets sent in the Path Visualization portion of a test use the same source and destination IP addresses and source and destination TCP port numbers \(a "four-tuple"\), but each has an initial sequence numbers \(ISN\) which is incremented by one with each increment of the Time to Live \(TTL\) field in the IP header \(the standard traceroute mechanism\). The Wireshark packet capture image below shows an Agent sending Path Visualization packets from source IP address 10.100.10.208 and source port 49221 to the target destination IP address 108.174.10.10 and destination TCP port 80:

IMAGE MISSING

As shown in the **Info** column, the first SYN packet \(with **Time to Live: 1** in the IP header\) has an initial sequence number of 1642740607. Each subsequent SYN packet increments the IP TTL and ISN by one. For example, the next SYN packet has an IP TTL of 2 and an ISN of 1642740608.

\(As a reference, the packet capture also displays the response to each SYN packet, which is an ICMP code 11 "time-to-live exceeded in transit" from which we obtain the IP address of the node in the path corresponding to the TTL of the SYN packet.\)

When a Cisco ASA receives the first TCP SYN packet, an entry is made in the ASA's embryonic connections table \(embryonic TCP connections are connections which are still performing the TCP handshake, i.e. have not reached the "established" state\). The entry is based on the four-tuple, but also records the ISN as part of the connection data. When a subsequent SYN packet is received with the same four-tuple but a different ISN, the Cisco ASA considers this a violation of normal TCP behavior, and drops the packet as a possible denial-of-service attack.

Logs from the ASA would be similar to the following:

```text
16:47:07.414577 10.100.10.208.49221 > 108.174.10.10.80: S 1642740608:1642740608 win 59261 <mss 1380,nop,nop,nop,nop,nop,nop,nop,nop,nop,nop,nop,nop> Drop-reason: (tcp-seq-syn-diff) TCP SEQ in SYN/SYNACK invalid
```

and

```text
Duplicate TCP SYN from source_interface_name: 10.100.10.208/49221 to destination_interface_name:108.174.10.10/80 with different initial sequence number
```

Steadily incrementing counters for [dropped packets in the accelerated security path \(ASP\)](https://www.cisco.com/c/en/us/td/docs/security/asa/asa-command-reference/show_asp_drop/show_asp_drop.html) can provide additional evidence:

```text
# show asp drop 

Frame drop:
  ...
  First TCP packet not SYN (tcp-not-syn)                                   13350
  TCP failed 3 way handshake (tcp-3whs-failed)                              4328
  TCP RST/FIN out of order (tcp-rstfin-ooo)                                 5766
  TCP SEQ in SYN/SYNACK invalid (tcp-seq-syn-diff)                         74630
  TCP packet SEQ past window (tcp-seq-past-win)                                1
  TCP RST/SYN in window (tcp-rst-syn-in-win)                                   1
  ...
```

## Remediation

Forwarding loss and missing nodes in Path Visualization can be corrected through the use of the ASA's TCP State Bypass feature, which eliminates the checks for stateful TCP data, and instead uses only the four-tuple to compare against basic access control lists \(ACLs\) with data such as source and destination IP address and source and destination TCP port.

The TCP State Bypass is configured using one or more ACL's to specify the IP addresses of the Enterprise Agents; a class map to group all such ACLs; and a policy map to specify the TCP state bypass is to be applied to the class of traffic specified in the class map. The policy map is typically applied on a per-interface basis. An example of the configuration is below. Consult the [Cisco ASA documentation](https://www.cisco.com/c/en/us/td/docs/security/asa/asa82/configuration/guide/config/conns_tcpstatebypass.html) on [configuring the TCP State Bypass](https://www.cisco.com/c/en/us/td/docs/security/asa/asa82/configuration/guide/config/conns_tcpstatebypass.html#wp1087434) for more information.

In the example, we use the following two IP addresses for Enterprise Agents:

10.100.10.208  
10.100.20.208

### Example configuration steps

1. Create the access list called "AgentIPs" with both Agents in the list

   ```text
   (config)# access list AgentIPs extended permit ip host 10.100.10.208 any
   (config)# access list AgentIPs extended permit ip host 10.100.20.208 any
   ```

2. Create the class called "TE-PathViz"

   ```text
   (config)# class-map TE-PathViz
   ```

3. Assign the access list to the class

   ```text
   (config-cmap)# match access-list AgentIPs
   ```

4. Exit to global configuration mode

   ```text
   (config-cmap)# exit
   ```

5. Create the policy called "TCP-bypass"

   ```text
   (config)# policy-map TCP-bypass
   ```

6. Assign the class to the policy

   ```text
   hostname(config-pmap)# class TE-PathViz
   ```

7. Set the policy to bypass TCP state

   ```text
   hostname(config-pmap-c)# set connection advanced-options tcp-state-bypass
   ```

8. Assign the policy to the interface named "outside"

   ```text
   hostname(config-pmap-c)# service-policy TCP-bypass interface outside
   ```

