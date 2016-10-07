The Nextcloud Box is designed to work out-of-the-box (forgive the pun). Here's a short description of how to get up and running!

# Putting it all together

On the [Nextcloud Box website](https://nextcloud.com/box) you can find pictures of the content of the Box as well as a PDF file showing you how to put everything together. The order is as follows:

1. Place the computer inside the Box. The Ethernet and USB ports should be on the inside, facing the same direction as the hard drive USB port. Use the screwdriver to screw it to the Box
1. Connect the larger connector of special cable to the hard drive
1. Connect the full-size USB plug to the computer
1. Plug the the microUSB male connector into the side of the computer (lead it over the hard drive) 
1. Place the microUSB female connector in the corner shown on the diagram
1. Make sure all cables stay inside the box by using the half-rounded plastic cable guide, as shown on the diagram
1. Connect the separate USB cable to the female microUSB connector (do not yet connect it to the charger!)
1. Connect the network cable and lead it out over the cable which will be connected to the charger
1. Insert the microSD card in the computer. You'll find a little hole for that on the opposite side of the USB ports
1. Now that everything is connected, close the Box, plug the network cable in your wireless router and connect the USB cable to the charger to turn it all on.

*Note: The "computer" is the single-board computer that you've purchased to use in the Box. It's typically a Raspberry Pi 2.*

The Box will now need some 8-10 minutes to prepare itself. It will boot up, copy the OS to the hard drive and check for and install updates.

Open a browser in a device connected to the same network as the Box (say, your mobile phone or laptop on the same wireless router) and visit the URL on the slip of paper in the box. This could be:
`ubuntu-standard.local` or `ubuntu-standard.localdomain` or `nextcloud.local`

There, give a username and password for the admin account and your Box is ready to go. Use the other pages on this wiki for more information like how to enable SSL or add more functionality with snaps!