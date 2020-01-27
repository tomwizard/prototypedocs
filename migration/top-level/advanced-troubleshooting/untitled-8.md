# Reasons for failure of private peering with ThousandEyes

The ThousandEyes platform provides [Inside-out BGP](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmmjKAC) visibility to allow network administrators to include their own private networks in the results of  BGP tests. Administrators configure their Border Gateway Protocol \(BGP\) speakers to peer with the ThousandEyes route collector and transfer the desired prefix announcements.  This will permit the ThousandEyes platform to display reachability of each BGP test's target from the vantage point of the customer’s own networks.

**Note:** A full routing information base \(RIB\) file is exported from the ThousandEyes route collector every two hours. Once you configure either a BGP test or a test that has the "Collect BGP data" box checked under the Advanced tab, the BGP Route Visualization may require up to two hours to fully populate.

If, after configuring your router\(s\) to peer with the ThousandEyes’ route collector, you cannot establish a BGP connection, review the items below to troubleshoot.

## Incorrect router configuration 

If your peering session is not uploading your BGP announcements to the ThousandEyes route collector, review your router’s configuration for errors.  An example Juniper router configuration for establishing a BGP session with ThousandEyes:

```text
set protocols bgp group thousandeyes-peer peer-as 65315
set protocols bgp group thousandeyes-peer type external
set protocols bgp group thousandeyes-peer multihop
set protocols bgp group thousandeyes-peer local-address xxx.xxx.xxx.xxx
set protocols bgp group thousandeyes-peer authentication-key <auth-key>
set protocols bgp group thousandeyes-peer import reject-all
set protocols bgp group thousandeyes-peer neighbor <ThousandEyes_BGP_peer_IP_address>*
```

\* Check the email you received from ThousandEyes for the correct ThousandEyes BGP Peer IP address.  Do not use a peer IP address from a previous private peer configuration, or any other source other than the configuration emailed to you for this specific peer.

##  Mismatched passwords for MD5 digest

To ensure the authenticity and integrity of route announcements, all devices peering with ThousandEyes’ route collector will use BGP MD5 authentication.  Your router will be configured with a common password \(sometimes called a key\) which is hashed in combination with certain TCP packet headers to authenticate the peer and verify each segment sent in the TCP connection.  If the password is not configured on one or both sides or does not match, messages like the following will be seen:

```text
*Sep 21 00:08:26.639: %TCP-6-BADAUTH: No MD5 digest from 10.10.10.1(23217) to 10.10.10.2(179)
```

```text
*Sep 21 00:08:26.959: %TCP-6-BADAUTH: Invalid MD5 digest from 10.10.10.1:23217 to 10.10.10.2:179
```

Verify that the password configured for the MD5 hash computation is identical to the one you provided ThousandEyes.

## Firewall/packet filter rules 

If your device which is peering with the ThousandEyes route collector is behind a firewall or packet filter, the firewall or packet filter must permit connections to the ThousandEyes route collector’s IP address on the standard BGP service port, 179/TCP.  Check your firewall’s logs for drops or rejections of packets from your router to the ThousandEyes route collector on destination port 179/TCP, and add an appropriate rule if needed to allow your router to make a connection to ThousandEyes on port 179/TCP.

You may see firewall logs showing drops or rejects of connection attempts from ThousandEyes to your router on port 179/TCP.  Blocked connections in this direction only will not result in failure to exchange BGP information.  Only failure to make the connection from your router to ThousandEyes requires modification to your firewall rules.

## Network Address Translation and Port Address Translation

BGP MD5 authentication computes a hash using portions of the IP and TCP header, including source and destination IP addresses and ports.  As a result, BGP MD5 authentication is incompatible with network address translation \(NAT\), Port Address Translation \(PAT\) and the combined form, network and port address translation \(NAPT\). Attempts to use MD5 authentication on a router with an interface configured with a non-routable \(RFC 1918-based\) IP address will cause failure of the of the MD5 hash comparison because of the NAT from the non-routable \(private\) IP address to a routable \(public\) IP address, prior to reaching the ThousandEyes route collector.  The receiver may generate error messages similar to:

```text
*Sep 21 00:08:26.959: %TCP-6-BADAUTH: Invalid MD5 digest from 10.10.10.1:23217 to 10.10.10.2:179
```

Additionally, any change to port numbers, sequence numbers or other fields used by the BGP MD5 hash will result in the same error.  See the following section for a common example.

## Cisco PIX/ASA

A BGP MD5 authentication may fail if the TCP connection passes through a Cisco PIX/ASA.  In addition to the need not to perform NAT described above, two other configuration parameters of the PIX/ASA can prevent successful MD5 authentication for packets that traverse the PIX/ASA.

1. Cisco PIX/ASA with software version 6.0 and higher by default randomizes both the sequence and the acknowledgement numbers in TCP headers before forwarding packets.  As indicated above, alteration of sequence numbers will result in an MD5 authentication error.  To use BGP MD5 authentication through a Cisco PIX/ASA, disable random-number sequencing for the router’s TCP connections to the ThousandEyes route collector, or if necessary disable random-number sequencing globally.  See the Cisco article [ASA/PIX: BGP through ASA Configuration Example](http://www.cisco.com/c/en/us/support/docs/ip/border-gateway-protocol-bgp/6500-bgp-pix.html#md5auth) for configuration options and additional details or contact the Cisco Technical Assistance Center.
2. Cisco PIX/ASA with software version 7.0 or greater by default overwrites the information in the TCP options field used by the BGP MD5 algorithm.  The PIX/ASA firewall replaces the 18 bytes of the kind \(1 byte\), length \(1 byte\), and MD5 Hash \(16 bytes\) with TCP No Operation \(NOP\) option bytes. Since the packet no longer has the needed BGP MD5 authentication credentials, the receiver drops the packet, and may log an error such as:

```text
*Sep 21 00:025:16.427: %TCP-6-BADAUTH: No MD5 digest from 10.10.10.10(23217) to 10.10.10.2(179)
```

## Summary

To troubleshooting BGP peering with ThousandEyes make sure to:

* **Review BGP peering configuration**
* **Check firewall/packet filter rules**
* **Disable NAT**
* **Disable TCP random number sequencing**
* **Disable TCP MD5 rewriting**

