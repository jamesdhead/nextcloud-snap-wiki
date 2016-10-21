There can be times when something goes really wrong and your SD card becomes unreadable. In this case, you may need to flash a new SD card and for this you will need to have a backup of the one you got with the Nextcloud Box.

We can't currently provide a download link, but here is how to back up the image which currently ships with it.

## Windows

https://www.raspberrypi.org/forums/viewtopic.php?p=239331

## Linux

Insert the SD Card and figure out which device it was assigned by viewing syslog.

```
# dmesg |tail

[576857.695594] scsi 8:0:0:0: Direct-Access     SanDisk  SDDR-113         9412 PQ: 0 ANSI: 0
[576857.695999] sd 8:0:0:0: Attached scsi generic sg2 type 0
[576857.879896] sd 8:0:0:0: [sdc] 7744512 512-byte logical blocks: (3.97 GB/3.69 GiB)
[576857.880613] sd 8:0:0:0: [sdc] Write Protect is off
[576857.880615] sd 8:0:0:0: [sdc] Mode Sense: 03 00 00 00
[576857.881387] sd 8:0:0:0: [sdc] No Caching mode page found
[576857.881389] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[576857.892594]  sdc: sdc1 sdc2
[576857.894960] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[576858.230304] EXT4-fs (sdc2): mounted filesystem with ordered data mode. Opts: (null)
```
On this system it was assigned _/dev/sdc._

Use dd to back up the card to a binary file.

```
# dd if=/dev/sdc of=./Nextcloud_sdcard.bin

7744512+0 records in
7744512+0 records out
3965190144 bytes (4.0 GB, 3.7 GiB) copied, 187.631 s, 21.1 MB/s
```
Where _if_ is the input file(the device) and _of_ is the output file.

You may need to be root to run this, so you can use _sudo_ or _su_ to root before running the back up.

This will back up up all of the partitions on the card. As of version 10, that 2 partitions and just under 4GB of space.

To restore the backup to another card, insert it, use the same procedure above to determine the device and use dd to copy the file the device.

```
# dd if=./Nextcloud_sdcard.bin of=/dev/sdc

7744512+0 records in
7744512+0 records out
3965190144 bytes (4.0 GB, 3.7 GiB) copied, 187.631 s, 21.1 MB/s
```

## OSX

*Missing instructions, feel free to post what works*
