---
title: "Gutsy Gibbon (7.10) installation issues"
date: 2007-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by andremedeiros on 2007-10-25
Hello forum.

I downloaded the 64-bit version of Gutsy Gibbon yesterday, and installed it on my PC. Here are the problems I stumbled upon:

1) Couldn't boot into normal mode from the LiveCD. Dunno why, but there's something about the graphics card i'm using:

```
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)
```

After that, the headache started. I'm not sure why, but Ubuntu (other distributions might have the same behaviour, but I'd rather stick with this one, thank you very much) doesn't seem to like RAID disks. My setup was the following:

2 160GB SATA disks in RAID 0 (for the operating system)
2 500GB SATA disks in RAID 0 (for data, movies and tv-shows)

At first, I couldn't even get past the partitioning, since it involved actually saving the partition table, which gparted and fdisk refused to do (both exiting with a segmentation fault). So, I decided to remove the RAID 0 from the first pair of disks so that I could dedicate one to Ubuntu. Got rid of Vista, got Ubuntu.

Now here's where the pain starts:

Every time I boot, I get this "Kernel is alive" message, which is shown for a couple of seconds when it decides to boot. When it doesn't, the message stays there indefinitely, until I restart the computer and decide to try my luck again.

When it finally decides to boot, I keep trying several methods to mount the other partition (the one with the 2 500GB disks), with no luck. It's formated on NTFS 6.0, and has to stay that way, since there is no way for me to move around the files I have now to make room for a format (FAT32 is also out of the question because I have some files > 4gb which it doesn't support).

So, here's the scenario:

There is a file under /dev/mapper called ```
"jmicron_DATA            "
``` (spaces included), which should represent the RAID group, and a "control" file. Nothing besides that. So, after running 

```
kpartx -a /dev/mapper/jmicron_DATA\ \ \ \ \ \ \ \ \ \ \ \  
```

and that is if I don't get the

```
device-mapper: reload ioctl failed: Invalid argument
```

error, or the cooler segmentation fault error, it creates a file called 

```
/dev/mapper/dm-0p1
```

When I succeed in creating that file, I try mounting that with ntfs-3g. Now, FUSE starts whining about the file / resource being busy when it was just created and nothing (AFAIK) is using it. Not mounted, nothing.

I'm including some data here so if anyone has a hint on why these errors occur (disregard the graphics card, i got around that one just fine), I'd appreciate the feedback. And nope, it's not because of [evms]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/119315/"). I've also tried using ntfs-utils with no luck.

**lspci**
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
``` 

**dmraid -ay**
```
RAID set "jmicron_DATA            " already active
```

**fdisk -l**
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007fdb7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f1bcfa2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19458   156288000    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33dcebc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121600   976746496    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table
```

**WHEN I AM ABLE TO DETECT THE PARTITIONS THROUGH KPARTX**

```
changelog@zeus:~$ sudo umount /media/windows
umount: /media/windows: not mounted
changelog@zeus:~$ sudo mount /media/windows/
fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/mapper/dm-0p1 ()
```


**/etc/fstab (just the relevant line)**
```
/dev/mapper/dm-0p1 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```


**fdisk -l | grep NTFS**
```
Disk /dev/sdd doesn't contain a valid partition table
/dev/sdb1   *           1       19458   156288000    7  HPFS/NTFS
/dev/sdc1               1      121600   976746496    7  HPFS/NTFS
/dev/dm-0p1               1      121600   976746496    7  HPFS/NTFS
```

---

### Post by hlmuller on 2007-10-26
Andre,

That was a fantastically detailed report.  Unfortunately, I only have one tip for you.  I have the Nvidia 8400M GS.  To boot the amd64 ISO and NOT get the screen/graphics configuration screen, I had to select the "Start Ubuntu in Safe Graphics Mode" option.

You'll probably have usplash / virtual terminal issues also.  This [comment]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930/comments/56") in bug #150930, is a good starting point when you get to troubleshooting and solving that.

Best of luck, hope you get some good help with that RAID issue.

Harvey

---

### Post by andremedeiros on 2007-10-26
Thanks for the pick-up. Fortunatelly, I solved the RAID issue.

Apparently, the RAID controller produces a filename with spaces, and DMRAID "sanitizes" that name when it is detected, so when the process is finished, DMRAID is trying to use a different file.

So, I downloaded the source from the author's website and applied a patch available on launchpad. Works great now.

BTW, I'm on 32-bit.

---

