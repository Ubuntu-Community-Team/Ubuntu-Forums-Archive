---
title: "[How-To] Ubuntu 7.04 64-bit Intel Compiler + Multimedia Install w/ special rt73 WLAN"
date: 2007-08-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by elmax on 2007-08-14
My System with Ubuntu 7.04 (Feisty Fawn) AMD64 64bit installation

Desktop PC Hardware Info
Asrock 4Core-1333-Viiv with P965 / ICh8 Chipset
Intel Core2Duo E6750
2 GB RAM
MSI ATI Radeon R X1650 PRO XT TD 512 MB
ASUS WL 167g (rt73 Chip)
16x DVD-RAM
250 GB HDD

Software info
I wanted to have 
- a Development environment, (especially Intel C and Fortran compiler 10 suite, MKL)
- a Multimedia (consumption) environment
on 64 bit.

Everything worked out fine by now (Compiling, Web, Music, Video, burning DVDs, WLAN connection). Only the ASUS USB-Stick WLAN stuff was cumbersome. I worked approx. 5 hours so far to get my 64 bit OS customized. If you do it, it is probably faster. I had to do all the recherche and get around the trouble. 

These were my steps so far.

1. Install from AMD64 CD. Everything works smooth.
2. Update via Synaptics.
3. Get proprietary ATI driver via restricted driver administration. Works fine (3D is on)!
4. Get Thunderbird install instructions from [http://ubuntu.iuculano.it/dists/feisty/thunderbird/](http://ubuntu.iuculano.it/dists/feisty/thunderbird/)
5. WLAN: After restart (keep the kernel update in mind). 
   a. Get Ralink Driver for WLAN 167g ASUS from  [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz)
   b. Compile Ralink Driver as described e.g. in [http://wiki.ubuntu-it.org/Hardware/DispositiviSenzaFili/RalinkRT73](http://wiki.ubuntu-it.org/Hardware/DispositiviSenzaFili/RalinkRT73) (Don't worry the commands are not in italian... :-) )
   c. Deinstall network-manager
   d. I have done this for WEP 128 bit and it worked fine. So no guarantee for WPA or WPA2.
6. Install beagle for Desktop Search purposes, if you like.
7. Install intel compiler
   a. Install ia32-libs and alien > 8.61
   b. extract tarballs provided by intel, go to data directory and alien -k  the rpm files as described here [http://www.nicdan.id.au/computers/compiling/intel_on_debian.html](http://www.nicdan.id.au/computers/compiling/intel_on_debian.html)
   c. Use deb_fix as described here [http://www.nicdan.id.au/computers/compiling/intel_on_debian.html](http://www.nicdan.id.au/computers/compiling/intel_on_debian.html)
   d. Install .deb packages with dpkg -i
8. Install Intel MKL
   a. Start installation process by install/install and wait til extraction has finished
   b. alienate rpm-file in the latest generated subdirectory in /tmp
   c. use dpkg -i to install (deb_fix is not working)
9. Copy your Intel license files to /opt/intel/licenses. (You have to register for the product at the Intel website to get .lic files.)
10. Update the Intel provided environment setting scripts to use /bin/bash and replace <INSTALLDIR> in /opt/intel/mkl/.../tools/environment/mklvars[..].sh by the installation root of mkl, e.g. /opt/intel/mkl/9.1.021
11. Include Intel compiler environment scripts in .bashrc
12. Install automatix2 following instructions from [http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.04_.28Feisty_AMD64.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.04_.28Feisty_AMD64.29)
13. Start automatix from the application -> system tools menu and install
    a. totem-xine
    b. vlc-player (works best so far)
    c. acrobat reader
    d. gftp
    e. backup and restore
14. Get Flash Player plugin from [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)
15. Get Skype: Do what is said under [http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)


I feel like I am pretty much done for now .... and happy. So maybe it helps you to feel happy, too.

With best regards, elmax


My uname -a:
Linux beta 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux

---

