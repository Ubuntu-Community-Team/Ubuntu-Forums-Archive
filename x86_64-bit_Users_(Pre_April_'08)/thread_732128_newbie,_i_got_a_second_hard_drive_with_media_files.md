---
title: "newbie, i got a second hard drive with media files"
date: 2008-03-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by cowboyup02119 on 2008-03-22
hello to all!!!

i just killed vista because i got the blue screen of death six times, while installing and doing updates....

i install everything in my first hard drive and did all the updates and got all the drivers...thanks to developers who including everything in the updates you all are awesome!

i have a second hard drive 500GB with only media on operating system on it. when i go to places>computer

i can see my second hard drive but when i click to open it says CANNOT MOUNT VOLUME. 
> UNABLE TO MOUNT THE VOLUME "MEDIA FILES" thats the name of second hard drive, i have like 10 GB of music and over 200GB of DVD's saved there. is there any way to recognize it and use my media on there...

thanks to all you can help and god bless!

---

### Post by cowboyup02119 on 2008-03-22
please any help. its just a second hard drive with files on it of music and videos. cant access it,, says unable to mount volume

---

### Post by eluminx on 2008-03-22
you could try going to System-->Administration-->storage device manager and see if you can mount the volume from there.  If else fails you can always do a sudo mount -a and see if that mounts the drive as well.

---

### Post by Rivendell63 on 2008-03-28
Hi,
Don't quote me on this, but even if you manage to get the drive mounted you may find that you can't make any changes to the content due to permissions issues unless maybe it's in NTFS or FAT32 format.

---

### Post by Jouke74 on 2008-03-29
There are two possibilities of a filesystem on that drive being used indeed, namely FAT32 and NTFS. NTFS is more likely. I assume that the drive was left "unclean" or "dirty"  in Vista with the blusecreen and that is a problem. In that case the NTFS-3g driver won't mount it under Ubuntu. If you would have a dualboot a simple reboot and chkdsk and correct errors under Vista should make it possible to read the drive.

If you have only Ubuntu now you have a problem. There is however a possibility use: 
ntfsfix /dev/sda2
ntfs-3g /dev/sda2 /media/X -o force

Where /dev/sda2 should be replaced by the HD directory of your dirty drive.
And /media/X by the mounting point of your dirty drive, likely "media files". 
If the program is not installed use sudo apt-get install ntfsprogs to get it.

You could also try to force load it first without fixing, but I assume it wont work too. Note: I am not taking responsibility in case you loose data this way!! If you have a FAT32 drive mention this and don't use the above commands, they won't work.

---

