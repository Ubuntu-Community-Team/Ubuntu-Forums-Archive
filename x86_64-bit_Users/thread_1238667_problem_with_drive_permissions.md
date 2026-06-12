---
title: "problem with drive permissions"
date: 2009-08-12
forum: x86 64-bit Users
---

### Post by Degradon on 2009-08-12
Hi all, 

I am pretty new at Linux. I searched all the documentation and forums and found someone that had a similar problem a year ago. I have installed Ubuntu 9.04 64bit. I have 4 hard drives, File System for the OS (around 18 GB), 147.1GB Media (both SCSI), 250.1 GB Media, NetMusic (111.8GB) (both IDE). I can read all 4 drives & the DVD writer, I can save to File System, I can write to DVD, but I can't save or write to the other 3 drives. I mounted them, unmounted them, checked permissions both ways and got the message: The permissions of "disk" could not be determined.

In the problem from 1 year ago the person trying to help asked for the output from the fstab file, but no solution was posted. I also had this problem with Ubuntu Server 8.04.3 LTS, so I decided to try the latest version. Here is the out put from my fstab file.

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=271fe294-3064-4b8c-ad2d-ead25a13066b /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=f293ce8c-7413-41e8-8cd4-a55ace3321f4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

This was with all drives mounted.

Any help would be greatly appreciated.

My computer is:

ASUS A8V motherboard
Opteron 165 dual core processor
2 GB RAM
ATI 9550PRO 256 MB Vid card
Promise Fasttrak 100 TX2 scsi controller card

---

### Post by Rizlaw on 2009-08-12
> **Degradon said:**
> Hi all, 

I have 4 hard drives, File System for the OS (around 18 GB), 147.1GB Media (both SCSI), 250.1 GB Media, NetMusic (111.8GB) (both IDE). I can read all 4 drives & the DVD writer, I can save to File System, I can write to DVD, but I can't save or write to the other 3 drives. I mounted them, unmounted them, checked permissions both ways and got the message: The permissions of "disk" could not be determined.


Degradon,

As you may or may not know, when you create/format new drives in Linux, you do it as root, so root is the owner of the new drive and you, as "user", don't automatically have any "user" permission to write to the drive. The same is true of Windows, except in Windows you don't notice the problem because you are always "root" (Administrator) in Windows.

What I do and recommend is that you individually mount each of the 3 drives and open a Terminal and use the command below to give yourself ownership of each drive:

		```
sudo chown -R username:username /media/Removable
```
  
Note: substitute your actual login username for "username"  & the name or label of the mounted drive in place of "Removable" in the above example.

This will give you ownership of the drive and the ability to read and write to the drive.

To find the mounted drive's ID info you can use:

```
sudo blkid
```

---

### Post by Degradon on 2009-08-12
Worked like a charm. Thank you very much. I am going to set it up as a file server. Thanks again.

---

