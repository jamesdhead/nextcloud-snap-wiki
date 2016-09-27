Test to see if you can install a Let's Encrypt SSL certificate

`$ sudo nextcloud.enable-https -d`

If everything went well, then install the certificate

`$ sudo nextcloud.enable-https`

If not, you can always use it with a self-signed certificate

`$ sudo nextcloud.enable-https -s`