---
title: "DVD RW not recognised, not written in fstab"
date: 2009-10-09
forum: x86 64-bit Users
---

### Post by Gael33 on 2009-10-09
I recently did a clean upgrade from 8.10 (64) to 9.04 (64) and now my DVD-RW is not working nor is it mentioned in the fstab file. As a relative newbie I have no idea how to fix the problem ... please help!
My DVD/CD player is working and mentioned in the fstab file.
If I need to edit the fstab file I would appreciate an example (snap-shot) of what it should look like and I will type it in verbatim.
I have a HP dx2250 desktop Computer
AMD 64 Athlon CPU
2 Gb Memory
160 GB HDD
The DVD-RW that is not showing up in the fstab file is a HP dvd1040
Thanks in advance.
gael.

---

### Post by dcstar on 2009-10-10
> **Gael33 said:**
> I recently did a clean upgrade from 8.10 (64) to 9.04 (64) and now my DVD-RW is not working nor is it mentioned in the fstab file. As a relative newbie I have no idea how to fix the problem ... please help!
My DVD/CD player is working and mentioned in the fstab file.
If I need to edit the fstab file I would appreciate an example (snap-shot) of what it should look like and I will type it in verbatim.
I have a HP dx2250 desktop Computer
AMD 64 Athlon CPU
2 Gb Memory
160 GB HDD
The DVD-RW that is not showing up in the fstab file is a HP dvd1040
Thanks in advance.
gael.

/dev/scd0 is for my system, you will have to find yours.
```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

---

### Post by Gael33 on 2009-10-10
> **dcstar said:**
> /dev/scd0 is for my system, you will have to find yours.
```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

Hi, I've got exactly the same line in my fstab ... which I assume is for my DVD/CD "player" which is working well.
However, there is no mention of my DVD/CD-RW in the fstab file or any mention of a DVD/CD-RW in the dev folder :confused:
What are the consequences of physically going into the box and swapping the cables of the DVD/CD Player and the DVD/CD-RW ... would Unbuntu 9.04 (64) find them automatically at boot-up?

Thanks,
gael.

---

### Post by Rizlaw on 2009-10-11
As I understand your question: You have two devices: a burner (DVD-RW) and player (DVD/CDrom). One is showing up in fstab and one is not.

My suggestion, assuming you have 2 SATA devices connected to your motherboard:

At the end of your "fstab" file you should have something like this:

> # DVD-RW
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0	0
#
# DVD/CD
/dev/scd1	/media/cdrom1	udf,iso9660 user,noauto,exec,utf8 0	0

In your /media folder you should have two folders to mount the two devices now listed in your "fstab" file:

"cdrom0" and "cdrom1"

If "cdrom1" is not there, you have to open a terminal window and create it, for example:

> sudo mkdir /media/cdrom1

Reboot and you should see both devices. Good luck.

---

### Post by Gael33 on 2009-10-12
> **Rizlaw said:**
> As I understand your question: You have two devices: a burner (DVD-RW) and player (DVD/CDrom). One is showing up in fstab and one is not.

My suggestion, assuming you have 2 SATA devices connected to your motherboard:

At the end of your "fstab" file you should have something like this:



In your /media folder you should have two folders to mount the two devices now listed in your "fstab" file:

"cdrom0" and "cdrom1"

If "cdrom1" is not there, you have to open a terminal window and create it, for example:



Reboot and you should see both devices. Good luck.

As a newbie I will try to explain exactly what I have ... I have a DVD/CD Player which is a SATA and is written in the fstab file exactly as in your snap shot. The DVD-RW is an IDE interface and is not showing in the fstab file, nor is there any reference to it in any of the other folders, ie, DEV, MEDIA, ETC.
Oddly, both showed up and worked perfectly well in Ubuntu 8.10 (64).
I take it that there is a difference between a SATA and a IDE device written and recognized in the fstab or where-ever these things get written ... it's just knowing which bit is written where to get the IDE interface recognized, am I correct? Hopefully, you can help with this and then I can stop having to reboot into WindowsXP to record anything :confused:

Thanks in advance,
gael.

PS. How does one make a Snap-Shot of the fstab?

---

### Post by rb0171610 on 2009-10-12
> **Gael33 said:**
> As a newbie I will try to explain exactly what I have ... I have a DVD/CD Player which is a SATA and is written in the fstab file exactly as in your snap shot. The DVD-RW is an IDE interface and is not showing in the fstab file, nor is there any reference to it in any of the other folders, ie, DEV, MEDIA, ETC.
Oddly, both showed up and worked perfectly well in Ubuntu 8.10 (64).
I take it that there is a difference between a SATA and a IDE device written and recognized in the fstab or where-ever these things get written ... it's just knowing which bit is written where to get the IDE interface recognized, am I correct? Hopefully, you can help with this and then I can stop having to reboot into WindowsXP to record anything :confused:

Thanks in advance,
gael.

PS. How does one make a Snap-Shot of the fstab?

For future reference, keep backup copies of your important system configuration files i.e. /etc/X11/xorg.conf, /etc/exports, /etc/fstab etc.  That way, you can refer to them if not restore them when you are experimenting with software and have a bad experience such as this one.

That being said, try booting with a liveCD of a previous version.  Read your /etc/fstab file and see what it says.  It may show up there.  You can then reboot and copy this information into your current fstab. This might help fix your problem.

---

### Post by Gael33 on 2009-10-12
> **rb0171610 said:**
> For future reference, keep backup copies of your important system configuration files i.e. /etc/X11/xorg.conf, /etc/exports, /etc/fstab etc.  That way, you can refer to them if not restore them when you are experimenting with software and have a bad experience such as this one.

That being said, try booting with a liveCD of a previous version.  Read your /etc/fstab file and see what it says.  It may show up there.  You can then reboot and copy this information into your current fstab. This might help fix your problem.

Here is a copy of my etc/fstab that fixed the problem ...
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=7b97ab2c-9d9a-48ca-8179-a9e9ded21578 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a6d61985-7f20-4aa0-8ba9-2f2b3076260a none            swap    sw              0       0
/dev/scd0       /media/cdrom   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdc /mnt/cdrom iso9660 defaults 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

thanks for all your help.

gael.

---

### Post by Gael33 on 2009-10-12
> **Gael33 said:**
> Here is a copy of my etc/fstab that fixed the problem ...
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=7b97ab2c-9d9a-48ca-8179-a9e9ded21578 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a6d61985-7f20-4aa0-8ba9-2f2b3076260a none            swap    sw              0       0
/dev/scd0       /media/cdrom   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdc /mnt/cdrom iso9660 defaults 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

thanks for all your help.

gael.

I'm afraid I spoke to soon. One minute I had both drives working and then only one drive again.
My SATA CD/DVD player works just fine.
My IDE DVD-RW doesn't mount.
I'm at a loss, help needed please.
Hopefully ...
gael.

---

### Post by Rizlaw on 2009-10-12
> **Gael33 said:**
> Here is a copy of my etc/fstab that fixed the problem ...
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=7b97ab2c-9d9a-48ca-8179-a9e9ded21578 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a6d61985-7f20-4aa0-8ba9-2f2b3076260a none            swap    sw              0       0
/dev/scd0       /media/cdrom   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdc /mnt/cdrom iso9660 defaults 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

thanks for all your help.

gael.

Gael,

The latest versions of Ubuntu, by default, place all the disk type device mount points in the /media folder, not the /mnt folder, although I don't think it makes alot of difference if the fstab file is written correctly.

Your fstab file has a SATA DVD/CD device (/dev/scd0) in the /media folder and the other IDE device (/dev/hdc) in the /mnt folder as a "cdrom" where it appears to be incorrectly listed as a hard disk device (hdc):

```
/dev/scd0       /media/cdrom   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdc /mnt/cdrom iso9660 defaults 0 0
```

Please look here on correct device naming: [http://www.debian.org/releases/stable/i386/apcs04.html.en](http://www.debian.org/releases/stable/i386/apcs04.html.en)

In any event, it seems to me that your problem is with the /dev/hdc line in your fstab file. It should start with a device name of "/dev/scd1 and a mount point of "/media/cdrom1" as I previously mentioned, since you are dealing with a cd device and NOT a hard disk.

So again, if you follow my previous posted suggestion, it should work.

---

