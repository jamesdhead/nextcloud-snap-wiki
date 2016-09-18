## Requirements

* 4GB RAM (more is better)
* Multi-core processor
* 8GB+ HD. You will need a minimum of 10GB of space to comfortably work on the Nextcloud snap

## Installing a development environment

## Windows

1. Install [VirtualBox](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html)
1. Download the AMD64 image of Ubuntu server: http://www.ubuntu.com/download/server
1. Create a 4GB RAM, 4 core virtual machine in VirtualBox and install Ubuntu
1. Create a NAT rule
	```
	Name    Protocol     Host IP       Host Port    Guest IP      Guest Port
	SSH     TCP          127.0.0.1     2222         10.0.2.15     22
	```

1. Start the VM
1. Start a SSH session to 127.0.0.1:2222 and login using ubuntu/ubuntu
1. Install Snappy: `apt install snapd`

### Linux

See: http://snapcraft.io/docs/core/install

## Configuring your environment

### Tooling

```
$ sudo apt-get install snapcraft git unzip nano ccache golang-go python3
```

### Configuring ccache

This will greatly reduce the time it takes to build snaps

```
$ mkdir ~/ccachecompilers
$ ln -s /usr/bin/ccache ~/ccachecompilers/gcc
$ ln -s /usr/bin/ccache ~/ccachecompilers/g++
echo 'export CC="${HOME}/ccachecompilers/gcc"' >> ~/.bashrc
echo 'export CXX="${HOME}/ccachecompilers/g++"' >> ~/.bashrc
```
