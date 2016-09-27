# Via the user interface

The Nextcloud Box comes with a built-in Snap manager which allows users to add and remove Snaps. We will integrate this interface with Nextcloud in the future but for now, you can access it by going to:

`http:<your box's IP or hostname>:4200`

*Note: That's the URL you access the box with and port 4200*

**Warning: Not all the Snaps you see have been designed for the Nextcloud Box**

## Recommendations

* spreed-webrtc
* Rocket Chat

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