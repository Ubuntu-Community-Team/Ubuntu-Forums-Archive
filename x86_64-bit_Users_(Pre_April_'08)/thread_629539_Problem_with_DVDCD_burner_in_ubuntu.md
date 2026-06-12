---
title: "Problem with DVD/CD burner in ubuntu"
date: 2007-12-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by CarstenA on 2007-12-02
Hi

I am using Ubuntu 7.04 - the Feisty Fawn (64 bit version)

I got the following problem, I cant burn DVDs or CDs when I insert a cd I get this:

Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

mount: block device /dev/hdc is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/hdc,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so



carsten@carsten-laptop:~$ dmesg | tail
[   40.033265] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6
[   40.033268] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x12
[   40.034587] powernow-k8: ph2 null fid transition 0xa
[   76.744560] NET: Registered protocol family 10
[   76.744643] lo: Disabled Privacy Extensions
[   81.207424] eth0: no IPv6 routers present
[ 2160.783755] Losing some ticks... checking if CPU frequency changed.
[ 2983.774248] attempt to access beyond end of device
[ 2983.774253] hdc: rw=0, want=68, limit=4
[ 2983.774257] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
carsten@carsten-laptop:~$ 

DVDrom, CDroms are working as far as reading.

Any good advice? And please explain how to do it ;) I am really new to Ubuntu...

Thanks in advance !

---

### Post by can8dnSix on 2007-12-04
It should not be able to "mount"? If I am correct, you can't mount a blank CD-R as there is no filesystem on the CD-R. I could be wrong, but I am about 80% confident in what I am saying. What do you have in your fstab? 

Lindis.

---

### Post by crjackson on 2007-12-04
> **can8dnSix said:**
> It should not be able to "mount"? If I am correct, you can't mount a blank CD-R as there is no filesystem on the CD-R. I could be wrong, but I am about 80% confident in what I am saying. What do you have in your fstab? 

Lindis.

You are correct, you don't mount  blank media.

---

