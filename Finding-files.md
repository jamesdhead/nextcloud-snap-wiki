The Nextcloud installation is split across several locations in the file system

## Read-only folder

Location: `/snap/nextcloud/current/`

Snap variable: `$SNAP`

Contains:
* Nextcloud application

## Configuration files

Location: `/var/snap/nextcloud/current/`

Snap variable: `$SNAP_DATA`

Contains:
* Apache, PHP, MySQL, and Redis logs
* Keys and certificates
* MySQL database
* Redis database
* Nextcloud config
* Any Nextcloud apps installed by the user

## Your data

Location: `/var/snap/nextcloud/common/`

Snap variable: `$SNAP_COMMON`

Contains:
* Nextcloud data
* Nextcloud logs