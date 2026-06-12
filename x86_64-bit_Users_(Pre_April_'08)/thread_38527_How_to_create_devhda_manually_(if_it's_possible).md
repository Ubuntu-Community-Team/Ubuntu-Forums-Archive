---
title: "How to create /dev/hda manually (if it's possible)"
date: 2005-05-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by jyp on 2005-05-31
I try to run Ubuntu on my AMD64 machine and there is quite a few problems (but Ubuntu runs fine on my AMD K6 32 bits).

The Pioneer DVR is never detected because the file /dev/hda is not created at boot time; so it is impossible to mount /dev/hda on /media/cdrom0. On the orther hand, the system creates the file /dev/hdb so that this device is properly mounted on /media/cdrom1 (as per /etc/fstab).

When I boot using Knoppix, there is no such problem; the /dev/hda and the /dev/hdb are both created and mounted according to the /etc/fstab.

Also it is not a BIOS problem; both ide are detected. 

Being a newbie, I don't know if it is possible to have the system detect the DVR afterwards (create the /dev/hda file).

Any idea?

Thank you.

---

### Post by thrift on 2005-05-31
You should really look into what is going on when you run dmesg.
There has to be some reason that this is not picking up.  Why is this on /dev/hda?  are you using SCSI for your primary disk?

you can use mknod to create a device after boot up, although I'm not sure you're going to be very happy with the results.  Sounds like something odd is occuring with your IDE controller or the ATAPI compliance of the drive...or maybe ubuntu is doing something screwy.  If you want help trying to figure out what exactly is causing this open a terminal

dmesg>dmesg.txt

and attach dmesg.txt, then me or someone else can take a look at what's going on.

---

### Post by jyp on 2005-05-31
Thank you for your reply.

I was using Debian before (Sarge testing 32bits) and I was not able to detect the DVR neither; but I put the blame on an older kernel and on my inability to put together the proper configuration. I thought that a more integrated distribution like Ubuntu would let me enjoy the power of my machine!

Effectively, the disks are using sata and are labeled as SCSII.

Here is the /etc/fstab.
In the future I plan to use the 2 200GB disks in a RAID1 setup (It was like that on the Debian)

>>>
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdc1       /Archive        reiserfs defaults        0       2
/dev/sdb5       /Data           reiserfs defaults        0       2
/dev/sda6       /home           reiserfs defaults        0       2
/dev/sdb1       /home_bu        reiserfs defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdb        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
>>>

Here is also some of the dmesg output (the whole thing is attached).

>>>
...
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Probing IDE interface ide0...
ide0: Wait for ready failed before probe !
hdb: HL-DT-STDVD-ROM GDR8162B, ATAPI CD/DVD-ROM drive
Probing IDE interface ide1...
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hdb: ATAPI 48X DVD-ROM drive, 256kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
...
>>>

Ubuntu seems to be a great community and I am happy to be part of it.

---

### Post by thrift on 2005-06-01
Ah.  It looks like your IDE card could be part of the problem.

If it so happens that your IDE controller functions as a RAID controller this could have a bit to do with your problems.  Many RAID controllers don't play particularly nice with ATAPI(CDROM) devices.

It looks like possibly two ide drivers are registered for use with your card.  A generic and an nforce driver.  You can tell the generic driver not to pickup by doing something like

hda=noprobe hdb=noprobe hdc=noprobe hdd=noprobe so on and so forth until you've specified all hdx's that your ide controller is responsbile for at the kernel command line


so for instance if you were to try to edit /boot/grub/menu.lst and 
find the kernel line for you current kernel such as:

kernel          /boot/vmlinuz-2.6.10-5-k7 root=/dev/sda1 ro quiet splash

you could append to it like so

kernel          /boot/vmlinuz-2.6.10-5-k7 root=/dev/sda1 ro quiet splash hda=noprobe hdb=noprobe hdc=noprobe hdd=noprobe

to disable the generic IDE driver from picking up the first two ide channels, and then hopefully only the nforce driver will atempt to use them.

This may help.  If you still continue to have problems, you may find that disabling any RAID functionatily if possible may help.  or simply purchasing a cheap IDE card and completely disabling the nforce may work best.

Good Luck.

---

### Post by jyp on 2005-06-01
I went through the BIOS to make sure that there was no RAID enabled.

Following your advice, I edited the /boot/grub/menu.lst.

I even reinstalled everything using Ubuntu i386.

Still the same problem.

Thank you anyway. I keep trying.

---

