---
title: "can't mount cdrom0 in chroot"
date: 2006-04-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by OakRand on 2006-04-29
I've set up chroot and have it working except for being able to mount the cdrom.

When the /chroot/etc/fstab file is empty, I get the following message:
%mount: can't find /media/cdrom0 in /etc/fstab or /etc/mtab

I've tried adding the following lines to fstab:

/home /chroot/home none bind 0 0
/tmp /chroot/tmp none bind 0 0
/dev /chroot/dev none bind 0 0
/proc /chroot/proc proc defaults 0 0
/media/cdrom0 /chroot/media/cdrom0 none bind 0 0
/usr/share/fonts /chroot/usr/share/fonts none bind 0 0

but now get the error:
%mount: only root can mount /media/cdrom0 on /chroot/media/cdrom0

If I try sudo mount /media/cdrom0, I get:
%mount: mount point /chroot/media/cdrom0 does not exist

And lastly, if I try mounting from the none chroot environment, chroot can't see the mount.

---

### Post by OakRand on 2006-04-29
Nevermind. I just had to copy /etc/fstab to /chroot/etc/fstab. I can then mount from chroot.

---

