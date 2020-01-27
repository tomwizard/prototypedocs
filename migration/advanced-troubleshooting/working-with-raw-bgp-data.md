# Working with Raw BGP data

The purpose of this article is to facilitate analysis of raw BGP data collected by various public monitors.  From time to time, one might need to look at the raw aggregated BGP data in order to convince oneself that there's not something wrong, or that data collected by ThousandEyes is in fact correct.  \(It almost always is, but proof helps.\)

## Working with Quagga BGP RIB files

First, it's important to understand how our BGP data collection works, and where the data comes from.

* _Public monitors_ shown in ThousandEyes consume data aggregated by the University of Oregon's RouteViews project \([www.routeviews.org](http://www.routeviews.org/)\). We download routes collected by various [collectors]() maintained by the RouteViews project, process the data and display it for use.
* _Private monitors_ peer directly with a ThousandEyes-maintained route collector and provide updates in real time. Data from private monitors is not presently available for inspection/analysis.

The RouteViews project makes full routing information base \(RIB\) dumps of data available every 2 hours \(UTC time\), and provides updates every 15 minutes. These files are compressed in .bz2 format. Data for each monitor we display can be found on the RouteViews site, in the location shown by the [table]() at the bottom of this page.

To review raw BGP data, you'll need an application to parse the data. For this, we use bgpdump, which provides human-readable data from the raw BGP information.

### Installing and using BGPdump

Find compiled versions of bgpdump for OSX \([here](http://downloads.thousandeyes.com/bgpdump-OSX.zip)\) or Ubuntu Linux \([here](http://downloads.thousandeyes.com/bgpdump-UBUNTU.zip)\).

**Note:** **This is simply a compiled version of RIPE bgpdump, The project is maintained by RIPE NCC and the Internet Research community.  The project source is available at https://bitbucket.org/ripencc/bgpdump/wiki/Home.**

To install and run bgpdump, follow these instructions:

* Download the file, and extract the contents
* move the bgpdump file to /usr/local/bin/ \(which puts it in the path for your user\)
* chmod +x it, to make it executable
* test it, by running bgpdump.  The following information should be displayed

```text
$ bgpdump
2014-08-12 17:13:17 [info] logging to syslog
bgpdump version 1.4.99.14
Usage: bgpdump [-m|-M] [-t dump|-t change] [-O <output-file>] <input-file>
bgpdump translates binary MRT files (possibly compressed) into readable output
Output mode:
    -H         multi-line, human-readable (the default)
    -m         one-line per entry with unix timestamps
    -M         one-line per entry with human readable timestamps
    (there are other differences between -m and -M)
Common options:
    -O <file>  output to <file> instead of STDOUT
    -s         log to syslog (the default)
    -v         log to STDERR
Options for -m and -M modes:
    -t dump    timestamps for RIB dumps reflect the time of the dump (the default)
    -t change  timestamps for RIB dumps reflect the last route modification
Special options:
    -T         run unit tests and exit
```

Next, download a RIB file from the appropriate collector. Use the [table]() at the bottom of this page to determine which collector to use. Data is stored in a year.month structure, with RIBS containing the full downloads made available every two hours \(UTC\), and UPDATES containing the updates captured by the collectors \(every 15 minutes\). Beneath the RIBS\|UPDATES folders, you will find a folder for each day of the month, and files saved using the convention \[rib\|updates\].yyyyMMdd.hhmm.bz2.  File sizes vary based on the number of monitors advertising routes to each specific collector, and by number of routes collected by each monitor.

Running bgpdump without -m will output a lot of data and includes column explanations to help better understand the data.  Given the form of the output and content of one of the files, it makes running prefix-based searches on the data difficult - thus without the -m or -M option, bgpdump tends to be less useful than you'd like.  Below, see an example of a single entry from a RIB file.

```text
$ bgpdump rib.20140801.0000.bz2
2014-08-07 13:47:13 [info] logging to syslog
TIME: 08/01/14 00:00:00
TYPE: TABLE_DUMP_V2/IPV4_UNICAST
PREFIX: 1.0.0.0/24
SEQUENCE: 0
FROM: 129.250.0.11 AS2914
ORIGINATED: 07/30/14 08:41:55
ORIGIN: IGP
ASPATH: 2914 15169
NEXT_HOP: 129.250.0.11
MULTI_EXIT_DISC: 96
COMMUNITY: 2914:420 2914:1001 2914:2000 2914:3000 65504:15169
```

Running with the -m option will output as shown below:

```text
$ bgpdump -m rib.20140801.0000.bz2
2014-08-07 13:49:42 [info] logging to syslog
TABLE_DUMP2|1406851200|B|167.142.3.6|5056|1.0.0.0/24|5056 6461 15169|IGP|167.142.3.6|0|0||NAG||
TABLE_DUMP2|1406851200|B|66.185.128.1|1668|1.0.0.0/24|1668 15169|IGP|66.185.128.1|0|0||NAG||
TABLE_DUMP2|1406851200|B|157.130.10.233|701|1.0.0.0/24|701 6453 15169|IGP|157.130.10.233|0|0||NAG||
TABLE_DUMP2|1406851200|B|198.129.33.85|293|1.0.0.0/24|293 15169|IGP|198.129.33.85|0|0||NAG||
TABLE_DUMP2|1406851200|B|89.149.178.10|3257|1.0.0.0/24|3257 15169|IGP|89.149.178.10|0|10|3257:8012 3257:30016 3257:50001 3257:54900 3257:54901|NAG||
```

bgpdump -m outputs data in the following column order:

* BGP Protocol
* timestamp \(in epoch format\)
* W/A/B \(withdrawal/announcement/routing table\)
* Peer IP \(address of the monitor\)
* Peer ASN \(ASN of the monitor\)
* Prefix
* ASPath
* Origin Protocol \(typically always IGP\)
* Next Hop
* LocalPref
* MED
* Community strings
* Atomic Aggregator
* Aggregator

A couple of use cases for using bgpdump to get necessary information:

* Determine all routes to a specific prefix \( **bgpdump -m &lt;file&gt; \| grep &lt;prefix&gt;**\)

```text
$ bgpdump -m rib.20140801.0000.bz2 | grep 1.0.0.0/24
2014-08-07 13:51:36 [info] logging to syslog
TABLE_DUMP2|1406851200|B|167.142.3.6|5056|1.0.0.0/24|5056 6461 15169|IGP|167.142.3.6|0|0||NAG||
TABLE_DUMP2|1406851200|B|129.250.0.11|2914|1.0.0.0/24|2914 15169|IGP|129.250.0.11|0|96|2914:420 2914:1001 2914:2000 2914:3000 65504:15169|NAG||
TABLE_DUMP2|1406851200|B|66.185.128.1|1668|1.0.0.0/24|1668 15169|IGP|66.185.128.1|0|0||NAG||
TABLE_DUMP2|1406851200|B|157.130.10.233|701|1.0.0.0/24|701 6453 15169|IGP|157.130.10.233|0|0||NAG||
```

*  Determine all routes that use a specific AS Path \(**bgpdump -m &lt;file&gt; \| grep "ASPath"** \)

```text
$ bgpdump -m rib.20140801.0000.bz2 | grep "37100 15169"
2014-08-07 14:04:17 [info] logging to syslog
TABLE_DUMP2|1406851200|B|41.217.212.5|37100|1.0.0.0/24|37100 15169|IGP|41.217.212.5|0|0|no-export|NAG||
TABLE_DUMP2|1406851200|B|41.217.212.5|37100|1.1.1.0/24|37100 15169|IGP|41.217.212.5|0|0|no-export|NAG||
TABLE_DUMP2|1406851202|B|41.217.212.5|37100|64.15.112.0/20|37100 15169 43515|IGP|41.217.212.5|0|0|no-export|NAG||
```

**Note: ASPaths are shown in monitor&gt;transit&gt;origin format.  When using AS Path as the filter, the results show all the updates having the filter as a part of the AS Path. In the example below, the Origin AS is 56203, but contains AS 577 in the AS Path string.  To target a specific origin, grep for the origin with a trailing pipe character \(ie, "577\|"\)**

```text
$ bgpdump -m rib.20140801.0000.bz2 | grep "577" | more
2014-08-07 15:37:48 [info] logging to syslog
TABLE_DUMP2|1406851200|B|216.18.31.102|6539|1.0.6.0/24|6539 577 6939 4826 38803 56203|IGP|216.18.31.102|0|0||NAG||
```

### Checking BGP changes over a period of time

You can also run bgpdump on a group of files, using the bzcat -- just concatenate them using bzcat, and then pipe the output to bgpdump. This can be useful to find any updates related to a specific monitor, path or prefix over a period of time - but is predicated on having all the data available to use. Below shows two methods: 

```text
$ cat rib.20140801.0000.bz2 rib.20140801.0200.bz2 > result_concat.bz2
$ bgpdump -m result_concat.bz2 | grep <filter>

or


$ bzcat *.bz2 | bgpdump -m - | grep <filter>
```

When you want more specific information, you can actually telnet to the [quagga collectors](), and use a limited set of commands to interact with quagga to show you data. The most typical usage is the **sh ip bgp &lt;prefix&gt;**, which will show you the last update to the routing table for each monitor using that collector for a specific prefix. Visit [http://archive.routeviews.org/](http://archive.routeviews.org/), and click the login link for the appropriate collector \(check the [table]() below to find the appropriate collector for the monitor you’re interested in reviewing\).

## Working with Quagga collectors  

```text
$ telnet route-views2.routeviews.org
Trying 128.223.51.102...
Connected to route-views2.routeviews.org.
Escape character is '^]'.
Hello, this is Quagga (version 0.99.21).
Copyright 1996-2005 Kunihiro Ishiguro, et al.
```

```text
route-views2.routeviews.org>  sh ip bgp 1.0.0.0/24
BGP routing table entry for 1.0.0.0/24
Paths: (33 available, best #19, table Default-IP-Routing-Table)
  Not advertised to any peer
  37100 15169
    41.217.212.5 from 41.217.212.5 (41.217.212.5)
      Origin IGP, localpref 100, valid, external
      Community: no-export
      Last update: Wed Aug  6 22:42:49 2014
  2914 15169
    129.250.0.11 from 129.250.0.11 (129.250.0.12)
      Origin IGP, metric 96, localpref 100, valid, external
      Community: 2914:420 2914:1001 2914:2000 2914:3000 65504:15169
      Last update: Tue Aug  5 09:58:21 2014
  8492 15169
    85.114.0.217 from 85.114.0.217 (85.114.0.104)
      Origin IGP, localpref 100, valid, external
      Community: 8492:1305 29076:223 29076:900 29076:51003 29076:53003 29076:60495 29076:64667
      Last update: Sat Aug  2 07:45:53 2014
```

```text
route-views2.routeviews.org> sh ip bgp summary
BGP router identifier 128.223.51.102, local AS number 6447
RIB entries 961711, using 103 MiB of memory
Peers 48, using 214 KiB of memory

Neighbor        V    AS MsgRcvd MsgSent   TblVer  InQ OutQ Up/Down  State/PfxRcd
41.217.212.5    4 37100 8288960   80256        0    0    0 1d18h15m   502043
4.69.184.193    4  3356 18146786  180159        0    0    0 03w2d11h   496968
12.0.1.63       4  7018 29305714   54041        0    0    0 07w4d01h   499044
64.57.28.241    4 11537 2107157  357770        0    0    0 01w0d04h    14846
66.185.128.1    4  1668 26907309  357321        0    0    0 01w0d04h   498641
67.17.82.114    4  3549 16541627  180168        0    0    0 03w2d11h   499753
68.67.63.245    4 22652 10690189  180158        0    0    0 03w2d11h   501666
80.91.255.62    4  1299 21217943  180155        0    0    0 02w2d15h   495653
85.114.0.217    4  8492 40104466  357732        0    0    0 6d09h11m   508154
89.149.178.10   4  3257 16473759  180252        0    0    0 01w2d15h   499352
91.209.102.1    4 39756       0       0        0    0    0 never    Connect    
95.140.80.254   4 31500       0       0        0    0    0 never    Active     
96.4.0.55       4 11686 34598321  180171        0    0    0 03w2d11h   504967
```

```text
route-views2.routeviews.org> sh ip bgp neighbors
BGP neighbor is 41.217.212.5, remote AS 37100, local AS 6447, external link
 Description: SEACOM
  BGP version 4, remote router ID 41.217.212.5
  BGP state = Established, up for 1d18h16m
  Last read 15:50:46, hold time is 180, keepalive interval is 60 seconds
  Neighbor capabilities:
    4 Byte AS: advertised and received
    Route refresh: advertised and received(old & new)
    Address family IPv4 Unicast: advertised and received
    Address family IPv4 Multicast: advertised
  Message statistics:
    Inq depth is 0
    Outq depth is 0
                         Sent       Rcvd
    Opens:                  8          6
    Notifications:          4          1
    Updates:                0    8216893
    Keepalives:         80245      72125
    Route Refresh:          0          4
    Capability:             0          0
    Total:              80257    8289029
  Minimum time between advertisement runs is 30 seconds
  Update source is 128.223.51.102
```

## Using BGPlay to work with RouteViews Data

You can also use [bgplay](http://bgplay.routeviews.org/) on the RouteViews site to look at the last 10 days' worth of data.  This can be useful when tracking changes that occur over a short period of time.  Note that it only works based on the previous 10 days' worth of data.

**Note: due to large data storage requirements, BGPlay only works with the trailing 10 days' of data**

When BGPlay starts, a query window opens us where you can enter the prefix to monitor and the time interval in UTC. Press OK to open up an animation window as shown below. Below the figure, a numbered list corresponding to the callouts on the figure, explains each field in the image.

IMAGE MISSING

Let us break the picture into different parts for better understanding

1. Indicates that the update shown is the 3rd update of the 399 updates within the specified time period.
2. Signifies the router collector which received the BGP update.
3. Path change indicates that the current BGP update contains new paths. Other possible BGP Update messages that can be seen are Route Announcement, Route Withdrawal and Route Re-Announcement.
4. IP address of the peer from which the current BGP Update was collected.
5. The date and time at which the current BGP Update was collected.
6. Displays the change in the AS Path as contained by the new BGP Update message.
7. Indicates the last clicked AS number and name.
8. Vertical time axis.
9. Each purple horizontal spike indicates a burst of BGP updates.
10. Any purple horizontal spike touching this vertical line indicates 1 BGP update.
11. Any purple horizontal spike touching this vertical line indicates 23 BGP updates.
12. The starting date and time specified in the query.
13. To scroll through the different BGP messages within the time period.
14. To rearrange the AS graph to its starting layout.
15. To start a new query.

## List of Monitors by Collector

| **Collector** | **Monitor name** | **ASN** | **Monitor IP** | **BGP data location** |
| :--- | :--- | :--- | :--- | :--- |
| rv/oreg | Amsterdam-2 | 286 | 134.222.87.1 | [http://routeviews.org/bgpdata](http://routeviews.org/bgpdata) |
| rv/telxatl | Atlanta, GA | 4181 | 198.32.132.28 | [http://routeviews.org/route-views.telxatl/bgpdata/](http://routeviews.org/route-views.telxatl/bgpdata/) |
| rv/telxatl | Atlanta, GA-2 | 6939 | 198.32.132.75 | [http://routeviews.org/route-views.telxatl/bgpdata/](http://routeviews.org/route-views.telxatl/bgpdata/) |
| rv/oreg | Calgary | 852 | 154.11.98.225 | [http://routeviews.org/bgpdata](http://routeviews.org/bgpdata) |
| rv/oreg | Chicago, IL | 1668 | 66.185.128.1 | [http://routeviews.org/bgpdata](http://routeviews.org/bgpdata) |
| rv/oreg | Frankfurt-2 | 3257 | 89.149.178.10 | [http://routeviews.org/bgpdata](http://routeviews.org/bgpdata) |
| rv/jinx | Johannesburg, South Africa | 30844 | 196.223.14.55 | [http://routeviews.org/route-views.jinx/bgpdata](http://routeviews.org/route-views.jinx/bgpdata) |
| rv/route-views3 | Kolding, Denmark | 3292 | 195.215.109.254 | [http://routeviews.org/route-views3/bgpdata](http://routeviews.org/route-views3/bgpdata) |
| rv/linx | London-10 | 8426 | 195.66.224.66 | [http://routeviews.org/route-views.linx/bgpdata](http://routeviews.org/route-views.linx/bgpdata) |
| rv/linx | London-11 | 6453 | 195.66.224.51 | [http://routeviews.org/route-views.linx/bgpdata](http://routeviews.org/route-views.linx/bgpdata) |
| rv/linx | London-12 | 8928 | 195.66.224.53 | [http://routeviews.org/route-views.linx/bgpdata](http://routeviews.org/route-views.linx/bgpdata) |
| rv/oreg | London-9 | 3549 | 208.51.134.246 | [http://routeviews.org/bgpdata](http://routeviews.org/bgpdata) |
| rv/oreg | Los Angeles, CA | 2152 | 137.164.16.84 | [http://routeviews.org/bgpdata](http://routeviews.org/bgpdata) |
| rv/oreg | New York, NY-1 | 7018 | 12.0.1.63 | [http://routeviews.org/bgpdata](http://routeviews.org/bgpdata) |
| rv/isc | Palo Alto, CA-4 | 36351 | 198.32.176.207 | [http://routeviews.org/route-views.isc/bgpdata](http://routeviews.org/route-views.isc/bgpdata) |
| rv/nwax | Portland, OR | 1798 | 198.32.195.23 | [http://routeviews.org/route-views.nwax/bgpdata](http://routeviews.org/route-views.nwax/bgpdata) |
| rv/oreg | San Francisco, CA | 3561 | 206.24.210.80 | [http://routeviews.org/bgpdata](http://routeviews.org/bgpdata) |
| rv/oreg | San Jose, CA-3 | 2914 | 129.250.0.11 | [http://routeviews.org/bgpdata](http://routeviews.org/bgpdata) |
| rv/route-views3 | San Jose, CA-4 | 209 | 205.171.3.22 | [http://routeviews.org/route-views3/bgpdata](http://routeviews.org/route-views3/bgpdata) |
| rv/route-views3 | San Jose, CA-5 | 5650 | 74.40.7.35 | [http://routeviews.org/route-views3/bgpdata](http://routeviews.org/route-views3/bgpdata) |
| rv/saopaulo | São Paulo-8 | 1916 | 187.16.216.4 | [http://routeviews.org/route-views.saopaulo/bgpdata](http://routeviews.org/route-views.saopaulo/bgpdata) |
| rv/oreg | Seattle, WA | 3356 | 4.69.184.193 | [http://routeviews.org/bgpdata](http://routeviews.org/bgpdata) |
| rv/oreg | St. Petersburg-1 | 8492 | 85.114.0.217 | [http://routeviews.org/bgpdata](http://routeviews.org/bgpdata) |
| rv/oreg | Stockton, CA | 1239 | 144.228.241.130 | [http://routeviews.org/bgpdata](http://routeviews.org/bgpdata) |
| rv/oreg | Sydney-1 | 1221 | 203.62.252.83 | [http://routeviews.org/bgpdata](http://routeviews.org/bgpdata) |
| rv/wide | Tokyo-1 | 2497 | 202.249.2.169 | [http://routeviews.org/route-views.wide/bgpdata](http://routeviews.org/route-views.wide/bgpdata) |
| rv/wide | Tokyo-2 | 7500 | 202.249.2.86 | [http://routeviews.org/route-views.wide/bgpdata](http://routeviews.org/route-views.wide/bgpdata) |
| rv/oreg | Tokyo-4 | 2497 | 202.232.0.3 | [http://routeviews.org/bgpdata](http://routeviews.org/bgpdata) |
| rv/route-views4 | Tokyo-5 | 2914 | 129.250.1.248 | [http://routeviews.org/route-views4/bgpdata](http://routeviews.org/route-views4/bgpdata) |
| rv/oreg | Vancouver | 6539 | 216.18.31.102 | [http://routeviews.org/bgpdata](http://routeviews.org/bgpdata) |
| rv/route-views3 | Washington, DC-6 | 209 | 205.171.202.202 | [http://routeviews.org/route-views3/bgpdata](http://routeviews.org/route-views3/bgpdata) |
| rv/route-views6 | Ashburn, VA-2 | 2914 | 2001:418:0:1000::f000 | [http://routeviews.org/route-views6/bgpdata](http://routeviews.org/route-views6/bgpdata) |
| rv/route-views6 | Burbank, CA | 209 | 2001:428::205:171:203:140 | [http://routeviews.org/route-views6/bgpdata](http://routeviews.org/route-views6/bgpdata) |
| rv/route-views6 | Frankfurt-3 | 3257 | 2001:668:0:4::2 | [http://routeviews.org/route-views6/bgpdata](http://routeviews.org/route-views6/bgpdata) |
| rv/linx | London-8 | 3356 | 2001:7f8:4::d1c:1 | [http://routeviews.org/route-views.linx/bgpdata](http://routeviews.org/route-views.linx/bgpdata) |
| rv/route-views6 | New York, NY-6 | 7018 | 2001:1890:111d:1::63 | [http://routeviews.org/route-views6/bgpdata](http://routeviews.org/route-views6/bgpdata) |
| rv/saopaulo | São Paulo-9 | 28329 | 2001:12f8::232 | [http://routeviews.org/route-views.saopaulo/bgpdata](http://routeviews.org/route-views.saopaulo/bgpdata) |
| rv/sydney | Sydney-5 | 4826 | 2001:de8:6::4826:1 | [http://routeviews.org/route-views.sydney/bgpdata](http://routeviews.org/route-views.sydney/bgpdata) |
| rv/route-views6 | Tokyo-3 | 2497 | 2001:240:100:ff::2497:2 | [http://routeviews.org/route-views6/bgpdata](http://routeviews.org/route-views6/bgpdata) |
| rv/route-views6 | Washington, DC-2 | 701 | 2600:803::15 | [http://routeviews.org/route-views6/bgpdata](http://routeviews.org/route-views6/bgpdata) |
| rv/oreg | Calgary | 852 | 154.11.98.225 | [http://routeviews.org/bgpdata](http://routeviews.org/bgpdata) |
| rv/oreg | Palo Alto, CA-2 | 3549 | 67.17.82.114 | [http://routeviews.org/bgpdata](http://routeviews.org/bgpdata) |

