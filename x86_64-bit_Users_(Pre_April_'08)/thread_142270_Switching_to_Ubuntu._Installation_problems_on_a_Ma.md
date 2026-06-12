---
title: "Switching to Ubuntu. Installation problems on a Mac G5."
date: 2006-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Astounded on 2006-03-10
All excited about installing Ubuntu, I partitioned my G5 and download the Ubuntu ISO-file.

a) I boot it up and the black screen prompt me with "boot: "
b) I enter (tried serveral options), "server -powerpc"
c) Ubuntu returns "Please wait, loading kernel"
d) Screen switches to black text on white background saying:

[INDENT]
```
opening display /pci@0, f0000000 /NVDA,Parent@10/NVDA,Display-B@1... ok
copying OF device tree...done
Initializing fake screen: NVDA,Display-A
Calling quiesce...
returning 0x0140000 from prom_init

Invalid Memory Access at  <some numbers>

Apple PowerMac8, 1 5.2.2f4 BootROM built on 11/09/04 at 11:06:15
Copyright 1994-2004 Apple Computer, Inc.
All Rights Reserved.

Welcome to Open Firmware, the system time and date is: 07:56:57 03/10/2006

To continue booting, type "mac-boot" and press return
To shut down, type "shut-down" and press return

Release keys to continue!
```[/INDENT]
e) Please note that everything is locked, keyboard not reacting on any key.

What to do? Anyone that has experinced this or have any idea what to do? The system has one big partition running Mac OS 10.3, one swap partition (4gb), and a final partition that was meant for Ubuntu.

Thanks in advance.

---

### Post by ponzio on 2006-03-10
With the live cd I think you have to boot it with livecd-powerpc64 or something similar. So I think you need make the installation program know that you have powerpc64, so try server -powerpc64, I am giving no guarantees it will work though.

---

### Post by Astounded on 2006-03-10
That actually did it. Just got my hands on this Mac and didn't really know what type it was. Thanks a lot bro'!

---

### Post by Astounded on 2006-03-10
Everything is now installed, however.. Ubuntu seems unable to identify the mouse & keyboard. My friend had the same problem for his PC, solving it switching to the PS2 port, but as the iMac is usb-only, I'm in a tough situation.

Ideas?

Thanks.

---

### Post by ssam on 2006-03-10
are you currently using a blue tooth keyboard? usb should work.

---

