# 1. Connect to the Box

1. Use Putty on Window or your Linux shell and connect to your Box's IP or internal hostname
1. Use the password/login ubuntu/ubuntu

# 2. Change your password

If you haven't done so already, you should change your SSH password

`$ passwd`

*Note: type your new password twice and make sure to remember it or you will lose access to the Box!*

# 3. Enable HTTPS

Test to see if you can install a Let's Encrypt SSL certificate

`$ sudo nextcloud.enable-https -d`

If everything went well, then install the certificate

`$ sudo nextcloud.enable-https`

If not, you can always use it with a self-signed certificate

`$ sudo nextcloud.enable-https -s`