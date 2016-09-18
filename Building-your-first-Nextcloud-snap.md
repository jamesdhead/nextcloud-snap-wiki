This is for developers looking for ways to modify the Nextcloud Snap by compiling a new version. This is not for people looking for ways to configure their existing Nextcloud Snap.

## Prerequisites

* [Having setup a development environment](https://github.com/nextcloud/nextcloud-snap/wiki/Creating-a-Snappy-development-environment)
* [Having followed the basic tutorial](https://github.com/nextcloud/nextcloud-snap/wiki/Building-your-first-snap)

## Working on the Nextcloud Snap

On top of the basic knowledge required to build a snap, you will need to understand the following technologies

* Unix sockets and pipes
* Process forking
* GCC compilation (Makefile, flags, linking, etc.)
* Proxy
* PHP
* Apache
* SQL

### Getting a working version

Retrieve the source code

```
$ mkdir snaps
$ cd snaps
$ git clone -b master https://github.com/nextcloud/nextcloud-snap.git
```

Create the snap

```
$ cd nextcloud-snap
$ snapcraft
```

It will take many minutes to compile the snap

### Sideload your custom snap

```
$ sudo snap install <the name of the snap you've just created> --force-dangerous
```