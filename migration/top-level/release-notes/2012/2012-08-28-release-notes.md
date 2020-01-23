# Release Notes: 2012-08-28

This summer is hot, and so is this new release with lots of new goodies:

* **MPLS tunnels in Path Visualization** - now you can see links that are part with MPLS tunnels in the path visualization screen. We include RFC4950 info with each link whenever is available, e.g.: **L=1242,E=0,S=1,T=1**where L is the label, E is experimental, S is bottom of the stack flag and T is MPLS TTL.
* **MTU information in Path Visualization** - we also added MTU information in the Path Visualization screen. If there are links with MTU&lt;1500, you will be able to spot them. Links with MTU&lt;1500 are typically entry points of tunnels and may create extra delay when transmitting data since large packets need to be fragmented.
* **Sticky selection of nodes/links in topology graphs** - this applies to both Path Visualization and BGP Route Visualization; if you select a node/link at a given time, it will remain visible \(expanded\) in the graph if you move to another time; this is useful to track changes of routes or BGP paths over time.
* **Configure HTTP headers in HTTP tests** - now you can add custom headers to basic HTTP tests. An example is the_Host_ header in HTTP. This is especially useful for cases where you want to target a specific IP address, but don't want to configure a DNS record for that IP. We also added an option to disable verification of matching between the hostname in the URL and the hostname in the certificate, which can be used for similar types of testing over HTTPS.

