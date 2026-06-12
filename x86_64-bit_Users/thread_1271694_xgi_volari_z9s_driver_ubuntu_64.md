---
title: "xgi volari z9s driver ubuntu 64"
date: 2009-09-21
forum: x86 64-bit Users
---

### Post by amikebous on 2009-09-21
Hello everybody

So far I have been searching on other people's posts (so thanks for the support so far!), but this time it looks like I had to make one myself! 

The problem is that I have an Asus Server with an xgi volari z9s card and I am having a hard time on installing the driver on Ubuntu 64. Any ideas?
Here is what I have on the read me of the driver folder 

Thanks a lot in advance

Michalis

XGI Linux Driver Package User Installation Guide

Decemeber 23, 2005  by Jill Wang (xgi0133)

Contents

1. System Requirement
2. Hardware  Requirement
3. Insallation with RPM
4. Insallation with TGZ
5. X Configuration


===========================================
1. System Requirement
===========================================

Supported Linux Distribution:
    Red Hat 9
    Red Hat Enterprise 3, 4
    Fedora Core 1-4
    
    Mandrake 9.2
    
    SUSE Server 9
    SUSE Professional 9.1, 9.2
    Novell SUSE 10
    
    Debian 5.3
    
Kernel Version:
    2.4.18-14 (RH 8)
    2.4.19
    2.4.20
    2.4.20-8 (RH 9)
    2.4.21
    2.4.21-4.EL
    2.4.22
    2.4.22-10mdk (Mandrake 9.2)
    (Suppose 2.4.18~2.4.22 are OK)
    2.6 and later (RHEL4 Serise, SUSE Pro 9.1 and 9.2, Novell SUSE 10)
    
XFree86 Version:
    4.4.0
    
XOrg Version:
    6.8.2


===========================================
2. Hardware  Requirement
===========================================
VGA adapter card:
    XGI Volari Z7/Z9

===========================================
3. Insallation with RPM
===========================================
Driver file:
   1. xgi_Xorg_6.8.2-#.#.#-#.x86_64.rpm --> RHEL4_64bit
   2. xgi_Xorg_6.8.2-#.#.#-#.i386.rpm   --> RHEL4_32bit
   3. xgi_xf86_4.4.0-#.#.#-#.x86_64.rpm --> RHEL3_64bit / SLES9_64bit
   4. xgi_xf86_4.4.0-#.#.#-#.i386.rpm   --> RHEL3_32bit / SLES9_32bit

SOURCE file:
   1. xgi_driver-#.#.#-#.src.rpm 

Usage:

RPM:
    -Install 
      Run "rpm -Uvh xgi_xxxx_#.#.#-<version>.rpm"
          ex: rpm -Uvh xgi_Xorg_6.8.2-1.2.9-1.x86_64.rpm
              rpm -Uvh xgi_xf86_4.4.0-1.2.9-1.i386.rpm
    
    -Uninstall    
      Run "rpm -e xgi_xxxx_#.#.#"
          ex: rpm -e xgi_Xorg_6.8.2
              rpm -e xgi_xf86_4.4.0
    
    -Query
      Run "rpm -i xgi_xxxx_#.#.#"

===========================================
4. Insallation with TGZ
===========================================
Usage:

    $ tar xvfzp xgipkg.tgz
    $ sh install.sh
    
Reference Environment
    
    X11R6 - use as the root path for X11R6 system.
    
Installation action 

    1. copy xgi_drv.o to ${X11R6}/lib/modules/drivers for driver of XFree86
    2. modify /etc/X11/XF86Config to enable it.        
    
Uninstallation action
    
    $ sh uninstall.sh
    
    1. remove xgi_drv.o from ${X11R6}/lib/modules/drivers for driver of XFree86
    2. Recover the /etc/X11/XF86Config to recover the original status.
    
===========================================
4. X Configuration
===========================================    
Tune the xorg.conf (or XF86Config if you are running XFree86) configuration file to taste.
    a. Open the file in a text editor such as emacs or vi.
    b. Check if the frequencies(HorizSync and VertRefresh in the Monitor section of X configure file) for the target system's monitor are correct. 
       These are usually expressed as a horizontal(HorizSync) and vertical synchronization(VertRefresh) rate. 
       These values are added to the xorg.conf file under the "Monitor" section:

        Section "Monitor"
                Identifier   "Monitor0"
                VendorName   "Monitor Vendor"
                ModelName    "Monitor Model"
                HorizSync    30-107
                VertRefresh  48-120
        EndSection
      
       The shorter the ranges of HorizSync and VertRefresh defined in the configure file are , The less the modes X support are.
       The user can use the utility such as Xconfigurator to update the horizontal(HorizSync) and vertical synchronization(VertRefresh) rate for the monitor
       , or simply edit the X configuration file (xorg.conf or XFree86) by hand.

---

