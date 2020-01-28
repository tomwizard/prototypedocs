# Troubleshooting automatic update problems on Enterprise Agents

Our software is architected to run a version check upon check-in with the ThousandEyes collector.  This process will validate the currently installed version of the agent against the expected version in our system.  If running a version lower than the expected version, the Agent will download the required packages, and update them.

This process is run during the update:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Ubuntu</th>
      <th style="text-align:left">Red Hat Enterprise Linux/CentOS</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>apt-get update</p>
        <p>apt-get install te-agent</p>
        <p>apt-get install te-browserbot*</p>
      </td>
      <td style="text-align:left">
        <p>yum update</p>
        <p>yum install te-agent</p>
        <p>yum install te-browserbot*</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">* te-browserbot package is only required for instances running a browserbot
        installation. This does require additional resources on a Enterprise Agent
        (minimum 2GB RAM is recommended)</td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>We have encountered circumstances where the keyrings for packages are centrally managed, and may not include the required public package keys. These errors will manifest in a manner similar to the following:

```text
GPG error: http://apt.thousandeyes.com lucid Release: the following signatures couldn't be verified because the public key is not available: NO_PUBKEY C99A1F5BE718900
```

When this occurs, a manual download and registration of the ThousandEyes public key is required. This can be done in either one or two steps: the one-step approach is shown below:

```text
wget -q http://apt.thousandeyes.com/thousandeyes-apt-key.pub -O- | sudo apt-key add -
```

This will download and register ThousandEyes public key, which will allow you to re-run the steps above as required in order to update the agent codebase.

