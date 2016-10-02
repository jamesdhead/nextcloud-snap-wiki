# FEATURE HAS NOT BEEN MERGED YET

You can now connect Nextcloud to other areas of the filesystem. To do so, you need to follow the following steps:

1. [Connect to the Nextcloud Box](How-to-connect-to-the-Nextcloud-Box)
1. Connect the Nextcloud Snap to the filesystem areas which were made available
	```bash
	$ snap connect nextcloud:home ubuntu-core:home
	$ snap connect nextcloud:removable-media ubuntu-core:removable-media
	```

1. Restart the service
	```bash
	$ sudo systemctl restart snap.nextcloud.apache
	```

1. Go to the internal app store in the Web GUI of Nextcloud

1. Install the "External storage support" app

1. Go to the admin section

1. In the left sidebar, click on "External Storage"

1. Type in a folder name and select "Local"

1. In the "Configuration" field, type /media

1. There should be a green dot on the left of that row

You can now go to the Files app and click on your newly created folder to access files placed in the `/media` folder
