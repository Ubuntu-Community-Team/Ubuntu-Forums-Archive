---
title: "[SOLVED] log error - cupsd and apple bonjour?"
date: 2007-12-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by brett611 on 2007-12-26
Hi,
I had some visitors for the holidays who are even more pc illiterate than I.  They left and now I am seeing all kinds of weird problems.  This one relates to sys log errors.  I've attached a screenshot of the system log viewer and the text is below:

I'm totally confused.  I was running XP and did a full install of Ubuntu 7.10, no partition for windows.  So the Apple reference is throwing me.  Ditto for the red-hat reference.

Advice is appreciated!

Dec 26 09:14:35 brett-desktop cupsd[5051]: *** WARNING *** The programme 'cupsd' uses the Apple Bonjour compatiblity layer of Avahi.
Dec 26 09:14:35 brett-desktop cupsd[5051]: *** WARNING *** Please fix your application to use the native API of Avahi!
Dec 26 09:14:35 brett-desktop cupsd[5051]: *** WARNING *** For more information see <http://0pointer.de/avahi-compat?s=libdns_sd&e=cupsd>
Dec 26 09:14:38 brett-desktop dhcdbd: Started up.
Dec 26 09:14:41 brett-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Dec 26 09:14:48 brett-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Dec 26 09:14:48 brett-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers

---

### Post by brett611 on 2007-12-28
<bumpled>

---

### Post by LeslieL on 2008-01-05
Me too, and my printer doesn't work. Says CUPS isn't running. Help!

---

### Post by brett611 on 2008-01-06
sorry to say that I ended up doing a fresh install of gutsy and it solved my problems.  I'm blaming it on compiz and ati...but who knows

---

### Post by LeslieL on 2008-01-06
I don't use compiz. Printing was working great until, I think, a set of updates last week.

---

### Post by LeslieL on 2008-01-07
Got the printer working again by removing all CUPS programs via Synaptic and reinstalling them.

---

### Post by brett611 on 2008-01-07
I'll take that as a solution, esp compared to a full reinstall of the os!
thanks

---

