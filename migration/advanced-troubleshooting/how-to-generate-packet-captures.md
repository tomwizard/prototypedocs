# How to generate Packet Captures

When a test is reporting loss from a location that is difficult to trace, and doesn't appear on the path visualization associated with a specific node, the ThousandEyes team might request a packet capture in order to attempt to isolate the loss.

Depending on your operating system, there are several options to run a packet capture.  On linux distributions the relevant command to start capture is “tcpdump”.  On Windows distributions you can run “netsh”.  Packet captures can also be run using the network packet analyzer called “Wireshark” which has versions that work on all major platforms.  For additional reference the following links are available for these and other options:

* Ubuntu Manpage: [http://manpages.ubuntu.com/manpages/cosmic/man8/tcpdump.8.html](http://manpages.ubuntu.com/manpages/cosmic/man8/tcpdump.8.html)
* Netsh Command Syntax: [https://docs.microsoft.com/en-us/windows-server/networking/technologies/netsh/netsh-contexts](https://docs.microsoft.com/en-us/windows-server/networking/technologies/netsh/netsh-contexts)
* Wincap: [https://www.winpcap.org/](https://www.winpcap.org/)
* Wireshark: [https://www.wireshark.org/docs/wsug\_html\_chunked/ChapterIntroduction.html\#ChIntroWhatIs](https://www.wireshark.org/docs/wsug_html_chunked/ChapterIntroduction.html#ChIntroWhatIs)

Basically what happens, is you bind the capture to a specific interface, and capture packets passing through that interface.  The capture is run over a specific duration to get the required data.  Typically, the ThousandEyes team will request a capture over a period of approximately 30 minutes, in order to capture all relevant information.  Generating a packet capture on UNIX based systems is achieved running the command "**tcpdump**".  This document will provide instructions for obtaining packet captures using either tcpdump or Wireshark. 

### Determine which network interface to capture

To start, you need to first identify which ethernet interface is being used to connect the machine to the network.  In most cases, this will be eth0, but to check, run ifconfig on the host to identify the correct interface.

```text
dave@vm-dave-dev-1:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 08:00:27:69:f3:a6 
 inet addr:192.168.1.12 Bcast:192.168.1.255 Mask:255.255.255.0
 inet6 addr: fe80::a00:27ff:fe69:f3a6/64 Scope:Link
 UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
 RX packets:216561 errors:0 dropped:0 overruns:0 frame:0
 TX packets:44521 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:1000 
 RX bytes:127096906 (127.0 MB) TX bytes:3891185 (3.8 MB)

lo Link encap:Local Loopback 
 inet addr:127.0.0.1 Mask:255.0.0.0
 inet6 addr: ::1/128 Scope:Host
 UP LOOPBACK RUNNING MTU:16436 Metric:1
 RX packets:905 errors:0 dropped:0 overruns:0 frame:0
 TX packets:905 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:0 
 RX bytes:84115 (84.1 KB) TX bytes:84115 (84.1 KB)
dave@vm-dave-dev-1:~$
```

In this case, I only have one network interface bound, so I'm going to select that interface by appending -i eth0 to the command.  This will bind the capture to the eth0 interface, and capture all the traffic requested through that interface.

```text
tcpdump -i eth0
```

### Restricting capture to a specific host or port

If directed by the ThousandEyes team, you may be requested to reduce the amount of data being captured, by targeting a specific port or host in the request.  To restrict based on port, simply append port &lt;portnumber&gt;.  To restrict based on host, simply append host &lt;w.x.y.z&gt; to the command.  These can be done in tandem, if required; the following commands are all syntactically valid.

```text
tcpdump -i eth0 host 1.2.3.4
tcpdump -i eth0 host 1.2.3.4 port 80
tcpdump -i eth0 port 80 
```

### Writing output to file

We also don't want to interpret the information in real time, but rather capture it to a file that can be used by the ThousandEyes team, so we'll write to a file.  This is accomplished by appending a -w &lt;filename&gt; to the command.

```text
tcpdump -i eth0 host 1.2.3.4 port 80 -w myfilename
```

This command will generate a 1000MB file, as soon as the first one reaches limit tcpdump will start writing the second one and the loop continues. This is very helpful if we need to catch some event in packets.

```text
tcpdump -n -s0 -C 1000 -W2 -w file.pcap  
```

## Running the capture

Once you have the required commands, simply start the TCP dump with appropriate parameters.  Starting a TCP dump must usually be done in the context of the root user.  Running as a root user is not recommended, so the command sudo is often used to run in the context of a super user account.  Simply prepend sudo to the command to run a tcpdump with superuser permissions.

```text
sudo tcpdump -i eth0 host 1.2.3.4 port 80 -w myfilename
```

The capture will run until cancelled \(press ctrl-c to cancel\).  Once the tcp dump is stopped, the number of packets captured by the request will be shown:

```text
dave@vm-dave-dev-1:~$ sudo tcpdump -i eth0 -w mycapturefile
[sudo] password for dave: 
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
^C
85 packets captured
85 packets received by filter
0 packets dropped by kernel
```

### Compress the capture

Once the file has been created, it should be compressed for simplicity of transfer.  Simplest method of compression is to use gzip, which is bundled with linux distributions.  The syntax is gzip -c uncompressedfile &gt; targetfile.gz, which will create a compressed version of the file for email transmission.

```text
gzip -c mycapturefile > mycompressedfile.gz
```

Once the compressed file has been created, send it to the ThousandEyes team for analysis by emailing the gzipped version of the file to support@thousandeyes.com.

## **Running a Packet Capture from Windows using Wireshark**

Since not everybody has a Mac or Linux server to use, you may need to generate a TCP dump using Windows.  The easiest and most common approach to this is using Wireshark \(using a GUI\), documented below.

First, download WireShark.  This will install both the WireShark app and winpcap libraries - these are used to bind to a network adapter, and can be used to capture packets.  Download WireShark from http://www.wireshark.org

Once you've downloaded WireShark, install it and launch.  The great thing about Wireshark is that everything is controllable from a single interface.  Under the Capture menu, select Options. 

IMAGE MISSING

Select the interface you wish to capture by checking the appropriate box, choose appropriate name resolution options \(defaults are fine\), and ensure that the option for 'use pcap-ng format' is unchecked.  Once you're ready to start capturing packets, click the Start button.

Once you click the start button, WireShark will begin capturing packets, and display them in real time.  This will be a very busy, color-coded interface, which is moving fast.

Once you've captured enough data, click the stop button \(also found under Capture &gt; Stop\)

If you want to filter your capture to be based on a specific target IP address, click the Capture &gt; Capture Filters option.  This is a very rich expression builder; to target a specific host and port combination \(similar to the example above\) create a filter similar to the following:

```text
tcp.dstport == 80 and ip.addr == 1.2.3.4
```

Once you've applied the filter \(if applicable\), click File &gt; Save and save the capture file.  The save will take the applicable filter into account and will exclude any data not displayed in the filter list.  The packet capture file will be large, so always remember to compress the file before sending to ThousandEyes support.

