---
title: "Help! Can't get dd to copy a partition to my ext. hdd!"
date: 2009-08-07
forum: x86 64-bit Users
---

### Post by oneofakindthe3rd on 2009-08-07
Ok, so I have 8.04 on a 64 bit system; I have a 200 GB SATA on it, with a 30 GB linux partition.  I also have a 1TB sata that I want to install.  

At the same time, I'm planning to wipe windows off the other 170gb, and format it - either for ext3, or ntfs (this goes for the 1tb drive as well - Another question - for media storage on a home network with both windows and linux, which is the better choice?)

I have a 500gb ext. hdd, that was fat 32.  I used gparted, formatted it to ntfs, ran a livecd session, and tried to dd.  I would copy my output, but its on the other comp.  Basically I kept getting variations on -

"dd: opening '/dev/sdb1/mainbackup.img': Not a Directory. "

i tried /mnt/sdb1, media/sdb1, I tried reformatting it to ext3, I tried mount the ext hdd through cli, even though it mounts itself automatically, and I read through every entry on dd support, mounting, dd copying, mkdir, what have you, until my eyes bleed.

Someone please help me figure out why I can't backup my damn parition, so if I nuke everything adding he new hdd, I don't have to spend another weekend getting the screens set up right:/.

Thanks in advance.

---

### Post by mikewhatever on 2009-08-07
There must be a space here '/dev/sdb1/mainbackup.img', in other words, not [s]opening '/dev/sdb1/mainbackup.img'[/s], but '/dev/sdb1 /mainbackup.img'. make sure the path is correct, because /mainbackup.img is currently going to the root directory and not to an external storage device.

Edit: I think I misunderstood. In case /dev/sdb1 is the partition you want to copy to, you need the mount point and not the device name. Verify the mount point with df -h command.

---

