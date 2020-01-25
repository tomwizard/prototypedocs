# Outage Detection - Overview

ThousandEyes aggregates and analyzes de-identified data generated from its users to understand when and where Internet outages may be occurring. The resulting insights help operators rapidly diagnose incidents and determine whether they are part of a broader Internet outage. By better understanding the root cause of an outage, you can improve decision-making and efficiently resolve performance issues affecting your organization.

ThousandEyes can currently detect two types of outages:

* **Traffic Outages in ISPs**: Network \(i.e. data plane\) outages detected using terminal forwarding loss in an Internet service provider \(e.g. Level 3, AT&T, etc.\) which are likely affecting a portion of the Internet larger than just your organization. Note: Traffic Outage Detection is currently not available for SaaS providers \(e.g., Salesforce, Microsoft\) or IaaS/PaaS providers \(e.g., CDN, Hosting, DNS\).
* **Routing Outages**: Routing \(i.e. control plane\) outages across the Internet that are detected by evaluating the BGP reachability of ASNs transited by or originating prefixes found in your tests.

