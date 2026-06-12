---
title: "mounting FAT with write permission for users"
date: 2005-08-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Garyu on 2005-08-24
*sigh*

I cannot get my FAT32 mount in r/w mode for other users than root. It is quite annoying to have to sudo every time I want to write a file to the common drive I have created for windows/linux sharing of files.

In fstab it originally said "defaults" only for the vfat options. I have tried with "uid=1000,gid=1000" and "umask=000" and "fmask=777,dmask=777" and probably a bunch of other things I stumbled across when googling for a solution, but what works for everyone else just doesn't seem to work for me...  ](*,) 

And yes, I have run "mount -a" after each change in fstab, and I actually noticed a difference, because my "FTP" drive now shows under "Computer" instead of just being mounted as "/FTP". But that doesn't help me much. 

I WANT TO WRITE WITHOUT BEING ROOT!!!!
please help?



**From fdisk -l:**
/dev/hda1   *           1         956     7679038+   b  W95 FAT32
/dev/hda2           11747       24321   101008687+   5  Utökad
/dev/hda3             957        7035    48829567+  83  Linux
/dev/hda4            7036       11746    37841107+  83  Linux
/dev/hda5           12164       24321    97659135    b  W95 FAT32
/dev/hda6           11951       12162     1702827   82  Linux växling / Solaris/dev/hda7           11747       11950     1638567   82  Linux växling / Solaris

[B]
From fstab:[/B]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /FTP            vfat    rw,auto,user,exec,umask=000        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Chris Cromer on 2005-08-24
/dev/hda5 /FTP vfat rw,auto,umask=000 0  0

should do it. And I know for a fact it works because I use it myself. Although my drive is FAT32 if it matters.

Please make sure that /FTP exists before you put this into fstab and try to mount it. Otherwise it won't work.

Oh and I had to reboot before it would actually work for me. No matter how many times I tried using the mount command it didn't show the changes till I rebooted.

I hope this helps you out.

---

### Post by felipe on 2005-08-24
i thought "mount" -a was useless if you don't use "umount" first :)

try this to test your settings without having to edit fstab each time:

[CODE]
mount -o remount,users,rw,<any comma separated options> /dev/hda5
[CODE]

i can write to my vfat partition, and yes, umask=000 is the correct value to achieve that

have fun

---

### Post by Chris Cromer on 2005-08-24
Yeah I had tried umount, but I kept getting messages saying the partition was busy and wouldn't let me umount it.

---

### Post by felipe on 2005-08-24
"the partition is busy" means you are occupying it with a shell or with nautilus etc...

close all of your windows, or ever reboot, and then try again

---

### Post by jamesrw on 2005-08-24
i have my mount set to noauto because it mounts as root otherwise. works fine for me. that may depend if the mount point is under your home directory or not.

---

### Post by Corbelius on 2005-08-24
[QUOTE=Garyu]
/dev/hda5       /FTP            vfat    rw,auto,user,exec,umask=000        0       2
[/QUOTE]

Change /ftp with /mnt/ftp and try again.

---

### Post by d0nk on 2005-08-25
My setup allows for users to read/write.  I have the drive owned by a group i made called "shared", and anyone in "shared" is able to write to it.  It is mounted by root, but owned by root:shared.

here's the line from my fstab:
```
/dev/hda4       /shared          vfat    user,quiet,rw,noatime,gid=1001,umask=002 	0 0

```

---

