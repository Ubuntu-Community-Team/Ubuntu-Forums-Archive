---
title: "[SOLVED] USB stick and mount problems"
date: 2008-05-09
forum: x86 64-bit Users
---

### Post by Tosa on 2008-05-09
I upgraded to 8.04 a few days ago. A couple of days ago there were some updates and among them I've noticed one named mount. After installing those updates my mount problems began...

Everything seems to work fine. When I insert a USB memory stick it's detected, but not mounted; I have to mount it manually, but it's not a big deal anyway.

The big deal is that after the USB stick is mounted all hard disks (except /) are unmounted! Further more, the memory stick is not mounted as a disk under media folder, but as **the **media folder. It's really annoying (I'm just trying to be polite...).

Help will be greatly appreciated.

---

### Post by IanW on 2008-05-09
The stick isn't named "media" by any chance?

---

### Post by Tosa on 2008-05-09
:) Thanks for trying!

No, the stick doesn't have any name. It's not happening with one stick only, but with every stick I've tried so far.

---

### Post by ASULutzy on 2008-05-09
How are you mounting it?

---

### Post by prosonik on 2008-05-09
Hi there.

I'm seeing the same thing for MTP devices, and certain USB devices. My Creative Zen, and my built-in compact flash reader on my display the same issue. I was looking into it a couple days ago.. I'm not seeing any errors in syslog, but i'm not seeing the devices detected either. 

my specs: 
Aspire 5100 model bl51, Hardy 8.04 64bit. It's a AMD integrated chipset. 

I don't have my devices on me right now, but I don't seem to recall seeing anything show up when i do a lsusb -vv

prosonik

---

### Post by Tosa on 2008-05-09
> **ASULutzy said:**
> How are you mounting it?

When I plug the memory stick in, the icon shows on my desktop. I right click on it and select the mount option from the menu. After that hard disks disappear from media folder and it only shows the content of the memory stick...

---

### Post by ASULutzy on 2008-05-10
Have you tried mounting it from the command line?

---

### Post by Tosa on 2008-05-10
No, I haven't. Actually I'm not sure how.
Before all this started, I would plug the memory stick in and it would mount automatically as *disk* folder under media folder. But, that *disk* folder would disappear when stick was unpluged, so I don't know where to mount it because the folder disk was created and removed by the system.

---

### Post by Tosa on 2008-05-12
It finally occurred to me to check fstab. At the end there was this line

 ```
/dev/sdd1 /media auto users,noauto,atime,rw,nodev,noexec,nosuid 0 0
```

and I am absolutely sure it wasn't there before the update...

Anyway I've removed it and everything is just fine again!

---

