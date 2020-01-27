# CLI network troubleshooting utilities

ThousandEyes provides a full suite of terminal based Network, DNS, and Voice utilities. These utilities come from the same code base that our Agents use to perform tests, and provide enhanced insight during troubleshooting.  
 

## Installing CLI Network Troubleshooting Utilities

The ThousandEyes Utilites Suite is bundled within the te-agent-utils package and is available for any host running a [supported Linux distribution](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnoKAC_Supported-Enterprise-Agent-operating-systems).

ThousandEyes repositories are automatically added to a host's package manager during [Enterprise Agent](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmnbKAC_What-is-an-Enterprise-Agent?) installation. Hosts without an Enterprise Agent will require manual installation of a ThousandEyes software package repository.  

### Installation for Ubuntu 16.04

#### Install the ThousandEyes APT repository

 Add the ThousandEyes repository

```text
sudo apt-add-repository https://apt.thousandeyes.com
```

 Add the ThousandEyes signing key

```text
sudo wget -q https://apt.thousandeyes.com/thousandeyes-apt-key.pub -O- | sudo apt-key add -
```

 Changes will be applied during the update process

```text
sudo apt-get update
```

 If the key has been properly added it will be listed as a trusted key

```text
~# sudo apt-key list

/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   4096R/C0B21F32 2012-05-11
uid                  Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>

pub   4096R/EFE21092 2012-05-11
uid                  Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   2048R/BE718900 2012-08-13
uid                  ThousandEyes <builduser@thousandeyes.com>

~#
```

#### Install the te-agent-utils software package

```text
sudo apt-get install te-agent-utils
```

### Installation for RedHat 7, CentOS 7, and Oracle Linux 7

#### Install the ThousandEyes YUM repository

 Add the ThousandEyes repository

```text
sudo yum-config-manager --add-repo https://yum.thousandeyes.com/CentOS/7/x86_64   # CentOS 7
sudo yum-config-manager --add-repo https://yum.thousandeyes.com/RHEL/7/x86_64     # RHEL 7
```

 Add the ThousandEyes signing key

```text
cd /etc/pki/rpm-gpg/
sudo wget -q https://yum.thousandeyes.com/RPM-GPG-KEY-thousandeyes
```

 Changes will be applied during the update process

```text
sudo yum update
```

 Check the GPG key

```text
sudo gpg --quiet --with-fingerprint /etc/pki/rpm-gpg/RPM-GPG-KEY-thousandeyes
```

 The ThousandEyes key fingerprint should be as follows

```text
pub 2048R/BE718900 2012-08-13 ThousandEyes <builduser@thousandeyes.com> Key fingerprint = AA5F BA03 CE4E F309 B7E3 D4E1 C99A 15F5 BE71 8900
```

#### Install the te-agent-utils software package

```text
sudo yum install te-agent-utils
```

## Network Utilities

### te-ping

A replacement for traditional ping, and can be run in a number of different application protocol modes.  te-ping includes options to run in SACK, SYN, ICMP and VoIP modes, designed for use with different types of targets, and is consistent with the way that ThousandEyes measures end-to-end metrics in Network tests.  Outputs include Loss, Latency and Jitter.  Requires sudo permissions.

#### Syntax & Options

\(sudo\) te-ping \[options\] &lt;target-ip&gt; 

| **Parameter** | **Description** |
| :--- | :--- |
| target-ip | IP address or DNS name of the target machine. |

| **Option \(short\)** | **Option \(long\)** | **Description** | **Default Value** |
| :--- | :--- | :--- | :--- |
| -h | --help | displays usage instructions | n/a |
|  | --source-port | source port to be used for the test, do not use in icmp mode | &lt;random value&gt; |
| -p  | --port | destination port for the probe, do not use in icmp mode | 80 |
| -c | --count | number of packets to be sent by the test  | 50 |
| -I | --interval | initial maximum interval between packets \(in ms\) | 40 |
| -i | --interface | interface name to use for the test \(use in conjunction with --source-ip option\) | any |
| -s | --source-ip | source IP address \(use in conjunction with the --interface option\) | n/a |
| -M | --mode  | transmission mode for the test; accepts **sack**, **syn**, **icmp, rtp** \(UDP+RTP\)**, or sip** options  | sack |
| -v | --verbose | verbosity of the test;  short command accepts -v \(verbose\) or -vv \(very verbose\), -vvv \(very very verbose\) | n/a |

#### Example

```text
$ sudo te-ping -i eth0 74.125.225.176
```

```text
--- 74.125.225.176 ping statistics ---
50 packets transmitted, 50 received, 0.0% packet loss
rtt min/avg/max/mdev = 68.00/69.42/71.00/0.58 ms
```

```text
$ sudo te-ping -c 25 thousandeyes.com
```

```text
--- 54.215.17.122 ping statistics ---
25 packets transmitted, 25 received, 0.0% packet loss
rtt min/avg/max/mdev = 5.00/5.68/6.00/0.44 ms
```

###  te-pathtrace

Runs a traceroute, using the same methods as are used by ThousandEyes to the endpoint.  In addition to obtaining the IP addresses transited by each probe, our code shows quoted-ttl, response-ttl and MPLS label values for each probe.  Since each agent test runs 3 probes \(test attempts\) to the target, if you want consistent results with that of the agent, run with option -P 3, to obtain three sets of trace data.  Requires sudo permissions.  Note in the example shown that the path to the same target IP diverges in two separate trace requests from the same target, at hop \# 4 \(shown in bold for emphasis\).  Using the Paris-traceroute algorithm \(which is used by ThousandEyes in our Path Visualization view\), this would show a path split, as in the image shown below.

IMAGE MISSING

#### Syntax & Options

\(sudo\) te-pathtrace \[options\] &lt;target-ip&gt; 

| **Parameter** | **Description** |
| :--- | :--- |
| target-ip | IP address or DNS name of the target machine. |

| **Option \(short\)** | **Option \(long\)** | **Description** | **Default Value** |
| :--- | :--- | :--- | :--- |
| -h | --help | displays usage instructions | n/a |
|  | --source-port | source port to be used for the test, do not use in icmp mode | &lt;random value&gt; |
| -p | --port  | destination port for the probe, do not use in icmp mode | 80 |
| -w | --wait-time | how long to wait for each probe reply \(in ms\) | 1000 |
| -g | --gap-limit  | maximum number of consecutive unresponsive hops before stopping  | 6 |
| -l | --max-loops | number of times the same IP can be encountered before stopping | 2 |
| -P | --paths | number of parallel paths to trace | 1 |
| -i | --interface  | network interface to use for this test \(use in conjunction with --source-ip option\) | any |
| -M | --mode  | transmission mode to use for the test; accepts **tcp, sack, icmp, rtp,** or **sip.**  | tcp |
| -v | --verbose | verbosity level, accepts -v \(verbose\), -vv \(very verbose\), -vvv \(very very verbose\)  | n/a |

#### Example

```text
$ sudo te-pathtrace -i eth0 -P 2 74.125.225.176
```

```text
Tracing 2 paths from 192.168.1.209 to 74.125.224.176:80...
1 192.168.1.1 (0 ms), q-ttl=1, icmp=(11-0), r-ttl=64 
2 71.119.37.1 (19 ms), q-ttl=1, icmp=(11-0), r-ttl=126 
3 130.81.195.70 (26 ms), q-ttl=1, icmp=(11-0), r-ttl=253 
4 130.81.29.126 (22 ms), q-ttl=1, icmp=(11-0), r-ttl=252 <MPLS:L=471833,E=0,S=1,T=1>
5 140.222.227.21 (26 ms), q-ttl=1, icmp=(11-0), r-ttl=251 <MPLS:L=562169,E=0,S=1,T=1>
6 152.63.114.229 (27 ms), q-ttl=1, icmp=(11-0), r-ttl=250 
7 *
8 216.239.46.40 (59 ms), q-ttl=1, icmp=(11-0), r-ttl=249 t
9 64.233.174.186 (58 ms), q-ttl=1, icmp=(11-0), r-ttl=249 <MPLS:L=649764,E=4,S=1,T=1>
10 216.239.46.154 (72 ms), q-ttl=1, icmp=(11-0), r-ttl=245 <MPLS:L=353169,E=4,S=1,T=1>
11 216.239.46.147 (89 ms), q-ttl=1, icmp=(11-0), r-ttl=245 
12 209.85.251.9 (71 ms), q-ttl=1, icmp=(11-0), r-ttl=245 
13 74.125.225.176 (70 ms), q-ttl=0, icmp=(0-0), r-ttl=53 

1 192.168.1.1 (0 ms), q-ttl=1, icmp=(11-0), r-ttl=64 
2 71.119.37.1 (20 ms), q-ttl=1, icmp=(11-0), r-ttl=126 
3 130.81.195.70 (22 ms), q-ttl=1, icmp=(11-0), r-ttl=253 
4 130.81.199.40 (22 ms), q-ttl=1, icmp=(11-0), r-ttl=252 <MPLS:L=471833,E=0,S=1,T=1>
5 140.222.227.21 (25 ms), q-ttl=1, icmp=(11-0), r-ttl=251 <MPLS:L=562169,E=0,S=1,T=1>
6 152.63.115.246 (25 ms), q-ttl=1, icmp=(11-0), r-ttl=250 
7 *
8 64.233.174.238 (24 ms), q-ttl=1, icmp=(11-0), r-ttl=249 
9 64.233.174.192 (41 ms), q-ttl=1, icmp=(11-0), r-ttl=249 <MPLS:L=595852,E=4,S=1,T=1>
10 216.239.46.152 (73 ms), q-ttl=1, icmp=(11-0), r-ttl=245 <MPLS:L=645961,E=4,S=1,T=1>
11 216.239.46.145 (73 ms), q-ttl=1, icmp=(11-0), r-ttl=245 
12 209.85.251.9 (71 ms), q-ttl=1, icmp=(11-0), r-ttl=245 
13 74.125.225.176 (70 ms), q-ttl=0, icmp=(0-0), r-ttl=53 
```

###  te-pathmtu

Designed to quickly interrogate the path between your test endpoint and the target.  The command will find the smallest allowed MTU on the path between the endpoints, allowing inference of certain types of tunnels, or misconfigurations of MTU size on routers between the endpoints.  By default, the MTU is 1500 bytes.

#### Syntax & Options

\(sudo\) te-pathmtu \[options\]  &lt;target-ip&gt; 

| **Parameter** | **Description** |
| :--- | :--- |
| target-ip | IP address of the target machine or DNS name of target machine. |

| **Option \(short\)** | **Option \(long\)** | **Description** | **Default Value** |
| :--- | :--- | :--- | :--- |
| -h | --help | displays usage instructions | n/a |
|  | --source-port | source port to be used for the test, do not use in icmp mode | &lt;random value&gt; |
| -p | --port  | destination port for the probe, do not use in icmp mode | 80 |
| -w | --wait-time | how long to wait for each probe reply \(in ms\) | 1000 |
| -m | --max-mtu | the maximum possible transmission unit of the output interface \(in bytes\) | 1500 |
| -P | --paths | number of parallel paths to trace | 1 |
| -i | --interface  | network interface to use for this test \(use in conjunction with --source-ip option\) | any |
| -s | --source-ip | source IP address \( use in conjunction with --interface option\) | n/a |
| -M | --mode  | transmission mode to use for the test; accepts **tcp, icmp, rtp,** or **sip** | tcp |
| -v | --verbose | verbosity level, accepts -v \(verbose\), -vv \(very verbose\) -vvv \(very very verbose\) | n/a |

#### Example

```text
$ sudo te-pathmtu -i eth0 98.139.183.24
```

```text
Looking up path MTU from 89.187.112.188 to 98.139.183.24:80 
 Path MTU: 1500
```

###  te-bw

Designed as a replacement for iPerf, te-bw allows measurement of bandwidth, while having control of a single endpoint, and without the need to have exclusive access to the pipe.   Use te-bw to measure estimated capacity, and available bandwidth on the pipe between the endpoint and target.  Requires sudo permissions.  When measuring bandwidth, te-bw shows the limiting bandwidth for UPSTREAM communication from the endpoint \(ability of the endpoint to send data to the target\), and DOWNSTREAM bandwidth from the target \(ability for the target to send data to the endpoint\).  This is an important point for servers behind asymmetric links, such as ADSL.

#### Syntax & Options

\(sudo\) te-bw \[options\] &lt;target-ip&gt; 

| **Parameter** | **Description** |
| :--- | :--- |
| target-ip | IP address or DNS name of the target machine. |

| **Option \(short\)** | **Option \(long\)** | **Description** | **Default Value** |
| :--- | :--- | :--- | :--- |
| -h | --help | displays usage instructions | n/a |
| -p | --port | destination port on the target.  Do not use in icmp mode | &lt;random value&gt;  |
| -j | --jitter | mean deviation of the round trip time \(in μs\)  | if not specified, will be calculated by running  an initial ping against the target |
| -z | --probe-size | maximum size of the probe packets \(in bytes\)  | 1440 |
|  -c | --capacity | capacity of the link \(in Mbps\), 0=unlimited. | if not specified, will be calculated by running  an initial calculation against the target |
| -s | --source-ip | source IP address \( use in conjunction with --interface option\) | n/a |
| -T | --timeout | timeout for the test to complete \(in secs\) , 0 = unlimited | 10 |
| -v | --verbose | verbosity level, short option accepts -v \(verbose\), -vv \(very verbose\), -vvv \(very very verbose\) | n/a  |
| -i | --interface | network interface to use for the test \(use in conjunction with --source-ip option\) | any |
| -M | --mode | transmission mode to use for the test; accepts **icmp** or **tcp** | tcp |

#### Example

```text
$ sudo te-bw -i eth0 192.168.1.209 74.125.225.176
```

```text
Running ping task to estimate jitter
80 bytes from 74.125.225.176: tcp_req=1 ttl=52 time=115 ms
80 bytes from 74.125.225.176: tcp_req=2 ttl=52 time=115 ms
80 bytes from 74.125.225.176: tcp_req=3 ttl=52 time=115 ms
80 bytes from 74.125.225.176: tcp_req=4 ttl=52 time=115 ms
80 bytes from 74.125.225.176: tcp_req=5 ttl=52 time=115 ms
80 bytes from 74.125.225.176: tcp_req=6 ttl=52 time=115 ms
80 bytes from 74.125.225.176: tcp_req=7 ttl=52 time=115 ms
80 bytes from 74.125.225.176: tcp_req=8 ttl=52 time=115 ms
80 bytes from 74.125.225.176: tcp_req=9 ttl=52 time=115 ms
80 bytes from 74.125.225.176: tcp_req=10 ttl=52 time=115 ms

--- 74.125.225.176 ping statistics ---
10 packets transmitted, 10 received, 0.0% packet loss
rtt min/avg/max/mdev = 115.00/115.00/115.00/0.00 ms

Capacity
========================================
Estimated rate: 96.1 Mbps +/-0
Data sent:      8.80 KB
Probe size:     1420 B
Wall time:      3.59 secs
PCap stats:     200/0 pkts
Return code:    0 ()
========================================

Available bandwidth
========================================
Estimated rate: 78.0 Mbps +/-8
Data sent:      50.60 KB
Probe size:     1420 B
Wall time:      4.34 secs
PCap stats:     1150/0 pkts
Return code:    0 ()
========================================
```

## DNS Utilities

### te-dns-trace

A special version of dig +trace which follows CNAME records across zones, in order to get to the requested record type.  This is the same logic as is followed using the DNS Domain Trace test inside ThousandEyes.  In addition, you'll receive more verbose feedback when the trace attempt is unsuccessful at retrieving records from an authoritative server, before the request fails over to a subsequent server.  In the example shown below for www.healthcare.gov A, notice how the trace is followed from CNAME retrieved from the .gov zone, to Akamai, where the ultimate A record resides.  A standard dig +trace request would stop at the line shown in bold.  Does not require sudo permissions.

#### Syntax & Options

\(sudo\) te-dns-trace &lt;domain&gt; \[type\]

| **Parameter** | **Description** | **Required?** | **Default Value** |
| :--- | :--- | :--- | :--- |
| domain | domain name to look up  | Y | n/a |
| type | DNS record type | N | A |

#### Example

```text
$ sudo te-dns-trace www.healthcare.gov A
```

```text
gov.      172800  IN      NS      b.gov-servers.net.
gov.    172800  IN      NS      a.gov-servers.net.
;; Received 143 bytes from 198.41.0.4(a.root-servers.net.) in 25 ms

healthcare.gov. 86400   IN      NS      eur5.akam.net.
healthcare.gov. 86400   IN      NS      usc3.akam.net.
healthcare.gov. 86400   IN      NS      use2.akam.net.
healthcare.gov. 86400   IN      NS      use4.akam.net.
healthcare.gov. 86400   IN      NS      usw2.akam.net.
healthcare.gov. 86400   IN      NS      asia1.akam.net.
healthcare.gov. 86400   IN      NS      ns1-78.akam.net.
healthcare.gov. 86400   IN      NS      ns1-252.akam.net.
;; Received 202 bytes from 209.112.123.30(b.gov-servers.net.) in 23 ms

www.healthcare.gov.     120     IN      CNAME   www.geodirector.hc.gov.akadns.net.
;; Received 83 bytes from 23.74.25.64(eur5.akam.net.) in 72 ms

net.    172800  IN      NS      m.gtld-servers.net.
net.    172800  IN      NS      l.gtld-servers.net.
net.    172800  IN      NS      k.gtld-servers.net.
net.    172800  IN      NS      j.gtld-servers.net.
net.    172800  IN      NS      i.gtld-servers.net.
net.    172800  IN      NS      h.gtld-servers.net.
net.    172800  IN      NS      g.gtld-servers.net.
net.    172800  IN      NS      f.gtld-servers.net.
net.    172800  IN      NS      e.gtld-servers.net.
net.    172800  IN      NS      d.gtld-servers.net.
net.    172800  IN      NS      c.gtld-servers.net.
net.    172800  IN      NS      b.gtld-servers.net.
net.    172800  IN      NS      a.gtld-servers.net.
;; Received 508 bytes from 198.41.0.4(a.root-servers.net.) in 27 ms

akadns.net.     172800  IN      NS      ns1-129.akadns.net.
akadns.net.     172800  IN      NS      ns2-129.akadns.net.
akadns.net.     172800  IN      NS      ns17-133.akadns.org.
akadns.net.     172800  IN      NS      a3-129.akadns.net.
akadns.net.     172800  IN      NS      a11-129.akadns.net.
akadns.net.     172800  IN      NS      a9-128.akadns.net.
akadns.net.     172800  IN      NS      a5-130.akadns.org.
akadns.net.     172800  IN      NS      a4-131.akadns.org.
akadns.net.     172800  IN      NS      a10-128.akadns.org.
akadns.net.     172800  IN      NS      a28-129.akadns.org.
;; Received 358 bytes from 192.55.83.30(m.gtld-servers.net.) in 80 ms

www.geodirector.hc.gov.akadns.net.      120     IN      CNAME   production.healthcare.gov.edgekey.net.
;; Received 99 bytes from 193.108.88.129(ns1-129.akadns.net.) in 72 ms

edgekey.net.    172800  IN      NS      ns1-66.akam.net.
edgekey.net.    172800  IN      NS      usw6.akam.net.
edgekey.net.    172800  IN      NS      use9.akam.net.
edgekey.net.    172800  IN      NS      adns1.akam.net.
edgekey.net.    172800  IN      NS      adns2.akam.net.
edgekey.net.    172800  IN      NS      adns3.akam.net.
edgekey.net.    172800  IN      NS      adns4.akam.net.
edgekey.net.    172800  IN      NS      ns4-66.akam.net.
edgekey.net.    172800  IN      NS      ns4-67.akam.net.
edgekey.net.    172800  IN      NS      ns7-65.akam.net.
edgekey.net.    172800  IN      NS      ns7-66.akam.net.
edgekey.net.    172800  IN      NS      ns5-66.akam.net.
edgekey.net.    172800  IN      NS      ns5-64.akam.net.
;; Received 497 bytes from 192.55.83.30(m.gtld-servers.net.) in 81 ms

production.healthcare.gov.edgekey.net.  21600   IN      CNAME   e8132.dscb.akamaiedge.net.
;; Received 91 bytes from 193.108.91.66(ns1-66.akam.net.) in 23 ms

akamaiedge.net. 172800  IN      NS      la1.akamaiedge.net.
akamaiedge.net. 172800  IN      NS      la6.akamaiedge.net.
akamaiedge.net. 172800  IN      NS      la7.akamaiedge.net.
akamaiedge.net. 172800  IN      NS      la3.akamaiedge.net.
akamaiedge.net. 172800  IN      NS      lar6.akamaiedge.net.
akamaiedge.net. 172800  IN      NS      lar2.akamaiedge.net.
akamaiedge.net. 172800  IN      NS      ns3-194.akamaiedge.net.
akamaiedge.net. 172800  IN      NS      ns2-194.akamaiedge.net.
akamaiedge.net. 172800  IN      NS      ns4-194.akamaiedge.net.
akamaiedge.net. 172800  IN      NS      ns6-194.akamaiedge.net.
akamaiedge.net. 172800  IN      NS      ns7-194.akamaiedge.net.
akamaiedge.net. 172800  IN      NS      ns5-194.akamaiedge.net.
akamaiedge.net. 172800  IN      NS      ns1-1.akamaiedge.net.
;; Received 497 bytes from 192.55.83.30(m.gtld-servers.net.) in 80 ms

dscb.akamaiedge.net.    21600   IN      NS      n3dscb.akamaiedge.net.
dscb.akamaiedge.net.    43200   IN      NS      n2dscb.akamaiedge.net.
dscb.akamaiedge.net.    32400   IN      NS      n4dscb.akamaiedge.net.
dscb.akamaiedge.net.    32400   IN      NS      n7dscb.akamaiedge.net.
dscb.akamaiedge.net.    32400   IN      NS      n1dscb.akamaiedge.net.
dscb.akamaiedge.net.    21600   IN      NS      n6dscb.akamaiedge.net.
dscb.akamaiedge.net.    43200   IN      NS      n5dscb.akamaiedge.net.
dscb.akamaiedge.net.    21600   IN      NS      n0dscb.akamaiedge.net.
;; Received 339 bytes from 184.26.161.192(la1.akamaiedge.net.) in 23 ms

e8132.dscb.akamaiedge.net.      20      IN      A       23.43.186.194
;; Received 59 bytes from 63.217.8.179(n3dscb.akamaiedge.net.) in 40 ms
```

### te-sigchase

Provides DNSSEC keychain validation \(using bottom-up method\) for the target record type.  Requires that DNSSEC extensions are supported by routers used by the endpoint. See http://www.icann.org/en/groups/ssac/documents/sac-035-en.pdf for a list of devices which do not currently support required extensions for DNSSEC compatibility.  Outputs of DNSSEC keychain validation will be the Data Chain, and Trust Tree responses for the validation request, similar to that which is shown in the output of DNSSEC tests in ThousandEyes.  Does not require sudo permissions.

#### Syntax & Options

\(sudo\) te-sigchase &lt;domain&gt; \[type\] \[key-file\]

| **Parameter** | **Description** | **Required?** | **Default Value** |
| :--- | :--- | :--- | :--- |
| domain | domain name to validate | Y | n/a |
| type | record type to validate | N | A |
| key-file | key file used for validation of root server signatures | N | A key file is provided and maintained with the te-agent-utils package.   To view the content of the file, look at /var/lib/te-agent-utils/dns-rootserver.key |

#### Example

```text
$ sudo te-sigchase www.fbi.gov A
```

```text
Data chain: 
;; rcode: NOERROR
;; qtype: DNSKEY
rrset:
.       172800  IN      DNSKEY  256 3 8 AwEAAb8sU6pbYMWRbkRnEuEZw9NSir707TkOcF+UL1XiK4NDJOvXRyX195Am5dQ7bRnnuySZ3daf37vvjUUhuIWUAQ4stht8nJfYxVQXDYjSpGH5I6Hf/0CZEoNP6cNvrQ7AFmKkmv00xWExKQjbvnRPI4bqpMwtHVzn6WybBZ6kuqED ;{id = 33655 (zsk), size = 1024b}
.       172800  IN      DNSKEY  257 3 8 AwEAAagAIKlVZrpC6Ia7gEzahOR+9W29euxhJhVVLOyQbSEW0O8gcCjFFVQUTf6v58fLjwBd0YI0EzrAcQqBGCzh/RStIoO8g0NfnfL2MTJRkxoXbfDaUeVPQuYEhg37NZWAJQ9VnMVDxP/VHL496M/QZxkjf5/Efucp2gaDX6RS6CXpoY68LsvPVjR0ZSwzz1apAzvN9dlzEheX7ICJBBtuA6G3LQpzW5hOA2hzCTMjJPJ8LbqF6dsV6DoBQzgul0sGIcGOYl7OyQdXfZ57relSQageu+ipAdTTJ25AsRTAoub8ONGcLmqrAmRLKBP1dfwhYB4N7knNnulqQxA+Uk1ihz0= ;{id = 19036 (ksk), size = 2048b}
sigs:
.       172800  IN      RRSIG   DNSKEY 8 0 172800 20140125235959 20140111000000 19036 . StojN0w3tpyJ6VR+ShcnuekubPXIS/8PHHtp6zJ1mEC/EyUNmGiIN9sEt4jl2yV72saerP6dHXrROceXHFDaGoIN2ge9wdOmzOuKu3zjlvgeUNVcLuzmJFIcPGOkX0vms1dLhEjElM1bBbXRGA8hLAOjbH/sccRSRabLiwpWBT42Gq9o4a1wU6pJhNkQc9nW60zyzLa1PCC+QFRIG53ENBFL1fub8cNjpzBH40RVLmynb4PgzulodAtRM1Rs6z7X8esfOP2dsVE+8ZkY2KzFS6cz5Xw/GkQ3vdiIOJt/QYJ5ZhytkEjPUOV8w01B5mU49qGzMkjW6solFzI3OSde4Q==
---
;; rcode: NOERROR
;; qtype: DS
rrset:
gov.    86400   IN      DS      7698 8 2 6bc949e638442ead0bdaf0935763c8d003760384ff15ebbd5ce86bb5559561f0
gov.    86400   IN      DS      7698 8 1 6f109b46a80cea9613dc86d5a3e065520505aafe
sigs:
gov.    86400   IN      RRSIG   DS 8 1 86400 20140127000000 20140119230000 33655 . GiRstE42TXAFs/76q+l+ED4WlrqWFS/qJWIzwQbSst5OpCsDuO2SMkJKuu8vWikYwVNrNdGJ4Jody1oYQWMKfXpirAqOVWOb3gpmoUgGn4O/c09xh1fRHx4TZ1gvg2rhit0UFiqrwPf5+aidXhU4O73ZY0A6o7IV1c6DCRPwlqo=
---
;; rcode: NOERROR
;; qtype: DNSKEY
rrset:
gov.    3600    IN      DNSKEY  257 3 8 AQO8daaz7B+yshOfL60rytKd9aOSujgponEw3fwBMEC3/+e9XzHw2k+VKnbJTZ+QaVtpfUd1q9HKZIv/ck83Gl5TjYKE5jtUZ2kpEDZfVNGv6yx0smtWAXv1nCJS9ohnyOTd397eMojGDHqkEC+uojEScZheEkMxzgCZwDAs+/CSU7mSuHtCRZn19xlZUd5Gv7yDQ3mbOUwuy30oSk0z1Q5UUPpoihOugIZHFX6Jk7NLiW2wlqfq9qhV4zj7TiBiJY0mCc4zHN8/aq2VKDHp2Na7mWzvKyTy+SYQkBQ/08LbPwj9YMc+uCzKL6sU/ObHv17EFhD8aPDftTHZvV9L+OZr ;{id = 7698 (ksk), size = 2048b}
gov.    3600    IN      DNSKEY  256 3 8 AQPUPnOmrICUKGXz/F17uwcAUDaOpSzXtYyVppfFKLCstRguG7MniUDQ7/T5kf+tV7EPcVXca4iJc5WPhKQxCW7O0mSVElgJTbZTgOPpl5TCDYNRLdas7XzJsxadv2FIdQeVopD3tlxgsiB3M1epVEyCS9SxPhEgStLb1A/CnkCYNw== ;{id = 51929 (zsk), size = 1024b}
gov.    3600    IN      DNSKEY  256 3 8 AQPXzCGIOpznwWOcAVVA4J0lUvtY+K9sEETwbUl8uoh4tmREv2PkfBFID3aL5Nyl3MUrCN6UsP+Tvu+Yj6pi7DEBhOHMxItwocix9cu9VxstQMQ2U2NYs1unUD77W5PmN/000hA4lQS/JrD89XfrmRv2zHPRzw5AsdrfVLm1K0rb+w== ;{id = 46733 (zsk), size = 1024b}
sigs:
gov.    3596    IN      RRSIG   DNSKEY 8 1 86400 20140128224731 20140113224231 7698 gov. UdHmEpD0jhpyM5QSI4Te4XYIoPYZiLLN2TvYt56rXDTrmClHNb2WfI5XyDzqAMhOlGvGF9vvkxCK+rxle3OTbKKKWzVzPhxQKDXCAB5ixvR5Mhu7yiH2T4W9FNo7EpyNQ3iI6y3/1SuoExhtgmC2fi0ajF2PkQgj6t+2G1bHJrcMxA9dbwf6ZSZF8JBTdVrW0rjSduAAccQ8URwZx54cF4aMI6idrq0XnFAcnIhw8oGu0EesKCgE3GAuMBtPRINMIFaEAqGGh5g07gOn2gu4I/JFRh5Ni2XCyG08FwbgL8sbTF0qJGr4wpWnzkr42dSQCmk/k0GabzYwAIPt0JNJnQ==
---
;; rcode: NOERROR
;; qtype: DS
rrset:
fbi.gov.        3600    IN      DS      60816 7 2 dafec16d6066c3b7086e27015061674570572819b3d9c79aeb4cd9d8f44889f6
fbi.gov.        3600    IN      DS      24840 7 1 1a587e6ffaf669448d6cef00403e3b91a9b33916
fbi.gov.        3600    IN      DS      24840 7 2 0c31ebaed7f6a22619eadd082417ab38fa4b4af871fd6507f040cd916b098d18
fbi.gov.        3600    IN      DS      60816 7 1 938e49efccdd177417b0c252c8c706b3108f6f79
sigs:
fbi.gov.        3600    IN      RRSIG   DS 8 2 3600 20140127160024 20140120160024 51929 gov. AABChEniI48Iiy5j47ZzUSiflNt8ksxJITw6xK021GKhm+qAfewtP/g50FDPFFw/ys51s9UNYmSRgS/Yx0qCX8TMZ7R/0mg3zlLeVm+iJIUdhaEHNLu8ZWYotmkDv6yM8lmNiMFVBQF30XVeXcni8eOFxu6d/+XCyWiNAi9dGFw=
---
;; rcode: NOERROR
;; qtype: DNSKEY
rrset:
fbi.gov.        600     IN      DNSKEY  256 3 7 BQEAAAAB17UX5M/RKhkRgfUM4GYr+wCTTfLpe232895mX0GH/3R2SnYFTTCEPF7hNF5nkt6yW57fs1wt8/FrdQom7lRLZhgaZdXHGNSbLraq8jMAq9CmNvoNzhoiXbOUdwf2Hw2zcrozYgAoEfxeX0cCf5je4DSRkwEHZ7L+t2y15M9WwZk= ;{id = 58969 (zsk), size = 1024b}
fbi.gov.        600     IN      DNSKEY  257 3 7 AwEAAcbqigwPaVWRtu5tXoSIHRnjafvgHIKVo/I1nWZpCgCgGEwy6AZ4+OxktFgaVtVEIqNyeeCM9pkjly1isnwZDcWRHbzwmJ3dgKfnml8c5GIJnPp+4NcUHh8YzV+NAurNxaOWp7VDgJRuUejkyKNStia8B4WgcHK26ztGjy6wA/lkVUmea0H/EawqxrolACAD44kYjSpHxTx2dLeoqLfA4BR38aVCT8QTR6jb0Prt2x3v5bGxsW8nv9EvYZOYJHxzhZ6qoPKTCSFpXbPJvJRe/OQpIM+oANQzqPJtnnXNQqa72bJz4xZ4ybZo5tDbqEbY9i/i1KfZxxin01tz1Sk8o8M= ;{id = 24840 (ksk), size = 2048b}
fbi.gov.        600     IN      DNSKEY  257 3 7 AwEAAco9GtgN9u27gk77N3mrGDJ/ifCuPjJVba6bNnEqcamqf/Zhz5ysspP2LuQN2Grn1neWPLNZxi/fIzQDw+r3fUw8++W28AXt4nH+7J3vmySBX+kEwCXuzhigxXWHnh6TawVDmKFHAh/VOqFjXVRvOBW18S4PJ+ee+AwOtQh60tNuPNBVQvNkuOrG6q1o1OnLYyP9dKkcEK7FwH6lo11qNhwq8z6VFgQV7Kc1RxPiKEI/22GCFlzzyqTdN3DGbwiwIMcgVeJWvOBhQRRjoF/VPZ0eEDqQAG8mFamTcz7YU7J0fmhRKnJxEnr/dNcDYgibDOpW/ZIDiDD2JX9BzJgPV/U= ;{id = 60816 (ksk), size = 2048b}
fbi.gov.        600     IN      DNSKEY  256 3 7 BQEAAAABo4psWp89WZYhcyU1e7HiJgURDcNSPRJigtcKjUZq+zm3smS++eQyjVDZQOWsQxyyCw/HF1sT/goY2VO7Nm6uQ7y/kxgGeTkTiQAkcJ9GEI30RHaWrdMlmFuMLHV0Hdf9OxuXqAxLdEjq4UcVz0C/L5y6KECIlrFwFA/PPsdbpZc= ;{id = 32497 (zsk), size = 1024b}
sigs:
fbi.gov.        593     IN      RRSIG   DNSKEY 7 2 600 20140205145352 20131107145352 24840 fbi.gov. lA986MS27bBKnX7eh7SltOHR9v/mtsHoQeIXzzfImghvfbZcl920RUVZk0byZOcIYq4xezY5eW4uHaBFQ+Ii2JypVhLT3kUks/PKRe1R3S+2Q9XMMTV3ArUtQfTwRvpSFCTJEoyWTE3bOQkbQdWjznyI6wyRARg/QS+v4J/2peVIsOAT5Zu9BbcpUkVVyxKA2uj72AAoH9la15oub1k9/2pUCKlZz+qNTVrJp2U0lV8tUij0YHE0gzoR3rYVQHmDd2xuGFPQj2oX9/im4LVsI1nyliXVKFSNht8CSGTKD5q7Q8rTaprQpptCDdmX1dqlv/hhycNNU66x7PiQEd2euQ==
fbi.gov.        593     IN      RRSIG   DNSKEY 7 2 600 20140205145352 20131107145352 32497 fbi.gov. FQmiZhw87K7RueZ9Bdu/MKn7A/SxCSUPEm3p+cAuK9ATbydaChgVF5YlWCceaVC0l8NRyePmKHouBMy9JocJh5sZkIZsFu0RRLezgd0h0UkMtyhvfivK7eIhFTbMrGgFnPUiS9JsFcBTQYb8KR6bhvIrSFv86CiuGhr96dzpX4g=
---
;; rcode: NOERROR
rrset:
www.fbi.gov.    598     IN      CNAME   www.fbi.gov.c.footprint6.net.
sigs:
www.fbi.gov.    598     IN      RRSIG   CNAME 7 3 600 20140205145352 20131107145352 32497 fbi.gov. WYmt4GrH4X8PLndOgSLy12MPlWzv85dS7HnSsIMCcqm54Ub66V1Bp/KgtFthUWNf7IMTAnk/X8cT2TXzffJ41I0SXXFdUlhi9WrQlUPTWzwbkKFxGICzzD6jpWPdXBJe/FMecSGwCFCdEPaL+9B5ZewzJk1XxQLlfE86hNQ7gKE=
---

Trust tree: 
www.fbi.gov. (CNAME)
|---fbi.gov. (DNSKEY keytag: 32497 alg: 7 flags: 256)
    |---fbi.gov. (DNSKEY keytag: 24840 alg: 7 flags: 257)
    |---fbi.gov. (DS keytag: 60816 digest type: 2)
    |   |---gov. (DNSKEY keytag: 51929 alg: 8 flags: 256)
    |       |---gov. (DNSKEY keytag: 7698 alg: 8 flags: 257)
    |       |---gov. (DS keytag: 7698 digest type: 2)
    |       |   |---. (DNSKEY keytag: 33655 alg: 8 flags: 256)
    |       |       |---. (DNSKEY keytag: 19036 alg: 8 flags: 257)
    |       |---gov. (DS keytag: 7698 digest type: 1)
    |           |---. (DNSKEY keytag: 33655 alg: 8 flags: 256)
    |               |---. (DNSKEY keytag: 19036 alg: 8 flags: 257)
    |---fbi.gov. (DS keytag: 24840 digest type: 1)
    |   |---gov. (DNSKEY keytag: 51929 alg: 8 flags: 256)
    |       |---gov. (DNSKEY keytag: 7698 alg: 8 flags: 257)
    |       |---gov. (DS keytag: 7698 digest type: 2)
    |       |   |---. (DNSKEY keytag: 33655 alg: 8 flags: 256)
    |       |       |---. (DNSKEY keytag: 19036 alg: 8 flags: 257)
    |       |---gov. (DS keytag: 7698 digest type: 1)
    |           |---. (DNSKEY keytag: 33655 alg: 8 flags: 256)
    |               |---. (DNSKEY keytag: 19036 alg: 8 flags: 257)
    |---fbi.gov. (DS keytag: 24840 digest type: 2)
    |   |---gov. (DNSKEY keytag: 51929 alg: 8 flags: 256)
    |       |---gov. (DNSKEY keytag: 7698 alg: 8 flags: 257)
    |       |---gov. (DS keytag: 7698 digest type: 2)
    |       |   |---. (DNSKEY keytag: 33655 alg: 8 flags: 256)
    |       |       |---. (DNSKEY keytag: 19036 alg: 8 flags: 257)
    |       |---gov. (DS keytag: 7698 digest type: 1)
    |           |---. (DNSKEY keytag: 33655 alg: 8 flags: 256)
    |               |---. (DNSKEY keytag: 19036 alg: 8 flags: 257)
    |---fbi.gov. (DS keytag: 60816 digest type: 1)
        |---gov. (DNSKEY keytag: 51929 alg: 8 flags: 256)
            |---gov. (DNSKEY keytag: 7698 alg: 8 flags: 257)
            |---gov. (DS keytag: 7698 digest type: 2)
            |   |---. (DNSKEY keytag: 33655 alg: 8 flags: 256)
            |       |---. (DNSKEY keytag: 19036 alg: 8 flags: 257)
            |---gov. (DS keytag: 7698 digest type: 1)
                |---. (DNSKEY keytag: 33655 alg: 8 flags: 256)
                    |---. (DNSKEY keytag: 19036 alg: 8 flags: 257)
```

## Voice Utilities

### te-rtp

Designed to initiate an instant voice call to a VoIP server. It includes options to choose different Differentiated Services Code Point \(DSCP\) and codec values. Voice packets are encapsulated by a Real Time Transport Protocol \(RTP\) header, followed by further encapsulation through the transport layer protocol UDP and then sent using IP

#### Syntax & Options

\(sudo\) te-rtp \[options\] &lt;target-ip&gt;

| **Parameter** | **Description** |
| :--- | :--- |
| target-ip | IP address of the VoIP server. |

| **Option \(short\)** | **Option \(long\)** | **Description** | **Default Value** |
| :--- | :--- | :--- | :--- |
| -h | --help | displays usage instructions | n/a |
|  | --source-port | source port to be used for the test | &lt;random value&gt; |
| -p  | --port | destination port for the probe | 5000 |
| -P | --paths | \# of paths to trace \(in parallel\) | 1 |
| -i | --interface | interface name to use for the test \(use in conjunction with --source-ip option\) | any |
| -s | --source-ip | source IP address \( use in conjunction with --interface option\) | n/a |
|  | --dscp | DSCP value to be used for the voice call | 0 = best effort |
|  | --codec | Audio codec value used for the VoIP call, 0=G.711, 1=G.722\_24, 2=G.722\_32 | 0 = G.711 |
| -d | --stream-duration | To run the voice test call for desired time in seconds. For each 5 seconds, 50 packets are sent to the server | 5 seconds |
| -o | --clock-offset | clock offset with the server | 0 |
| -v | --verbose | verbosity of the test;  short command accepts -v \(verbose\) or -vv \(very verbose\), -vvv \(very very verbose\) | n/a |

### te-server

Designed to open up a port on the local machine to allow communication with the VoIP client. The desired server port should be configured to accept UDP connections inbound. It is always the machine running the te-voipserver utility that logs the probe statistics.

#### Syntax & Options

\(sudo\) te-server \[options\]  &lt;local-port&gt;

| **Parameter** | **Description** |
| :--- | :--- |
| local-port | Port on which the sever listens for incoming VoIP connections \(UDP traffic\) |

| **Option \(short\)** | **Option \(long\)** | **Description** | **Default Value** |
| :--- | :--- | :--- | :--- |
| -h | --help | displays usage instructions | n/a |
|  | --stunner-host | host in which to reach the STUNNER server |  |
|  | --stunner-port | port in which to reach the STUNNER server |  |
| -6 | --ipv6 | use IPv6 instead of IPv4 | n/a |
| -j | --jitter | the size of the de-jitter buffer | 0.1000000001 secs |
|  | --check-nat | whether to check if the NAT allows hole punching \(only valid when using --stunner-host\)  | 1 |
|  | --agent-id | the agent id to use when connecting and authenticating to the STUNNER server | 0 |
| -v | --verbose | verbosity of the test;  short command accepts -v \(verbose\) or -vv \(very verbose\), -vvv \(very very verbose\) | n/a    |

#### Example

```text
user@ubuntu:~$ sudo te-server 49152
13 [0x7fab82d4c700] INFO te.pte null - ProbeTaskExecutor started.
65 [0x7fab82d4c700] INFO te.port_49152#1 null - port_49152 server task started.
```

```text
[user1@centos]$ sudo te-rtp 10.100.10.166 -p 49152
241 packets sent in 5000ms @96% of rate
```

```text
user@ubuntu:~$ sudo te-voipserver 49152
13 [0x7fab82d4c700] INFO te.pte null - ProbeTaskExecutor started.
Server listening at port 49152 on interface any
65 [0x7fab82d4c700] INFO te.port_49152#1 null - Voip server receiving streams at 0.0.0.0:49152
44435 [0x7fab82d4c700] INFO te.port_49152#1 null - Task/Client 0/0: round #1407879622 (G.711_64kbps): 482/0/0 (total/lost/discarded frames); wall time: 5001 @ 98% of desired rate; MOS: 4.4; OWD: 0.0; jitter(RTCP/PDV): 0.0/0.0;
```

**Note: The wall time accounts for the total time taken for the test to complete including the programmatically added time and/or time taken  
            for the resources to be made available.** 

