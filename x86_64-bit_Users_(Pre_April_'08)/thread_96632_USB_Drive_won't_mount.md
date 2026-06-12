---
title: "USB Drive won't mount"
date: 2005-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by grsing on 2005-11-29
Actually, it mounts the first time I plug it in after a reboot, but when I eject it and use it elsewhere, then plug it back in, it doesn't mount, necessitating a reboot, which is a rather major annoyance.  Any suggestions?

---

### Post by earobinson on 2005-11-29
can you post a dmesg | tail when you plug it in the first time and the second

also try using a sudo mount -a (for more info type man mount) the second time you plug it in

EDIT: dmsg changed to dmesg

---

### Post by grsing on 2005-11-29
I'm still something of a newbie, how do I do the dmsg | tail thing?  Thanks.

---

### Post by earobinson on 2005-11-29
[QUOTE=grsing]I'm still something of a newbie, how do I do the dmsg | tail thing?  Thanks.[/QUOTE]
Im sorry my bad, these are all terminal commands in the terminal just type it in.

---

### Post by grsing on 2005-11-29
When I type dmsg | tail, the terminal outputs dmsg: command not found

I also found that I don't have to restart to make it work, just log out and back in, if that says anything.

---

### Post by earobinson on 2005-11-29
sorry my bad (wow guess I need more coffee), im not actualy at my linux box im on windows :( and made a small typo its dmesg no dmsg

I assume sudo mount -a did nothing?

---

### Post by grsing on 2005-11-29
sudo mount -a did nothing

Here's the dmesg, with the drive working (I'm working on stuff from it now, so it'll be a bit before I can get it with it not working).

[140705.942251] sdg: Write Protect is off
[140705.942254] sdg: Mode Sense: 23 00 00 00
[140705.942256] sdg: assuming drive cache: write through
[140705.942260]  /dev/scsi/host13/bus0/target0/lun0: p1
[140705.944531] Attached scsi removable disk sdg at scsi13, channel 0, id 0, lun 0
[140705.945680] usb-storage: device scan complete
[140779.804077] btdownloadgui[30631]: segfault at 0000000000000000 rip 0000000000000000 rsp 00007fffffd6d798 error 14
[141151.924826] btdownloadgui[30638]: segfault at 0000000000bf1900 rip 0000000000bf1900 rsp 00007fffffc58bc8 error 15
[141400.574462] rhythmbox[14526] general protection rip:43ab4a rsp:7fffffafea18 error:0
[141413.615944] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

---

### Post by earobinson on 2005-11-29
no problem, the diff between the working and not should tell us something.

also this info could help:
```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by grsing on 2005-11-29
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1824    14651248+  83  Linux
/dev/hdb2            1825        2432     4883760   82  Linux swap / Solaris
/dev/hdb3            2433        6609    33551752+   c  W95 FAT32 (LBA)
/dev/hdb4            6610       19457   103201560    7  HPFS/NTFS

Disk /dev/sdg: 504 MB, 504365056 bytes
32 heads, 16 sectors/track, 1924 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1        1924      492536    e  W95 FAT16 (LBA)

Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              14G  2.9G   11G  23% /
tmpfs                 500M     0  500M   0% /dev/shm
tmpfs                 500M   14M  487M   3% /lib/modules/2.6.12-9-amd64-generic/volatile
/dev/hda1             150G   75G   75G  51% /media/Windows
/dev/hdb3              32G   18G   15G  54% /media/FATMedia
/dev/hdb4              99G   89G   11G  90% /media/NTFSMedia
/dev/sdg1             481M  306M  176M  64% /media/TRAVELDRIVE
/dev/hdd              4.4G  4.4G     0 100% /media/cdrom1

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/Windows     ntfs    nls=utf8,umask=0222        0       0
/dev/hdb3       /media/FATMedia     vfat    iocharset=utf8,umask=000        0     0
/dev/hdb4       /media/NTFSMedia     ntfs    nls=utf8,umask=0222        0 0
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by grsing on 2005-12-06
Wow, sorry it took so long to get to it while it wasn't working.

the dmesg is:

[230363.455245] sdf: Write Protect is off
[230363.455248] sdf: Mode Sense: 23 00 00 00
[230363.455250] sdf: assuming drive cache: write through
[230363.462246] SCSI device sdf: 985088 512-byte hdwr sectors (504 MB)
[230363.463244] sdf: Write Protect is off
[230363.463247] sdf: Mode Sense: 23 00 00 00
[230363.463250] sdf: assuming drive cache: write through
[230363.463253]  /dev/scsi/host7/bus0/target0/lun0: p1
[230363.465526] Attached scsi removable disk sdf at scsi7, channel 0, id 0, lun 0
[230363.466826] usb-storage: device scan complete

fdisk:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1824    14651248+  83  Linux
/dev/hdb2            1825        2432     4883760   82  Linux swap / Solaris
/dev/hdb3            2433        6609    33551752+   c  W95 FAT32 (LBA)
/dev/hdb4            6610       19457   103201560    7  HPFS/NTFS

Disk /dev/sdf: 504 MB, 504365056 bytes
32 heads, 16 sectors/track, 1924 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        1924      492536    e  W95 FAT16 (LBA)

df:

Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              14G  3.1G   10G  24% /
tmpfs                 500M     0  500M   0% /dev/shm
tmpfs                 500M   14M  487M   3% /lib/modules/2.6.12-10-amd64-generic/volatile
/dev/hda1             150G   75G   75G  50% /media/Windows
/dev/hdb3              32G   15G   18G  45% /media/FATMedia
/dev/hdb4              99G   89G   11G  90% /media/NTFSMedia

cat:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/Windows     ntfs    nls=utf8,umask=0222        0       0
/dev/hdb3       /media/FATMedia     vfat    iocharset=utf8,umask=000        0     0
/dev/hdb4       /media/NTFSMedia     ntfs    nls=utf8,umask=0222        0 0
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Thanks for your help.

---

