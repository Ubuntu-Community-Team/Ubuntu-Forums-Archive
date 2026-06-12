---
title: "success: of Edgy on RIOWORKS HDAMEX-SLi with dual Opteron and nVidia GeForce 7800GTX"
date: 2007-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by aikishugyo on 2007-01-03
I waited a while before installing Edgy on my machine already running Dapper,
but finally did upgrade on a new partition over the new year, using a Desktop CD
for AMD64 downloaded from the Ubuntu site.

Specs:

MB: RIOWORKS HDAMEX-SLi (with nForce Professional 2200)
CPU: dual AMD Opteron 275 (2.2GHz) [total 4 processors]
RAM: PC3200 DDR 4GB ECC registered [4x1, still very pricey]
Video card: dual nVidia GeForce 7800GTX (PCI-e/256MB) [total two cards, 4 connectors]
HDD: two 500GB SATAII/8MB cache (7800rpm)
Screens: two Mitsubishi Diamondcrysta RDT1712V (SXGA)
Network: dual Gigbit (10/100/1000) LAN port card
other: floppy, SD card reader, USBx6, 1394x1, DVD writer combo,
            PS/2 mouse and USB keyboard

Installation:

1. checked partition to use from inside Dapper
2. started Edgy from Desktop CD
3. rechecked partitioning when desktop appeared
4. chose Install from desktop
5. selected simple choices of language, keyboard, location
6. waited until base system was installed, then removed CD and rebooted
7. system came up fine, I chose single-user mode (no X)
8. added repositories in sources.list and added proxy, did update, dist-upgrade
9. edited xorg.conf to allow for nvidia and twinview, and installed nvidia-glx
10. started gdm and logged in successfully
11. installed various GNOME desktop components, texlive (my main reason to upgrade),
       emacs21, bbdb, gnus, sylpheed, UIM, Anthy, Canna. Japanese input worked fine.
12. Set up OpenOffice to use Japanese input (make sure GTK parts of Openoffice installed).
13. linked other partitions to my desktop to access their data.
14. setup network printers. Here when trying to setup an LPD device the GNOME print manager
       crashed every time I tried to enter the server  IP. I could enter the server full name instead
       to get around this (I prefer to use IP in case of DNS trouble). This particular printer driver was 
       *not* working in my Dapper installation (EPSON LP-2500 b/w laser) but works flawlessly in
       Edgy. Also the Xerox Phaser 8500 works perfectly using a Tektronix Phaser-850 driver. I
       tested both cups manager in GNOME and from the web browser.

No major problems at all to report. Missing are a lot of plugins that I would like and which need
some effort to install (since they are 32-bit), but I left these out for now, as this is a work machine.

Very happy with Ubuntu

PS I installed GNU/linux Edgy on an i386 PC the same time and this also installed flawlessly.
The newer GNU/linux distributions are a joy to install and use.

Regards, Gernot

---

