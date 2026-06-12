---
title: "successful ATI Radeon Mobility HD 3650 install on Ubuntu 9.04 - 64bit"
date: 2009-06-21
forum: x86 64-bit Users
---

### Post by Blue88 on 2009-06-21
After trying to get this to work for hours on Fedora Core 11, I installed Ubuntu 9.04 64-bit, then immediately did *only* the following.

1.  System->Administration->Update Manager; Update all packages.
2.  sudo apt-get install fglrx
3.  sudo apt-get install system-display-config
4.  sudo X --configure
5.  aticonfig --initial -f

Obviously step #4 is not necessary since I didn't actually run it, but I wanted to post exactly what I did starting from the first bootup.  Probably only steps 1, 2 and 5 are necessary.  Now glxinfo | grep 'vendor' reports the following on my Toshiba Satellite:

server glx vendor string: ATI
client glx vendor string: ATI
OpenGL vendor string: ATI Technologies Inc.

I verified with Alien Arena that hardware acceleration actually is working.

---

### Post by Th3_uN1Qu3 on 2009-06-21
You will get even better results by installing the latest version directly off ATI's site. The one in the repository is 2 revisions behind (8.6.0 vs 8.6.2). 

**Make sure you have lib-ia32 installed else your video will be broken upon reboot!**

Download the .run file, open a terminal, navigate to the folder where you downloaded it, key in
```
chmod +x ati-driver-installer-9-6-x86.x86_64.run
sudo ./ati-driver-installer-9-6-x86.x86_64.run
``` and you're good to go. This version plays nicer with Compiz and allows to run most games and OpenGL apps without having to disable Compiz. :)

---

### Post by Blue88 on 2009-06-22
I may try that later and hopefully it will work, however, many people such as myself have had the ATI drivers cause black-screen on bootup with the Mobility HD 3650.  I know for sure that this happened in FC11, so I only tried the fglrx drivers in Ubuntu.  FC11 is seems to be missing a 64-bit package for akmod-fglrx, so this wasn't an option at the time.

I have tried various desktop features and 3D games, as well as the ATI config tool, and everythign seems to work fine.

---

### Post by tenmoi on 2009-06-23
> **Th3_uN1Qu3 said:**
> You will get even better results by installing the latest version directly off ATI's site. The one in the repository is 2 revisions behind (8.6.0 vs 8.6.2). Download the .run file, open a terminal, navigate to the folder where you downloaded it, key in
```
chmod +x ati-driver-installer-9-6-x86.x86_64.run
sudo ./ati-driver-installer-9-6-x86.x86_64.run
``` and you're good to go. This version plays nicer with Compiz and allows to run most games and OpenGL apps without having to disable Compiz. :)

If anyone without the lib-ia32 already in place should do as you advise, they will be dropped to a black box on reboot.

That's the way to go with debian.
Ati just sucks. They can't even provide a proper 64 bit driver.:confused:

---

### Post by Th3_uN1Qu3 on 2009-06-23
> **tenmoi said:**
> If anyone without the lib-ia32 already in place should do as you advise, they will be dropped to a black box on reboot.

Thank you for the info, edited. ;)

---

