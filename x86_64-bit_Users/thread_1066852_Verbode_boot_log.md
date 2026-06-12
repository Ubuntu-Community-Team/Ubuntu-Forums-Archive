---
title: "Verbode boot log?"
date: 2009-02-11
forum: x86 64-bit Users
---

### Post by dsmith1974 on 2009-02-11
After turning on bootlogd, installing sysvinit and running:

update-rc.d -f bootlog remove
update-rc.d bootlogd defaults 08

I now get a /var/log/boot file (of ~4KiB) which lists most of the salient events and errors, but I'd like a more complete log which shows the order of all hardware probes etc. (for diagnosis).

Reading around it seems that the 'quiet' kernel flag needs to be 'tuned' so I tried:

sysctl -w quiet=0

But that didn't work.  Another candidate would be to put it in the /boot/defaults/sysctl.conf file, but then it occured to me that the flag probably has no meaning after booting.  BSD systems have a /boot/loader.conf file for these kinds of flags, but I can't seem to find one for Ubuntu.

How do I get all events into /var/log/boot?

Many thanks,

Duncan

---

