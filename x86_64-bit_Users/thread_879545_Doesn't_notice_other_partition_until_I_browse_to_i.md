---
title: "Doesn't notice other partition until I browse to it?"
date: 2008-08-04
forum: x86 64-bit Users
---

### Post by mace2 on 2008-08-04
Hi all,

This is probably a simple question but I am new so forgive me.

I have Ubuntu on one partition and Windows on the other. It so happens that I have my music on the Windows partition. When I first boot Ubuntu, I am not able to play my music files in Rhythmbox until I browse to my Windows drive. At that point all the music files are available and the Windows drive seems to mount itself on the desktop.

Is there some way I can make it 'auto-mount' so I don't have to manually on start-up?

Thanks!

---

### Post by Jouke74 on 2008-08-04
Are you using Wubi? I have the same problem when using this. When you are not using Wubi the partition should have been there automagically. 

You can edit your fstab file to include the Windows drive.

---

### Post by mace2 on 2008-08-04
Oh yes, I am using Wubi. Sorry, I should have mentioned that.

Sorry, what do I have to add to this fstab file? Thanks!

---

### Post by philinux on 2008-08-04
If you'd like a gui to to this then install pysdm from synaptic or use

sudo apt-get install pysdm

It's a nice gui for modifying fstab etc.

---

### Post by Goop on 2008-08-04
I'm having the same problem as the person above me, except that I installed Ubuntu 8.04 64-bit via the regular desktop CD. It is especially noticeable for me as my wallpapers are usually stored on my Windows partition, so I have to browse to my hard drive (using a shortcut on the desktop) for any background to appear.

Shouldn't Ubuntu be mounting my Windows partition automatically?

---

### Post by Kilz on 2008-08-04
> **Goop said:**
> I'm having the same problem as the person above me, except that I installed Ubuntu 8.04 64-bit via the regular desktop CD. It is especially noticeable for me as my wallpapers are usually stored on my Windows partition, so I have to browse to my hard drive (using a shortcut on the desktop) for any background to appear.

Shouldn't Ubuntu be mounting my Windows partition automatically?

No, the mounting of windows partitions is not automatic. Please read the excellent suggestions above for making the partition mount all the time.

---

### Post by Jouke74 on 2008-08-04
**Here is an example of my fstab. Please note, do not copy this file as your own fstab. It is just for illustration. In your own fstab the disk ID numbers will be different and therefore this one won't work on your computer. Change your fstab, when you know how to read and alter it, and when you have made a good backup of the file. Faults can make the system inoperable. Of course, you need root rights to alter the file.**

The UUIDs can be found under "Places" > "My computer" > select the right partition and right-click. 
Then select the volume tab.

Copy: sudo cp /etc/fstab /etc/fstab.backup
Edit: sudo gedit /etc/fstab

My fstab:
```
 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=ceffe06a-7f69-4372-ac54-e302eb07d362 /               ext3    noatime,nodiratime,commit=60,errors=remount-ro 0       1
# /dev/sda1
UUID=CAD0D65AD0D64BF7 /media/osswap   ntfs    defaults,umask=007,gid=100,uid=1000 0       1
# /dev/sda2
UUID=7E6447076446C19F /media/store    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=C04821D34821C8CC /media/winsys   ntfs    ro,utf8,gid=46 0       1
# /dev/sdb3
UUID=ae38b676-bde4-4648-ba98-c3ac2b21afd0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Notice that my Ubuntu filesystem is ext3, and I tweaked it to have the extra parameters "noatime,nodiratime,commit=60". This saves the journal harddisk activity during my calculations at night. 

The windows drives Winsys, Store and Osswap are mounted using the NTFS file system (ntfs). 

Store I have mounted as root and the default Ubuntu settings. 

Winsys I have mounted as read only (ro). The Defaults option is gone. 

Osswap is the parttion I use for lots of files that are in between Windows and Ubuntu. Since I write a lot of data I made this partition my own. I have given myself read and write rights on the whole partition. That is what "umask=007,gid=100,uid=1000" does. Note, do not do this if your partition contains data which is important. Uid is my user Id. Gid is my user group.

Read also [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) for an excellent tutorial.

---

### Post by soxs on 2008-08-04
If you didn't explicitly say to mount the windows parttitions at install stage of ubuntu, they won't be mounted later.
They will show up in the left part of  nautilus, but they will only be mounted, in case you doubleclik/browse to them, at this point you get access to your windows hd/files.
On next rebot the same game starts again.
The only exit is to add it your /etc/fstab (as allready pointed out)

---

### Post by fparedesg on 2008-08-21
> **philinux said:**
> If you'd like a gui to to this then install pysdm from synaptic or use

sudo apt-get install pysdm

It's a nice gui for modifying fstab etc.

Thank you! This fixed my problems. I had a shortcut in my Desktop to a Windows directory, and it wouldn't open unless I went to the directory myself (without the shortcut). Now it works normally. Thanks!

---

