---
title: "How to get Opera working?"
date: 2006-07-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by srikat on 2006-07-30
> **gorod said:**
> Just download a binary installer with static qt library from opera's site. You might try to get a deb file with static qt and install it with dpkg -i --force-architecture opera*.deb so you can uninstall it later if you want.

I downloaded opera_9.0-20060616.6-shared-qt_en_i386.deb

I installed libqt3-mt and when I do > sudo dpkg -i --force-architecture opera_9.0-20060616.6-shared-qt_en_i386.deb it got installed.

But when I type 'opera' in the terminal, get:

> ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.00-20060616.6/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory


Help pls.

---

### Post by Alinoe on 2006-07-30
Look at this: [http://ubuntuforums.org/showthread.php?t=193605&highlight=opera]("http://ubuntuforums.org/showthread.php?t=193605&highlight=opera")

---

### Post by srikat on 2006-07-30
Thanks for that. 

I tried the fix suggested at [http://ubuntuforums.org/showpost.php?p=1167982&postcount=62](http://ubuntuforums.org/showpost.php?p=1167982&postcount=62) and get:
> 
sri@sri-desktop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
QSettings: error creating /home/sri/.qt
opera: Can not use personal directory: /home/sri/.opera

---

### Post by hajk on 2006-07-31
Need to install ia32-libs package...

---

### Post by srikat on 2006-07-31
IC..TY. 

I've actually installed 32-bit Ubuntu erasing the 64-bit version. Opera installation was as easy as point and click using Automatix.

---

