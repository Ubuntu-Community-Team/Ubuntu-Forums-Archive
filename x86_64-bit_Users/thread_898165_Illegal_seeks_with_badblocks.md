---
title: "Illegal seeks with badblocks"
date: 2008-08-22
forum: x86 64-bit Users
---

### Post by NFITC1 on 2008-08-22
I've got a laptop HD that I'm pretty sure has bad clusters. I tried to fix it with Windows XP's scandisk, but it wasn't getting anywhere (stuck in Phase 4 overnight with no progress). So I'm trying to use badblocks to run a sector-by-sector scan to see which ones are bad. I'm not sure if it's working at all though. It seems no matter what I select for a starting sector it doesn't do anything. It's connected using a USB enclosure. Here's the general output:

```
Laptop-Name:~$ sudo badblocks -s /dev/sg4 117210240 1000
last_block = 117210240 (117210240)
from_count = 1000
badblocks: Invalid argument during ext2fs_sync_device
Checking for bad blocks (read-only test): badblocks: Illegal seek during seek
           1000/      117210240
```

I've tried a few starting numbers from 0 - 1000 and it all works the same. Nothing happens, it just hangs there. The light on the enclosure stays green (no activity) when it starts and occasionally flashes to red (disk active).
Is there anything else I can use to either test for bad sectors or retrieve what data I can off of this drive?

---

### Post by prshah on 2008-08-23
> **NFITC1 said:**
> 
```
Laptop-Name:~$ sudo badblocks -s /dev/sg4 117210240 1000
last_block = 117210240 (117210240)
from_count = 1000
badblocks: Invalid argument during ext2fs_sync_device
Checking for bad blocks (read-only test): badblocks: Illegal seek during seek
           1000/      117210240
```
Is there anything else I can use to either test for bad sectors or retrieve what data I can off of this drive?

If you don't specify a block size, the block size defaults to 1024. In that case, you have specified lastblock as 11 terabytes (I think...)

However, if you are using badblocks to check the hard disk you should be aware that badblocks does not perform any repair/recovery. In this case, you should use```
sudo fsck.ext2 -c -v /dev/sg4
``` Of course this assumes your external hard drive is ext2/3; unfortunately ntfs recovery is not yet available.

You can also try a live Windows CD.. search Google for BartPE.

---

### Post by Loaded.len on 2008-08-23
If there's still data on this drive you would like to try and salvage, might I make a suggestion that you do 

```
sudo apt-get install dd_rescue
sudo ddrescue /dev/sg4 /[SOMEWHERE YOU HAVE ENOUGH SPACE TO MAKE AN IMAGE]
```then mount that image to mess with.  Otherwise, you run the risk of that HDD becoming so degraded that A) either no data can be got from it, or B) you won't be able to POST with it connected to your system.

You can mount the image by first doing an```
sudo  fdisk -ul /[NAME OF IMAGE]
```that will tell you the starting block of the partition you want to recover and the sector size

then doing ```
sudo mount -o loop,offset=$((NN*XX)) /[NAME OF IMAGE] /[MOUNT POINT]
``` where NN is the start of your partition, XX is the sector unit size.

then you can use testdisk or photorec or whatever suits your fancy without worrying about how much longer that drive is going to keep spinning.

---

