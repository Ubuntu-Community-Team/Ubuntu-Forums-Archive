---
title: "DVD drive is mounted in chroot?"
date: 2006-01-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2006-01-29
A couple weeks ago I set up chroot so I could run Firefox with RealPlayer, Flash and so I could get Adobe Reader 7.0 installed. Today I read about a script to get libdvdcss installed, which supposedly might solve my problem getting DVD movies to play. So I ran the script. And then I opened Totem. And this time instead of instantly disappearing, Totem is still running. Hooray!

But when I tried to open a movie in the DVD drive Totem announced "Failed to Play Audio/Video Disc - Unexpected error status 256 while mounting /media/cdrom0." 

In fooling around trying to get Totem to see the DVD drive I remembered something else. For the past several days the eject button on the drive has not worked -- have to resort to the paper clip. And just now I discovered that evidently the DVD drive is mounted in /chroot/breezy/32bits/media/cdrom0. How did that happen? More important, how do I change it? I umounted it, but can't figure out how to remount it or where it is supposed to be mounted. If I type "mount /media/cdrom0" I get an error message telling me I must specify the file system. I typed "mount --help" but nothing in the resulting text helped me figure out what is wrong.

Now that I may actually have Totem ready to play a movie, how do I get it to read my DVD drive?

---

### Post by John Jason Jordan on 2006-02-04
I really need to get my DVD drive mounted back in the 64-bit world. Right now it is completely unusable because neither world can see it. I've read all the man pages and documentation I can find, but "mounting" must require the skills of a sorcerer. I just can't figure out how to get it mounted so the 64-bit world can see it. Can't it be mounted in both the chroot world and the 64-bit world? How do I do that?

When I type "mount" I get the following:

```
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
/home on /chroot/breezy/32bits/home type none (rw,bind)
/tmp on /chroot/breezy/32bits/tmp type none (rw,bind)
/dev on /chroot/breezy/32bits/dev type none (rw,bind)
/proc on /chroot/breezy/32bits/proc type proc (rw)
/media/cdrom0 on /chroot/breezy/32bits/media/cdrom0 type none (rw,bind)
/usr/share/fonts on /chroot/breezy/32bits/usr/share/fonts type none (rw,bind)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
```

Unfortunately, I don't understand much of what it says, except that it appears that the DVD drive is mounted in chroot. Can someone please help a dummy figure this out?

---

