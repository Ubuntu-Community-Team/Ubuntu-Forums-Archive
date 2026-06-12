---
title: "how do I mount a windows partition?"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by digisoft on 2008-04-26
Hi, When I first installed Ubuntu I had an icon that let me go right into my windows partition, but I rebooted with a USB drive attached and ever since that I can't seem to figure out how to get the windows partition mounted again.

---

### Post by snafilter on 2008-04-26
So you don't have your Windows partition listed under Places, Removeable Media?

---

### Post by digisoft on 2008-04-26
Under "places" I don't see removable media.

---

### Post by ASULutzy on 2008-04-26
Usually Ubuntu mounts all your stuff under /media/

If you need to mount it manually you'll have to first find the partition you want to mount. It'll be /dev/hda1 or /dev/sda1 or /dev/sdb1 etc...

Once you figure out which of those is your windows partition (you can use fdisk to look, fdisk /dev/hda or /dev/sda or whatever the different hdletter or sdletter things you see in /dev/

So let's say my Windows install was on /dev/sdc1 I would type

```
 sudo mount /dev/sdc1 /media
```

---

### Post by digisoft on 2008-04-27
I looked in media and I don't see it, just the dvd drive and disk, and thats the linux files in disk. This is a latop, only one internal hard drive, what would be the command to mount it? It's a PATA drive if that helps. Also, this Unbuntu install was done through windows so windows has the main partition.

Thanks

---

### Post by digisoft on 2008-04-27
this worked: sudo mount /dev/hda1 /media

Will I have to mount it every time I reboot?

---

