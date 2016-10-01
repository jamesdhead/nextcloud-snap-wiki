The Nextcloud Box is designed to work out-of-the-box (forgive the pun). Here's a short description of how to get up and running!

# putting it all together

On [the Nextcloud.com/box website](https://nextcloud.com/box) you can find pictures of the content of the box as well as a pdf showing how to put everything together. The order is as follows:

1. put the pi in the box. The ethernet and USB ports should be on the inside, same direction as the hard drive USB port. Use the screwdriver to screw it to the box.
2. connect the USB plug in the Pi, put the power for the pi into the pi (lead it over the hard drive) and leave the power input in the hole. It is best to put the power cable on the bottom and the pi power on top. Then plug the USB3 into the drive and route the cables on the inside of the half-rounded plastic cable guide so they are all inside.
3. Connect the separate USB cable to the power side in the Box (do not yet connect it to the charger!) and connect the network cable and lead it out over the power.
4. Put the micro-sd card in the Pi. You'll find a little hole for that on the opposide side of the USB ports.
5. Now all is connected, close the Box, plug the network cable in our wireless router and connect the USB cable in the charger to turn it all on.

The Box will now need some 8-10 minutes to prepare itself. It will boot up, copy the OS to the hard drive and check for and install updates.

Open a browser in a device connected to the same network as the Box (say, your mobile phone or laptop on the same wireless router) and visit the URL on the slip of paper in the box:
`ubuntu-standard.local` or `ubuntu-standard.localdomain` or `nextcloud.local`

There, give a username and password for admin and your Box is ready to go. Use the other pages on this wiki for more information like how to configure network or add more functionality with Snaps!