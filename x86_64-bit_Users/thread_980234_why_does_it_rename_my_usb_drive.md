---
title: "why does it rename my usb drive??"
date: 2008-11-12
forum: x86 64-bit Users
---

### Post by dd1linux on 2008-11-12
Hi all, first time posting here.  I can get through most problems myself by reading around but I haven't seen anything quite like this anywhere on here (please do correct me if I'm wrong, and I'm sorry).  

Anyway, I have an external HD I would like to mount so i nano'd fstab to include:
/dev/sdb1 ntfs-3g /media/Storage defaults 0 0

This worked one time, the next time I restarted my computer it did not automount, and I figured out it had renamed the device /dev/sdh1

So I added:
/dev/sdh1 ntfs-3g /media/Storage defaults 0 0 

to the fstab.

After the next restart, it did not mount again and it is now called /dev/sdc

This problem is driving me nuts, and I can't imagine why it comes up with a new name or device location or whatever for it everytime I restart.  Any help would be greatly appreciated.

---

### Post by cariboo on 2008-11-12
Instead of using the device number to mout your external drive, use the block id. To find the block id of the drive in a terminal run:

```
blkid
```

the output should look something likethis:

```
blkid
/dev/sda1: UUID="7E002ED0002E8F69" TYPE="ntfs" 
/dev/sda5: UUID="f22882e4-5e1f-483f-94b6-0212bb76b012" TYPE="swap" 
/dev/sda6: UUID="efccc4e7-3273-43d3-871c-1eb69aeaaa27" TYPE="ext3" 
/dev/sda7: UUID="9f702ef1-20bd-4aef-8f22-cd6830d83a50" TYPE="ext3" 
/dev/sdb1: UUID="3311c01c-be41-4fa7-962e-987f0123812d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="3d4a0ca8-b260-456b-82a5-70f71afda09e" SEC_TYPE="ext2" TYPE="ext3"
```

note the id of your extranl drive and use it.

Jim

---

### Post by dd1linux on 2008-11-13
Thank you!  That worked perfectly.  Any idea as to why it changed the name?

---

