---
title: "Need help getting USB flash drive mounted"
date: 2006-12-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by tomdkat on 2006-12-17
Hi!  Well, for some bizarre reason my 1GB USB Flash drive won't mount.  :(

Some dmesg output contains this:

[  537.404529] usb 3-7: new high speed USB device using ehci_hcd and address 12
[  548.934470] usb 3-7: device not accepting address 12, error -110
[  549.046345] usb 3-7: new high speed USB device using ehci_hcd and address 13
[  560.576283] usb 3-7: device not accepting address 13, error -110
[  560.688155] usb 3-7: new high speed USB device using ehci_hcd and address 14
[  571.099483] usb 3-7: device not accepting address 14, error -110
[  571.211358] usb 3-7: new high speed USB device using ehci_hcd and address 15
[  581.622853] usb 3-7: device not accepting address 15, error -110
[  610.468004] APIC error on CPU0: 40(40)
[  610.783639] APIC error on CPU0: 40(40)

tom@gwanna:~$ uname -a
Linux gwanna 2.6.17-10-generic #2 SMP Tue Dec 5 21:16:35 UTC 2006 x86_64 GNU/Linux
tom@gwanna:~$ 

The drive has worked as recent as a few days ago.  I believe I did run a software update within the last day or two but I'm not sure what was updated.

Any ideas?

I'm running Edgy for AMD64 64-bit.

Thanks!

Peace...

---

### Post by tomdkat on 2007-01-05
^^^bump^^^

Peace...

---

### Post by woobie on 2007-01-05
Seeing the same issue here. For me, I was able to mount my Lexar Jumpdrive initially after a reboot, but subsequent reconnections do not work. I also am having problems with my Ipod Nano. 

Anyone have any ideas on this? I have seen numerous reports of this issue via google search, but no solutions so far. 

Thanks!

---

### Post by tomdkat on 2007-01-25
When I boot from my Edgy Live CD, I can mount the USB Flash drive (and my Compact Flash card) just fine.  I think an update to the base Edgy release might have broken something in a 64-bit environment.  My Edgy Live CD is a 32-bit environment.

Peace...

---

