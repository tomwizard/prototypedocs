# Connecting to the ThousandEyes Virtual Appliance using SSH \(Windows\)

In order to access the command line of a ThousandEyes Virtual Appliance or Physical Appliance, the Appliance can be configured with one or more SSH public keys. An SSH client configured with the corresponding SSH private key can then log into the Appliance's command line.

This article provides instructions for users of a Microsoft Windows operating system to perform the following steps:

* [Obtain an SSH client]()
* [Create an SSH key pair]()
* [Configure the ThousandEyes Appliance]()
* [Create an SSH connection]()
* [Troubleshooting]()

## Obtain an SSH client

An SSH application such as PuTTY is required. Download the latest [PuTTY installer](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) \(normally the 64-bit MSI\) to install the PuTTY suite of programs, most relevantly:

* PuTTY \(putty.exe\): An SSH client
* PuTTYgen \(puttygen.exe\): An SSH key generator
* \(Optional\) PSCP \(pscp.exe\): A command-line Secure Copy Protocol client, for copying files from the Appliance

Run the MSI installer to installer once the MSI file has been downloaded. Alternatively, individual executables may be downloaded separately from the PuTTY site.  
 

## Create an SSH key pair

If you don't already have an SSH key pair \(public key and matching private key\), you'll need to generate one using PuTTYgen.  Open the PuTTYgen program, and follow the steps below.

1. In the PuTTY Key Generator window click the **Generate** button:  
2. Move your mouse back and forth inside the **Key** field to generate randomness.  
3. \(Optional\) Add a passphrase using the fields provided, if desired.
4. Highlight the public key and copy to the clipboard:  
5. Save your public and private keys using the **Save public key** and **Save private key** buttons.  Note the directory or directories where you save the keys. You'll need the path to the private key for the PuTTY SSH client.

## Configure the ThousandEyes Appliance

The public key of a user's SSH key pair must be present on each Agent that is to be accessed. Log into the web interface of a ThousandEyes Appliance, then follow the steps below to configure the Appliance with your public key.

1. On the Appliance Access tab paste [the key that was copied in step 4]() of the **SSH key creation** section into the **Add New SSH key** field.  
2. Click the **Add Key** button.

    The key will be added with the identifying string that follows the key:

### Add Key failures

If the key addition fails, most failures are caused by unnecessary beginning and ending lines, comment fields or carriage returns/line feeds. For example, the file saved by the PuTTY Key Generator contains beginning and ending lines and comment fields that need to be removed in order to have a valid public key format:

```text
---- BEGIN SSH2 PUBLIC KEY ----
Comment: "An RSA SSH key key example"
AAAAB3NzaC1yc2EAAAABJQAAAQEAgXp4D3V6OGVv24Anh2P4Uh1N1KZ+DP9oT3sx
E8U9MybSho1ev4eZuwso2q3M0tC1YU+PQu1RFd0hzZdcS8zTg7+soopI9HRaOoSL
p5IyywDC28AvoJE8q9DtKZoKKp/cNfyT4h+YiaUx7DMrTYXcLfpEVwu40fqiqmHb
s42RJ/yVMq4MKYEp0AvZcC8l/ByYvU9b/ogEKI8g175RLgVVmJqSaZW/w/ZhzG7u
89q1F1bYgJlEbrINSoBKC7CPyKB8N3KqTl1vOqiqSe6DSCzLIDk+NPEPSWGf3LoO
bAKcV9O2ml74rCipBBGyslsQVIINLxyUpXFC42/sS1ZN+MXYnQ==
---- END SSH2 PUBLIC KEY ----
```

If you copy the public key from the saved file rather than from the PuTTYGen window [in step 4]() of the **Create an SSH key pair** section, please remove the BEGIN and END lines, the Comment: line\(s\) and any carriage return, new line or line feed characters. The correct format should look like this:

```text
ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEAgXp4D3V6OGVv24Anh2P4Uh1N1KZ+DP9oT3sxE8U9MybSho1ev4eZuwso2q3M0tC1YU+PQu1RFd0hzZdcS8zTg7+soopI9HRaOoSLp5IyywDC28AvoJE8q9DtKZoKKp/cNfyT4h+YiaUx7DMrTYXcLfpEVwu40fqiqmHbs42RJ/yVMq4MKYEp0AvZcC8l/ByYvU9b/ogEKI8g175RLgVVmJqSaZW/w/ZhzG7u89q1F1bYgJlEbrINSoBKC7CPyKB8N3KqTl1vOqiqSe6DSCzLIDk+NPEPSWGf3LoObAKcV9O2ml74rCipBBGyslsQVIINLxyUpXFC42/sS1ZN+MXYnQ== An RSA SSH key example
```

If attempts are failing despite following these instructions, then copy the above example and attempt to add it. If the example key addition is successful, the failure is likely due to a carriage return, new line or line feed character that remains in the newly generated key.

The example key can be immediately deleted by clicking the  button to the right of the key, in the listing of keys added to the Appliance.

## Create an SSH connection

Once a public key has been installed on the Appliance, follow the instructions below to configure PuTTY and log into the command line of the Appliance.

1. Run the PuTTY program \(putty.exe\).
2. In the PuTTY Configuration window's **Category** section, open the **Connection &gt; Data** panel.
3. Enter the username "thousandeyes" in the **Auto-login username** field.  
4. In the PuTTY Configuration window's **Category** section, open the **Connection** &gt; **SSH** &gt; **Auth** panel.
5. Click the **Browse** button and navigate to [the location selected in Step 5]() of the **Create an SSH key pair** section, above.
6. In the PuTTY Configuration window's **Category** section, open the **Session** panel.
7. Enter the IP address or hostname of the Enterprise Agent in the **Host Name \(or IP address\)** field.
8. Enter a name for this PuTTY session in the **Saved Sessions** field.
9. Click the **Save** button to save the session for future uses.
10. Click the **Open** button to open the SSH connection to the Appliance's command line.
11. If a [passphrase was created in Step 3]() of the **Create an SSH key pair** section then provide the passphrase to the SSH key.  
12. If the login is successful, the prompt "thousandeyes@appliance\_hostname:~ appears, indicating the user is in the home directory of the "thousandeyes" user.
13. Now you're SSH'd in. Have fun!

## Troubleshooting

**Connection problem symptoms when using PuTTY SSH client:**

* `Error: Server unexpectedly closed network connection` error message
* `fatal: no matching mac found:...` error message

**Solution:** Make sure that PuTTY is at the current version as these errors have been encountered when using older versions of PuTTY.

