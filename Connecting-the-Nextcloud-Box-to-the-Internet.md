# 1. Point your domain to your network

1. Register for a service which redirects a domain name to your home network
1. Open both port 80 and port 443 in your firewall
1. Forward both ports on your router to the IP used by your Box

# 2. Connect to the Box

Follow the instructions at: [How to connect to the Nextcloud Box](How-to-connect-to-the-Nextcloud-Box)

# 3. Add your external domain to Nextcloud

`# sudo nextcloud.occ config:system:set trusted_domains 2
--value=your.domain`

*Note: replace "your.domain" with the domain name registered at step 1*

# 4. Enable HTTPS

Test to see if you can install a Let's Encrypt SSL certificate

`$ sudo nextcloud.enable-https -d`

If everything went well, then install the certificate

`$ sudo nextcloud.enable-https`
