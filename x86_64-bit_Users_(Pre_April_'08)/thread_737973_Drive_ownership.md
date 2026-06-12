---
title: "Drive ownership"
date: 2008-03-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by hvacr on 2008-03-28
I have set up hellanzb to use a drive on my windows system to download to. This drive is a ntfs drive, which I can read and write to from ubuntu with no problems. I get errors when using hellanzb about permissions, so I tried changing ownership of the drive, but it will not stay that way. If I run gksudo nautilus and try to change the ownership to myself, it goes right back to root.

How can I do this and make it stick.

---

### Post by wieman01 on 2008-03-28
NTFS cannot handle owerships, nor permissions. So no matter what you do, it won't change a thing.

I had similar problems with FAT32 volumes. Unison - a backup tool - refused to work with it for the exact same reason... permissions. 'rsync' does not work well with FAT32 either.

So my recommendation is to use 'EXT3' instead and use 'fs-driver' so that Windows can read the volume as well:

[http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by utUtu on 2008-03-28
wieman01:

You should install ntfs-3g, 
```
i   ntfs-3g                                                - read-write NTFS driver for FUSE
```

and it has to be mounted differently like mine below

```
root@kubu64:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=897fc7c1-df2f-4e41-a3da-714a6d925f44 /               ext3    defaults,errors=remount-ro 0       1
#[COLOR="Blue"] /dev/hda1
UUID=E0D83E3AD83E0EF2 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1[/COLOR]
# /dev/hda2
UUID=3afca0de-de49-4f69-89dc-37adf7f6f040 /media/hda2     ext3    defaults        0       2
# /dev/hda4
UUID=ce2c1ae2-5f56-45b5-b053-235ad40267ef none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
root@kubu64:~#
```

---

### Post by wieman01 on 2008-03-28
Isn't "ntfs-3g" installed by default in Gutsy? I think there may be a misunderstanding... The OP can access NTFS drives just. I was referring to a 'ext3' driver for Windows so that he/she can format the drive to 'ext3' instead...

---

### Post by utUtu on 2008-03-28
> **wieman01 said:**
> Isn't "ntfs-3g" installed by default in Gutsy? I think there may be a misunderstanding... The OP can access NTFS drives just. I was referring to a 'ext3' driver for Windows so that he/she can format the drive to 'ext3' instead...

There could be, that's why I addressed it to you because I thought you are having the ntfs problem.  I didn't install gutsy - upgraded from feisty, and the early issues were ntfs support.  :)

---

### Post by wieman01 on 2008-03-28
> **utUtu said:**
> There could be, that's why I addressed it to you because I thought you are having the ntfs problem.  I didn't install gutsy - upgraded from feisty, and the early issues were ntfs support.  :)
The OP's problem is a bit different...

---

### Post by hvacr on 2008-03-29
> **wieman01 said:**
> NTFS cannot handle owerships, nor permissions. So no matter what you do, it won't change a thing.

I had similar problems with FAT32 volumes. Unison - a backup tool - refused to work with it for the exact same reason... permissions. 'rsync' does not work well with FAT32 either.

So my recommendation is to use 'EXT3' instead and use 'fs-driver' so that Windows can read the volume as well:

[http://www.fs-driver.org/]("http://www.fs-driver.org/")

Thanks, did the trick.

---

