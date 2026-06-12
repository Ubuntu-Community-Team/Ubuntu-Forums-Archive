---
title: "Contents of /tmp not being deleted"
date: 2007-02-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by pseudonym on 2007-02-26
Hi,

I just noticed that my /tmp directory is not being emptied at shutdown or restart. To my knowledge, this directory's contents should be deleted by default when shutting down or rebooting a *nix system. Is this not the case in Ubuntu?

I'm using Xubuntu 64 with a custom 2.6.19 kernel. /tmp is not mounted separately, instead it resides on the default / , which on my system is a xfs partition. Here is the output of 'mount' - ```
/dev/sda2 on / type xfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sda1 on /boot type ext3 (rw)
/dev/sda6 on /home type xfs (rw)
/dev/sda8 on /media/data type xfs (rw)
/dev/sda9 on /media/share type vfat (rw,utf8,umask=007,gid=46)
/dev/sda7 on /media/video type xfs (rw)
```
Could the fact that I'm using xfs on / make a difference here? (I've used ext3 or reiserfs on / for all previous Linux distros).

I also have some GNOME libraries plus kdelibs installed (on Xubuntu). Could they perhaps have changed a setting?

If /tmp not being emptied is default in Ubuntu, can someone tell me how to change this? If it isn't default, what could be causing the problem and how can I fix it?

Thanks.

---

### Post by Dr Eigen on 2007-02-26
> **pseudonym said:**
> Hi,

I just noticed that my /tmp directory is not being emptied at shutdown or restart. To my knowledge, this directory's contents should be deleted by default when shutting down or rebooting a *nix system. Is this not the case in Ubuntu?


I don't think emptying /tmp every shutdown is a default on any *nix system I've ever worked on.  On my old Red Hat system there was (IIRC) a cron script to clean things up periodically.  I don't see a cron job in ubuntu, but there must be something that cleans up.

---

### Post by ferrit on 2007-02-26
I don't think that emptying of /tmp is standard fare on Linux. I have some experience with Solaris, and the /tmp directory for that (at least on Solaris 8/9) is actually its own little pseudo filesystem that is a bit of swap and physical memory. So this will definitely be emptied upon rebooting.

You could always create an init script to do this for you.

---

### Post by pseudonym on 2007-02-27
AFAIK /tmp is a tmpfs filesystem, like udev, and would normally be emptied on reboot/shutdown. At least it was like this on Debian. Looks like Ubuntu must be different (though it is of course Debian-based, but I can't see the need to modify how it handles /tmp).

I noticed there's no cronjob for emptying /tmp on this system. I think I'll just set one to resolve this issue. Thanks for the responses.

---

