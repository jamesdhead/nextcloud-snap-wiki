## 1. Find the Box

You can first try to use the hostname defined in the Box, which is:

`ubuntu-standard.local` or `ubuntu-standard.localdomain`

If that doesn't work, you can open a command prompt in your favourite OS and type:

`$ arp -a`

In the list of entries, if you're using a Raspberry Pi 2, you should see one which starts with:

`b8-27`

Use the IP address next to it as the URL to use to connect to the Box

## 2. Connect to the Box

1. Use [Putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/) on Window or your Linux command line and open an SSH session using your Box's IP or internal hostname
1. Use the password/login ubuntu/ubuntu

## 3. Change your password

If you haven't done so already, you should change your SSH password

`$ passwd`

*Note: type your new password twice and make sure to remember it or you will lose access to the Box!*