# Crash Reporting for Enterprise Agents

In order to improve diagnosis of problems with Enterprise Agents, ThousandEyes has added a crash report feature.  Similar to other common programs and operating systems which send reports to their parent companies when execution is halted by an error, this feature allows Enterprise Agents to send error data to ThousandEyes when the te-agent process encounters a fatal error.

When an error occurs and a crash report is generated, the data is uploaded automatically—no user interaction or configuration is required for this feature to function, other than allowing outbound access from the Enterprise Agent to the URL https://crashreports.thousandeyes.com.  Many customers will already have firewall rules permitting general outbound HTTPS access.  Alternatively, customers may have already enabled HTTPS access to the 192.150.160.0/24 network for the standard communication between Enterprise Agents and ThousandEyes.  Either of these firewall rules will cover crashreports.thousandeyes.com.  To further narrow your firewall rule down to a single host, simply perform DNS resolution on crashreports.thousandeyes.com with a tool such as `dig` or `nslookup`, or `ping crashreports.thousandeyes.com.`; For customers behind web proxies, the crash reporting feature will employ your Agent’s existing proxy configuration.

Crash reports are typically on the order of 1 megabyte in size, so should not create problems consuming bandwidth or similar resources.  Data sent contains no sensitive information pertaining to customer test data or configuration. Download a sample crash report:

[Sample crash report](https://success.thousandeyes.com/servlet/servlet.FileDownload?file=01544000009Wpb5AAC)

This binary file can be inspected with crash report parsers which accept .dmp formatted reports, a generic tool such as `od` or similar binary file editors, or an online crash report parser such as [http://www.osronline.com/](http://www.osronline.com/).

In general, this feature should have minimal or no impact on customers.  This feature is currently enabled automatically and not user-configurable.  Future releases will include the option to disable crash reporting.

