---
title: "Hardy Heron boot up problem"
date: 2008-06-06
forum: x86 64-bit Users
---

### Post by Torqumada286 on 2008-06-06
I ran Gutsy with little to no problems (ATI card problems) on my 64bit AMD 5200.  When the upgrade came available, I upgraded.  Now the 2.622-14 kernel works fine.  However, the 16,17 and 18 kernels will not boot.  They just hang.  Though I haven't checked for the exact error message for 17 and 18, here is the error message I get for 16.  Could someone interpret this for me and tell me a possible solution?

"Checkroot-bootarg cat/proc/cmdline or missing modules devices:cat/proc/modulesls/dev Altert! 1dev/disk/by-uuid/a75aodb4-cb2e-4327-a6cd-1082b2f905f3 does not exist

Dropping to shell"

Torqumada

---

### Post by Sef on 2008-06-06
> "Checkroot-bootarg cat/proc/cmdline or missing modules devices:cat/proc/modulesls/dev Altert! 1dev/disk/by-uuid/a75aodb4-cb2e-4327-a6cd-1082b2f905f3 does not exist

It looks like a module did not install to the update.  I would have to find out what one, then you could install it.

---

### Post by Yellow Pasque on 2008-06-06
> **1**dev/disk/by-uuid/a75aodb4-cb2e-4327-a6cd-1082b2f905f3
should be
> **/**dev/disk/by-uuid/a75aodb4-cb2e-4327-a6cd-1082b2f905f3

---

### Post by Torqumada286 on 2008-06-08
> **Sef said:**
> It looks like a module did not install to the update.  I would have to find out what one, then you could install it.

How can we go about doing that?

Torqumada

---

### Post by Sef on 2008-06-08
> How can we go about doing that?

Temujin is right: 1 should be a /.

---

### Post by Torqumada286 on 2008-06-11
> **Sef said:**
> Temujin is right: 1 should be a /.

OK, so I made an error in transcribing a large string of numbers, letters and symbols.  How does that fix my problem?

Torqumada

---

### Post by Yellow Pasque on 2008-06-11
Sorry, I assumed you were copying/pasting. Let's look at the UUID's. Please run these commands:
```
fdisk -l
blkid
```

---

### Post by Torqumada286 on 2008-06-11
> **Temüjin said:**
> Sorry, I assumed you were copying/pasting. Let's look at the UUID's. Please run these commands:
```
fdisk -l
blkid
```

These commands go into the terminal, correct?

Torqumada

---

### Post by Yellow Pasque on 2008-06-11
> **Torqumada286 said:**
> These commands go into the terminal, correct?

Torqumada
Yes.

---

### Post by Torqumada286 on 2008-06-11
> **Temüjin said:**
> Yes.

Nothing happens.  It just shows the next command prompt.  To be sure I had the format correct, I even copy and pasted them into the terminal and still nothing.  

Torqumada

---

### Post by meierfra. on 2008-06-11
You need to use:

```
sudo fdisk -l
```
(the l is a lowercase L)
and

```
 sudo blkid
```

---

### Post by Torqumada286 on 2008-06-11
> **meierfra. said:**
> You need to use:

```
sudo fdisk -l
```
(the l is a lowercase L)
and

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdca4dca4

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2add431d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37434   300688573+  83  Linux
/dev/sda2           37435       38913    11880067+   5  Extended
/dev/sda5           37435       38913    11880036   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    c  W95 FAT32 (LBA)

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xad1b685d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       10337    78147688+   7  HPFS/NTFS

> ```
 sudo blkid
```
/dev/sda1: UUID="a75a0db4-cb2e-4327-a6cd-1082b2f905f3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="c6387a63-6050-44ed-a898-b55cee1b1964" 
/dev/hda1: UUID="5498F88C98F86E3C" TYPE="ntfs" 
/dev/sdb1: LABEL="My Book" UUID="9CB6-5546" TYPE="vfat" 
/dev/sdc1: UUID="CED8A57FD8A56685" LABEL="EXTERNAL" TYPE="ntfs" 

There is the output of those two commands.  

Torqumada

---

### Post by Yellow Pasque on 2008-06-11
Hmm. The UUID is correct. Let's make sure the GRUB and fstab entries are correct. Please post output from the following commands:
```
cat /boot/grub/menu.lst | grep root=
cat /proc/cmdline 
cat /etc/fstab
```

---

### Post by Torqumada286 on 2008-06-11
> **Temüjin said:**
> Hmm. The UUID is correct. Let's make sure the GRUB and fstab entries are correct. Please post output from the following commands:
cat /boot/grub/menu.lst | grep root=

# kernel	/vmlinuz root=/dev/hda2 ro
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a75a0db4-cb2e-4327-a6cd-1082b2f905f3 ro
## e.g. groot=(hd0,0)
# groot=(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=a75a0db4-cb2e-4327-a6cd-1082b2f905f3 ro quiet splash
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=a75a0db4-cb2e-4327-a6cd-1082b2f905f3 ro single
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=a75a0db4-cb2e-4327-a6cd-1082b2f905f3 ro quiet splash
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=a75a0db4-cb2e-4327-a6cd-1082b2f905f3 ro single
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a75a0db4-cb2e-4327-a6cd-1082b2f905f3 ro quiet splash
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a75a0db4-cb2e-4327-a6cd-1082b2f905f3 ro single
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a75a0db4-cb2e-4327-a6cd-1082b2f905f3 ro quiet splash
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a75a0db4-cb2e-4327-a6cd-1082b2f905f3 ro single

> cat /proc/cmdline 

root=UUID=a75a0db4-cb2e-4327-a6cd-1082b2f905f3 ro quiet splash



> cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a75a0db4-cb2e-4327-a6cd-1082b2f905f3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=c6387a63-6050-44ed-a898-b55cee1b1964 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

There is the output from those commands.

Torqumada

---

### Post by Torqumada286 on 2008-06-14
Bump for some more help.

Torqumada

---

### Post by meierfra. on 2008-06-14
To you have an IDE drive? Try this

[URL="http://ubuntuforums.org/showthread.php?t=828568#26"]
http://ubuntuforums.org/showthread.php?t=828568#26[/URL]

---

### Post by Torqumada286 on 2008-06-14
> **meierfra. said:**
> To you have an IDE drive? Try this

[URL="http://ubuntuforums.org/showthread.php?t=828568#26"]
http://ubuntuforums.org/showthread.php?t=828568#26[/URL]

My Ubuntu drive is an SATA drive.  

Torquamda

---

### Post by meierfra. on 2008-06-14
You still might try it.

---

### Post by Torqumada286 on 2008-06-17
OK the 19 kernel is not working either.

Torqumada

---

### Post by Torqumada286 on 2008-06-17
> **meierfra. said:**
> You still might try it.

Should is say something about generic SATA then?  Sorry, but I am confused here.  GRUB finds my Windows partition on the IDE drive already.  No problems there.  Ubuntu is in a SATA drive.  How will telling GRUB to look for IDE drives fix the problem?

Torqumada

---

### Post by ravindran.k on 2008-06-17
hi..

Are you sure there is no initrd..? Can you try to boot with this grub entry :

kernel		/boot/vmlinuz-2.6.24-18-generic root=/dev/sda1 ro 
initrd          /boot/initrd.img-2.6.24-18-generic
boot

---

### Post by meierfra. on 2008-06-17
> How will telling GRUB to look for IDE drives fix the problem?

I don't have much hope that it will  would work (in fact I am   pretty sure it won't). But I don't see any harm in trying. Sorry, I  don't have any better ideas .

---

### Post by Torqumada286 on 2008-06-18
> **ravindran.k said:**
> hi..

Are you sure there is no initrd..? Can you try to boot with this grub entry :

kernel		/boot/vmlinuz-2.6.24-18-generic root=/dev/sda1 ro 
initrd          /boot/initrd.img-2.6.24-18-generic
boot

This didn't work.

Torqumada

---

### Post by Torqumada286 on 2008-06-21
Well, I guess I have stumped the Ubuntu experts.  Is there a prize for that?

Torqumada

---

### Post by ravindran.k on 2008-06-21
hehe.. yah.. you 've won yourself a nomination for testing the next version of Ubuntu Interpid Ibex .. just kidding ;)

btw you get the same message.. ? 
Are you able to use the Ubuntu CD to boot and mount the partition ? ..just to do a fsck and check whether everything is ok..(let us know if u need help with this)

---

### Post by Torqumada286 on 2008-06-21
> **ravindran.k said:**
> hehe.. yah.. you 've won yourself a nomination for testing the next version of Ubuntu Interpid Ibex .. just kidding ;)

Yay me!!

\\:D/

b> tw you get the same message.. ? 
Are you able to use the Ubuntu CD to boot and mount the partition ? ..just to do a fsck and check whether everything is ok..(let us know if u need help with this)

Yep.  Same message for 16-19.  I did the upgrade from GG to HH through the updater.  I am getting a disc set up and try to fix it that way.  There is some sort of option for repair isn't there?

Torqumada

---

### Post by Torqumada286 on 2008-06-21
> **ravindran.k said:**
> hehe.. yah.. you 've won yourself a nomination for testing the next version of Ubuntu Interpid Ibex .. just kidding ;)

btw you get the same message.. ? 
Are you able to use the Ubuntu CD to boot and mount the partition ? ..just to do a fsck and check whether everything is ok..(let us know if u need help with this)

With the boot disk I was able to access the drive.  It went to the GRUB men and kernels1 16-19 wouldn't load.  Kernel 14 boots fine.  What next?

Torqumada

---

