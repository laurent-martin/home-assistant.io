---
title: "Systemd-Resolved"
description: "More information on why systemd-resolved marks the installation as unsupported."
---

## The issue

systemd-resolved is used over D-Bus to resolve DNS queries made by Home Assistant, Supervisor,
and add-ons. Without it, DNS will not work correctly in your installation.

## The solution

If you see a message about an issue with D-Bus, [resolve that first](/more-info/unsupported/dbus#the-solution).

If the systemd-resolved service is not running or disabled, enable and start it: Login to th host system as root:

```bash
systemctl status systemd-resolved
```

```text
● systemd-resolved.service - Network Name Resolution
     Loaded: loaded (/lib/systemd/system/systemd-resolved.service; disabled; vendor preset: enabled)
     Active: inactive (dead)
       Docs: man:systemd-resolved.service(8)
```

If the service is stopped, start it:

```bash
systemctl start systemd-resolved
```

If the service is disabled, enable it:

```bash
systemctl enable systemd-resolved
```

If that does not help, reboot your operating system.

As a last resort, you need to reinstall the host running the Supervisor
with one of the supported operating systems, [see instructions here](/more-info/unsupported/os).
