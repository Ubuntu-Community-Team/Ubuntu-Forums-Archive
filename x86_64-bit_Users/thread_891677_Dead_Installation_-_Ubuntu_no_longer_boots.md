---
title: "Dead Installation - Ubuntu no longer boots"
date: 2008-08-16
forum: x86 64-bit Users
---

### Post by madad2005 on 2008-08-16
I had installed ubuntu 64-bit onto my hard drive as an iso image, and it all has worked fine for months. However, now it only gets as far as the bootup page with the side scrolling bar and then stops midway through.

I had a lot of data stored including some source code (not backed up.. doh!). Is there any way for me to access this data? Trying to mount it doesn't seem to work. Has anyone else had this problem at all, and is it recoverable?

Thanks for your help.

Regards,

Adriano

---

### Post by Stemp on 2008-08-16
Hi Adriano,

You try to boot up using the recovery mode in the grub menu ?

---

### Post by madad2005 on 2008-08-16
No, infact I haven't, although I probably should have by now. I'll give it a go in the morning. :-)

---

### Post by Sef on 2008-08-16
> I had a lot of data stored including some source code (not backed up.. doh!). Is there any way for me to access this data? Trying to mount it doesn't seem to work. Has anyone else had this problem at all, and is it recoverable?

With a Live CD, you should be able to access the data and get the information off.

---

### Post by madad2005 on 2008-08-17
I tried recovery mode and it also wouldn't boot, but at least it seems to have reported the problem:

run init: /sbin/init not found
kernel panic - not syncing: attempted to kill init


then it just stops. I haven't a clue what to do about this, but I'll attempt to get the data off using a liveCD. I would prefer to get this install working again though, as I downloaded a lot of software using synaptic.

Cheers for the help.

---

### Post by Crafty Kisses on 2008-08-17
What are your system specs, sounds like a possible hardware issue if you're having a kernel panic.

---

### Post by IntuitiveNipple on 2008-08-17
> **madad2005 said:**
> 
run init: /sbin/init not found
kernel panic - not syncing: attempted to kill init

That looks like the initial ram-disk (initrd) image isn't being loaded. That suggests the GrUB menu is incorrect or the files it points to have been changed.

Using a LiveCD start the system and open a terminal, then report the results of these commands:

List any auto-mounts the LiveCD found:
```

mount

```

List the devices:
```

for dev in $(ls -l /dev/disk/by-path/* | sed -n 's,.*\(hd.\|sd.\)$,/dev/\1,p'); do fdisk -ul $dev 2>/dev/null; done

```

Report any Linux ext2/ext3 file-system details:
```

for dev in $(ls -l /dev/disk/by-path/* | sed -n 's,.*\(hd.\|sd.\)$,/dev/\1,p'); do fdisk -ul $dev 2>/dev/null | sed -n '/83  Linux$/p' | cut -d" " -f 1 | while read dev; do tune2fs -l $dev; done ; done

```

---

### Post by madad2005 on 2008-08-18
I don't have time to do the liveCD check this week (I get married on Sunday so very busy), however, my image is stored on an external hard drive that appears to be working fine otherwise (in windows at  least). I always make sure it is unmounted from windows before trying to boot ubuntu, but clearly that's where the problem lies then. 

I'll get that extra information here as soon as I can.

---

