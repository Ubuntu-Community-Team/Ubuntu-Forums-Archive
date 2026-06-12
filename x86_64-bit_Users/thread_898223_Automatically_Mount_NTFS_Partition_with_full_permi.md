---
title: "Automatically Mount NTFS Partition with full permissions"
date: 2008-08-23
forum: x86 64-bit Users
---

### Post by golfmania on 2008-08-23
Hi! I'm brand new on Linux & Ubuntu
As I didn't want to re-mount the drives each time I start the system, I tried the way explained on 

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

However, the permissions became 'READ ONLY'. I, then, no longer being able to save my work or download bittorent file onto these NTFS drives.

I formated Ubuntu partition and re-install Ubuntu. Now, I can cut/move/paste files between ext3 partition and ntfs partitions.

But it's inconvenience to re-mount drives everytime especially when you use bittorent client. IS THERE ANY WAY TO BOOT UP AND CAN AUTOMATICALLY MOUNT DRIVE WITH PERMISSION RETAIN???

Thank you!

---

### Post by dominiquec on 2008-08-23
Which steps did you follow?

Normally, you'll need to edit your /etc/fstab file to include a line for your NTFS partition.  You'll need to add the rw option and also make sure that you're the owner of the mount directory.

---

### Post by Ehtetur on 2008-08-25
Hi golfmania - can you post your /etc/fstab file so we can see what's going on...

If you have your NTFS filesystem, mount points, & permissions properly set in fstab, it will automount on boot... since you can mount the NTFS rw at times, it just sounds like maybe a setting is a bit off... should be easy enough to fix...  :twisted:

completely unrelated to your problem: watch your CAPS! :evil:

---

### Post by dominiquec on 2008-08-25
Eh heh, I think you mean Golfmania, Ehtetur.

---

### Post by Jouke74 on 2008-08-26
Try this: [http://ubuntuforums.org/showpost.php?p=5522749&postcount=7](http://ubuntuforums.org/showpost.php?p=5522749&postcount=7)

Best wishes, JJH.

---

### Post by bpl07 on 2008-08-26
> **golfmania said:**
> IS THERE ANY WAY TO BOOT UP AND CAN AUTOMATICALLY MOUNT DRIVE WITH PERMISSION RETAIN???


Install ntfs-config in synaptic package manager.

Then run it from Applications > System Tools > NTFS Configurational Tool

---

