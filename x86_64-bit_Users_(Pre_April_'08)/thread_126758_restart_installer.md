---
title: "restart installer"
date: 2006-02-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by sredlich on 2006-02-07
Hi,

I am installing Breezy to my AMD64.  I had an unimportant problem copying all the files to the hard disk.
Grub Installed, rebooted machine, removed CDROM and the installer is stuck running apt trying to 
read from the CD (that is not there).  I updated sources.list to use the network. 

apt-get still not working so I killed it. and update/upgrade (only base package installed at this point)
however installer (menu/gui) never returns.

What is the path to the ubuntu installer, so that I may continue later stages of the installation.  e.g. X, etc.

Thanks,
Steve

---

### Post by sredlich on 2006-02-08
No anwer, so I Reinstalled

Turns out problems were due to errors reading CD.  I don't have md5sum on windows, so I never checked it.

 I had a problem installing the base system.

 Failed to fetch file:///cdrom/pool/main/z/zlib/zlib1g_1.2.3-3ubuntu4_amd64.deb
 MD5Sum mismatch

 I brought up a shell
 chroot /target

 added ubuntu sources to /etc/apt/sources.list

 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 commented out the CDROM

 apt-get update
 apt-get -f install
 apt-get upgrade

Then continued with the install.

Now to get X working:
(WW) RADEON: No matching Device section for instance (BusIDPCI:1:0:1) found
(EE) No devices detected.

---

