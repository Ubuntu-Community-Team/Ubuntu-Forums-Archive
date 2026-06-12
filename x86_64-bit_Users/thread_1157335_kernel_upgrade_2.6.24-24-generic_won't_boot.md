---
title: "kernel upgrade 2.6.24-24-generic won't boot"
date: 2009-05-12
forum: x86 64-bit Users
---

### Post by Michael Matthews on 2009-05-12
NEVER MIND. Screwed up grub/menu.lst.

After upgrade to 2.6.24-24 generic ubuntu 8.4 system panics and won't boot. Something about vfx file system not recognized. Will boot in recovery mode or old versions will boot. Have no idea what the problem is. Did nothing except software upgrade.

I did not allow install to replace grub menu.lst but edited it myself. Usually no problem.

---

### Post by pixel :-) on 2009-05-12
Wheeel is this really a problem? Do you really nead a new kernel? The problem could be an obscure bug. With upgrades you always run the risk of regressions, i would recommend to just wait the next one.

You may want to post menu.lst, some one will check for errors (not me), and also after a crash and a successful boot post /var/log/dmesg.0

post them as attachments

Maybe someone will figure whats going on.

start a thread here, it should give results faster. It's not necessarily a 64bit problem.
[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

---

### Post by Michael Matthews on 2009-05-15
My mistake. Duh..

---

