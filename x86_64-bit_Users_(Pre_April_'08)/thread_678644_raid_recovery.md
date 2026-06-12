---
title: "raid recovery"
date: 2008-01-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by LoneWolfJack on 2008-01-26
ok, this is probably the wrong forum but I didn't know where exactly to put it.

I have an adaptec hardware raid controller with 4 SCSI disks. One of the disks broke, which wasn't a problem as I had a spare disk. During rebuilt, adaptec storage manager (ASR) closed with an error and the array seems to have gone offline exactly at that time.

during reboot, the controller now displayed the raid as failed because it can't find any of the three disks left in the array.

so I booted from a SATA disk into windows and from there, accessed ASR, which shows the three disks as OK but with "logical segment missing". I assume that when ASR crashed, it failed to properly finish some sort of command that left those segments corrupted.

my first idea was to recover the raid by software, which apparently is possible if the data is still on the drives and the drives are OK from a technical standpoint. the problem with that is, no program I found was able to see the SCSI disks, which is probably because they need to be re-initialized to function properly (even though ASR sees them anyway).

my second idea was to create images of the three drives and then recover the data from those images. problem there is that blasted ASR doesn't even offer something simple as creating an image of a drive.

so I'm asking for help here... I'd need to either find some magical way to restore those logical segments or to find a way to make windows see my drives. if it can't be done for windows, ubuntu works, too, as long as I can work from the live CD as the PC with the raid array was my ubuntu machine...

I'm also wondering if I should initialize the drives... even though initializing is usually considered fromatting, it ain't. it just writes something like a FAT to the disk, so it's quite possible that I could initialize and then see the disks in windows which would enable me to create images. but this is a last resort.

thanks for any help you can provide.

---

### Post by aikiwolfie on 2008-01-26
Ubuntu has the software you need to make the images and then recover your data.

[https://help.ubuntu.com/community/DataRecovery?highlight=%28Testdisk%29](https://help.ubuntu.com/community/DataRecovery?highlight=%28Testdisk%29)

Was the array RAID-0? If so then your data could be lost as one of the original drives is gone.

---

### Post by LoneWolfJack on 2008-01-26
thanks for trying to help.

there's a (with any luck) perfect workaround for people that may have a similar problem. note that the following instructions are intended for adaptec raid controllers (even though they might work for others as well) and should be considered a last resort.

Both options only work if you somehow lost your raid definitions or if the controller failed, they will NOT work if your array went offline because of failing disks.

> 
Option A:

Open ASR and right click the logical drive that has failed. Choose "force online" from the menu. With any luck it will bring the array back online. According to adaptec, you should nevertheless set up a new raid array as soon as you have saved your data.



> 
Option B:

This should work for most raids. 
1. delete the logical drive that has failed
2. initialize all drives (according to adaptec, their controllers write raid data to the first 128 and last 512kb of a disk and initializing just removes this data)
3. create a new raid with the EXACT SAME options (number of drives, stripe size, etc.) as the one that has failed
4. Choose "quick init" to set up the array

Given you don't have a drive failure and you didn't write to the discs since your raid disappeared, your raid should be accessible again now (even though it will most likely not be bootable).

Again, set up a new raid after saving your data.


> 
As a final note:

Always make sure your backup script works properly even if you're running raid 5 or 10. :(


---

