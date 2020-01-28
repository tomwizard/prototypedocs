# Connecting to the ThousandEyes Virtual Appliance using SSH \(Mac/Linux\)

In order to connect to the ThousandEyes VA, you first need to configure the Virtual Appliance with an SSH public key.

## Generate an SSH key

### Step 1: Check for SSH keys

First, we need to check for existing ssh keys on your computer. Open a terminal session and run:

```text
cat ~/.ssh/id_rsa.pub
```

If it says "No such file or directory" go to **step 2**. Otherwise, you already have an existing keypair, and you can skip to **step 3**.

#### Step 2: Generate a new SSH key

To generate a new SSH key, enter the code below. We want the default settings so when asked to enter a file in which to save the key, just press enter.

```text
ssh-keygen -t rsa -C "your_email@example.com"
Generating public/private rsa key pair.
Enter file in which to save the key (/your/home/dir/xxxx/.ssh/id_rsa): [Press enter]
```

Now you need to enter a passphrase.

```text
Enter passphrase (empty for no passphrase): [Type a passphrase]
Enter same passphrase again: [Type passphrase again]
```

Which should give you something like this:

```text
Your identification has been saved in /your/home/dir/.ssh/id_rsa.
Your public key has been saved in /your/home/dir/.ssh/id_rsa.pub.
The key fingerprint is:
01:0f:f4:3b:ca:85:d6:17:a1:7d:f0:68:9d:f0:a2:db your_email@example.com
```

#### Step 3: Add your SSH key to the VA

Copy the contents of the public key to your clipboard.  The following command can be used on Mac OS X to do so:

```text
pbcopy < ~/.ssh/id_rsa.pub
```

On Linux, you can display the public key in a console with the following command:

```text
cat ~/.ssh/id_rsa.pub
```

Copying part is done by selecting the whole public key \(starting with "ssh-..." and ending with "...== your@email.com", where "your@email.com" can be anything - it is essentially a comment to distinguish this particular public key from others\). Once selected, use combination of "Ctrl+Shift+C" keys to copy selected text to your clipboard.

## Copy the public key to the ThousandEyes VA

Access the web interface of the Virtual Appliance, and navigate to the Appliance Access tab, then copy the public key \(which should be on your clipboard\) into the "Add New SSH key" text widget.  

IMAGE MISSING

The text will show as green if it validates successfully, or red if there is a problem.  For most circumstances where there is a problem, remove trailing line feeds.

## Create an SSH connection to the ThousandEyes VA

Once you have a valid public key on the ThousandEyes VA, you can connect.  Connections are established to the VA using the thousandeyes user account, with the passphrase specified while creating the SSH key:

```text
$ ssh thousandeyes@<hostname or IP of virtual appliance>
```

The first time you connect to the target virtual appliance, your system will note that the identity has been added.

```text
Identity added: /Users/xxxx/.ssh/id_rsa (/Users/xxxx/.ssh/id_rsa)
```

It is strongly recommended that you use static IP addresses for agents in this circumstance, in order to prevent host key checking problems.  When you connect, you'll get a warning similar to the one below:

```text
The authenticity of host '10.0.100.103 (10.0.100.103)' can't be established.
RSA key fingerprint is bc:15:ab:be:d5:09:xx:xx:xx:xx:a7:5a:6e:d7:df:3a.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '10.0.100.103' (RSA) to the list of known hosts.
```

Once you accept, you're locked into using that IP address unless you modify your list of known hosts.  After adding the host, you'll be directed to the home directory of the ThousandEyes VA user.

```text
thousandeyes@<hostname or IP of virtual appliance>:~$
```

Now you're SSH'd in.  Have fun!

Portions of this text graciously borrowed from GitHub at https://help.github.com/articles/generating-ssh-keys

