---
title: "Mount points and partitions"
date: 2007-05-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by j3cakes on 2007-05-22
Hi,

I've got a 64-bit system on which I originally installed the 32-bit Dapper (I was under the impression it was more stable) but, since reading the various threads here, I've decided to upgrade to the 64-bit Edgy.

When I set the system up I wasn't sure how I wanted to split my private (/home) and shared (/storage) data partitions and have since found that the shared area is nowhere near big enough whereas the private area has loads of space free.

I have two drives: a 500GB one (450GB usable) and a 320GB one (290GB usable.)
 
I want to allocate the following:
 
100GB to /home (from the 320GB drive)
450GB to /storage (from the 500GB one)
170GB to /storage (from the 320GB one)
19GB for the system partition 
1GB for the swap partition
 
Can I allocate partitions from different drives to the same mount point. Is that even possible?

I've already done a backup my data figuring that, if I want to change the size of /home I'll have to delete it and recreate it.
 
I remember reading that for 32-bit Edgy and Dapper 11GB was enough for the system partition; is it the same for 64-bit? I allocated 19GB just in case but I'd rather put it to use than see it sitting there, lonely and wasted. :)

I'm pretty new to linux/ubuntu so if there's a better way please let me know.

thx
Jason

ps: Is Edgy more stable than Feisty? Would Feisty be a better option? I'd prefer fewer things to need tweaking and more things to be stable and working (which is why I first went for the 32-bit install.)

pps: As I understand it, the process for AMD64 and EM64T is the same. Is that right?

---

### Post by shad0w_walker on 2007-05-22
You should be able to use gparted to resize your partitions without data loss (Gparted should be available from synaptic/apt/add-remove programs)

Its a fairly easy GUI to use and shows you exactly what its doing at any given time. There shouldnt be any data loss (Resized my main partition 4 times in as many hours with no loss) but backups are always a good thing to have. 

Also, i would recommend fiesty over edgy, its not got any painfully important new features but it seems more stable (Edgy was rushed and released ahead of schedule so certain things never seemed to worked right) but edgy seems stable so really its all choice now.

---

### Post by dabl on 2007-05-22
> **j3cakes said:**
> 
 
Can I allocate partitions from different drives to the same mount point. Is that even possible?

No, I don't think so.  Better make it /Storage_1 on the 500GB drive, and /Storage_2 on the 320GB drive.

> Would Feisty be a better option?

Yes, IMHO -- Feisty has been noticeably more stable than Edgy, on my hardware.

;)

---

### Post by John Jason Jordan on 2007-05-22
> **j3cakes said:**
> 
I want to allocate the following:
100GB to /home (from the 320GB drive)
450GB to /storage (from the 500GB one)
170GB to /storage (from the 320GB one)
19GB for the system partition 
1GB for the swap partition 
Can I allocate partitions from different drives to the same mount point. Is that even possible?
I've already done a backup my data figuring that, if I want to change the size of /home I'll have to delete it and recreate it. 
I remember reading that for 32-bit Edgy and Dapper 11GB was enough for the system partition; is it the same for 64-bit? I allocated 19GB just in case but I'd rather put it to use than see it sitting there, lonely and wasted. :)
I'm pretty new to linux/ubuntu so if there's a better way please let me know.
ps: Is Edgy more stable than Feisty? Would Feisty be a better option? I'd prefer fewer things to need tweaking and more things to be stable and working (which is why I first went for the 32-bit install.)
pps: As I understand it, the process for AMD64 and EM64T is the same. Is that right?
First, You can mount as many partitions as you want and the mount points can be anywhere you want, but each partition needs a different mount point. In the olden days of Linux everything was mounted in /mnt, but the modern way is to mount everything in /media. So you could go into /media, make a folder /storage and use it as the mount point for the storage partition. Then make other folders and use them as mount points for your other partition(s).

Second, I recommend using more than the minimum for the system folder. I'd use about 20-25 GB even if it needs only 11 GB. Why? Because disk space is pretty cheap and I'd rather waste some than end up having to resize later. You never know what you might suddenly decide you want to store on your system folder. Plus, reads and writes to the filesystem get bogged down and bad things start to happen when a partition gets too full. Give it some room to breathe.

Third, as others have noted, Gparted (gnome Partition Editor, installed by default under System > Administration) will resize a partition. It is also the easiest tool for creating and formatting new partitions.

Fourth, yes emt64 (Intel) and amd64 (AMD) use the same version of 64-bit Ubuntu. But ia64 is a different 64-bit critter.

Fifth, Edgy was appropriately named. Stay away from it. Use Dapper for best stability and long term support, or Feisty if you need support for the latest hardware, drivers, etc. These days I am recommending Feisty to just about all newcomers. As far as I can tell it's just as stable as Dapper and it's always nice to have the latest features. Plus, when newer versions come out you can upgrade only one level at a time. So if you installed Edgy today and six months from now you want to upgrade to Gutsy, you'd have to upgrade in two steps, first to Feisty and then to Gutsy. Upgrades are scary things and doing two, one right after the other, is just asking for it.

---

### Post by j3cakes on 2007-05-22
ok, I went for Feisty and I chose to redo the partitions from scratch because I'd backed up all the important data and I wanted a fresh, clean install.

but,.. something I don't understand from this:
> **John Jason Jordan said:**
>  ... but each partition needs a different mount point.... So you could go into /media, make a folder /storage and use it as the mount point for the storage partition. Then make other folders and use them as mount points for your other partition(s).

I have a 200GB partition on one drive and a 450GB partition on the other and I want to use them both in one folder called /storage. Surely it's possible to combine space from two drives into one folder..?

What I mean is that I want them to present as one folder, not as separate subdirectories under /storage. Can I combine the partitions to make a 650GB volume?

thx.

---

### Post by John Jason Jordan on 2007-05-22
> **j3cakes said:**
> ok, I went for Feisty and I chose to redo the partitions from scratch because I'd backed up all the important data and I wanted a fresh, clean install.
but,.. something I don't understand from this:
I have a 200GB partition on one drive and a 450GB partition on the other and I want to use them both in one folder called /storage. Surely it's possible to combine space from two drives into one folder..?
What I mean is that I want them to present as one folder, not as separate subdirectories under /storage. Can I combine the partitions to make a 650GB volume?
Aaaah. What you want is called a stripe set (Windows) or logical volume (Linux), also known as a RAID 0 device (RAID 0 array). The idea is to create the logical volume first, then mount it at the mount point, e.g., /media/storage.

The tool to create logical volumes is mdadm. It is command line only, and there is no GUI front end for it. At a command line type "man mdadm" and that will get you started. The man page and other instructions are also available on the web.

To create the array you start by creating the partitions in Gparted. But be sure to leave them unformatted and then set the flag for each partition to RAID. Having done so, then you finish creating the RAID 0 array with mdadm. And once it is created it will have a name (probably md0) and you can mount it on your storage folder with the command:

sudo mount /dev/md0 /media/storage

I think the mdadm command to create the array would be:

sudo mdadm --create /dev/md0 --level=0 raid-devices=2 /dev/hda1 /dev/hda2

where "hda1" and "hda2" in the command above will be whatever name Gparted gave the partitions when it created them. If the drives are SCSI or SATA the "h" will be an "s." Note also that you can give the device any name you want; it does not have to be md0. Just remember what you called it so that you will know what name to use for the mount command.

Once you get all that done and the device mounted and working, we'll work on editing your /etc/fstab file so the volume will automatically mount when you reboot.

---

### Post by j3cakes on 2007-05-22
thanks.

I'll let you know how I get on.

edit: ok, I haven't formatted the partitions and /dev/md0 exists but when I try to mount the /dev/md0 it tell me to specify a filesystem. If I use ext3 it gives the following

```

x@mediaBox:/dev$ sudo mount -t ext3 /dev/md0 /media/storage
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

x@mediaBox:/dev$ dmesg | tail
[ 2897.622157] raid0 : md_size is 682705984 blocks.
[ 2897.622158] raid0 : conf->hash_spacing is 388644224 blocks.
[ 2897.622170] raid0 : nb_zone is 2.
[ 2897.622172] raid0 : Allocating 16 bytes for hash.
[ 3234.275776] cramfs: wrong magic
[ 3234.277989] VFS: Can't find ext3 filesystem on dev md0.
[ 3290.500433] VFS: Can't find ext3 filesystem on dev md0.
[ 3703.223707] cramfs: wrong magic
[ 3703.225972] VFS: Can't find ext3 filesystem on dev md0.
[ 3939.890162] VFS: Can't find ext3 filesystem on dev md0.


```

Here is the --detail output for the new device:

```

x@mediaBox:/etc/mdadm$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Tue May 22 22:08:29 2007
     Raid Level : raid0
     Array Size : 682705984 (651.08 GiB 699.09 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue May 22 22:08:29 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : 83855713:e58c2946:cc953713:57ecd0fd (local to host mediaBox)
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5
       1       8       21        1      active sync   /dev/sdb5

```


edit (again): found this thread: [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461) which looks promising.

---

### Post by j3cakes on 2007-05-22
cool. it works! once i'd formatted it (used sudo mkfs.ext3 /dev/md0) it came up a treat.

thanks to everyone for their contributions, esp JJJ for pointing me in the right direction with mdadm.

---

### Post by John Jason Jordan on 2007-05-22
> **j3cakes said:**
> thanks.
I'll let you know how I get on.
edit: ok, I haven't formatted the partitions and /dev/md0 exists but when I try to mount the /dev/md0 it tell me to specify a filesystem. If I use ext3 it gives the following
```

x@mediaBox:/dev$ sudo mount -t ext3 /dev/md0 /media/storage
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
x@mediaBox:/dev$ dmesg | tail
[ 2897.622157] raid0 : md_size is 682705984 blocks.
[ 2897.622158] raid0 : conf->hash_spacing is 388644224 blocks.
[ 2897.622170] raid0 : nb_zone is 2.
[ 2897.622172] raid0 : Allocating 16 bytes for hash.
[ 3234.275776] cramfs: wrong magic
[ 3234.277989] VFS: Can't find ext3 filesystem on dev md0.
[ 3290.500433] VFS: Can't find ext3 filesystem on dev md0.
[ 3703.223707] cramfs: wrong magic
[ 3703.225972] VFS: Can't find ext3 filesystem on dev md0.
[ 3939.890162] VFS: Can't find ext3 filesystem on dev md0.


```
Here is the --detail output for the new device:
```

x@mediaBox:/etc/mdadm$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Tue May 22 22:08:29 2007
     Raid Level : raid0
     Array Size : 682705984 (651.08 GiB 699.09 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent
    Update Time : Tue May 22 22:08:29 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
     Chunk Size : 64K
           UUID : 83855713:e58c2946:cc953713:57ecd0fd (local to host mediaBox)
         Events : 0.1
    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5
       1       8       21        1      active sync   /dev/sdb5

```
edit (again): found this thread: [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461) which looks promising.
The only thing I can think of is that the mdadm --create command has not finished. As I recall, when you create an array mdadm says it created the array and returns you to a command line prompt. But, in fact, it then has to format and sync the partitions, and this can take an hour or two. It ought to say something like "OK, I created the array, but it's going to take me all day to finish setting it up, so just cool your jets, dude." You can just look at the hard disk light -- if it is on solid, then you know mdadm is working silently to finish setting up the array.

As for the mount command, it is pretty lame when it comes to error messages. If anything goes wrong the only thing it knows is "bad filesystem." 

If that's not the problem, then I don't have any other ideas.

---

### Post by John Jason Jordan on 2007-05-22
> **j3cakes said:**
> cool. it works! once i'd formatted it (used sudo mkfs.ext3 /dev/md0) it came up a treat.
thanks to everyone for their contributions, esp JJJ for pointing me in the right direction with mdadm.
Excellent. You are now a Linux filesystem expert! 

Now you need to edit your /etc/fstab file so that it will mount automatically when you boot. Best way to do this is "sudo gedit /etc/fstab," which will bring it up with read/write privileges in the text editor.

WARNING: Don't change anything that is already in there. You are going to ADD a line, and adding is safe. If you muck up the new line the only thing that will happen is that the device on the new line won't mount. Deleting or changing existing stuff might make the system fail to boot.

OK, adding the new line is easy. Look for the line that mounts your filesystem, copy it, and paste it into a new line. I always add an extra little line above it just to document to myself what I did:

# the following line added by me 5/22/2007

Note that lines with a # in front of them are ignored. Also, extra spaces are ignored.

Now you need to edit the line you just pasted so it will mount /dev/md0 at /media/storage (assuming that is what it's called and where you want it mounted). That should be pretty simple, unless your fstab file is using UUIDs to identify devices. If you see big long-*** lines of numbers and letters that start with UUID, replace the UUID stuff in the new line with /dev/md0. Some think that UUIDs are a better way to specify device locations, but /dev names work just as well and are a lot easier for us humans to handle.

---

### Post by j3cakes on 2007-05-22
So I could be done now...

I've added the line to fstab but before I reboot I need to find out one last thing.

When I did the apt-get for mdadm it went through a bit of a setup wizard thing asking me for devices and partitions. I just pressed escape cause none of it made much sense. I've had a look at the mdadm.conf file and I just want to know whether it's going to undo everything when i reboot.

```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Tue, 22 May 2007 22:07:08 +0100
# by mkconf $Id: mkconf 261 2006-11-09 13:32:35Z madduck $

```

Is that all ok? Do I need to change anything?

---

### Post by John Jason Jordan on 2007-05-22
> **j3cakes said:**
> So I could be done now...

I've added the line to fstab but before I reboot I need to find out one last thing.

When I did the apt-get for mdadm it went through a bit of a setup wizard thing asking me for devices and partitions. I just pressed escape cause none of it made much sense. I've had a look at the mdadm.conf file and I just want to know whether it's going to undo everything when i reboot.

```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Tue, 22 May 2007 22:07:08 +0100
# by mkconf $Id: mkconf 261 2006-11-09 13:32:35Z madduck $

```

Is that all ok? Do I need to change anything?

It looks fine to me. Just remember, if you didn't change anything else in the fstab file, that is, all you did was add the new line, then the system will boot. If the new line is incorrect it won't automatically mount /dev/md0, but everything else will mount and work as before, and you can still mount /dev/md0 manually. If that is what happens, then you just have to go fix the line in fstab until it works properly.

<Crossing fingers>

---

### Post by j3cakes on 2007-05-23
Actually, I did have to remove a couple of lines from fstab - the ones that mounted the old partitions. I rebooted a couple of times but it told me that these were unavailable and to Ctrl-D to continue. So I commented them out (just in case) and it works.

Thanks for your help.

---

