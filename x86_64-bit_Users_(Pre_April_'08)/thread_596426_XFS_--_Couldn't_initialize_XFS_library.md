---
title: "XFS -- Couldn't initialize XFS library"
date: 2007-10-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by cenwesi on 2007-10-29
Does anyone know how to get rid of this error. I converted 2 of my drives to XFS and every time i go into GParted, and look at the drive it says 

Fatal Error -- Couldn't initialize XFS library.   

I can load files and view stuff on the drive...just wondering if there is a way to fix this. I don't want to convert the other two 500gigs yet.

---

### Post by insane_alien on 2007-10-29
install xfsprogs and xfsdump

---

### Post by cenwesi on 2007-10-30
Thank you so much, that fixed it.

---

### Post by cenwesi on 2007-10-31
hmmmm, its back again.... Is there there something wrong with "Partition Editor" because that is where this error comes up

---

### Post by WestCoastSuccess on 2007-11-06
I'm having the same problem after moving my drives around in the case. The cables are all still connected to the same drives they were before, however computer fails to boot. On booting up with an old Edgy CD I can select "boot from first hard drive" and it boots OK, but gparted reports the "XFS -- Couldn't initialize XFS library".

I have no problem accessing files on the drive.

Any ideas? Is this a problem in Gutsy?

---

### Post by dabl on 2007-11-06
I used the GParted Live CD to make my partitions and format them.  I don't believe there is anything about Gutsy that presents a problem for XFS partitions.  I have 5 hard drives running a mix of XFS, reiserfs, and ext3 filesystems, and it all seems to hang together OK.  Here's more:

[http://kubuntuforums.net/forums/index.php?topic=3087434.0](http://kubuntuforums.net/forums/index.php?topic=3087434.0)

:guitar:


P.S. You realize, of course, that you need a separate /boot partition when you use XFS? It only needs to be 200MB, but it needs to be on its own partition.

---

### Post by cenwesi on 2007-11-07
Still having the same issue.... had it working when **insane_alien** had me install the xfsprogs and xfsdump. and dmesg | grep -i xfs reports nothing.

---

### Post by dabl on 2007-11-07
I think you've something else going on.  I didn't install xfsprogs until several weeks after I had set up the XFS filesystems -- when I finally got interested in the possibility of fragmentation.  Those programs have nothing to do with the booting and running, only with administration post-install.

If it were me, I'd get my data off those drives and do some experiments with other filesystem formats on them, to see if this really has anything to do with XFS. You might have a controller problem, or some other timing thing going on, that is not related to the filesystem type.  The fact that GParted is having a problem with them would be a concern to me.

---

### Post by skskarda on 2007-11-09
I was searching for an answer to the same problem.   I found that on my system the error goes away if the device is unmounted.  There are some threads that suggest tools such as xfs-check and xfs-repair only work on devices that are not mounted so I am guessing that is the reason the error comes up.

---

### Post by cenwesi on 2007-11-09
But after you ran those check, did the error return?

---

### Post by skskarda on 2007-11-09
The error goes away when I unmount the device.  The error comes back only after I remount the device.  This is a snip of my terminal:

steve@steve-desktop:~$ xfs_check /dev/sda6
xfs_check: /dev/sda6 contains a mounted and writable filesystem

fatal error -- couldn't initialize XFS library
steve@steve-desktop:~$ sudo umount /mnt/oldhard
[sudo] password for steve:
steve@steve-desktop:~$ sudo xfs_check /dev/sda6
steve@steve-desktop:~$ sudo mount -a
steve@steve-desktop:~$ sudo xfs_check /dev/sda6
xfs_check: /dev/sda6 contains a mounted and writable filesystem

fatal error -- couldn't initialize XFS library

---

### Post by cenwesi on 2007-11-09
Same error i am geting...

---

### Post by GermanPabloGentile on 2007-12-18
Sames here. I start having problem in my system and crash at all. Then i reinstall, work fine, but cannot check the XFS.

get that message; couldn't initialize XFS library


Anybody find the solutions? Already installed:

$ sudo aptitude install xfsprogs xfsdump

How follow that?

---

### Post by kuja on 2007-12-18
> DESCRIPTION
       xfs_check  checks  whether an XFS filesystem is consistent.  It is nor&#8208;
       mally run only when there is reason to believe that the filesystem  has
       a  consistency  problem.   The filesystem to be checked is specified by
       the xfs_special argument, which should be the disk or volume device for
       the filesystem.  Filesystems stored in files can also be checked, using
       the -f flag.  [b]The filesystem should normally be unmounted or  read-only
       during  the  execution  of xfs_check.  Otherwise, spurious problems are
       reported.[/b]


There you have it, straight from the man page .....

---

### Post by cenwesi on 2007-12-18
All jebris.... still giving me the same error even a newer 500gig HD.

---

