---
title: "Formatting an external hard drive"
date: 2008-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by buntu_hugenewbie11 on 2008-01-15
I am formatting a new external hard drive.
I am running dualboot Gutsy 64 bit and Windows XP.
Unfortunately I need both systems.
I want to format this new drive to be half ext3 and the other half to be NTFS.
On my internal hard drive I used gparted off a cd and successfully formatted my drive in this fashion (plus a swap drive).
I have a few simple questions about this procedure:
1. Do I want this drive to have a primary partition or an extended partition ? (I assume primary makes it a bootable drive which is unnecessary for me, but let me know if I am out to lunch please)
2. I installed gparted via a repo but I cannot choose the NTFS option, how can I do this?
3. Are there optimal partition sizes? (I know this used to be an issue with FAT32 but is it on these other formats?)

---

### Post by prince_niceguy on 2008-01-15
1. Yes primary is required only for boot so logical should be fine.
2. Gparted will not be able to make it ntfs. you will have to make it fat32 and then use convert utility in windows to make it ntfs. I will keep it fat32 personally as it is easier to access in linux.
3. I am not sure about optimal size but fat 32 has a limitation but I am having 65GB of fat32 on my box.

---

### Post by PuterT on 2008-01-15
1. Use XP , go to Computer Management  to create an extended partition, then a logical partition with NTFS. Leave the rest of the drive unallocated.

2. Reboot into Ubuntu, run gparted to create an ext3 partition.

3. No conversion utility needed

---

### Post by rechick on 2008-01-15
Unless you need the special features of NTFS (permissions, etc, files greater than 2 GB) fat32 provides a more universal format which can be read and written from all windows platforms, linux and even MAC.

---

### Post by buntu_hugenewbie11 on 2008-01-16
Ya I am not interested in FAT32. My internal drive has both ext3 and NTFS and I love how well it works.  I often end up with files over 4gigs as well.
In gparted: How come when I choose an extended drive I don't get to pick a format?
Also, how do I set-up permissions after formatting the drive? (I always have issues with permissions in linux)
And can someone recommend a good backup utility? (I tend to use kde or command line tools)
Thanks for all your help.

---

### Post by PuterT on 2008-01-16
You'll first need to create the extended by clicking apply. Now that you have the extended created, you can create a logical partition that can be formated to ext3.

When logged in as a user, you only have permissions for limited folders and files on the root partition. That's why Linux is so secure. The ext3 partition you're creating won't be a root partition, just a  partition for storage.

I use Acronis 10. After installing, create the bootable Rescue Media CD. Boot from this CD to image both Linux and XP, saving them onto your external drive.

---

### Post by buntu_hugenewbie11 on 2008-01-16
What about backup utilities for linux?

---

### Post by Bokonon on 2008-01-17
I use tar :)

More seriously tho, I guess it depends on what you want to do.  Since you use the command line, I assume you know where the stuff you want to backup is.

Really it is just determine what kind of backup strategy you want and then implement it.  I just tar (not zip) my movies/photos and other pre-compressed stuff manually when I have time and it hasn't been done in a while.  I tar/zip my documents and other stuff. ->  .tgz

If you want it more automated, you could make a script and then setup a cron task to do it for you periodically.  I do that twice a week on my mysql data.  You could set it up to purge old data after a while, but I tend to do that manually since there really isn't much that gets automatically backed up.

I put the files on an external drive and rest well.  The only times I have lost data is due to human error, but my backups saved me.

---

