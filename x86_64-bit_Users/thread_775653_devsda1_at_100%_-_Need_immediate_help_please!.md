---
title: "/dev/sda1 at 100% - Need immediate help please!"
date: 2008-04-30
forum: x86 64-bit Users
---

### Post by misterfixit on 2008-04-30
My /home (/dev/sda1), a 200GB SATA drive was just fine, properties showing about 30% useage.  We had a power failure and the UPS ran down and the system shut down.  I did a cold reboot and now see that the HD is at 100%.  This has hosed everything from Thunderbird to Firefox.  Recommendations?  How to fix?  I've tried to find some file which might show up as 120GB in size, but with no luck.  I'm trying to get this system back up today.  TIA, Dave

---

### Post by plazo on 2008-04-30
Hi misterfixit,
Did you try a fsck on your disk ?

You might have some problems with your filesystem
Try this "touch /forcefsk" then reboot

---

### Post by Sef on 2008-04-30
If you have the live cd handy, then check your partitions:

Applications > Accessories > Terminal

Then type in this code:

```
sudo fdisk -l
``` (Small L)

Then copy and paste the results here.

---

### Post by misterfixit on 2008-04-30
> **Sef said:**
> If you have the live cd handy, then check your partitions:

Applications > Accessories > Terminal

Then type in this code:

```
sudo fdisk -l
``` (Small L)

Then copy and paste the results here.

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b1125

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       29164   234259798+  83  Linux
/dev/sda2           29165       30401     9936202+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde54d8c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24792   199141708+  83  Linux

Disk /dev/sdd: 32 MB, 32768000 bytes
8 heads, 16 sectors/track, 500 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         500       31982+   1  FAT12

Disk /dev/sde: 2014 MB, 2014838784 bytes
255 heads, 63 sectors/track, 244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ddeaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1         244     1959898+  83  Linux

---

### Post by misterfixit on 2008-04-30
> **plazo said:**
> Hi misterfixit,
Did you try a fsck on your disk ?

You might have some problems with your filesystem
Try this "touch /forcefsk" then reboot

OK, I am trying it right now :)

---

### Post by misterfixit on 2008-04-30
OK, I did everything recommended above.  Still no joy.  All of my data folders (documents, etc) are on another drive, so I don't have a problem accessing anything that I work with.  However, Ubuntu HH64 is set up on the drive which says it is at 100% ... so, none of the applications run except at a minimal way.  For example, email won't work, FF works only when invoked from the terminal and complains about no place to put anything, I am sure you know what I am talking about.  Everything acts as if the drive was completely filled up.  Uhhhh, which it seems to be.

I don't know of any tools or command line by which I can go in and actually find the biggest (hugest?) file and delete it.  I am sure there is one file which is hosed that is doing this.

TIA,

Dave
:popcorn:

---

### Post by misterfixit on 2008-04-30
[QUOTE=misterfixit;4847632]OK, I did everything recommended above.  Still no joy.  All of my data folders (documents, etc) are on another drive, so I don't have a problem accessing anything that I work with.  However, Ubuntu HH64 is set up on the drive which says it is at 100% ... so, none of the applications run except at a minimal way.  For example, email won't work, FF works only when invoked from the terminal and complains about no place to put anything, I am sure you know what I am talking about.  Everything acts as if the drive was completely filled up.  Uhhhh, which it seems to be.

Here is results of the lf -h command:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             220G  219G     0 100% /
varrun                2.0G  248K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G   76K  2.0G   1% /dev
devshm                2.0G   12K  2.0G   1% /dev/shm
lrm                   2.0G   43M  1.9G   3% /lib/modules/2.6.24-16-generic/volatile
overflow              1.0M   40K  984K   4% /tmp
/dev/sdd1              32M  1.8M   30M   6% /media/disk
/dev/sde1             1.9G  1.1G  744M  59% /media/disk-1
gvfs-fuse-daemon      220G  219G     0 100% /root/.gvfs
/dev/sdb1             189G   96G   84G  54% /media/disk-2


As you can see /dev/sda1 is at 100%.  It seems to me that the "gvfs-fuse-daemon" is the culprit.  I "think" I've hear stories at our local LUG about the gvfs-fuse daemon being screwed up and should not be allowed to operate as it will do exactly what has happened ...  Does that sound correct??

:oops:
Thanks

Dave

---

### Post by ASULutzy on 2008-05-01
Heh, you could try something like ```
find /opt -type f -printf "%k %p\n" | sort -rn | head -10
```

This would show the 10 largest files in /opt.

You can change the number of large files you want to show and the path to fit your needs.

I honestly don't know how helpful this may be, as to go from fine to 100% seems weird... But you could certainly give it a shot. I'd bet fsck will be the fix for you, not looking for large files, but who knows

---

### Post by misterfixit on 2008-05-01
> **ASULutzy said:**
> Heh, you could try something like ```
find /opt -type f -printf "%k %p\n" | sort -rn | head -10
```

This would show the 10 largest files in /opt.

You can change the number of large files you want to show and the path to fit your needs.

I honestly don't know how helpful this may be, as to go from fine to 100% seems weird... But you could certainly give it a shot. I'd bet fsck will be the fix for you, not looking for large files, but who knows


OK!  I did it but no joy:

dave@TheMightyWurlitzer:~$ sudo find /opt -type f -printf "%k %p\n" | sort -rn | head -10
[sudo] password for dave: 
11952 /opt/picasa/wine/drive_c/Program Files/Picasa2/picasai18n.dll
5492 /opt/picasa/wine/drive_c/Program Files/Picasa2/Picasa2.exe
2500 /opt/picasa/wine/drive_c/Program Files/wine_gecko/components/gklayout.dll
2036 /opt/picasa/wine/drive_c/Program Files/Picasa2/runtime/respack.yt
1868 /opt/picasa/wine/drive_c/Program Files/Picasa2/Picasa2.scr
1392 /opt/picasa/wine/lib/wine/license.exe.so
1048 /opt/picasa/wine/lib/wine/kernel32.dll.so
1024 /opt/picasa/wine/lib/wine/user32.dll.so
1020 /opt/picasa/wine/lib/libwine.so.1.0
984 /opt/picasa/wine/drive_c/Program Files/Picasa2/plugins/expwebsites/expwebsites.yti
dave@TheMightyWurlitzer:~$

---

### Post by misterfixit on 2008-05-01
OK, I did some more work ...

I went in with locate and found any and all boabab and deleted all of them; then I did a locate on any and all .gvfs and deleted all of them; then I rebooted.

Still no joy

---

### Post by misterfixit on 2008-05-01
OK, I am going through /dev/sde1 and doing a file size look at each directory.  At the end of that, if I do not find a 100GB file, I will move my /home to a removable SCSI drive and then reboot with a modified fstab which point towards the /home on another drive.

I have done a lot of searching for answers on this problem -- I am not willing to call it a "bug" yet ... but it IS a problem!.

ANy other ideas from the group????

Dave

---

### Post by t-molli on 2008-05-16
I think you can call it a bug. I think this is the "gvfs-fuse-daemon" bug you can find by searching Launchpad. I've got the same problem and posted my situation there. It's already bugged a few times, so hopefully a fix will come out soon as they're calling it a critical fix.

---

### Post by misterfixit on 2008-05-24
> **t-molli said:**
> I think you can call it a bug. I think this is the "gvfs-fuse-daemon" bug you can find by searching Launchpad. I've got the same problem and posted my situation there. It's already bugged a few times, so hopefully a fix will come out soon as they're calling it a critical fix.

I did some more investigating and discovered that the actual offender was Simple Backup.  While doing the usual archive cleaning, Backup put 96GB of files into the trash which clogged the system; worse, baobab then tried to index or mirror or whatever the fsck baobab is there for, and I ended up with a totally filled HD.

Sweet.

Simple Backup has no way (I checked via command line, etc) to send an archive directly to /dev/null or bit bucket or whereever deleted files go to when they die.

Sweet.

OK, problem solved.

Thanks to all who kindly replied to my "immediate request".

As for now, I am going to the lake to catch some catfish for lunch. 

 :lolflag:

Cheers,

Dave

---

### Post by freackout on 2009-03-15
> **misterfixit said:**
> My /home (/dev/sda1), a 200GB SATA drive was just fine, properties showing about 30% useage.  We had a power failure and the UPS ran down and the system shut down.  I did a cold reboot and now see that the HD is at 100%.  This has hosed everything from Thunderbird to Firefox.  Recommendations?  How to fix?  I've tried to find some file which might show up as 120GB in size, but with no luck.  I'm trying to get this system back up today.  TIA, Dave

must have a look at pmagic3.7 its brilliant least yo get your files back and possibly fix your problem too, it uses partedmagic as a base but includes programes to fix your system works nicely with ubuntu and ext4 too. its a linux boot disk which can run in memory and with or without settings enabled, ie fast or slow boxes.

---

