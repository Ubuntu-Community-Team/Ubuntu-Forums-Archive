---
title: "Grub installs on wrong HDD"
date: 2008-07-31
forum: x86 64-bit Users
---

### Post by jpaulb on 2008-07-31
I installed Ubuntu server 8.04-1 on a AMD 64. At reboot time there was a warning from GRUB that files could not be found. I did manage a reboot by editing the loader file. For some reason I wanted grub to install in the MBR of (hd0,0) and grub installed it on (hd1,0)

Is this an undocumented feature?

---

### Post by Jouke74 on 2008-08-01
That depends on how you did it. I assume you know that Grub starts counting at 0 and not at 1? I only used the desktop version of Ubuntu both Alternate and normal Disks, and I also have a hard time installing Grub on a different harddisk than the one it wants to install on. In the end I changed the boot order of my HDs in BIOS.

---

### Post by jpaulb on 2008-08-01
I used the install scipt from Server cd in the default mode.     Next time in the expert mode, which asks where you want it installed. Both time GRUB installed on the wrong drive.

At least I learnt how to use the GRUB editor.

---

### Post by philinux on 2008-08-01
> **jpaulb said:**
> I used the install scipt from Server cd in the default mode.     Next time in the expert mode, which asks where you want it installed. Both time GRUB installed on the wrong drive.

At least I learnt how to use the GRUB editor.

Be interesting to see menu.lst

cat   /boot/grub/menu.lst

---

### Post by spyckotic on 2008-08-01
I run into this all the time with my SATA and IDE drives.. It can be a pain.. My solution..... Unplug the power from my IDE while I install onto the SATA.

---

### Post by jpaulb on 2008-08-01
I think I found the problem, however the solution is...

I have been running Debian for about 4 years and never ran into this.

One of my IBM ATA which has been pretty well running 24/7 since 2002 died, so I though I would try Ubuntu 64 bit since I had to reinstall the system anyways and setting up LTSP 5 on Debian 64 is quite difficult.

I thought I would use the SCSI as the swap file,  the remaining 2 ATAs as  RAID 1, replacing them with SATA as they retire. The SATA is for some video editing

The MOBO boot priority are first the 2 IDE Ch 0 M. S. then the SCSI then the SATA, Debian would boot from this setup.

GRUB in Ubuntu seems to set a different boot priority, SCSI, ATA then SATA. This is where this issue started I thought the MOBO Ch 0 Master was hd0 and GRUB labels the SCSI swap as hd0 then first ATA hd1.

---

### Post by jpaulb on 2008-08-04
> **philinux said:**
> Be interesting to see menu.lst

cat   /boot/grub/menu.lst

I'll start a little farther back.
setup
MoBo MSI K8N Neo4
SYN8751SP SCSI card
1 - 4.6 gb SCSI, I wanted to use as  swap
2 -  80gb ATA Ch 0 master slave to use as RAID 1 if it works
1 - 500gb SATA for video.

MoBo BIOS boot priority  is Ch 0. Master, Ch 0. Slave

At partitioning time the partition manager shows
sda 	4.6 gb
sdb	80 gb
sdc	80 gb
sdd	500 gb

/boot/grub/device.map
(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd

/boot/grub/menu.lst

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)


## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-server
root		(hd1,0)
kernel		/vmlinuz-2.6.24-19-server root=UUID=79abd58c-1ea6-4c34-9570-c5d9fee36012 ro quiet splash
initrd		/initrd.img-2.6.24-19-server
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-server (recovery mode)
root		(hd1,0)
kernel		/vmlinuz-2.6.24-19-server root=UUID=79abd58c-1ea6-4c34-9570-c5d9fee36012 ro single
initrd		/initrd.img-2.6.24-19-server

### END DEBIAN AUTOMAGIC KERNELS LIST


On boot there is a GRUB error 17 cannot mount partition press any key.

that bring up the GRUB menu press e to edit
grub edit > root	(hd1,0) edit to (hd0,0)
press b to boot

system boots

To have the system boot without the error 17 I had to make the following changes. Notice I left groot=(hd1,0) as is,
change that and the system is really f*cked.

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)


## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-server
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-server root=UUID=79abd58c-1ea6-4c34-9570-c5d9fee36012 ro quiet splash
initrd		/initrd.img-2.6.24-19-server
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-server (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-server root=UUID=79abd58c-1ea6-4c34-9570-c5d9fee36012 ro single
initrd		/initrd.img-2.6.24-19-server

### END DEBIAN AUTOMAGIC KERNELS LIST


It looks like the partition manager has one way of ordering disks and GRUB a different

I hope that this is of use

---

### Post by jpaulb on 2008-08-04
> **spyckotic said:**
> I run into this all the time with my SATA and IDE drives.. It can be a pain.. My solution..... Unplug the power from my IDE while I install onto the SATA.

Never had that problem with Debian.

---

### Post by logos34 on 2008-08-04
can you post your fdisk?

sudo fdisk -l

---

### Post by jpaulb on 2008-08-04
> **logos34 said:**
> can you post your fdisk?

sudo fdisk -l

Compare fdisk -l to fstab and the menu.lst all ready posted, to philinux, very strange.
I partitioned sdb & sdc the way fstab shows sdb. sdc was to be the RAID 1 disk with each partition the same size of the one on sdb. I used the script in the installer to set up a RAID 1 array.

sudo fsdisk -l

Disk /dev/sda: 4569 MB, 4569600000 bytes
255 heads, 63 sectors/track, 555 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4984e4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         555     4458006   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000401c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d568356

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          12       96358+  83  Linux
/dev/sdc2              13         620     4883760   83  Linux
/dev/sdc3             621        9729    73168042+   5  Extended
/dev/sdc5             621        1228     4883728+  83  Linux
/dev/sdc6            1229        1836     4883728+  83  Linux
/dev/sdc7            1837        2444     4883728+  83  Linux
/dev/sdc8            2445        3052     4883728+  83  Linux
/dev/sdc9            3053        3660     4883728+  83  Linux
/dev/sdc10           3661        9729    48749211   83  Linux

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dc420

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        9729    78148161   83  Linux


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=79abd58c-1ea6-4c34-9570-c5d9fee36012 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdd1
UUID=286272b6-19a0-4559-9179-a2655fbd1c6b /backup         ext3    relatime        0       2
# /dev/sdb1
UUID=ed646ca4-bb79-4df3-b4d9-19752695e065 /boot           ext3    relatime        0       2
# /dev/sdb10
UUID=7a4f49ee-3c3f-42d8-86c3-b2cc878d007d /home           ext3    relatime        0       2
# /dev/sdb8
UUID=3f8fd2ec-e042-48b9-a561-459157aa5fa0 /opt            ext3    relatime        0       2
# /dev/sdc1
UUID=654ba8f7-b0f0-4647-bc32-d6dc805d2535 /spare          ext3    relatime        0       2
# /dev/sdb5
UUID=9e947e87-3009-4f60-9478-2735c91f048f /tmp            ext3    relatime        0       2
# /dev/sdb6
UUID=847f9b0b-be03-4ee8-8926-6ba7f19751ec /usr            ext3    relatime        0       2
# /dev/sdb9
UUID=d6e7d2af-2139-43ba-8b95-16f29c9a0d41 /usr/local      ext3    relatime        0       2
# /dev/sdb7
UUID=3d553ab3-d290-4409-9fcb-263d8a9c31b4 /var            ext3    relatime        0       2
# /dev/sda1
UUID=2150065f-e1cc-4879-8ac3-f7f6f90aa181 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by logos34 on 2008-08-04
What's really confusing matters is that the drives are being recognized (/dev/sd?) differently now than during installation, maybe because the order in which the storage controller modules are loaded has changed...good thing hardy is looking only at the UUIDs for each drive partition, otherwise you wouldn't be able to boot at all or mount partitions.  

It appears that this is the old problem of SCSI/SATA and IDE disks throwing grub for a loop.  During installation the default location for Grub is (hd0)--i.e. whatever is set as the Bios boot disk at the time.  (Note: that's just the tiny stage1/1.5 file--your actual grub menu.lst is on /, which it looks for at boot).  In your case, according to device.map that was the SCSI disk.  However, to the best of my knowledge Grub is hardcoded to scan the IDE/PATA channels first and rank them before the rest, regardless of actual Bios boot order...but apparently the presence of a scsi drive changes that.  At any rate it would seem that grub stage1 only is indeed on the MBR of the scsi, and was configured to look for menu.lst on (hd1,0), but that has changed and now ide drive with ubuntu is seen as (hd0).   

All I can say is continue to use 'root (hd0,0)'  if it works.

Forgive me if I've misunderstood something, but it's quite a confusing setup.

add: oh, and I'm not sure what you mean by

> Notice I left groot=(hd1,0) as is,
change that and the system is really f*cked.

but if you want to be able to update grub it must match the 'root' location (so it can find your /boot folder)

---

### Post by Cresho on 2008-08-04
> **jpaulb said:**
> I installed Ubuntu server 8.04-1 on a AMD 64. At reboot time there was a warning from GRUB that files could not be found. I did manage a reboot by editing the loader file. For some reason I wanted grub to install in the MBR of (hd0,0) and grub installed it on (hd1,0)

Is this an undocumented feature?

you are probably using master in the jumpers on your drives.  YOUR hardrives and cd's all need to be set to cable select.  your cables should define your master and not the jumpers.  your cables should be pluged into the order as well as ide0 ide1 or sata0 or sata1.  if not, you will confuse the hell out of your hardware.

THE ONLY REASON YOU USE JUMPERS ON A HARDRIVE IS IF YOU ARE HAVING TROUBLE CONFIGURING YOUR SYSTEM AND IS EXOTIC OR CRAZY!  LEAVE THEM AT CABLE SELECT.

---

### Post by jpaulb on 2008-08-04
> **Cresho said:**
> you are probably using master in the jumpers on your drives.  YOUR hardrives and cd's all need to be set to cable select.  your cables should define your master and not the jumpers.  your cables should be pluged into the order as well as ide0 ide1 or sata0 or sata1.  if not, you will confuse the hell out of your hardware.

THE ONLY REASON YOU USE JUMPERS ON A HARDRIVE IS IF YOU ARE HAVING TROUBLE CONFIGURING YOUR SYSTEM AND IS EXOTIC OR CRAZY!  LEAVE THEM AT CABLE SELECT.

I ran into that problem already, every thing is at cable select.

---

### Post by Cresho on 2008-08-05
what you have left is your bios.  you will need to figure out if the bios you have preffers running your scsi first or your sata or ide.

---

### Post by logos34 on 2008-08-05
> **Cresho said:**
> you are probably using master in the jumpers on your drives.  YOUR hardrives and cd's all need to be set to cable select.  your cables should define your master and not the jumpers.  your cables should be pluged into the order as well as ide0 ide1 or sata0 or sata1.  if not, you will confuse the hell out of your hardware.

THE ONLY REASON YOU USE JUMPERS ON A HARDRIVE IS IF YOU ARE HAVING TROUBLE CONFIGURING YOUR SYSTEM AND IS EXOTIC OR CRAZY!  LEAVE THEM AT CABLE SELECT.

just for the record, that's not entirely true--it's either/or.  I always configure my hard disks and cdrom drive master/slave.  Never had a problem.

In fact, most new IDE drives I've seen come jumpered 'master', not CS.

---

### Post by XxOsurfer3xX on 2008-08-05
I had the same problem, and there is two ways of solving it there is an advanced option when you are making the new partitions, you can use that and specify which HD you want to install the grub on.

The easiest way on my opinion is unplugging all the hd's, and then installing ubuntu, after that plug them back in, and everything will be ok...

This worked for me, hope it helps you...

---

### Post by Cresho on 2008-08-05
> **logos34 said:**
> just for the record, that's not entirely true--it's either/or.  I always configure my hard disks and cdrom drive master/slave.  Never had a problem.

In fact, most new IDE drives I've seen come jumpered 'master', not CS.

you said, "I never had a problem" so you don't know.  I been telling people this and once they change the to cable select, it fixes the problem. :guitar:

You are right when you say it is either.  Some motherboards come out with funky bios.

---

### Post by jpaulb on 2008-08-06
> **Cresho said:**
> what you have left is your bios.  you will need to figure out if the bios you have preffers running your scsi first or your sata or ide.

That is getting close. I took the box to someone I know who maintains servers. He suggested the SCSI disk should to be set to any number except 0 or 7, since 0 is considered bootable and we all know what 7 is.

There were a number of other issues which had to be resolved, a couple caps in the PS were starting to bulge, replaced the PS since it was cheaper than labour to replace the caps; a fan on the North bridge was making a noise keeping the neighbours awake at night, oiled the bearings let it run for 12 hours, sweet silence. Spaced the Hdd so there was good air movement between them. 

When I reconnected the ATA hdds Channel 0 master & slave were not found; but they could be found if connected to channel 1. It would be either the cable or MoBo, when I tried to move channel 1 cable to channel 0 the slave connector fell apart; but one drive was found. Had to replace the two ATA cables.

Maybe tomorrow I will reinstall. Tonight I am going fill some beer bottles and empty others :biggrin:

---

### Post by jpaulb on 2008-08-09
Remove the SCSI card so Linux Vista doesn't get to confused.:confused:


There is a bug (inconsistency) in the system, the installer labels the hdd in one sequence, gparted another way, at least fstab agrees with the installer

---

