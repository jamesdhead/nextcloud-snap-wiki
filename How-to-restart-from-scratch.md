It you need to start from scratch, please follow these steps, but **beware, all data on the hard drive will be lost!**

1. Power off the Raspberry Pi 2
1. Plug the SD card in a card reader connected to a laptop or desktop computer
1. Open the SD card's 1st partition
1. Open the `cmdline.txt` file
1. Modify "root=/dev/sda2" to "root=/dev/mmcblk0p2"
1. Plug the SD card back into the Raspberry Pi 2
1. Power on
1. Wait up to 10 minutes

The hard drive will be formatted and mounted and you will have access to a fresh installation of Nextcloud.