The Nextcloud Snap comes with a general purpose SSL configuration compatible with all the clients we currently offer, but it's important to tighten the configuration based on your needs.

## Making changes to your configuration

### Editing the file

*Note: We assume you already know how to [connect to your Nextcloud Box via SSH](How-to-connect-to-the-Nextcloud-Box)*

Edit the provided custom.conf file and make modifications to the SSL section.

```bash
$ nano /var/snap/nextcloud/current/apache/conf/custom.conf
```

*Note: `nano` may not be available in all setups, use the file editor of your choice*

The custom configuration already comes with some recommended hardening settings.

* TLSv1.2 only
* ECDHE only
* Drop support for HMAC-SHA1
* Disable session ticket
* Enable OCSP stapling
* SSL cipher logging (for debugging)

You simply need to uncomment the ones you want to use. Make sure to read the associated comment!

For more information on a typical modern configuration, please visit Mozilla's [dedicated page](https://wiki.mozilla.org/Security/Server_Side_TLS)

**Important: This configuration will prevent OSX and Android <4.4 clients from connecting**

### Restarting Apache

Restart Apache to apply the settings

```bash
$ systemctl restart snap.nextcloud.apache
```

## Testing your new settings

There are various tools available, but some of them are available exclusively online and you may not want to give those tools access to you Nextcloud Box.

One way to get some feedback about your configuration is to use [CipherScan](https://github.com/mozilla/cipherscan) from Mozilla.

### Install CipherScan

Install git if not already installed:

```bash
$ sudo apt install git
```

Download CipherScan from Github

```bash
git clone https://github.com/mozilla/cipherscan.git
```

Run it against Nextcloud to test the current config

```bash
$ cd cipherscan/
$ ./cipherscan -o /usr/bin/openssl localhost:443
```

*Note: On anything but AMD64, you need to provide the path to your openssl binary for the command to work*