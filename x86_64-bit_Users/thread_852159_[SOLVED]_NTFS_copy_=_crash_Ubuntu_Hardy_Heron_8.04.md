---
title: "[SOLVED] NTFS copy = crash Ubuntu Hardy Heron 8.04"
date: 2008-07-07
forum: x86 64-bit Users
---

### Post by veiloctane on 2008-07-07
hi there i am having a problem with my Ubuntu Hardy Heron 8.04 
every time i access a ntfs partition and copy a large file 8gb it crashes my whole system and the only way to get out is to force fully reboot.
i need help and i have been at it for a whole week. i have done a memtest everything checks ok. at first i thought it was my videocard but ihave swaped out a video card and everything checks fine. i have a dual boot installed and i can copy fine with windows.

here i will post some log files hopefully some one can help me.


Release Version:
Code:

lsb_release -rd
[HTML]Description:	Ubuntu 8.04.1
Release:	8.04[/HTML]


CPU Model:
Code:

cat /proc/cpuinfo | grep "model name"
[HTML]model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 6400+
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 6400+[/HTML]


Kernel Version:
Code:

uname -r
[HTML]2.6.24-19-generic[/HTML]


sources file 
Code:

cat /etc/apt/sources.list
[HTML]cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
[/HTML]

And the version numbers of FireFox and Amarok
Code:

apt-cache policy amarok firefox
[HTML]amarok:
  Installed: (none)
  Candidate: 2:1.4.9.1-0ubuntu3
  Version table:
     2:1.4.9.1-0ubuntu3 0
        500 http://ca.archive.ubuntu.com hardy/main Packages
firefox:
  Installed: 3.0+nobinonly-0ubuntu0.8.04.1
  Candidate: 3.0+nobinonly-0ubuntu0.8.04.1
  Version table:
 *** 3.0+nobinonly-0ubuntu0.8.04.1 0
        500 http://ca.archive.ubuntu.com hardy-updates/main Packages
        100 /var/lib/dpkg/status
     3.0~b5+nobinonly-0ubuntu3 0
        500 http://ca.archive.ubuntu.com hardy/main Packages
[/HTML]

partitions setup.
Code:

df -Th
[HTML]Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sdb3     ext3    167G   12G  147G   8% /
varrun       tmpfs    4.0G  132K  4.0G   1% /var/run
varlock      tmpfs    4.0G     0  4.0G   0% /var/lock
procbususb   usbfs    4.0G  108K  4.0G   1% /proc/bus/usb
udev         tmpfs    4.0G  108K  4.0G   1% /dev
devshm       tmpfs    4.0G   12K  4.0G   1% /dev/shm
lrm          tmpfs    4.0G   43M  3.9G   2% /lib/modules/2.6.24-19-generic/volatile
/dev/sdb1  fuseblk    296G  267G   30G  91% /media/sda1
/dev/sda1  fuseblk    466G   80M  466G   1% /media/Spare
/dev/hda   iso9660    587M  587M     0 100% /media/cdrom0
/dev/sdc5  fuseblk    187G  165G   22G  89% /media/xbox games



[/HTML]

here is my mobo specs maybe this will help 

[HTML]Gigabyte GA-MA69GM-S2H
CPU:
- Support for Socket AM2 processors:
AMD AthlonTM 64 FX processor/AMD AthlonTM 64 X2 Dual-Core processor/AMD AthlonTM 64 processor/AMD SempronTM processor
(Go to GIGABYTE's website for the latest CPU support list.)
- Front Side Bus: 2000 MHz FSB

Chipset
North Bridge: AMD 690G
South Bridge: AMD SB600

Memory:
- 4 x 1.8V DDR2 DIMM sockets supporting up to 16 GB of system memory
- Dual channel memory architecture
- Support for DDR2 800/667/533 MHz memory modules

Onboard Graphics:
- Integrated AMD 690G / ATI™ Radeon™ X1250-based graphics

Audio:
- Realtek ALC889A codec
- High Definition Audio
- 2/4/5.1/7.1-channel
- Support for DTS (dts NEO:PC)
- Support for S/PDIF In/Out
- Support for CD In

LAN
- RTL 8110SC chip (10/100/1000 Mbit)

Storage Interface
South Bridge:
- 1 x floppy disk drive connector supporting up to 1 floppy disk drive
- 1 x IDE connector supporting ATA-133/100/66/33 and up to 2 IDE devices
- 4 x SATA 3Gb/s connectors supporting up to 4 SATA 3Gb/s devices
- Support for SATA RAID 0, RAID 1, and RAID 10

IEEE 1394a
- T.I. TSB43AB23 chip
- Up to 3 IEEE 1394a ports (1 on the back panel, 2 via the IEEE 1394 bracket connected to the internal IEEE 1394 headers)

USB: Integrated in the South Bridge
- Up to 10 USB 2.0/1.1 ports (4 on the back panel, 6 via the USB brackets connected to the internal USB headers)

Onboard Peripherals
- 1 x PS/2 keyboard port
- 1 x PS/2 mouse port
- 1 x D-Sub port
- 1 x DVI-D port (Note 2)
- 1 x HDMI port
- 1 x optical S/PDIF Out connector
- 3 x IEEE 1394a port (1 rear)
- 10 x USB 2.0/1.1 ports (4 rear)
- 1 x RJ-45 port
- 6 x audio jacks (Center/Subwoofer Speaker Out/Rear Speaker Out/Side Speaker Out/Line In/Line Out/Microphone)

Expansion Slots:
- 1 x PCI Express x16 slot
- 1 x PCI Express x4 slot
- 2 x PCI slots

Form Factor:
- Micro ATX form factor
- 24.4cm x 24.4cm
[/HTML]

---

### Post by cprofitt on 2008-07-21
I am not sure what would be going wrong... and I am not strong enough yet with log-fu to tell you what logs to look at.

I tried moving a 32gb file and it moved with no issues...

I wonder if it would be worth trying to move a different 8gb+ file... to eliminate the possibility of some sort of file corruption.

---

### Post by veiloctane on 2008-07-26
fixed problem had to turn off "acpi"


found fix in this forum

[http://ubuntuforums.org/showthread.php?t=787573&page=2](http://ubuntuforums.org/showthread.php?t=787573&page=2)

---

