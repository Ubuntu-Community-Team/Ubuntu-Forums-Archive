---
title: "250GB HD Partition Scheme in Ubuntu 64?"
date: 2008-11-03
forum: x86 64-bit Users
---

### Post by drdoom20 on 2008-11-03
Hi all,  

Long time reader, first time poster. :) 

I used linux periodically about 7 years ago, and I'm familiar with the older partitioning schemes.  I recently decided to install linux on my home computer, and I'm not familiar with the current standards for partitioning.

I'm interested in dual-booting XP/Ubuntu64 on a machine with an Athlon64X2 processor.  I have 4GB of DDR2 RAM.

I currently have XP on an 80 GB partition, so I have roughly 170GB to play with.

I have a lot of data and frequently download, so I like having extra space to move things around.  I rarely do any serious computing.  I use quanta plus and some of the multimedia programs, but I rarely give my computer a good work-out.  I have a few questions:

1.  Do I need a swap partition, and if so, how large should it be?
2.  If setting up a share partition for XP and Ubuntu to access, should I make it ntfs or fat32?  Is the ntfs support good nowadays?
3.  Should I set up a separate partition for home?
4.  How big should I make the / partition?

I realize that these are pretty basic questions, but I don't want to make any mistakes due to old/bad habits.

Thanks for your time.

---

### Post by drdoom20 on 2008-11-03
I realize that this is a lot of personal preference... I'm mainly wondering about the necessity of a swap partition.  In the gold ol' days, swap partitions would be 2 X RAM so that would make mine 8GB.  That just seems outrageous. Would a swap of 1GB make more sense?

---

### Post by roelpeeters on 2008-11-04
Here's what I did with my 400Gb hdd:

1. Vista 50Gb
2. / 30 Gb (which is waaayyy to much, now I am only at 3.7Gb with a lot of stuff installed)
3. /home 160Gb
4. /swap 6Gb (I have 4Gb RAM)
5. 50 Mb for GRUB, such that you can easily add and remove partitions that contain operating systems without worrying about your grub installation.
6. rest: not partitioned

The advantage of having a separate home partition is that you can switch distributions and/or versions without having to reconfigure your environment and backup/restore your data.

For normal usage, I don't think you would ever reach the full 4 GB of memory (I realize this sounds a lot like Mr. Gates: 640Kb ought to be enough for everybody ;-) ; this happens only in cases of software like databases, video editing, etc.
I understood (correct me if I am wrong) that for hibernation (laptop) it is useful to have a swap partition that is slightly bigger than your memory. Not sure if this is correct.

Roel.

---

### Post by drdoom20 on 2008-11-04
This is exactly the information I was looking for.  I'll be using a 6GB swap and setting up a very large home partition.  I'm not going to be setting up a share partition because I don't see any need to go back to using inferior systems after using Ubuntu.  

Thanks Roel!

---

### Post by leehach on 2008-11-04
There's great information about this at Psychocats: [http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning").  Note in particular that (a) /home has to be an ext2 or ext3 partition, and (b) WinXP can access ext3 partitions using FS-Drive.  

Also, I got some great answers to this when I set up my first Ubuntu computer in February.  Check out the thread here: [http://ubuntuforums.org/showthread.php?t=690048]("http://ubuntuforums.org/showthread.php?t=690048").  Posters to the thread rejected /swap = 2 x RAM out of hand.  They said /swap = RAM is plenty, perhaps even excessive.

I ended up setting up the following:
/ 20 GB (currently using ~5 GB)
/home 5 GB (currently using ~4.5 GB)
/data 400 GB
/swap 2 GB

/home is small because all my actual documents are on /data.  So, for example, /home/[username]/Documents is a symbolic link to /data/[username]/Documents.  All downloads for all users go to /data/Downloads.  /home has filled up with config files and other assorted stuff, so that I wish I had given it more than 5 GB.  I will probably have to resize it soon.  So your main decision to make is
[LIST=1]
[*]Big /home (ext2/3) - throw all your extra space into home and access it from WinXP using FS-Drive; OR
[*]Small /home (ext2/3), big /data (ext2/3 | ntfs | fat32)
[/LIST]

The choice of ext2/3 or ntfs for /data probably comes down to whether you want to enforce permissions.  There's at least one advantage to *not* enforcing partitions: my wife and I share music, photos, etc, but each time one of us creates a new file it is set to read-only for other users.  I haven't found a way around this yet.  If I changed my /data drive to ntfs, all files would be unrestricted to all users.

I learned firsthand the advantages of a separate /home partition when an attempt to upgrade to Intrepid turned into a disaster.  I blew away the / partition and reinstalled.  Everything after the reinstall worked the same as I left it: Firefox still had its history and bookmarks, Thunderbird still had all the email accounts set up, the desktop still had my wallpaper, and the terminal still remembered my recent commands.

Hope this helps,
--Lee

---

### Post by dabl on 2008-11-04
> **drdoom20 said:**
> 

1.  Do I need a swap partition, and if so, how large should it be?



Yes, particularly if you ever want to Suspend to RAM (S2RAM) -- kind of a neat trick to put it to sleep at night and then wake it up in the morning, with no actual boot.  But, 2G is plenty of swap space.  I have 4G of RAM and use a 1.5G swap.

> 

2.  If setting up a share partition for XP and Ubuntu to access, should I make it ntfs or fat32?  Is the ntfs support good nowadays?



NTFS is fine.  Use the ntfs-3g package in Linux to read/write it.

> 

3.  Should I set up a separate partition for home?



I don't.  I use a separate partition for all my serious data, with directories "DOCS", "IMAGES", "VIDEOS", etc, and then symlink them into my /home/dabl folder.

> 

4.  How big should I make the / partition?



6G minimum.  Considering the occasional forgotten downloaded ISO image and stuff like that, maybe 10G is a safer size to let you forget about it for awhile.

Good luck with it.  :p

---

### Post by drdoom20 on 2008-11-04
Excellent. 

Thank you all very much for your input.  

Every question was answered in less than a day!

I've found the transition from Windows to Linux to be quite overwhelming at first.  However, with the quality of help and support offered on this forum, everything becomes way easier!

Keep up the great work!

---

