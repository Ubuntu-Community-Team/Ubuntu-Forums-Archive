---
title: "Mounting Mac HD"
date: 2005-11-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by N.V. on 2005-11-10
I have no idea how. There's some files on my Mac HD that I need but I'm mid panther-tiger upgrade (I misplaced disc 2) and I need to mount my Mac HD. simple really. :P  I'm on Live boot Ubuntu 5.04 on a G3 iBook. Any help appreciated.

---

### Post by ssam on 2005-11-10
first we need to find them, open a teminal (applications -> acessories) and type

```
sudo fdisk -l /dev/hda
```

this will list all the partitions on the disk. paste that here then we can work out a mount command for you.

---

### Post by N.V. on 2005-11-10
/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k )  Partition map
/dev/hda2        Apple_Driver_ATA Macintosh                64 @ 64       ( 32.0k )  Unknown
/dev/hda3        Apple_Driver_ATA Macintosh                64 @ 128      ( 32.0k )  Unknown
/dev/hda4           Apple_Patches Patch Partition         512 @ 192      (256.0k )  Unknown
/dev/hda5               Apple_HFS Untitled           58604406 @ 704      ( 27.9G )  HFS
/dev/hda6              Apple_Free                          10 @ 58605110 (  5.0k )  Free space

Block size=512, Number of Blocks=58605120
DeviceType=0x0, DeviceId=0x0
Drivers-
1: @ 64 for 21, type=0x701
2: @ 128 for 34, type=0xf8ff



There you go.

---

### Post by ssam on 2005-11-10
ok try these

```

sudo mkdir /media/mac
sudo mount -t hfsplus -o "ro" /dev/hda5 /media/mac

```

this makes a mount point at /media/mac and mounts the disk with filesystem type hfsplus, options readonly, from the 5 partition of the primary disk (hda5), to the mount point.

to unmount it

```
sudo umount /dev/hda5
```

(note that its **u**mount no **un**mount)

---

### Post by N.V. on 2005-11-10
It worked. Thankyou. :) However, I need to move the file over. but the file has spaces in the name and I get this when I try to move it. (I can't get into this folder in the GUI)

root@ubuntu:/mnt/mac/users/user/desktop # mv English coursework.doc /mnt/mac
mv: cannot stat `English': No such file or directory
mv: cannot stat `coursework.doc': No such file or directory


What do I do?

---

### Post by ssam on 2005-11-10
are you trying to get the file on or off the mac disk?

if you want to get it on, you will need to take the 
```
-o "ro"
```
out of the mount command. this will mount the disk read+write. but beware, you can do damage like this.

you can put quotes around the name on the command line to contain the space.

```
mv "English coursework.doc" /mnt/mac
```
although that would move it to the root of the mac file system. where do you want to move it to? you might be better off using cp instead of mv, so that you copy the file.

---

