---
title: ":( Hard Time with Mounting / Sound"
date: 2007-05-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mutal1ty on 2007-05-08
Having a Rough time going cold turkey from windows.... 

Took several hours to figure out how to get the boot to NOT FREEZE and shut my monitor after selecting gereric in the GRUB menu, turned out I had to edit the Kernel Line with vga=771 in the menu.lst file now I can get down to business since this also solved my "Failed to Initialize HAL" error as well

Ok... Here goes Que Wall'O'Text

System Specs:
-Abit AN8 SLI Mobo
-2gb ddr400
-Athlon 64 4000+
-ATI X850XT 256mb
-Audigy XFi Platinum (taken out for lack of driver support)
-reverting back to the MOBO built in sound. The integrated sound is placed on a small daughterboard, it is basically a Realtek ALC850 chip which has been moved off the motherboard, and it goes under the name: Abit AudioMAX. The ALC850 chip provides 7.1 Channel AC'97 audio, jack sensing and S/PDIF in/out.
WD 80 GB HD (Linux install) 
WD 250 (Linux/ntfs)(2 partitions)
Maxtor 300 (FAT) (2 partitions)
WD 500 GB (FAT) (1 partition

Kernel(Ubuntu Feisty 64bit desktop):   Linux dj-desktop 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

--------------------------------------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------------------------------------------
First the Sound problem:
the system isn't seeing it at all
I tried the following commands which returned nothing
> lsmod | grep ac97
lsmod | grep ac97

Then I scanned through dmesg and found no error msges
then I tried this :
# echo "options snd_intel8x0 index=-2" | sudo tee -a /etc/modprobe.d/alsa-base
which returned:  options snd_intel8x0 index=-2

at this point I'm clueless as what to do, I've spent 2 days looking all over the web to no avail.



--------------------------------------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------------------------------------------------
now onto the more major problem, Mounting:
command
> # Sudo fdisk -l
returned the following
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
1 heads, 15 sectors/track, 65118211 cylinders
Units = cylinders of 15 * 512 = 7680 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1    17895697   134217727+   4  FAT16 <32M

Disk /dev/sda1: 137.4 GB, 137438952960 bytes
1 heads, 15 sectors/track, 17895697 cylinders
Units = cylinders of 15 * 512 = 7680 bytes

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   *           1    17895697   134217727+   4  FAT16 <32M

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9327    74919096   83  Linux
/dev/hdb2            9328        9729     3229065    5  Extended
/dev/hdb5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5099    40957686   83  Linux
/dev/sdb2            5100       30515   204154020    7  HPFS/NTFS

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
86 heads, 15 sectors/track, 454319 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      208090   134217727+   4  FAT16 <32M

Disk /dev/sdc1: 137.4 GB, 137438952960 bytes
86 heads, 15 sectors/track, 208089 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes

     Device Boot      Start         End      Blocks   Id  System
/dev/sdc1p1   *           1      208090   134217727+   4  FAT16 <32M

So I added the following lines to the fstab file 

> /dev/sdb2 /media/windows ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 0
/dev/sda1 /media/windows vfat user,auto,fmask=0111,dmask=0000 0 0
/dev/sda1p1 /media/windows vfat user,auto,fmask=0111,dmask=0000 0 0
/dev/sdc1 /media/windows vfat user,auto,fmask=0111,dmask=0000 0 0
/dev/sdc1p1 /media/windows vfat user,auto,fmask=0111,dmask=0000 0 0

still assuring the last line was empty
 
and when I attempt to mount I get the following:

> dj@dj-desktop:~$ mount -a
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb2': Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software.
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: special device /dev/sda1p1 does not exist
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: special device /dev/sdc1p1 does not exist


If somone could help me mount my drives I will love you forever.

I really want to stick with Ubuntu, as I really hate windows, but I'm having a hard time just getting started :(

---

### Post by Cappy on 2007-05-08
All this stuff should be automatic.
Post your output from:
```
aplay -l
```

You'll want to run this code incase you don't have folders:
```

sudo mkdir /media/sdb2
sudo mkdir /media/sda1
sudo mkdir /media/sdc1

```

```

/dev/sdb2 /media/sdb2 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 0
/dev/sda1 /media/sda1 vfat user,auto,fmask=0111,dmask=0000 0 0
/dev/sdc1 /media/sdc1 vfat user,auto,fmask=0111,dmask=0000 0 0

```

You'll have to reboot to windows to follow the chkdsk instructions.

I've never written a whole fstab myself so someone else should fix it some more.

---

### Post by Mutal1ty on 2007-05-09
```
dj@dj-desktop:~$ aplay -l
SNDCTL_SYSINFO: No such device or address
aplay: device_list:222: no soundcards found...

```

after doing the directory creation and modifying the fstab, I still get the following:
```
dj@dj-desktop:~$ sudo mount -a
Password:
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb2': Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software.
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

I KNOW those partitions are good thats all my Anime/archives/pr0n  :(

---

### Post by Cappy on 2007-05-09
```

/dev/sdb2 /media/sdb2 ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 0
/dev/sda1 /media/sda1 fat fat=16,user,auto,fmask=0111,dmask=0000 0 0
/dev/sdc1 /media/sdc1 fat fat=16,user,auto,fmask=0111,dmask=0000 0 0

```
sda1 and sdc1 are fat16? if so, try the above.

Ubuntu should have set all this stuff up automatically, did you install Feisty Fawn from a CD?

This should have been posted in the "Absolute Beginner Talk" since the people browsing that section have probably dealt with these problems more.

---

### Post by Mutal1ty on 2007-05-09
I installed the 64bit Feisty from the Live CD, I Checksummed and verified it to make sure it was perfect before attempting the installation.

as posted above the fdisk returned HD descriptions like this:

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
1 heads, 15 sectors/track, 65118211 cylinders
Units = cylinders of 15 * 512 = 7680 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 17895697 134217727+ 4 FAT16 <32M

Disk /dev/sda1: 137.4 GB, 137438952960 bytes
1 heads, 15 sectors/track, 17895697 cylinders
Units = cylinders of 15 * 512 = 7680 bytes

```

Now I'm assuming that "FAT16 <32M" means they are either fat16 or 32 which is why I used the vfat rule.

I'll Post in that forum as well, see if I can't get some help.

---

