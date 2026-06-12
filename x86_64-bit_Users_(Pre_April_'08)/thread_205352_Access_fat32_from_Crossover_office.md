---
title: "Access fat32 from Crossover office"
date: 2006-06-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by immanueloffice on 2006-06-28
AMD 64, Dapper 64bit (upgraded from Breezy 64bit)

Problem: When I have Word or Excel open in Crossover office (trial version), and I try to open a file on the FAT32 partition (/documents), the application hangs. 

I have asked the CXOffice mailing list and they said the following, but haven't offered any more help at this time:

> I think there is a bug with the vfat driver on the x86-64 build however I am
not sure, I've seen two tickets reporting this problem. I have a x86-64
system here for testing but I have not gotten around to trying to access a
vfat partition yet. Give me a day or so and I will look in to this and let
you know if its a wine bug or something going on in the kernel.

I also found somewhere in the ubuntu forums that it might be a problem in my fstab for mounting the FAT32 partition. My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /boot           ext3    defaults        0       2
/dev/sda5       /documents      vfat    umask=000        0       0
/dev/sda9       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     ntfs    defaults        0       0
/dev/sda2       /media/sda2     vfat    defaults        0       0
/dev/sda7       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

I'm trying to keep all my files in the FAT32 partition so that someone can dual boot to Windows XP and see all the same files. 

Does anyone have any ideas to try? I have no problem accessing the files on the FAT32 in openoffice or any other program, only in CXOffice. For some reason, I can't install wine in synaptic (says it is not installable), so I can't try to see if wine can access the FAT32.

Thanks!
Crystle

---

### Post by Kilz on 2006-06-29
[QUOTE=immanueloffice]AMD 64, Dapper 64bit (upgraded from Breezy 64bit)

Problem: When I have Word or Excel open in Crossover office (trial version), and I try to open a file on the FAT32 partition (/documents), the application hangs. 

I have asked the CXOffice mailing list and they said the following, but haven't offered any more help at this time:



I also found somewhere in the ubuntu forums that it might be a problem in my fstab for mounting the FAT32 partition. My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /boot           ext3    defaults        0       2
/dev/sda5       /documents      vfat    umask=000        0       0
/dev/sda9       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     ntfs    defaults        0       0
/dev/sda2       /media/sda2     vfat    defaults        0       0
/dev/sda7       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

I'm trying to keep all my files in the FAT32 partition so that someone can dual boot to Windows XP and see all the same files. 

Does anyone have any ideas to try? I have no problem accessing the files on the FAT32 in openoffice or any other program, only in CXOffice. For some reason, I can't install wine in synaptic (says it is not installable), so I can't try to see if wine can access the FAT32.

Thanks!
Crystle[/QUOTE]

Here is what the line I have commented out in my fstab looks like. I deleted the windows partition ages ago and left the line in place in case I needed to create a windows partition and access it in the future.
```
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0 1
```
But if Open Office can read and write to it , the line may not be the problem. 
Wine isn't available for a 64bit system with synaptic. You will see it listed, but it wont install. You can use a work around to [install wine wit this howto]("http://www.ubuntuforums.org/showthread.php?t=185557") but be aware that wine isn't a gui program, its a kind of emulator that allows you to run some windows programs on Linux. I would install a simple text editor to check read and write access under wine.

---

### Post by immanueloffice on 2006-07-06
My partition is vfat and I think that is the kicker - anyone else able to access a vfat partition from wine or cxoffice? 

I have to follow a how to yet to install wine and try it from there.

---

