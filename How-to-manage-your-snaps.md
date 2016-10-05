# Via the web interface

The Nextcloud Box comes with a built-in Snap manager which allows users to add and remove Snaps. We will integrate this interface with Nextcloud in the future but for now, you can access it by following these steps:

## Install the store

*Note: This will not be required in the future*

If you can't access the web interface, it could be because the store has not been enabled yet. 

[Follow these steps](How-to-connect-to-the-Nextcloud-Box) to connect to the Box via SSH and type:

`$ sudo snap install snapweb --beta`

# Adding the store to Nextcloud

1. In nextcloud, as an admin, click on the apps menu and then select the big plus sign which says "apps"
1. In the left column, click on "Not enabled"
1. At the top, click on the search field and select "External Sites"
1. Enable the app
1. Go to the admin section
1. In the left column, click on "External Sites"
1. In the "Name" field, type "Ubuntu store"
1. In the URL field, type "http://localhost:4200"
1. Refresh the page
1. Click on the apps menu and you'll see your new app store icon

**Warning: Not all the Snaps you see have been designed for the Nextcloud Box**

**This doesn't work if you've enabled SSL for your Nextcloud. If you did follow the instructions below**

Connect to the store at `http:<your box's IP or hostname>:4200`

*Note: That's the URL you access the box with and port 4200*

# Via the command line

## 1. Connect to the Box

Follow the instructions at: [How to connect to the Nextcloud Box](How-to-connect-to-the-Nextcloud-Box)

## 2. Look for specific Snaps

You can't list all available snaps, but you can enter search terms.

```bash
$ sudo snap find spreed
Name           Version        Developer  Notes  Summary
spreed-webrtc  0.28.1oparoz1  oparoz     -      WebRTC audio/video calls and conferences
```
## 3. Install Snaps

Once you've found what you were looking for, install it

`$ sudo snap install spreed-webrtc`

# Beta Snaps

Unfortunately, beta Snaps are not shown in the GUI and cannot be found via the `find` command, so the best thing to do is to follow our Twitter account @nextcloudbox to hear about new and interesting snaps in development and then to install them via the command line by following the recommendations of the Snap builder.

Typically, you would do something like:

`$ sudo snap install transmissionbt --beta`

but sometimes, a Snap cannot be confined and requires a special switch to be installed:

`$ sudo snap install transmissionbt --beta --devmode`

## Recommended Snaps

* nextcloud
* spreed-webrtc
* Rocket Chat
* transmissionbt (beta, devmode)
