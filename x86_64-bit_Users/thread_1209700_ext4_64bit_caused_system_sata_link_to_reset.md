---
title: "ext4 64bit caused system sata link to reset"
date: 2009-07-10
forum: x86 64-bit Users
---

### Post by azelter on 2009-07-10
I installed a fresh version of Ubuntu 9.04 64bit onto my system (hardware:
Intel(R) Core(TM) i7 CPU, 9GB RAM)
Installation seemed to go fine and I spent a day configuring the computer as I wanted it.
When I installed I chose ext4 filesystem for the whole harddrive.
I begun to notice very long delays and unresponsiveness in the system as a whole. Looking at the error log I saw the SATA link being reset all the time.Things like the clip from the message log at the end of this post began appearing. 
I was running Kernel  2.6.28-13-generic #45-Ubuntu SMP

To cut a log story short, pulling the disk out and connecting it via usb also cause problems after some time.

In the end I managed to copy the data off the disk (between resets) and reformat the disk with ext3 and copy the OS back on. The system is now running fine.

It took me 2 days of troubleshooting to figure out the problem as the ext4 file system. I'm just posting this here in case anyone else runs into similar problems - perhaps it will save them some time.

ERROR MESSAGES WHEN SATA DRIVE PLUGGED IN DIRECTLY:

Jul  9 13:53:02 devcore kernel: [ 1255.930190] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  9 13:53:02 devcore kernel: [ 1258.424520] ata2.00: configured for UDMA/133
Jul  9 13:53:02 devcore kernel: [ 1258.424530] ata2: EH complete
Jul  9 13:53:02 devcore kernel: [ 1260.677112] ata2.00: configured for UDMA/133
Jul  9 13:53:02 devcore kernel: [ 1260.677121] ata2: EH complete
Jul  9 13:53:02 devcore kernel: [ 1263.424541] ata2.00: configured for UDMA/133
Jul  9 13:53:02 devcore kernel: [ 1263.424550] ata2: EH complete
Jul  9 13:53:02 devcore kernel: [ 1265.669216] ata2.00: configured for UDMA/133
Jul  9 13:53:02 devcore kernel: [ 1265.669225] ata2: EH complete
Jul  9 13:53:02 devcore kernel: [ 1267.916576] ata2.00: configured for UDMA/133
Jul  9 13:53:02 devcore kernel: [ 1267.916586] ata2: EH complete
Jul  9 13:53:02 devcore kernel: [ 1270.336520] ata2.00: configured for UDMA/133
Jul  9 13:53:02 devcore kernel: [ 1270.336531] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul  9 13:53:02 devcore kernel: [ 1270.336535] sd 1:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jul  9 13:53:02 devcore kernel: [ 1270.336539] Descriptor sense data with sense descriptors (in hex):
Jul  9 13:53:02 devcore kernel: [ 1270.336541]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jul  9 13:53:02 devcore kernel: [ 1270.336549]         0b 04 47 4c 
Jul  9 13:53:02 devcore kernel: [ 1270.336552] sd 1:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jul  9 13:53:02 devcore kernel: [ 1270.336573] ata2: EH complete
Jul  9 13:53:02 devcore kernel: [ 1270.403280] sd 1:0:0:0: [sda] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
Jul  9 13:53:02 devcore kernel: [ 1270.403492] sd 1:0:0:0: [sda] Write Protect is off
Jul  9 13:53:02 devcore kernel: [ 1270.404426] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul  9 13:53:02 devcore kernel: [ 1270.404878] sd 1:0:0:0: [sda] 1250263728 512-byte hardware sectors: (640 GB/596 GiB)
Jul  9 13:53:02 devcore kernel: [ 1270.405087] sd 1:0:0:0: [sda] Write Protect is off
Jul  9 13:53:02 devcore kernel: [ 1270.405542] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

ERROR MESSAGES WHEN SATA DRIVE PLUGGED IN VIA EXTERNAL USB:
Jul 10 09:08:47 muumimamma kernel: [60283.034843] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
Jul 10 09:08:49 muumimamma kernel: [60285.587129] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
Jul 10 09:08:49 muumimamma kernel: [60285.587135] Info fld=0x0
Jul 10 09:08:49 muumimamma kernel: [60285.587143] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
Jul 10 09:08:52 muumimamma kernel: [60287.971671] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
Jul 10 09:08:52 muumimamma kernel: [60287.971677] Info fld=0x0
Jul 10 09:08:52 muumimamma kernel: [60287.971680] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
Jul 10 09:08:54 muumimamma kernel: [60290.189473] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
Jul 10 09:08:54 muumimamma kernel: [60290.189479] Info fld=0x0
Jul 10 09:08:54 muumimamma kernel: [60290.189481] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
Jul 10 09:08:56 muumimamma kernel: [60292.740767] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
Jul 10 09:08:56 muumimamma kernel: [60292.740774] Info fld=0x0
Jul 10 09:08:56 muumimamma kernel: [60292.740776] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
Jul 10 09:08:59 muumimamma kernel: [60294.959562] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
Jul 10 09:08:59 muumimamma kernel: [60294.959568] Info fld=0x0

---

### Post by paulisdead on 2009-07-11
Did you run the hard drive manufacturer's disk diagnostics to rule out hardware failure?  I know you said the issue hasn't been happening under ext3, but you should still rule out hardware failure.  It is possible you've just masked the problem by switching filesystems, though it could be a bug.  Always run the long test from the manufacturer. If the manufacturer doesn't make their own diagnostic CD you can download, then just use seatools, since it will work on just about any drive.

I've been running 3 systems on ext4, but only one is 64bit.  I've not seen that on any of my systems, though my 64bit system has been running the 2.6.30 kernel.  I'm on a P45 motherboard, but I think the southbridge is the same as on yours.

---

### Post by azelter on 2009-07-11
The drive does indeed have a few unreadable sectors and does not make it through a long SMART test without a read error, however, the SMART overall health check currently passes.
So the drive is on the way, out - but I've dealt with alot of dying drives (too many) and they can often run happily for months with those kind of errors and give no problems that would be apparent unless you looked at the SMART info of the drive (which I always do).
I'm not convinced that this is the reason for the symptoms I described but am too ignorant of filesystems to be sure. I do know that all modern harddrives and filesystems should be able to workaround a few unreadable sectors.
Do you think ext4 is so much more sensitive to such issues - in that case it would be a worse choice than ext3 in any system where stability is more important than speed.

---

### Post by paulisdead on 2009-07-11
A SMART failure and bad sectors during the long test is enough for a manufacturer to consider the drive defective and qualify it for warranty replacement.  You should RMA it, and let us know what happens with a new drive.

---

### Post by azelter on 2009-07-11
Thanks. I am intending to RMA it. I'm waiting for a second to arrive first. Not sure if I'll have the time to switch back to ext4 again though - also, I do prefer a fs that is more tolerant to drive errors over one that is less tolerant.
I'll post back if I learn more.

---

### Post by theozzlives on 2009-07-11
Just because a fs ignores drive errors doesn't mean the data can't get corrupt. If it ignores bad sectors, it might try to write to one. I've been running ext4 (32 bit) on two systems without a hitch.

---

### Post by azelter on 2009-07-11
So if the fs knew about the errors, why do you think I got the SATA (or USB) resetting all the time, and not a more informative error? Do you then think this is a fault of ext3 and that it is less safe? I suppose I should try ext4 on a good drive and see - still I feel it's dangerous as I very nearly never managed to get the data off the ext4 fs in the first place. It took a lot of work. Once I reformated to ext3 and put the data back everything seems to be running smoothly.

---

### Post by paulisdead on 2009-07-12
It's up to you what you want to use.  I admittedly am not ready to entrust ext4 on my production machines at work, and keep my home server as ext3.  My laptop, desktop, and htpc at home all run ext4 though, since I backup anything important to my server, so it's not a big deal if something terrible were to happen on those machines.  So, ya, I'd say if you can afford to lose the data on the ext4 partitions, it's well worth it to play around with.  So far for me, it's been great and stable, but I want to see it mature and run in the wild longer before I'd trust it to anything really important.

---

### Post by jefelex on 2009-07-13
Ya - I always trust the tried and true systems for anything important - I will try the ext4 sooner or later, but I'd like to try it on a separate drive/partition.  Question is, can I do that? mix filesystem types on different hard drives in the same computer?  I'll have to start reading (again) :-k

John

---

### Post by paulisdead on 2009-07-13
> **jefelex said:**
> Ya - I always trust the tried and true systems for anything important - I will try the ext4 sooner or later, but I'd like to try it on a separate drive/partition.  Question is, can I do that? mix filesystem types on different hard drives in the same computer?  I'll have to start reading (again) :-k

John

Sure, you can do that.  The installer should setup the fstab fine for you if it's a new install and you mix file systems for different partitions.  If you're doing it manually after you've installed, you just need to set the correct filesystem in /etc/fstab.

---

