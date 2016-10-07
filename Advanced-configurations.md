The system in the Box comes with some defaults to make sure that it's always updated, but it's possible to make some modifications by following the following instructions.

## Auto security update

The system is configured to check for any available security updates every 6 hours via a tool called `auto-security-update`.

If you would like to modify the behaviour of the update process, then you may do so by modifying a cron job in `/etc/cron.d/auto-security-update`.

If you need to disable `auto-security-update`, you need to modify two configurations:

1. Comment out `/etc/cron.d/auto-security-update`
1. Modify `/etc/apt/apt.conf.d/20auto-upgrades`, set `APT::Periodic::Unattended-Upgrade` to "0"

## Auto snapd update

The `auto-snapd-update` is executed every 2 hours. 

If you would like to change it, then you may modify the cron job in `/etc/cron.d/auto-snapd-update`.