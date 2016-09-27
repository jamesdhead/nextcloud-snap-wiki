There are a few CLI utilities included:

- `nextcloud.occ`:
    - Nextcloud's `occ` configuration tool. Note that it requires `sudo`.
- `nextcloud.mysql-client`:
    - MySQL client preconfigured to communicate with Nextcloud MySQL server.
      This may be useful in case you need to migrate Nextcloud installations.
      Note that it requires `sudo`.
- `nextcloud.enable-https`:
    - Enable HTTPS, either via self-signed certificates or via Let's Encrypt.
      HTTP will redirect to HTTPS. The certificates will automatically be kept
      up-to-date. See `nextcloud.enable-https -h` for more information.
- `nextcloud.disable-https`:
    - Disable HTTPS (does not remove certificates).