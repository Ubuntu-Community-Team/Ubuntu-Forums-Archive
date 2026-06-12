---
title: "Help - cannot write to USB flash drive"
date: 2006-08-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Apostata on 2006-08-16
I've looked all over the Ubuntu forums and I cannot find a solution for this (and yes, there are many threads regarding this anomaly).

Problem: I can mount my SanDisk flashdrive, but it will not let me copy anything to it. At all. Not as user. Not as root. Result:
> sudo cp file.txt /media/sdb1
cp: cannot create regular file `/media/sdb1/file.txt': Read-only file system

I've changed my fstab so many times, I finally just removed any occurrence of the usb drive (and it makes no difference anyway).

I **HAVE** to be able to write to this drive, and I'm at my wits end. I've wasted an entire day working on this one, single problem (which I haven't experienced since my days of Libranet).

Any help appreciated.

M

---

### Post by Apostata on 2006-08-16
Some more info (assume USB drive is on /dev/sda1):

fdisk:

> $ fdisk -l

Disk /dev/sda: 262 MB, 262144000 bytes
64 heads, 32 sectors/track, 250 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         249      254960    b  W95 FAT32

fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               reiserfs notail          0       1
/dev/hdb1       /home           ext3    defaults        0       2
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/sda1	/media/usbdrive	auto	defaults,user	0	0

mount:

> $ mount
/dev/hda2 on / type reiserfs (rw,notail)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-amd64-generic/volatile type tmpfs (rw)
/dev/hdb1 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/usbdrive type vfat (rw,noexec,nosuid,nodev,user=me)


---

### Post by Portable_Jim on 2007-01-19
(bump) I also have the same problem.

My MP3 player seems to mount as rw: 
```
~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
/dev/hda1 on /media/Win_XP type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hdb1 on /media/hdb1 type ntfs (rw,nls=utf8,umask=007,gid=46)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```but when I try and write to it (even as root) I get the following message:
```
chmod: changing permissions of `/media/usbdisk': Read-only file system
``````
touch: cannot touch `/media/usbdisk/1.try': Read-only file system
``````
sudo chmod -R 777 /media/usbdisk
Password:
chmod: changing permissions of `/media/usbdisk': Read-only file system
```Please Help!

---

### Post by ADT on 2007-01-20
I found a manual solution to this problem on the ubuntuguide website:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)

If you have software installed that automatically mounts your usbdisk,
and when mounted you only have read permissions then you should first
unmount the usbdisk and then remount it again but with extra options to
trick the fat32 filesystem to giving you read/write permissions for accessing the
usbdisk.

Example (replace "usbdisk" with whatever you have as your usb folder in /media):

```

sudo umount /media/usbdisk

```

then type:

```

sudo mount /dev/sda1 /media/usbdisk/ -t vfat -o iocharset=utf8,umask=000

```

This worked for me. It won't work for ntfs filesystems.

I don't know how to get automatically usb mounting to grant these permissions
because I don't use automounting software.
Try ivman it is meant to be good for automounting usb devices.

```

sudo apt-get install ivman

```

Hopefully this will help. I just found it out a few minutes ago myself.

---

### Post by ADT on 2007-01-21
I got automounting working thanks to this HOWTO:

[http://greenfly.org/tips/autofs.html]("http://greenfly.org/tips/autofs.html")

---

### Post by medomedo on 2007-03-25
I still strongly believe that the default Ubuntu behavior should allow for read/write permissions. The beauty of Ubuntu is complete only when every thing works conveniently out of the box, right!

Here we are not talking about peace of hardware that we don't have its specifications to write a driver for it. Just make the auto mount with write permissions.


Hello Mr. Ubuntu! please put this on the todo list.

---

### Post by mmogar on 2007-06-22
Medomedo,

I don't know that it is Ubuntu. I have a 2.0 GB flash that will not allow me to write to it but a 256 MB that will. I wish it were the other way around!
They are both FAT. I am going to reformat the 2.0 GB drive and see if that helps.

---

### Post by mmogar on 2007-07-05
The 256 MB was formatted as FAT and the 2.0 GB as FAT32. I reformatted the 2 GB as FAT and now have no problem writing to it.

---

### Post by Dimitriid on 2007-07-28
I tried that auto.fs thing and it did not work, still mounts my SD ( fat16 so that is not a format problem ) cards as read only. This is driving me Insane ive searched for hours and I cannot find any solutions and I am not able to write when 5 days ago I was able to write TO THE EXACT SAME CARD just fine, now its broken. Should I just keep mounting and unmounting for hours until I get lucky?

---

### Post by john8_36 on 2007-09-11
I just added this line to my /etc/fstab:

     #/dev/sdb
     /dev/sdb	     /media/usbdisk     vfat	iocharset=utf8,umask=000	0	0

Of course, your would vary depending on your device...

     #/dev/DEV_ID
     /dev/DEV_ID /media/YOUR_MOUNT_POINT     [FSTYPE}	iocharset=utf8,umask=000	0	0

Have you tried that?

The fstype of your flash drive may vary from mine, but normally USB drives are of the fstype "vfat" (FAT32, etc).

---

### Post by netseer on 2007-10-18
Hi, I had the same issue, but my NTFS support for external drives stopped working after I re-installed Ubuntu (long story of broken HDD).  I used Synaptic to install a package called "ntfs-config" (Desc: Enable/disable write support for any NTFS devices).  After starting the configuration, the option to enable write support on external devices was unchecked, I checked it and after mounting the NTFS external drives I can read and write on them.

Good Luck!!!
NetSeer

---

### Post by SoloSalsa on 2007-11-19
I am having the same problem (but I do not use 64 bit).  I tried all the stuff mentioned, but I can not write to the dang drive!  I swear, everything worked fine on the drive just until yesterday.  It always reports that it is all read and write, but it actually can only read, not write.  I tried mounting from command line, and the only difference made is that root owns it now, but cannot write to it.  Before, with it mounted automatically, it claimed to give everyone read and write full access.
Window on left is opened as user, and reports root as owner and the only one to write.
Window on right is opened as root, and reports full access, but really is only read-only (and it has these weird face things, I do not know what they stand for).
I am extremely mad right now, because I NEED to transfer things!  The solutions mentioned here do not help me.

---

### Post by Jouke74 on 2007-11-20
Any system log messages, while mounting / trying to write? Open a terminal and type: "dmesg" and hit enter.

---

### Post by Mithrilhall on 2007-11-20
I connected an external hard drive the other day for the first time and couldn't write to it.

It was mounted as something like '/media/disk'. I just chowned it and all was good.

```

chown -Rv myname:myname /media/disk

```

---

### Post by MichaelSM on 2007-11-25
Hi Mithrihall
Nice to read your fix.
But .....
Why THIS?

michael@michael-desktop:~$ sudo chown -Rv michael:michael /media/sda1
chown: changing ownership of `/media/sda1/fsck0000.rec': Operation not permitted
(Stuff omitted)
chown: changing ownership of `/media/sda1': Operation not permitted
failed to change ownership of `/media/sda1' to michael:michael
michael@michael-desktop:~$ 

A USB stick has been mounted, from /dev/sda1 to media/sda1. It is owned by 'root'.

Having done "sudo mount /dev/sda1 /media/sda1" I now have a Desktop icon called sda1 which I can read the files inside of, but cannot write to it. I can take files out of it......

Is there another command I can use?

Thank you,

Mike.

---

### Post by Mithrilhall on 2007-11-26
What do you get with this?

```

cd /
cd media
sudo chown -Rv michael:michael sda1/

```

---

### Post by MichaelSM on 2007-11-28
Thanks Mithrilhall.

I ran those commands and all looked good at first. Bummer.

In the end I gave up and updated to Gutsy. 

I HATE giving up, but I'll put my old Edgy hard drive in a drawer and worry about it later.

Feisty and Gutsy don't have any problems with USB permissions, so far.

I just wish that the Ubuntu developers had a more circumstantial approach to simple programming for the masses rather than relying upon everyday users becoming overnight programmers.

Thanks for your help.

Michael.

---

### Post by soumo on 2007-12-04
Hi guys,

same issue here.  I have 3 SD cards, 2 are 512, 1 is 2GB.  They all mounted fine via my external card reader with read-write access until unexplicably all denied me write accesss.  This happened at the same time for all three.  I may have inadvertantly hotswapped, but have done so previously with no issues.  Another possibility is that it happened after a system suspend with usb plugged in, but I cannot confirm.

When I tried  Mithrilhall's chown solution, it recursively told me for every file on card including the trash bibs, and folders that:

> chown: changing ownership of `/media/disk/DCIM/107PENTX': Read-only file system
failed to change ownership of `/media/disk/DCIM/107PENTX' to soumo:soumo

I have tried chmod:
> soumo@vortex:~$  chmod 777 '/media/disk'
chmod: changing permissions of `/media/disk': Read-only file system


I have tried using nautilus as root and not (soumo) to change the emblems & permissions:
As soumo, there is no locked emblem on 'disk' but there is an unreadable one on .hal-mtab-lock.  When I check the emblems, it is unchecked.  The permissions for owner:soumo, are folder access read/write, file access ---.  When I try to change them to r/w as well, it appears to work, but on checking the properties again, they've reverted.  If I try to change the file access for group:root or others, the same thing happens.  If I try to change folder access for those two, I get the message, > Couldn't change the permissions of "disk" because it is on a read-only disk.

As root, I get the same behaviour except there is a locked emblem on 'disk' which does not appear in the properties, and no emblem on the .hal-mtab-lock!  So reversed from soumo nautilus.

The media directory appears as:
> drwx------ 7 soumo root    16384 1969-12-31 19:00 disk

Which I gather means only soumo has rwx and that's it?

The mount command shows:
> soumo@vortex:/media$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda2 on /media/sda2 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/disk type vfat (ro,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)

where, sda3 is ubuntu, sda2 is windows vista, and sdb1 is the SD card.
I have no idea what the other stuff is, and pretty sure my swap file is sda1. 

sudo fdisk -l yields:
> soumo@vortex:/media$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95f3457a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             742         864      987997+  82  Linux swap / Solaris
/dev/sda2   *         865       14592   110270160    7  HPFS/NTFS
/dev/sda3               1         741     5952051   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 512 MB, 512229376 bytes
9 heads, 8 sectors/track, 13895 cylinders
Units = cylinders of 72 * 512 = 36864 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               4       13896      500107+   6  FAT16


Finally my fstab contains no reference to the usb reader/card:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=4c0fe717-7ff7-4b0b-a4e0-0e64520cd8bb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=9CE08CE0E08CC1CE /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=fd2bd21d-cf14-4c02-a553-722cc67d1891 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

and I used mtools to automount the cards:
> sudo mlabel -i /dev/sdb1 -s ::
sudo mlabel -i /dev/sdb1 ::SD-2GB


which worked perfectly.  Even when I swapped the 2gb card for the others, it showed up as SD-2GB with the SD icon I set manually on my desktop.  Now the icon remains but the label is just 'disk'.

When I put the card in my camera and hook up the device via usb, the usb icon comes up with the apropriate disk label, ie. Canon or Pentax as the cards were originally in different cameras, AND I have full rw privileges!

I hope this info can be used to figure out what's going on.

-thanks.

---

### Post by soumo on 2008-01-09
Another update:

I have switched to a SanDisk 4GB SDHC Ultra II card, formated as FAT16, and it has been read-only from the get-go!

Using mtools, mlabel:
> soumo@vortex:~/Desktop$ sudo mlabel -i /dev/sdb1 -s ::
 Volume has no label
soumo@vortex:~/Desktop$ sudo mlabel -i /dev/sdb1 ::SD2GB
plain_io: Operation not permitted
buffer_flush: write: Illegal seek
buffer_flush: write: Illegal seek
plain_io: Operation not permitted
buffer_flush: write: Illegal seek
plain_io: Operation not permitted
buffer_flush: write: Illegal seek
plain_io: Operation not permitted
buffer_flush: write: Illegal seek


Using ntfsprogs:
> soumo@vortex:~/Desktop$ sudo ntfslabel /dev/sdb1 SD2GB
Error opening partition device : Read-only file system
Failed to startup volume : Read-only file system
Couldn't mount device '/dev/sdb1' : Read-only file system

Again, all works well when linked to usb via my camera.  Is it possible that the card reader is the problem?  It is a MobileLite.

---

### Post by kelvin spratt on 2008-01-09
Just throwing a spanner in the works I have about 15 flash drives and about the same number of SD cards, Only once have I ever had a problem with read/write and that was my first post I got just one reply. Now I don't think you should be entering them in your fstab They are not entered in mine, I also have 2 usb 500gb hdd they a permanently plugged in they are not in the fstab as far as I know I might wrong. Its hal that mounts and unmounts removable USB media. and mounts every thing read/write? On My Debian setup i have not mounted any drives as yet as i'm setting it up but all plug in media is read / write on install. my Flash/ SD media are all brands and all formats with no problems.All used on Gutsy or anything else I might have setup at the time.

---

### Post by madflyguy on 2008-01-22
I have this problem with 1 specific flash drive, my other flash drives work fine. The non-writeable flash drive was given to me from a  company I used to work for, so I can't give any OEM manufact details, but its mount pt details I'll post later.

---

### Post by Ghuloomo on 2008-02-27
I have the same problem! Reading 3 pages of replies and following all the solutions still didn't help!
I got this 4 GB USB flash drive (myFlash) from a friend of mine. I was supposed to see the movie she put for me, and then put some movies for her. I saw the movie :D , now I can't put for her.. lolz.. It's been 4 hours I'm reading and trying..

Wish this gets fixed with Ubuntu 8.4 ..
I respect the security, but there should be flexibility too.
PLUG THE USB
PUT YOUR FILES IN
UNPLUG IT

---

### Post by YAOMTC on 2008-05-15
I have the same problem here. I think it's because I previously used it with 7.10, and I'm no longer the "owner" since I've done a fresh install to 8.04.

None of these fixes are working.

---

### Post by jabeez on 2008-05-23
> **YAOMTC said:**
> I have the same problem here. I think it's because I previously used it with 7.10, and I'm no longer the "owner" since I've done a fresh install to 8.04.

None of these fixes are working.

I had a similar problem before and appear to have it again. Before I had used a flash drive with no issues on my laptop, but then after I did a fresh install it still had my old user as owner, so I couldn't do anything with the drive?!?!? I think the same is happening, I was just gonna have the wife put a file I really need on the drive and bring it to work, but she can't write to the thing....grrrrrrrrrrrrrrrr. Talk about irritating, it should be completely brainless to use a flash drive without delving into retarded permission issues (unless you want to put them on of course). I mean, isn't the whole point of removable storage to be able to, you know, remove it and take it elsewhere to use??? Sometimes..............:confused:

---

### Post by MehowS on 2008-06-10
I had the same problem. Out of blue I couldn't write to my cards because they were mounted as read only. It just happened like this, day before they were fine, next not. 

In my case solution was to reformat them with DOS/Win format. Everything back to normal after I've done that.

I think I'd played too much with them, swaping between Ipaq, Win laptop and Linux box and somehow fat got confused....

When I had this problem I tried to search for some solutions on the web and I found out few posts about similar problem but none really working solution. 

Luckily reformat worked like charm, hope it will for others !

---

