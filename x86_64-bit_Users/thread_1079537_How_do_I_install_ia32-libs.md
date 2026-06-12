---
title: "How do I install ia32-libs?"
date: 2009-02-24
forum: x86 64-bit Users
---

### Post by kungfujoe1110 on 2009-02-24
This seems simple, but I must be missing a step somewhere. First off, I'm on intrepid, running an Nvidia card 177.

KFJ@BobTheLinuxComputer:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs

Do I need a deb or something?

Thanks
KFJ

---

### Post by oldos2er on 2009-02-24
Make sure you have the universe repository enabled.

---

### Post by kungfujoe1110 on 2009-02-24
I do. Thanks for the quick reply

---

### Post by SuperSonic4 on 2009-02-24
It works fine on mine, have you tried enabling Multiverse?

```
lee@lee-desktop:~$ sudo apt-get install ia32-libs
[sudo] password for lee:
Reading package lists... Done
Building dependency tree
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
lee@lee-desktop:~$
```

---

### Post by kungfujoe1110 on 2009-02-24
main, uni, res, and multiverse are all enabled

---

### Post by jespdj on 2009-02-24
Try
```
sudo apt-get update
```

---

