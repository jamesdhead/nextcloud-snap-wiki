# 1. Connect to the Box

Follow the instructions at: [How to connect to the Nextcloud Box](How-to-connect-to-the-Nextcloud-Box)

# 2. Enable HTTPS

Test to see if you can install a Let's Encrypt SSL certificate

`$ sudo nextcloud.enable-https -d`

If everything went well, then install the certificate

`$ sudo nextcloud.enable-https`

If not, you can always use it with a self-signed certificate

`$ sudo nextcloud.enable-https -s`