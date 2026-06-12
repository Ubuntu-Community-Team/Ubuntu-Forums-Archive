---
title: "ubuntu 8.10 64bit gxine dvd path"
date: 2009-01-07
forum: x86 64-bit Users
---

### Post by klein de usa on 2009-01-07
hi 
can someone explain how to find the path or how to create a symbolic link to my dvdrom and the path to my dvd+-rw?

gxine set up wizard is giving me these.

FAILED - could not access dvdrom: /dev/dvd

Either create a symbolic link /dev/dvd pointing to your cdrom device or set your cdrom device in the preferences dialog.


FAILED - Could not read stats for /dev/dvd.

If you are using the ide-cd module ensure
that you have the following entry in /etc/modules.conf:
options ide-cd dma=1
 Reload ide-cd module.
otherwise run hdparm -d 1 on your dvd-device.

---

### Post by cariboo on 2009-01-07
On my system /dev/dvd is linked to /dev/scd0. To check on your system, in a Applications-->Accessories-->Termianl type:

```
ls -l /dev/dvd
```

I haven't used xine in a while, but using vlc I just set the dvd drive to /dev/scd0.

Jim

---

