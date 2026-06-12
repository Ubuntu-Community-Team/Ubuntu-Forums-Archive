---
title: "Can't mount SATA drives."
date: 2006-06-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Huggy on 2006-06-10
I can't seem to mount my SATA drives in Ubuntu. I have info on them, so I can't erase them, and they are reserfs file format, so I know ubuntu supports the format. Is there anyway I can mount them without erasing the entire discs, because I really don't want to call it quits for ubuntu. Just tell me what info you need to be able to help me, and how to get it, and I'll get it to you. Thanks for any help I can get. As of right not it's not recognizing anyhing else, except that they are there.

---

### Post by Princey on 2006-06-10
[QUOTE=Huggy]I can't seem to mount my SATA drives in Ubuntu. I have info on them, so I can't erase them, and they are reserfs file format, so I know ubuntu supports the format. Is there anyway I can mount them without erasing the entire discs, because I really don't want to call it quits for ubuntu. Just tell me what info you need to be able to help me, and how to get it, and I'll get it to you. Thanks for any help I can get. As of right not it's not recognizing anyhing else, except that they are there.[/QUOTE]

When you say you try to mount them, what exactly are you talking about? Also, did you install Ubuntu on them using LVM? A little bit more detail including the steps you took to mount them might just speed up you getting help.

---

### Post by Huggy on 2006-06-11
O, I tried using the Gnome Partioner to mount them. I've kinda been able to stumble my way through it to kinda know what I'm doing. No, I did not use LVM, they were actually originally formatted bunder SUSE as Reserfs using Raid 0 I think, It may have been Raid 1. I'll have to check on that. This is my first time trying to mount them under Ubuntu. I know the way they work is they are both used at the same time. So instead of having 2 mirrored 250Gigs. I have 1 500 Gig of Raid storage space. It also stores things in 32 bit chuncks. I know that much. Is there anything else I can give you? I am honestly a newbie to Ubuntu, and I don't quite know where to get all the info yet. Thanks for your help.

---

### Post by kuja on 2006-06-11
Any idea what their device name is?

Also, take a look at the /etc/fstab file (cat /etc/fstab in a terminal) and see if it's in the list.... maybe you'll be able to mount it manually without issues.

---

### Post by Princey on 2006-06-11
[QUOTE=Huggy]O, I tried using the Gnome Partioner to mount them. I've kinda been able to stumble my way through it to kinda know what I'm doing. No, I did not use LVM, they were actually originally formatted bunder SUSE as Reserfs using Raid 0 I think, It may have been Raid 1. I'll have to check on that. This is my first time trying to mount them under Ubuntu. I know the way they work is they are both used at the same time. So instead of having 2 mirrored 250Gigs. I have 1 500 Gig of Raid storage space. It also stores things in 32 bit chuncks. I know that much. Is there anything else I can give you? I am honestly a newbie to Ubuntu, and I don't quite know where to get all the info yet. Thanks for your help.[/QUOTE]

I'd need to know how Ubuntu recognises the drives. To post here, do the following: ```
sudo gedit /etc/fstab
``` copy and post in here the contents of that file and we'll see if we can help you manually mount that drive. In addition, do you know to which drive Ubuntu has been installed?

---

### Post by Huggy on 2006-06-11
I don't think I see them in here.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


I know the gnome partion tool sees them as dev/sda and dev/sdb, but that's about all I know. I also know when you find them in the dev folder. They say xspecial/device-blocked and 0 bytes. What does that mean?
Also, Ubuntu was installed on my 80 Gig hard drive. Gnome partioner calls it the 74.5 Gig hda drive. I believe it's also the only drive showing in the fstab there. Is there any other info I can give you? THanks fo your help too, I'd be lost otherwise.

---

### Post by Princey on 2006-06-14
Sorry for the late response, huggy. Haven't been home on my linux machine. From the contents posted from your fstab file it appears that only one hard drive is mounted: that's hda. Of course, though that hasn't got anything to do with your situation, just a bit of clarification on your hard drive size. The manufacture measures your capacity differently from how your system sees it. They measure 1GB=1000MB but in reality, 1 GB= 1024MB, that alone accounts for an offset in the figures. Additionally, your system has to partition the drive and set it up to create the master boot record, file allocations, sectors, segments, et cetera. That takes space as well, that's why there's a discrepancy with the sizes. 

Now on to your case in point with the hard drive. Try this command and give me the output. ```
sudo fdisk -l
``` this should list all drives/partitions on your system. Maybe if it's recognised we can manually mount it.

---

### Post by Huggy on 2006-06-15
Here's the output...
....................................................................................................................................
huggy@huggy-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+  fd  Linux raid autodetect

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30400   244187968+  fd  Linux raid autodetect

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9355    75144006   83  Linux
/dev/hda2            9356        9729     3004155    5  Extended
/dev/hda5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/md0: 500.0 GB, 500096827392 bytes
2 heads, 4 sectors/track, 122093952 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table
.....................................................................................................................................

Ok so does it atleast see my 2, 250Gig Sata's? and where do I go from here?

---

### Post by Princey on 2006-06-16
OOps, I was halfway through giving the commands to mount your drives manually when re-reading your post I see this > Disk /dev/md0 doesn't contain a valid partition table

I'm not expert here. Just trying to help. But it appears that your raid array is messed up that's why it wasn't mounted properly. Without a valid partition table, the raid array can't be seen as the partition table is what that stores the directory structure and file locations of files on the drive. I'm subject to correction here on this one, but it appears that the contents of the drive may be lost. However, you can attempt to manually mount the drives individually. But I'd search around first. I can tell you how to do it, but I don't want to be responsible for any data loss should you attempt so at my advice without **FIRST** looking around to see what else you can sum up on that issue.

---

