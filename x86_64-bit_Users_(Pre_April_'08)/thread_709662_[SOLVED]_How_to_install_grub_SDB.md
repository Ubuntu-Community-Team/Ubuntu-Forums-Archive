---
title: "[SOLVED] How to install grub SDB"
date: 2008-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lukasz Tarkowski on 2008-02-27
I'm trying to install Grub on SDB Its is my pendrive and whenever I install it I get an Geom error?
Its a 4gb Usb pen drive :)
Im trying to install Nimblex
lukasz@lukasz-laptop:~$ sudo grub-install /dev/sdb
[sudo] password 
/dev/sdb does not have any corresponding BIOS drive.
lukasz@lukasz-laptop:~$

I also get #  grub-install --no-floppy --root-directory=. /dev/sdb
 cd /root hat is the command I tried to use and get _Geom Boot error_

---

