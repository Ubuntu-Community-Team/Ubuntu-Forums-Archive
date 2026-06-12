---
title: "drive recovery"
date: 2007-05-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by Angelbeast on 2007-05-03
I just formatted my second hard drive for torage from windows to linux format...now the drive will not show up...how do i get it back?

---

### Post by kagashe on 2007-05-03
> **Angelbeast said:**
> I just formatted my second hard drive for torage from windows to linux format...now the drive will not show up...how do i get it back?Do you mean it is not appearing in Windows? It won't. Windows does not show drives or partitions formated for Linux.

kagashe

---

### Post by Angelbeast on 2007-05-03
> **kagashe said:**
> Do you mean it is not appearing in Windows? It won't. Windows does not show drives or partitions formated for Linux.

kagashe

It's not showing up in Ubuntu :-) I formattedi FROM NFTS to Linux. Now i don't see it in the places folder.

---

### Post by John Jason Jordan on 2007-05-03
> **Angelbeast said:**
> It's not showing up in Ubuntu :-) I formattedi FROM NFTS to Linux. Now i don't see it in the places folder.
That is because it is not mounted. There are two ways to mount it; manually and automatically. First, I'll explain the manual method.

The first step in mounting it is to determine what it is called. Hard disks in Linux are usually preceded by "hd" followed by a letter and a number. The letter is which hard disk it is and the number refers to which partition it is. Thus, "hda2" means the second partition on the first hard disk. While most hard disks will be "hd" -something, if it is a SATA or SCSI hard disk it will be "sd" -something. If these instructions are confusing, just open the partiton editor in the System > Administration menu. It will show the partitions and how they are labeled.

The second step in mounting a partition is to create a mount point. A "mount point" means where in the fielsystem you want it to appear. In Ubuntu just about everything will be mounted in /media and each partition in /media will get its own folder. Let us suppose your partition is hda2. If you want a mount point that is easy to recognize and understand, create a folder in /media called hda2. From the terminal the command would be 

sudo mkdir /media/hda2

Replace "hda2" above with your partition.

OK, now you are ready to mount it. The command would be:

sudo mount -t ext3 /dev/hda2 /media/hd12

This command mounts a partition named hda2 formatted with the ext3 filesystem on mount point /media/hda2. If it worked it will appear in Places.

OK, that's enough for one lesson. Besides, it's my bedtime. Go try out the above and report back. As soon as I hear you have managed to mount it manually as above, I will take the next step and explain how to make the mounting automatic.

---

### Post by Angelbeast on 2007-05-03
> **John Jason Jordan said:**
> That is because it is not mounted. There are two ways to mount it; manually and automatically. First, I'll explain the manual method.

The first step in mounting it is to determine what it is called. Hard disks in Linux are usually preceded by "hd" followed by a letter and a number. The letter is which hard disk it is and the number refers to which partition it is. Thus, "hda2" means the second partition on the first hard disk. While most hard disks will be "hd" -something, if it is a SATA or SCSI hard disk it will be "sd" -something. If these instructions are confusing, just open the partiton editor in the System > Administration menu. It will show the partitions and how they are labeled.

The second step in mounting a partition is to create a mount point. A "mount point" means where in the fielsystem you want it to appear. In Ubuntu just about everything will be mounted in /media and each partition in /media will get its own folder. Let us suppose your partition is hda2. If you want a mount point that is easy to recognize and understand, create a folder in /media called hda2. From the terminal the command would be 

sudo mkdir /media/hda2

Replace "hda2" above with your partition.

OK, now you are ready to mount it. The command would be:

sudo mount -t ext3 /dev/hda2 /media/hd12

This command mounts a partition named hda2 formatted with the ext3 filesystem on mount point /media/hda2. If it worked it will appear in Places.

OK, that's enough for one lesson. Besides, it's my bedtime. Go try out the above and report back. As soon as I hear you have managed to mount it manually as above, I will take the next step and explain how to make the mounting automatic.

well it seems to have worked...but there is a folder in there now called lot n found that i can't seem to get rid of...i've included a screenshot with the permissions box

---

### Post by skibrianski on 2007-05-03
> **Angelbeast said:**
> well it seems to have worked...but there is a folder in there now called lot n found that i can't seem to get rid of...i've included a screenshot with the permissions box

That's ok, lost+found directory is included by default in linux filesystems. It is used when the disk crashes for putting anything the disk checker finds there (partial or whole files and directories, etc.)

---

### Post by Angelbeast on 2007-05-03
> **skibrianski said:**
> That's ok, lost+found directory is included by default in linux filesystems. It is used when the disk crashes for putting anything the disk checker finds there (partial or whole files and directories, etc.)

ah...well okay then it seems to be mounted and i THINK i have the permissions changed propery but..do i have to reboot for the new permissions to take effet?

---

### Post by John Jason Jordan on 2007-05-03
> **Angelbeast said:**
> ah...well okay then it seems to be mounted and i THINK i have the permissions changed propery but..do i have to reboot for the new permissions to take effet?
No, you do not need to reboot for the permissions to take effect. However, in my experience Nautilus sometimes does not display the changed permissions, sometimes not even after you reload the page. Sometimes I have to shut down all the file browser windows and reopen them to see the changed permissions. Other times the changes show up right away. 

Now that you have the mounting under control, you need to learn how to make the mounting automatic every time you boot. That is controlled by a file called fstab located in the /etc folder. It's just a text file and you can edit it with Text Editor, although you need to be root in order to save changes to it. To open it as root go to a terminal and type "sudo gedit /etc/fstab." 

CAUTION
Don't mess with stuff that's already in there! All you want to do is add a device to be mounted. If you mess up what you add for the new device all that will happen is that the new device won't automatically mount, but adding a new device won't change the mounting of other stuff, so adding a device is safe. Changing any of the existing lines, however, could be a Really Bad Thing. Because this is important, any time you make changes and save the fstab file, Linux will automatically make a backup of the original fstab file called fstab~. I always make a copy of fstab even before I open it. To do so type on the command line "sudo cp /etc/fstab /etc/fstab-mybackup-for-when-I-screw-up."

OK, start by reading the man page for fstab. From the command line type "man fstab." You probably won't understand everything that is in the man page because it's a reference for people who already understand fstab, not a wiki or how-to for a beginner. But you might pick up a bit from it and it's good to know where the reference is. 

Next, look at fstab in Text Editor. You will see a bunch of lines. Each one is a device that gets mounted on booting. Some of them are system devices, like /proc and /sys. Look for the line that represents the partition where Ubuntu is installed. That line will be sort of a template for your new line, because a lot of the stuff you will want on the new line will be the same.

Notice the spaces between items. The spaces are there just for legibility. Extra spaces beyond the first one are ignored. Note also the lines starting with #. The # means "ignore everything on this line." The # is used just to enter a comment for a human. It is good to comment your work so you can understand what you did in case you need to look at fstab months from now. I would add a line "# the following device was added by me 5/4/2007" and then put your mount line underneath it.

Notice the order in which things are laid out on the lines. First there is the name of the device, then the mount point, then the file system type (ext3 in your case) and then some other options. Fiddle with your new line and see if you can get it to mount automatically when you reboot. Use the man page as a resource. If you get stuck and can't get it to work, post back your fstab file and we'll see what might be wrong.

---

### Post by Angelbeast on 2007-05-04
Okay i'm a little confused here...I ee what you mean pretty much but i'm confused as to the string after "UID" ... where do i find the information to put in that line?

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=de70cf45-29aa-436e-8e8a-31ae633c3a14 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=ab7ac934-f156-4c18-b8a1-f525c7a09578 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by ronocdh on 2007-05-04
> **kagashe said:**
> Do you mean it is not appearing in Windows? It won't. Windows does not show drives or partitions formated for Linux.

kagashe
John Jason Jordan, way to post!

I know this is slightly off-topic, but I couldn't let it slip by without mentioning an [installable ext3 filesystem]("http://www.fs-driver.org/") for Win XP. =) I have found it quite useful for using computers I don't own; you can stick the exe on a flash drive and keep it with you!

---

### Post by Angelbeast on 2007-05-04
Okay now i'm REALLY confused. I ended up having to reboot and i thought i would have to start with the mounting all over again. Well what ifound was that in my places folder i have a volume called "disc" that i have the proper permissions for and seems to e all good. But. When i go to the computer folder i ee a generically labeled volume with different permissions. Now when i mounted the drive initially th? I mean if i unmount it will the other one unmount s well? I'm includige drive showed up with the name of the one in the computer folder but with no permissions. So i would ssume that the one labeled "disc" is the one that i actually want to keep. So assuming that they are both for the same drive and the one in the computer folder is just redundant, do i just get rid of it? and how do i do that? Andif i do unmount it will it unmount the other one labeled "disc". I've included a couple more screenshots so you can see what i'm talking about...

---

### Post by John Jason Jordan on 2007-05-04
> **Angelbeast said:**
> Okay i'm a little confused here...I ee what you mean pretty much but i'm confused as to the string after "UID" ... where do i find the information to put in that line?
Aaah. Your Linux is using UUIDs.

First, the way to get a UUID address for a device is:

sudo tune2fs -l /dev/hda2

Where you need to substitute your device name as it appears in Gnome Partition Editor for "hda2."

Now, let's see what we are talking about here. There are two ways to tell Linux which partition you want to mount. One is to say (e.g.) /dev/hda2  The other is to specify a UUID location for the partition. I don't totally understand UUID addresses, but I have been told that they are better because you might add another partition some day and then "hda2" would become "hda-something-else." UUID, in contrast, is a physical block location on the disk and cannot change. Personally, I avoid UUID because it is a pain to have to use tune2fs for figure them out all the time and I have never had a problem just using (e.g.) /dev/hda2. 

The fstab file can use either UUID or the /dev/hda2 type of designation. So if you want you can ignore the tune2fs command I gave at the beginning here and just use your /dev/hda2 type designation for the partition.

Note in your fstab file the two lines that start with UUID. The first one is hda5, which is where your Ubuntu installation is located. The other is hda1, which is your swap partition. But notice underneath, the CD-ROM is designated by /dev/hdc instead of a UUID address. I point that out just to illustrate that you don't absolutely have to use the UUID address to designate the partition.

Just for the fun of it, however, you might want to use the tune2fs command at the top here on hda5 and hda1 to see if the results match the UUID addresses for those partitions in your fstab file. 

Post back if you still have problems. Oh, and since the fstab file is a listing of partitions that are to be mounted automatically on booting, you'll have to reboot to see if your edits of the fstab file work.

---

### Post by Angelbeast on 2007-05-04
> **John Jason Jordan said:**
> Aaah. Your Linux is using UUIDs.

First, the way to get a UUID address for a device is:

sudo tune2fs -l /dev/hda2

Where you need to substitute your device name as it appears in Gnome Partition Editor for "hda2."

Now, let's see what we are talking about here. There are two ways to tell Linux which partition you want to mount. One is to say (e.g.) /dev/hda2  The other is to specify a UUID location for the partition. I don't totally understand UUID addresses, but I have been told that they are better because you might add another partition some day and then "hda2" would become "hda-something-else." UUID, in contrast, is a physical block location on the disk and cannot change. Personally, I avoid UUID because it is a pain to have to use tune2fs for figure them out all the time and I have never had a problem just using (e.g.) /dev/hda2. 

The fstab file can use either UUID or the /dev/hda2 type of designation. So if you want you can ignore the tune2fs command I gave at the beginning here and just use your /dev/hda2 type designation for the partition.

Note in your fstab file the two lines that start with UUID. The first one is hda5, which is where your Ubuntu installation is located. The other is hda1, which is your swap partition. But notice underneath, the CD-ROM is designated by /dev/hdc instead of a UUID address. I point that out just to illustrate that you don't absolutely have to use the UUID address to designate the partition.

Just for the fun of it, however, you might want to use the tune2fs command at the top here on hda5 and hda1 to see if the results match the UUID addresses for those partitions in your fstab file. 

Post back if you still have problems. Oh, and since the fstab file is a listing of partitions that are to be mounted automatically on booting, you'll have to reboot to see if your edits of the fstab file work.

whoa...okay now i'm lost...i'll have to digest this one a paragraph at a time *LOL* ... but whatdo i do about the problem in my last post?

---

### Post by Angelbeast on 2007-05-04
Okay now i'm even more confused. I got the info for the drive and it says the user is still root and it has no volume name. o what's up with the one named "disc"


ron@ron-laptop:~$ sudo tune2fs -l /dev/hdb1
Password:
tune2fs 1.40-WIP (14-Nov-2006)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          1e761227-96c3-487b-a5d0-fc67b3196e7d
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed directory hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              9781248
Block count:              19537040
Reserved block count:     976852
Free blocks:              19184049
Free inodes:              9781237
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1019
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Filesystem created:       Thu May  3 01:01:52 2007
Last mount time:          Fri May  4 02:29:10 2007
Last write time:          Fri May  4 02:29:10 2007
Mount count:              3
Maximum mount count:      32
Last checked:             Thu May  3 01:01:52 2007
Check interval:           15552000 (6 months)
Next check after:         Tue Oct 30 01:01:52 2007
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      59422b3f-cf4d-4c30-9b16-72e0bf692c9d
Journal backup:           inode blocks

---

