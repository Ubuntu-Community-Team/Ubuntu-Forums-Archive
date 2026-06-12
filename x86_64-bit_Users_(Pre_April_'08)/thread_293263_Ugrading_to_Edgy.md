---
title: "Ugrading to Edgy?"
date: 2006-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by confusimo on 2006-11-05
I have DD 6.06 64 bit.  160gb SATA HD.  I got a second 20gb IDE ATA100 hard drive to test other OSes.  I unpluged the SATA and installed Edgy 6.10 64bit on the 20gb.  Everytyhing went smooth.  Now without dual booting.  Can I just plug in the SATA back in and without reoformatting and mount it as storage at least.  6.10 boots fine so boot loader is not the question.  Can I just skip the loader and mount it as a backup HD.  I don't see a disks area in System like in 6.06 DD.  So it is possible in 6.10 64bit.

Thanks,
Confusimo

---

### Post by kuja on 2006-11-05
Everything is possible, seeing as things like that disk manager are essentially "frontends" to doing things the good old fashioned way, which never disappears, ever.

All of this is governed by the /etc/fstab file.

---

### Post by confusimo on 2006-11-05
So what part of that do I alter to mount my SATA HD?

Thanks,
Confusimo

---

### Post by kuja on 2006-11-05
Well, first open the file /etc/fstab with your editor of choice, with root privileges. 

There are a number of things on each line, each thing seperated either by a lot of space, or a tab.

Here's a sample line to give you an idea:
```
/dev/sdb1	/home	xfs	defaults	0 0
```


**/dev/sdb1:** This is the device to be mounted, for example, sdb1 would be my second sata drives first partition.
To obtain a list of partitions on a device, do this in a terminal (change the device as needed):
```
sudo parted /dev/sda print
```

**/home:** the mount point, mount it wherever you'd like, but it has to be an otherwise empty folder. In my example I mounted that partition on /home, making it the container of my home partition.

**xfs:** the filesystem goes here. ext3 is the default for Ubuntu.

**defaults:** special mount options go here, if unsure, leave it as defaults.

**0 0:** dump and pass, advanced stuff, leave alone unless you know what you're doing.

Afterwards save the file and close.

You can mount the partitions you've added with this command:
```
sudo mount -a
```

It will automatically be mounted on boot.

If you have any questions, let me know.

---

### Post by confusimo on 2006-11-05
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=9148442f-727b-422d-b2da-8e42a1f91100 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=0d82e7d4-6479-4caa-a243-60a5d19ef5e0 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

----------------------------------------------------------------------------------------------------------------------------------------------------

Not sure which part of that fstab is the SATA and which is the IDE I'm booting with.

Thanks,
Confusimo

---

### Post by kuja on 2006-11-05
Well, the part you just pasted only mentions the ide drives (/dev/hd?)
SATA drives are /dev/sd?
(Where "?" is a letter)

You'll have to add a new line for the SATA drives partition manually.

To figure out which partitions are available on the first SATA drive, use this command:
```
sudo parted /dev/sda print
```

It will tell you which partitions are on the SATA drive, what their /dev entry is, how big they are, and what the filesystem type is.

---

### Post by confusimo on 2006-11-05
administrator@ivlaga:~$ sudo parted /dev/sda print
Password:

Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  157GB  157GB   primary   ext3         boot 
 2      157GB   160GB  3084MB  extended                    
 5      157GB   160GB  3084MB  logical   linux-swap        

Information: Don't forget to update /etc/fstab, if necessary.             

administrator@ivlaga:~$

---

### Post by kuja on 2006-11-05
Here's some lines you should consider adding to the fstab, given that information, though I'd be careful about the boot partition?

First, lets make the mountpoint (this is an example, anyway)
```

sudo mkdir /media/sda1

```

Next, add these lines to the end of the /etc/fstab file:

```

/dev/sda1 /media/sda1 ext3 defaults 0 0
/dev/sda5 none swap swap 0 0

```
Save the file, now, mount the "new" partitions:
```

sudo mount -a

```

Now, to make sure you can write to the partion:
```

sudo chown $USER:$USER /media/sda1

```

---

### Post by confusimo on 2006-11-05
Wow, that actually worked, thanks.  Conmfusimo

---

### Post by confusimo on 2006-11-07
Also is Xbuntu the same.  It's using the same fstab file.  But if I do 

sudo mount -a

from a terminal and restart nothing shows up.

Thanks,
Confusimo

---

