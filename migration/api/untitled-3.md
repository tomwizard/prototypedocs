# Obtaining a list of ThousandEyes Agent IP Addresses

Customers may need the IP addresses of ThousandEyes Agents in order to construct firewall rules or similar filters. The ThousandEyes application program interface \(API\) provides the IP addresses of both Cloud Agents assigned to your organization and Enterprise Agents assigned to your Account Group.

Note that for Cloud Agents, the IP address assignment is relatively constant but subject to change without notice. ThousandEyes periodically adds Cloud Agent locations, adds instances of Agents to increase capacity in a given geographic location \(all Cloud Agent locations have multiple instances of actual hosts running the Agent software\), changes providers in a given geographic location due to reliability issues, or makes changes for other reasons. We recommend that you check the listing periodically for changes, and review our [Release Notes](https://success.thousandeyes.com/Articles?category=Release_Notes) for updates to our Cloud Agents. Consider [subscribing](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA0E0000000CmmUKAS_Notification-of-upgrades-maintenance-and-outages) to the Release Notes forum for automatic notification of new postings.

## Querying the API

To list the IP addresses of all Agents available to your Account Group, query the /agents endpoint of the ThousandEyes API. The query can be sent by a command-line tool such as [Wget](https://en.wikipedia.org/wiki/Wget) or [cURL](https://en.wikipedia.org/wiki/CURL), with a standard browser, or through a RESTful API client, such as [Postman](https://www.getpostman.com/).

The query is a simple HTTP GET request to

```text
https://api.thousandeyes.com/agents
```

for [XML](https://en.wikipedia.org/wiki/XML)-formatted output, or

```text
https://api.thousandeyes.com/agents.json
```

for [JSON](https://en.wikipedia.org/wiki/JSON)-formatted output.

In addition, you will need to supply your ThousandEyes username \(email address\) and API token as the HTTP Basic Authentication username and password, respectively. If you issue one of the above requests in a browser, your browser should prompt you for your ThousandEyes username and API token. Alternatively, you may include the username and API token in the URL, in the following form:

```text
https://username:API_token@api.thousandeyes.com/agents
```

Your API token can be found in the **User API Token** section of the **Profile** tab of the [Account Settings](https://app.thousandeyes.com/settings/account/?section=profile) page:

IMAGE MISSING

For users with access to multiple Account Groups, be sure to use to the correct Account Group context to obtain the correct set of results from the API. The current context is displayed in the menu bar to the right of the User icon. For example, the current context in the example below is the "Support" Account Group:

IMAGE MISSING

If you need to query a non-default Account Group you have access to, you will need to use the [Account Group context](https://developer.thousandeyes.com/v6/#/accountcontext) parameter.

## Example

Here is an example curl command for querying the **/agents** API endpoint:

```text
curl "https://api.thousandeyes.com/agents" -u noreply@thousandeyes.com:g351mw5xqhvkmh1vq6zfm51c62wyzib2
```

A section of the resulting output in XML format:

IMAGE MISSING

The image above shows a portion of the response listing some of the Singapore Cloud Agent IP addresses. The "agentType" parameter identifies them as type "Cloud". Enterprise Agents will be identified as type "Enterprise". If your output's format is missing the whitespace and/or line termination, you can use any publicly available web-based tool to [format the XML](http://www.freeformatter.com/xml-formatter.html) \(or [format the JSON](https://jsonformatter.curiousconcept.com/) below\) to present the output in a similar fashion as shown in the image above.

Alternatively, similar curl command can be used to receive a JSON-formatted response. The only adjustment that is needed is the addition of the **.json** suffix to the API endpoint URL:

```text
curl "https://api.thousandeyes.com/agents.json" -u noreply@thousandeyes.com:g351mw5xqhvkmh1vq6zfm51c62wyzib2
```

The command above will generate output in JSON format, which is \(arguably\) easier to read for humans:

IMAGE MISSING

For more information on querying the ThousandEyes API, consult the documentation available at [https://developer.thousandeyes.com](https://developer.thousandeyes.com/).

**NOTE:** ThousandEyes does not provide and does not recommend using CIDR blocks as a shortcut to enumerating each of the Agent IP addresses. Most user interfaces of filtering devices provide the capacity to create groups of objects such as a "ThousandEyes Cloud Agents" group. Once created, the effort required to maintain such a list is minimal. In contrast, attempting to use whois information or assuming a CIDR mask that fits the existing IP addresses of an Agent is liable to be error-prone as Agent IP addresses are updated, and is less secure.

## Obtaining a list of ThousandEyes Agent IP Addresses with te-iplist tool

In addition to querying ThousandEyes API directly, we provide a command-line interface \(CLI\) utility called **te-iplist**. This utility abstracts away raw API queries and provides a simpler method for exporting agent IP addresses in various formats. It is available for Linux, MacOS and Windows OS. For more information, here are the [instructions on how to use te-iplist](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000Cn2GCAS_Obtaining-a-list-of-ThousandEyes-Agent-IP-Addresses-with-te-iplist).

