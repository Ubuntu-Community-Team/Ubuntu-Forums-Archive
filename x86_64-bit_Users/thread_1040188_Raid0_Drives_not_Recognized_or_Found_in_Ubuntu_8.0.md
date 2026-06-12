---
title: "Raid0 Drives not Recognized or Found in Ubuntu 8.07 or 8.10 Gnome Environments"
date: 2009-01-15
forum: x86 64-bit Users
---

### Post by ronparent on 2009-01-15
This may not be exclusively an x86 64bit issue so you may redirect me is so fit. I have a AMD 64 box with a pair of SATA disks configured in a raid0 array and containing an intact WinXP install. I have been keeping it that way by installing Ubuntu 8.10 on dedicated partion on a separate IDE disk. So far, so good. With the much appreciated help of the Absolute Beginner Forum I have been able configure grub on the IDE disk to dual boot sucessfully. However, booted in Ubuntu I cannot see or access the raid0 filesystems. 

Forget about mdadm for a while. After much mucking around with a terminal (sometimed three or more at a time so that I can view the relevant man while I attempt to construct coherrant commands) I have discovered the following facts. 1) The array is activated on each boot as found in /dev/mapper and date/time stamped. 2) All of the array elements are properly identified in the various /dev/disk/ directories. 3) I have been more sucessful in discovering details of the array with dmraid than mdadm. 4) All elements of the array are mountable with the command: sudo mount -t auto /dev/mapper/nvidia_aebhdfib7 /target

In this case, the WinXP drive f:\Files structure is mounted in /target. I have concluded that if the bootup scripts were working properly the individual drives would be mounted at /// and be identified as separate drives with the proper labels (as found in /dev/disks/by-label). So how do I fix??

I have found Linux a beguiling alternative to Windows from Redhat (early 80's) thru Suse (90's) into Ubuntu 8.07 last year. Although Ubuntu has been the most promising distribution to date, I have literaly grown old waiting for Linux to arrive! Any help in getting full functuality into my install before I die would be much appreciated.

---

### Post by cariboo on 2009-01-15
Mount your array in fstab using something similar to this:

```
/dev/mapper/nvidia_ifdejefh1	/home/storage	ext3	relatime	0	1

```

Using a similar command to the above the array will be mounted at boot.

You will of course have to to change the ext3 to ntfs-3g.

Just a qestion, but why would you want to mount the elements of your array seperately?

Jim

---

### Post by ronparent on 2009-01-15
Many thanks Jim. I suspected as much, but wasn't too sure of the specific syntax. I do have my work cut out for me though because some of the drive references already in fstab (the raid array is absent) seem to be in error. I'll have to feel my way and let you know what happens.

In answer to your question, I don't. But right now they aren't mounted at all on boot - or mountable in nautilus. I would like to see them in the nautilus based file system and access selected data drives as needed. Apparently this wasn't accomplished during installation rendering the raid drives inaccessible except through terminal commands which I had no knowledge on how to apply until now. Hopefully your suggestion will accomplish that.

---

### Post by ronparent on 2009-01-15
Jim:

I used a varient of your code to plant the raid set file structure in various /WinXP corresponding subdirectories I created in the Filesystem root. This is a GREAT workaround to make the Win file structure accessible. It begs the question however why aren't these drives showing up for mounting at the /// directory ?

Again, much thanks for your help.

---

