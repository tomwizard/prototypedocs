# Obtaining a list of ThousandEyes Agent IP Addresses with te-iplist

Customers may need the IP addresses of ThousandEyes Agents in order to construct firewall rules or similar filters. We do not publish a list of IP addresses, but customers can use the [ThousandEyes application program interface \(API\)](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnuKAC) to obtain the IP addresses of both Cloud Agents assigned to your organization and Enterprise Agents assigned to your Account Group. You can query the API with a web browser, a custom script, or a RESTful API tool to obtain the latest list of IP addresses, or you can use our command-line tool - **te-iplist**.

Note that for Cloud Agents, the IP address assignment is relatively constant but subject to change without notice. Consult the Knowledge Base article [Obtaining a list of ThousandEyes Agent IP Addresses](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnuKAC) for more information.

## te-iplist

**te-iplist** is a command-line interface \(CLI\) utility that queries ThousandEyes API for the Agents available for your account and outputs Agent IPs in different forms \(IP list, subnet list, IP range list, IP block list\) and formats \(plain text, CSV, JSON, XML\).

### Download

* [te-iplist \(Linux\)](https://github.com/thousandeyes/te-iplist/raw/master/bin/linux-32/te-iplist)
* [te-iplist \(macOS\)](https://github.com/thousandeyes/te-iplist/raw/master/bin/macos/te-iplist)
* [te-iplist \(Windows\)](https://github.com/thousandeyes/te-iplist/raw/master/bin/win/te-iplist.exe)

 On Linux and macOS ensure the utility is executable before the usage:

```text
chmod +x te-iplist
```

### Usage

Refer to the t[e-iplist documentation](https://github.com/thousandeyes/te-iplist/blob/master/README.md) for all available parameters or issue the command with the `-h` switch:

```text
./te-iplist -h
```

### Usage examples

Display a list of all Cloud and Enterprise Agent IP addresses \(`-o ip`\):

```text
$ ./te-iplist -u <user> -t <user-api-token> -o ip5.45.179.194
5.45.179.195
5.45.179.196
5.148.182.136
5.148.182.137
...
2400:8900::f03c:91ff:fec8:c7b2
2400:8900::f03c:91ff:fec8:c7d3
2400:8900::f03c:91ff:fedf:65c4
2403:7000:8000:400::20
2600:3c03::f03c:91ff:feae:cd41
...
```

Display a minimal list of subnets \(`-o subnet-loose`\) that cover Enterprise Agent IP addresses \(`-e`\). List should include Agent names as comments \(`-n`\):

```text
$ ./te-iplist -u <user> -t <user-api-token> -o subnet-loose -e -n10.0.0.3    # kubernetes te-agent-pod
10.0.1.0/26 # ip-10-0-1-48.localdomain; csc-internal; office-12
1.2.3.4     # kubernetes te-agent-pod; ip-10-0-1-48.localdomain; csc-internal; office-12
```

Display a list of IP blocks \(`-o block-strict`\) of Cloud Agents \(`-c`\) IPv6 \(`-6`\) addresses:

```text
$ ./te-iplist -u <user> -t <user-api-token> -o block-strict -c -62400:8900::f03c:91ff:fec8:c7b2
2400:8900::f03c:91ff:fedf:65c4
2403:7000:8000:400::[18-20]
...
```

Display a list of IP ranges \(`-o range-strict`\) of Enterprise Agents private \(`-e-private`\) IPv4 \(`-4`\) addresses:

```text
$ ./te-iplist -u <user> -t <user-api-token> -o range-strict -e-private -4 -n10.10.10.202 - 10.10.10.203 # primoz-centos-te; centos6
192.168.0.2 - 192.168.0.4   # thousandeyes-va-14244; thousandeyes-va-14403; thousandeyes-va66
```

Create a comma separated values \(CSV\) file which includes all Agents and all output formats:

```text
$ ./te-iplist -u <user> -t <user-api-token> -o csv > all-agents.csv
```

You can open CSV file as a spreadsheet in your favorite Spreadsheet editor, such as LibreOffice Calc, Numbers or Google Sheets. Unfortunately Microsoft Excel does not support CSV files with new lines inside cells and will not import the generated CSV.

### Loose vs Strict

IP subnets, IP ranges and IP blocks can be displayed in **loose** or **strict** notations. Strict notation covers only the IP addresses that are used by the Agents. Loose notation covers all IP addresses that are used by the Agents, but may also cover some of the addresses that are not used by the Agents. Loose notation typically covers all the Agent IP addresses with fewer entries. For example, IP addresses:

```text
10.0.0.2
10.0.0.3
10.0.0.5
```

can be covered by multiple **strict** subnet notations:

```text
10.0.0.2/31
10.0.0.5
```

or by a single **loose** subnet notation:

```text
10.0.0.0/29
```

You should select the notation that is acceptable by your security standards.

### Account Groups

Users assigned to multiple Account Groups can list the Agents available in a specific Account Group with the `-a <accountGroupId>` argument. You can list available Account Group IDs with:

```text
te-iplist -u <user> -t <user-api-token> -account-groups
```

If `-a` is not provided, user's login Account Group is used.  For users in multiple organizations, only one login Account Group can be assumed; others will need to be specified.

