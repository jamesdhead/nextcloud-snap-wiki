# 1. Point your domain to your network

1. Register for a service which redirects a domain name to your home network
1. Open port 80 in your firewall
1. Forward port 80 on your router to the IP used by your Box

# 2. Connect to the Box

Use Putty on Window or your Linux shell.
Use the password/login ubuntu/ubuntu

# 3. Add your external domain to Nextcloud

`# sudo nextcloud.occ config:system:set trusted_domains 2
--value=your.domain`