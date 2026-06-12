---
title: "Grub failure on install"
date: 2008-01-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by jjazz on 2008-01-18
Hi all,

Was installing Gutsy 64bit on my machine and got the error: 'Fatal error Grub can not be installed(hd0)'

After doing some reading I did a reinstall using ext2 as the file system and installation went without a hitch. This seems to be a fairly common error that has multiple workarounds, however I would still like to use ext3. Does anyone know if running tune2fs -j against this partition will cause Grub to fail after migration to ext3 or is this strictly an issue that occurs when the system is being installed?

Thanks

---

### Post by jjazz on 2008-01-19
After spending a lot more time trying to figure out what was/is causing this issue, I think it has something to do with the LSI logic card that I am using. I rebuilt the system with an ext2 boot and a reiserfs root partition and I am still getting errors on boot and lockups periodically.

---

