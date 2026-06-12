---
title: "Spontaneous Reboots?"
date: 2007-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by trmentry on 2007-12-05
I'm having an issue after I reinstalled Gutsy 64bit.   Its spontaneously rebooting now.

Its done it twice in the past 12 hours or so.

```

Dec  5 03:40:05 kashyyyk dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Dec  5 03:40:05 kashyyyk dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Dec  5 03:40:05 kashyyyk dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Dec  5 03:45:44 kashyyyk syslogd 1.4.1#21ubuntu3: restart.
Dec  5 03:59:58 kashyyyk -- MARK --
Dec  5 04:19:58 kashyyyk -- MARK --
Dec  5 04:39:58 kashyyyk -- MARK --
Dec  5 04:59:58 kashyyyk -- MARK --
Dec  5 05:19:59 kashyyyk -- MARK --
Dec  5 05:39:59 kashyyyk -- MARK --
Dec  5 05:59:59 kashyyyk -- MARK --
Dec  5 06:19:59 kashyyyk -- MARK --
Dec  5 06:39:59 kashyyyk -- MARK --
Dec  5 07:00:00 kashyyyk -- MARK --
Dec  5 07:20:00 kashyyyk -- MARK --
Dec  5 07:40:00 kashyyyk -- MARK --
Dec  5 08:00:00 kashyyyk -- MARK --
Dec  5 08:20:01 kashyyyk -- MARK --
Dec  5 08:40:01 kashyyyk -- MARK --
Dec  5 09:00:01 kashyyyk -- MARK --
Dec  5 09:20:01 kashyyyk -- MARK --
Dec  5 09:40:02 kashyyyk -- MARK --
Dec  5 10:00:02 kashyyyk -- MARK --
Dec  5 10:20:02 kashyyyk -- MARK --
Dec  5 10:40:02 kashyyyk -- MARK --
Dec  5 11:00:03 kashyyyk -- MARK --
Dec  5 11:20:03 kashyyyk -- MARK --
Dec  5 11:40:03 kashyyyk -- MARK --
Dec  5 11:50:19 kashyyyk syslogd 1.4.1#21ubuntu3: restart.
Dec  5 11:50:19 kashyyyk kernel: Inspecting /boot/System.map-2.6.22-14-generic
Dec  5 11:50:20 kashyyyk kernel: Loaded 26084 symbols from /boot/System.map-2.6.22-14-generic.
Dec  5 11:50:20 kashyyyk kernel: Symbols match kernel version 2.6.22.
Dec  5 11:50:20 kashyyyk kernel: No module symbols loaded - kernel modules not enabled.

```

I'm not exactly sure what is going on.  I wasn't have this issue a few weeks ago on gutsy on the same hardware.  But brain child here completely borked it and decided to reinstall fresh.  So this is a fresh install with the exception of Thunderbird and VMware Server (but those were on old system as well).

Not a heat issue from what I can tell as everything is in spec for temps.  All fans are running.  Memory seems fine as well.

Any speculations?  Highly annoying when remoted into the box and then poof.

Thanks

---

### Post by ddoxey on 2008-01-05
I'm having the same issue on Ubuntu Gutsy 2.6.22-14-server.

Here's a syslog snippet:
...
Jan  5 09:17:01 gutsysrv /USR/SBIN/CRON[6777]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan  5 09:20:01 gutsysrv /USR/SBIN/CRON[6783]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Jan  5 09:27:02 gutsysrv syslogd 1.4.1#21ubuntu3: restart.
Jan  5 09:27:02 gutsysrv kernel: Inspecting /boot/System.map-2.6.22-14-server
...

I only recently started using sendmail. Since then I've been noticing the there's a lot of syslog noise about sendmail. (It may have always been that way.) 
Could there be any relationship?

---

