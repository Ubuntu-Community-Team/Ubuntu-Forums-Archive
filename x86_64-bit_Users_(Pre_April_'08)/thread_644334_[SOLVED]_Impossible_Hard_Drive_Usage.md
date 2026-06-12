---
title: "[SOLVED] Impossible Hard Drive Usage"
date: 2007-12-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by brett611 on 2007-12-18
I'm in my first week of non XP and loving it.  As such I'm checking things frequently, such as hard disk space usage, etc.  Last night my hard disk showed I had 90 gb of my HD used, leaving me with approx 90 gb free(aka total HD size is 180 gb).  I transferred 40 gigs of files from my external drive.  By my math that would leave me with about 50 gb free.

An hr ago I took a look at disk usage and saw some craziness.  See screenshot 'filesystem properties'.  Shows I have just under 30 gb free.  20 gb is a big diff so I fired up the disk usage analyzer.  Then I was shocked - 

D.U.A shows my hd is 360+gb!  See screenshot 'disk usage analyzer'.  It looks like everything is being double counted.

If true this leads me to 3 questions:
1-how do I find out how much space is left
2-how do I find out what files/folders are consuming most space
3-does Ubuntu have "temp" files similar to XP that I need to clean out?  or other 'junk' files that I should be purging?  What about the equivelant of the XP 'disk cleanup'?

Thanks

---

### Post by stalker145 on 2007-12-19
> **brett611 said:**
> I'm in my first week of non XP and loving it.  As such I'm checking things frequently, such as hard disk space usage, etc.  Last night my hard disk showed I had 90 gb of my HD used, leaving me with approx 90 gb free(aka total HD size is 180 gb).  I transferred 40 gigs of files from my external drive.  By my math that would leave me with about 50 gb free.

An hr ago I took a look at disk usage and saw some craziness.  See screenshot 'filesystem properties'.  Shows I have just under 30 gb free.  20 gb is a big diff so I fired up the disk usage analyzer.  Then I was shocked - 

D.U.A shows my hd is 360+gb!  See screenshot 'disk usage analyzer'.  It looks like everything is being double counted.

If true this leads me to 3 questions:
1-how do I find out how much space is left
2-how do I find out what files/folders are consuming most space
3-does Ubuntu have "temp" files similar to XP that I need to clean out?  or other 'junk' files that I should be purging?  What about the equivelant of the XP 'disk cleanup'?

Thanks

1 - For a broad overview of your system go to the terminal and type```
df -h
```this will show you a list of all of your drives with some other junk thrown in for good measure.

Now, do you have just the one drive or do you happen to be running two 160 drives? If you notice my attachment, my root/home drive is only 60GiB, but Disk Analyzer shows much more because it takes into account the entire file system. That's why I was wondering.

2 - Using the Disk Analyzer should do OK for figuring out where your problem is, unless you really do have only one 160, then we'll talk more.

3 - I've never noticed temp files to be a problem. I have, though, forgotten many times to empty the trash for my account and for the root. Maybe if you have a lot of space missing, that *could* be part of the issue.

Check back if this doesn't help.

---

### Post by brett611 on 2007-12-20
Thanks.  I think its a bug.  I'll report it later tonight w/more screenshots

But to answer your question - I only have the single hard drive.  I ran that command and it displayed the usage and total size correctly, which further supports my guess that its a bug.

I'll mark it as solved.  Thanks for the command suggestion

---

### Post by chrisccoulson on 2007-12-20
Could you show us the output of df -h? It might give a clue as to what is happening

Edit: I've just noticed from your disk usage analyzer screenshot that there is over 140GB under /media. Are you sure you don't still have the external drive connected? The two screenshots shown in your first post aren't comparing like-for-like. The Nautilus screenshot is showing you the space on your root filesystem '/', whereas the Disk Usage Analyser is showing all mounted filesystems.

---

### Post by brett611 on 2007-12-20
Hi,
See attached screenshots.  Maxtor, WD and WDMyBook are all external usb drives that i was having problems mounting.  WD & WDMyBOok are the same unit and I was able to get it mounted...I think as sdg1!

So not sure if all these phantom drives/mounts are causing some problems but I don't know how to 'fix' them if that's the right term.

Thanks

---

### Post by chrisccoulson on 2007-12-21
Your issue is that /dev/sda1 is mounted twice. You've got it mounted as the root filesystem, and also mounted again under /media/sda1. The disk usage analyser will count this twice, which is why it lists /media as taking up exactly 50% of the used space. Could you post the contents of your /etc/fstab?

---

### Post by brett611 on 2007-12-21
Damn.  Thanks!  I have to admit - mounting drives, fstab, etc are things I'm having trouble getting straight in my head.  I'll post it tonight.

Thanks for continued help

---

### Post by brett611 on 2007-12-22
Here it is.  How do I delete any of the unnecessary entries?
thx

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc            proc         defaults                    0  0  
# /dev/sda1
UUID=40fe63c6-ad64-468b-8c7a-7c368603a205  /                ext3         defaults,errors=remount-ro  0  1  
# /dev/sda5
UUID=e3d7de2f-e79f-448b-a456-130431ee7a03  none             swap         sw                          0  0  
/dev/hdc                                   /media/cdrom0    udf,iso9660  user,noauto,exec            0  0  
/dev/sdb1                                  /media/WDMyBook  vfat         defaults                    0  0  
/dev/sda1                                  /media/sda1      ext3         defaults                    0  0  
/dev/sda5                                  /media/sda5      swap         defaults                    0  0  
/dev/sdg1                                  /media/Maxtor    ntfs         defaults                    0  0  
/dev/sdf1                                  /media/WD        vfat         defaults                    0  0

---

### Post by dbott67 on 2007-12-22
1. Open the fstab file using nano or gedit as root:

```
sudo nano /etc/fstab
```

2. Put a comment (#) in front of the line you wish to ignore:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc            proc         defaults                    0  0  
# /dev/sda1
UUID=40fe63c6-ad64-468b-8c7a-7c368603a205  /                ext3         defaults,errors=remount-ro  0  1  
# /dev/sda5
UUID=e3d7de2f-e79f-448b-a456-130431ee7a03  none             swap         sw                          0  0  
/dev/hdc                                   /media/cdrom0    udf,iso9660  user,noauto,exec            0  0  
/dev/sdb1                                  /media/WDMyBook  vfat         defaults                    0  0  
[COLOR=Purple]# /dev/sda1                                  /media/sda1      ext3         defaults                    0  0  [/COLOR]
/dev/sda5                                  /media/sda5      swap         defaults                    0  0  
/dev/sdg1                                  /media/Maxtor    ntfs         defaults                    0  0  
/dev/sdf1                                  /media/WD        vfat         defaults                    0  0
```

3. Save & exit.

4. Remount the file system:
```
sudo mount -a
```

-Dave

---

