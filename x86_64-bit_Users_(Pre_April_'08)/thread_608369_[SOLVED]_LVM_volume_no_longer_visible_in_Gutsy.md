---
title: "[SOLVED] LVM volume no longer visible in Gutsy"
date: 2007-11-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by ahrtu on 2007-11-09
Hello all,

I recently decided to rebuild my MythTV box after the TV card stopped working. 

Specs:

AMD Athlon 64 2800+
512 MB RAM
200 GB HDD
Lite-On 16X DVD+-R/RW
Hauppauge WinTV PVR-250

When I set up the machine the last time (Feisty), I created a LVM volume out of the majority of the drive (around 180GB) to allow for future storage expansion.

The other night I installed Gutsy from the x86-64 Alternate CD. There was very little data on the drive except for the LVM volume, so I did a clean install, but did not format that volume (XFS from previous install).

To make a long story short, I cannot get to the LVM volume. It does not appear in /etc/fstab, but it does show up with a sudo fdisk -l . The two reformatted partitions appear in /etc/fstab with their UUIDs, and the DVD appears as /dev/hdc .

How do I get my music back?

Here are the results of diagnostics:

```

**$ cat /etc/fstab**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=48a9a5e7-d568-406e-aebe-5efa15f3c896 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=41a9c805-5929-4070-9da6-f6c430a3a2a3 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

**$ sudo fdisk -l**

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000491c8

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406   83  Linux
/dev/hda2            1276        1406     1052257+  82  Linux swap / Solaris
/dev/hda3            1407       24321   184064737+  8e  Linux LVM

**$ ls -l /dev/disk/by-uuid**
total 0
lrwxrwxrwx 1 root root 10 2007-11-08 21:56 41a9c805-5929-4070-9da6-f6c430a3a2a3 -> ../../hda2
lrwxrwxrwx 1 root root 10 2007-11-08 21:56 48a9a5e7-d568-406e-aebe-5efa15f3c896 -> ../../hda1

```

Thank you for your help. So far, Gutsy rocks! From past experience with these forums, so does the community.

-Ahrtu

---

### Post by mlind on 2007-11-10
You probably have lvm2 package installed already. Could you post the output of
```

sudo vgs
sudo lvs

```

You can mount the the partition inside LV using
```

sudo mount /dev/mapper/foo-bar /mnt

```
--> where foo is the VG and bar is the LV.



You can use device-mapper names or the UUID's to mount the partition in /etc/fstab. I'm using device-mapper names myself. You can get the vol id of a LV using
```

sudo vol_id /dev/mapper/foo-bar

```

Here's one entry from my /etc/fstab where I'm mounting a device-mapper thingy as /mnt/tmp
```

/dev/mapper/Ubuntu-stuff /mnt/tmp ext3 defaults,noatime 0 2

```

---

### Post by ahrtu on 2007-11-10
Thanks for your reply. I had not re-installed LVM2 after I rebuilt the system. Here's what I got when I issued the requested commands:

```

**$ sudo vgs**
sudo: vgs: command not found

**$ sudo lvs**
sudo: lvs: command not found

```

I installed the lvm2 package and tried again:

```

**$ sudo apt-get install lvm2**
... package installs ...

**$ sudo vgs**
  VG   #PV #LV #SN Attr   VSize   VFree 
  Myth   1   1   0 wz--n- 175.53G 32.00M

**$ sudo lvs**
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  Incompatible libdevmapper 1.02.20 (2007-06-15)(compat) and kernel driver 
  LV    VG   Attr   LSize   Origin Snap%  Move Log Copy% 
  Media Myth -wi--- 175.50G 

```

So apparently I'm missing a driver. Do I need to compile it into the kernel, or can it be a module? I'll experiment and report back. Any advice in the meantime would me most helpful.

Thanks,
Ahrtu

---

### Post by mlind on 2007-11-10
Are you using a custom kernel?

I guess dm_mod must be loaded in your kernel (you may want to modprobe dm_snapshot and dm_mirror too)

Here's my output of 'lsmod | grep dm'
```

$ lsmod | grep dm
dm_crypt               14984  1 
dm_mirror              24448  0 
dm_snapshot            18980  0 
dm_mod                 58816  19 dm_crypt,dm_mirror,dm_snapshot

```

---

### Post by ahrtu on 2007-11-10
I have not customized my kernel - it is straight off of Gutsy x86-64 Alternate:

```

**uname -r**
2.6.22-14-generic

```

The following gave no results:
```

**$ lsmod | grep dm**

```
so I loaded the drivers (I included dm_crypt for consistency with your list)::
```

[B]$ sudo modprobe dm_snapshot
$ sudo modprobe dm_mirror
$ sudo modprobe dm_crypt[/B]

**$ sudo lsmod | grep dm**
dm_crypt               16528  0 
dm_mirror              25472  0 
dm_snapshot            19656  0 
dm_mod                 67440  3 dm_crypt,dm_mirror,dm_snapshot

```

Now I get the following results:
```

**$ sudo lvs**
 LV    VG   Attr   LSize   Origin Snap%  Move Log Copy% 
 Media Myth -wi--- 175.50G

```

However, I cannot mount the volume (/mnt/myth exists):
```

**$ sudo mount /dev/mapper/Myth-Media /mnt/myth**
mount: special device /dev/mapper/Myth-Media does not exist

```

I do not know if Myth-Media is supposed to appear under /dev/mapper via ls or not, but here are my results:
```

**$ sudo mount /dev/mapper/Myth-Media /mnt/myth**
mount: special device /dev/mapper/Myth-Media does not exist

```

I feel I am closer to a solution - thanks again for all the help.
-Ahrtu

---

### Post by mlind on 2007-11-11
This all should just happen automatically, so I guess there's something wrong with your install. Try to re-create your initrd image by doing
```

sudo update-initramfs -u -k *2.6.22-14-generic*

```
and make sure the parameter after -k matches your current kernel, which you can check by using 'uname -r'

btw. I think it's udev in Ubuntu which is supposed to create the device mapper devices
[https://wiki.ubuntu.com/UdevDeviceMapper](https://wiki.ubuntu.com/UdevDeviceMapper)

---

### Post by x0as on 2007-11-11
Post the results of 

```
sudo lvscan
```

from the results of lvs it looks like the logical volume isn't active.

---

### Post by mlind on 2007-11-11
I forgot to say, you need to reboot after re-creating the initrd image..

---

### Post by ahrtu on 2007-11-11
Success!

I executed:
```

sudo update-initramfs -u -k 2.6.22-14-generic

```
and rebooted the machine.

Once the machine came back up, I entered:
```

**$ sudo lvscan**
  ACTIVE            '/dev/Myth/Media' [175.50 GB] inherit

**$ ls /dev/mapper**
control  Myth-Media

```

I then mounted the volume and listed its contents:
```

[B]$ sudo mount /dev/mapper/Myth-Media /mnt/myth
$ ls /mnt/myth[/B]
1004_20070609210000.mpg      1034_20070626093000.mpg.png
1004_20070609210000.mpg.png  1034_20070626200000.mpg
...

```

I can see my files!
The only other question I have is this...
I obviously want to add this volume to my /etc/fstab so it will be available on startup. My other volumes are listed by UUID. Can I use:
```

/dev/mapper/Myth-Media /mnt/myth xfs defaults,noatime 0 2

```
or do I need to use the UUID? If the latter, how do I accomplish that?

Sincere thanks to all involved in helping me reach this point,
Ahrtu

---

### Post by mlind on 2007-11-11
You can either mount device-mapper devices by name or UUID. UUID is more flexible because you don't need to alter configuration files (like /etc/fstab) if you someday decide to change the LV or VG name to something else. Using device-mapper names is more 'human readable' though.

You can get the UUID of a partition by doing
```

sudo vol_id /dev/mapper/Myth-Media

```
and look the ID_FS_UUID value.

Then your /etc/fstab entry would be
```

**UUID=**foo-bar-baz /mnt/myth xfs defaults,noatime 0 2

```
where foo-bar-baz is the value of ID_FS_UUID

---

### Post by dis-abled on 2007-11-12
I have the same problem. The Gutsy Alternative CD (the alternative usually has a text installer that recognizes LVM volumns) bailed out with a libc error, I downloaded again and got the same error again. Then I downloaded 6.06.1 using the default download page and had the same problem again, only to realize that the default download page was not pointing me to the Alternate install. Really frustrating, but when I went for the 6.06.2-alternate cd manually I am now getting the correct ISO at least. Will report back with results.

---

### Post by ahrtu on 2007-11-19
Thank you! This works perfectly. I added the UUID for the volume to /etc/fstab, using the other entries as models, and I can see the media drive on boot.

Marking this one closed,
Ahrtu

---

### Post by sameerds on 2008-02-04
> **ahrtu said:**
> 
However, I cannot mount the volume (/mnt/myth exists):
```

**$ sudo mount /dev/mapper/Myth-Media /mnt/myth**
mount: special device /dev/mapper/Myth-Media does not exist

```


I know that this problem was solved by recreating the initramfs. But there is a way to solve this without having to reboot the machine. The problem here is that the recently detected volume group called "Myth" is not *active* yet. To do that, you have to run the following command:

```

vgchange -a y Myth

```

That *activates* the volume group, and all the logical volumes in it become visible under /dev/Myth/ ...

Sameer.

---

