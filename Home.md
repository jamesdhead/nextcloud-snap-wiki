# Welcome

This wiki is about providing help for both, users of the [Nextcloud Box](https://nextcloud.com/box), and developers of the Nextcloud snap.

A snap is a package which contains a confined application running on the snapd platform which is available for many Linux distributions. For more information, please visit: http://snapcraft.io

## Users

The official Nextcloud snap is designed to offer a fully working instance of Nextcloud which only requires a minimum amount of configuration via the Nextcloud Web user interface before it's ready to use. Do no expect to be able to tweak it like you would a Nextcloud instance set up via shared hosting, a VM or your own server.

It comes with [some tools](https://github.com/nextcloud/nextcloud-snap/wiki/Included-CLI-utilities) which require the use of the command line to enable SSL per example, but that's the exception.

If you need more advanced features, you need to look for other Nextcloud snaps or to build your own by forking this project per example.

## Developers

Snaps are a great way to deploy and manage software, but building a Nextcloud snap is very different than working on Nextcloud and you will need to be familiar with the following technologies:

* File system permissions
* Bash scripting
* Debian packaging
* Python and or Go
* systemd, daemons, process forking
* Unix sockets and pipes
* GCC compilation (Makefile, flags, linking, etc.)
* HTTP Proxy
* PHP-FPM
* Apache or NGINX
* Database administration
* SQL

The ideal background would be someone with experience of the web hosting industry, but of course, it's a fun project to start learning about all these technologies, even if things don't run the same way in a snap as they do on a server.

