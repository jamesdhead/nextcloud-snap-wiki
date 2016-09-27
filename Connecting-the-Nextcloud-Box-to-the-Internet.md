# 1. Point your domain to your network

1. Register for a service which redirects a domain name to your home network
1. Open port 443 in your firewall
1. Forward port 443 on your router to the IP used by your Box

# 2. Connect to the Box

1. Use Putty on Window or your Linux shell and connect to your Box's IP or internal hostname
1. Use the password/login ubuntu/ubuntu

# 3. Change your password

If you haven't done so already, you should change your SSH password

`$ passwd`

*Note: type your new password twice and make sure to remember it or you will lose access to the Box!*

# 4. Add your external domain to Nextcloud

`# sudo nextcloud.occ config:system:set trusted_domains 2
--value=your.domain`

*Note: replace "your.domain" with the domain name registered at step 1*

# 5. Enable HTTPS

Test to see if you can install a Let's Encrypt SSL certificate

`$ sudo nextcloud.enable-https -d`

If everything went well, then install the certificate

`$ sudo nextcloud.enable-https`
