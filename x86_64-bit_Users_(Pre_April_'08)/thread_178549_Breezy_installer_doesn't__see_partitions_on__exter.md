---
title: "Breezy installer doesn't  see partitions on  external hard dive"
date: 2006-05-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by seatea on 2006-05-17
I have tried off and on all day to get my new Iomega (I think my  real mistake was getting Iomega) external firwire drive to  install ubuntu. After much time and many hassles, I finally got the drive partitioned for my needs. When I ran the installer for Breezy, it  saw the drive, but none  of the partitions. I aborted because I want to use this as a multi-purpose drive and eventually run OS X on it as well. The  partitioned  drives all mount when I boot  into ubuntu and also show up with  "mount"  and "fdisk -l" in terminal. I have made several runs with fdisk and mke2fs to try to  get the partition  in shape to attempt  installing Breezy on it again, but I have not had  any success. The partition I  want to use  is /dev/sda5 and is about 40 GB. Could someone help me out with  some rather  concrete  advice on how to get the installation  done on  the /dev/sda5 partition?

*Forgot to note that I am using Mac OS 9.2.2. I  don't yet have Mac OS X.

Here is my fdisk -l and mount output:
"/dev/sda
        #                    type name                  length   base      ( size )  system
/dev/sda1     Apple_partition_map Apple_partition_map        63 @ 1         ( 31.5k)  Partition map
/dev/sda2          Apple_FWDriver El Gato FireWire Disk Support       512 @ 64        (256.0k)  Unknown
/dev/sda3              Apple_Free Apple_Free              5120 @ 576       (  2.5M)  Free space
/dev/sda4               Apple_HFS Apple_HFS           78144028 @ 5696      ( 37.3G)  HFS
/dev/sda5               Apple_HFS Apple_HFS           78144028 @ 78149724  ( 37.3G)  HFS
/dev/sda6               Apple_HFS Apple_HFS           78144028 @ 156293752 ( 37.3G)  HFS
/dev/sda7               Apple_HFS Apple_HFS           78144028 @ 234437780 ( 37.3G)  HFS

Block size=512, Number of Blocks=312581808
DeviceType=0x0, DeviceId=0x0

/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hda2          Apple_Driver43 Macintosh                54 @ 64       ( 27.0k)  Driver 4.3
/dev/hda3          Apple_Driver43 Macintosh                74 @ 118      ( 37.0k)  Driver 4.3
/dev/hda4        Apple_Driver_ATA Macintosh                54 @ 192      ( 27.0k)  Unknown
/dev/hda5        Apple_Driver_ATA Macintosh                74 @ 246      ( 37.0k)  Unknown
/dev/hda6          Apple_FWDriver Macintosh               200 @ 320      (100.0k)  Unknown
/dev/hda7      Apple_Driver_IOKit Macintosh               512 @ 520      (256.0k)  Unknown
/dev/hda8           Apple_Patches Patch Partition         512 @ 1032     (256.0k)  Unknown
/dev/hda9               Apple_HFS untitled           16762406 @ 1544     (  8.0G)  HFS
/dev/hda10        Apple_Bootstrap untitled               1954 @ 16763950 (977.0k)  NewWorld bootblock
/dev/hda11              Apple_HFS untitled 3          2875148 @ 37313790 (  1.4G)  HFS
/dev/hda12        Apple_UNIX_SVR2 untitled           19634766 @ 16765904 (  9.4G)  Linux native
/dev/hda13        Apple_UNIX_SVR2 swap                 913120 @ 36400670 (445.9M)  Linux swap
/dev/hda14             Apple_Free Extra                    22 @ 40188938 ( 11.0k)  Free space

seatea@equipage:~$ mount
/dev/hda12 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-powerpc/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda6 on /media/MyMacStuff type hfsplus (rw,nosuid,nodev,uid=1000,gid=1000)
/dev/sda7 on /media/XtraStorage type hfsplus (rw,nosuid,nodev,uid=1000,gid=1000)
/dev/sda4 on /media/MacX type hfsplus (rw,nosuid,nodev,uid=1000,gid=1000)
/dev/sda5 on /media/Ubuntu type hfs (rw,nosuid,nodev,uid=1000,gid=1000)"

---

