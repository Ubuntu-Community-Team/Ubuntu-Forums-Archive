---
title: "Wine PPA crashes on x64"
date: 2012-09-18
forum: Wine
---

### Post by Toufik on 2012-09-18
After latest update of wine from ppa (wine-1.5.13) on my x64 laptop, wine crashes with this message:

p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
wine: Unhandled page fault on read access to 0xffffffff at address 0x11df:0x00006f82 (thread 0025), starting debugger...
Unhandled exception: page fault on read access to 0xffffffff bad address.

Any idea?

---

### Post by nowashburn on 2012-09-18
same here. have you found a fix?

---

### Post by nowashburn on 2012-09-18
I don't think the issue in my last comment had anything to do with the application. After upgrading to 1.5.13 from 1.5.11 I never created a new winebottle. I backed up the old wine directory, and then created a new one with: 

WINEARCH=win32 WINEPREFIX=~/.wine winecfg 

Then, I moved my files over to the new wine directory. everything now works fine.

---

