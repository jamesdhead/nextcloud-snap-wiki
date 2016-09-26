**Q: I can't connect to my Nextcloud Box any more. What can I do?**

A: Connect a monitor/TV/projector to the HDMI port and see what the Box is telling you.
As an alternative, try connecting the hard drive to another USB port to see if that helps.

----

**Q: How to switch Nextcloud Box on/off?**
There is no button :) Is there a way to switch Nextcloud on/off in a friendly way?

A: You need to connect to the Box using SSH and type the following:

```bash
$ sudo shutdown -h now
```
Unfortunately, you then don't know when the process has completed unless the device is connected to a monitor, so you'll have to wait a few minutes and then disconnect the power source.

----

**Q: Is there a "sleep mode"?**

A: The hard drive has several sleep modes and spins down automatically after a few hours, but as long as there is some activity, from logs per example, then it won't be able to go to sleep. 

----