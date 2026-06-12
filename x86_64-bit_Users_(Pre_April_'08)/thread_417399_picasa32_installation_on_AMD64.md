---
title: "picasa32 installation on AMD64"
date: 2007-04-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by vax on 2007-04-21
Trying to force installation I got the following:
hanan@ubuntu:~$ sudo dpkg --force-architecture -i picasa_2.2.2820-5_i386.deb
Password:
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 130023 files and directories currently installed.)
Preparing to replace picasa 2.2.2820-5 (using picasa_2.2.2820-5_i386.deb) ...
Unpacking replacement picasa ...
Setting up picasa (2.2.2820-5) ...
ldconfig: /usr/lib32/libaudio.so.2 is not a symbolic link

any idea how to overcome it?

---

### Post by jpeddicord on 2007-04-22
It looks like Picasa is trying to find a file that only 32-bit systems have. Forcing an install on this one will not work. You could try F-Spot, which is actually very similar to Picasa and works on x64.

You can also try a [chroot]("https://wiki.ubuntu.com/DebootstrapChroot") to get things working right.

Jacob

---

### Post by greensky on 2007-04-25
I was able to get it installed/working using the same exact command you used. Before that I installed Firefox32/flash using the instructions here ([https://help.ubuntu.com/community/FirefoxAMD64FlashJava)](https://help.ubuntu.com/community/FirefoxAMD64FlashJava)). I would see if all of the packages listed there are installed..

(sudo apt-get install ia32-libs ia32-libs-gtk linux32 lib32asound2)

-Greensky

---

### Post by vax on 2007-04-26
Firefox32 works OK
checked files they all exist....
It seems that the installer is expecting a link rather than a file

---

