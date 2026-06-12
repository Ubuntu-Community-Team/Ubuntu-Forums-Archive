---
title: "USB doesn't automount after using gparted in SuSE 10.3"
date: 2008-01-11
forum: openSUSE and SUSE Linux Enterprise
---

### Post by some-guy on 2008-01-11
I installed gparted to reformat a flash drive, but after that gparted crashed and since then gnome and KDE don't automount **any** flash drives, on any account.

If I run
```
su
mkdir /media/flash-drive
mount /dev/sdb1 /media/flash-drive

```

It works, but all the permissions are read-only and it's a big hassle, can anyone help me? :(

See my signature for the computer specs
this is the *main* one

Here's the error message from gparted when it crashed
```
# gparted
======================
libparted : 1.8.7
======================
Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Unable to open /dev/sr0 - unrecognised disk label.
Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Unable to open /dev/sr0 - unrecognised disk label.
glibtop: cannot find btime in /proc/stat: Resource temporarily unavailable
```

---

### Post by lambchops468 on 2008-01-14
Hi, I have the same exact problem...but I didn't know it was because of Gparted's crash.

Now we have to fix this.

I already tried posting in [linuxquestions.org]("http://www.linuxquestions.org/questions/susenovell-60/usb-automount-doesnt-work-613386/")

edit: whoa...fixed it: [https://bugs.launchpad.net/gparted/+bug/134712](https://bugs.launchpad.net/gparted/+bug/134712)

---

