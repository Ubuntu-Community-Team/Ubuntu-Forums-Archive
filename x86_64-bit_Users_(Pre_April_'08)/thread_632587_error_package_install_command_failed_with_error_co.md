---
title: "error: package install command failed with error code 100"
date: 2007-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by biddy on 2007-12-05
Hello again,

I'm having a lot of trouble trying to install hplip 2.7.10 from terminal from the following link:
[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

, i am following instructions and have checked that mymultiverse/universe repository is active, infact all software sources are tabbed & I have also tried with my CD/DVD off but no luck, when I try with install disc i get the title error. following is the terminal output once I ran command sh hpli-2.7.10.run

warren@warren-desktop:~/Desktop$ sh hplip-2.7.10.run
Creating directory hplip-2.7.10
Verifying archive integrity... All good.
Uncompressing HPLIP 2.7.10 Self Extracting Archive.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

HP Linux Imaging and Printing System (ver. 2.7.10)
HPLIP Installer ver. 3.0

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Wed-05-Dec-2007_21:43:30.log

Initializing. Please wait...
 
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.


INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to chose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, q=quit) : a


INTRODUCTION
------------
This installer will install HPLIP version 2.7.10 on your computer.
Please close any running package management systems now (YaST, Adept, Synaptic, Up2date, etc).


DISTRO/OS CONFIRMATION
----------------------
Distro appears to be Ubuntu 7.10.

Is "Ubuntu 7.10" your correct distro/OS and version (y=yes*, n=no, q=quit) ? y


ENTER ROOT/SUPERUSER PASSWORD
-----------------------------
Please enter the root/superuser password: 
Password accepted


INSTALLATION NOTES
------------------
Enable the universe/multiverse repositories. See: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for more information.  Disable the CD-ROM/DVD source if you do not have the Ubunbtu installation media inserted in the drive.

Please read the installation notes. Press <enter> to continue or 'q' to quit: 


RUNNING PRE-INSTALL COMMANDS
----------------------------


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 8 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: cups (cups - Common Unix Printing System)
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
warning: Missing REQUIRED dependency: libpthread (libpthread - POSIX threads library)
warning: Missing REQUIRED dependency: python-devel (python-devel - Python development files)
warning: Missing REQUIRED dependency: cups-devel (cups-devel- Common Unix Printing System development files)
warning: Missing REQUIRED dependency: libusb (libusb - USB library)
warning: Missing REQUIRED dependency: libtool (libtool - Library building support services)
warning: Missing REQUIRED dependency: libjpeg (libjpeg - JPEG library)


INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 7 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency for option 'network': libcrypto (libcrypto - OpenSSL cryptographic library)
warning: Missing REQUIRED dependency for option 'network': libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)
warning: Missing REQUIRED dependency for option 'gui': pyqt (PyQt - Qt interface for Python)
warning: Missing OPTIONAL dependency for option 'fax': reportlab (Reportlab - PDF library for Python)
warning: Missing REQUIRED dependency for option 'scan': sane-devel (SANE - Scanning library development files)
warning: Missing OPTIONAL dependency for option 'scan': pil (PIL - Python Imaging Library (required for commandline scanning with hp-scan))
warning: Missing OPTIONAL dependency for option 'scan': scanimage (scanimage - Shell scanning program)
A package manager 'apt-get' appears to be running. Please quit the package manager and press enter to continue (i=ignore, q=quit*) :q
A package manager 'apt-get' appears to be running. Please quit the package manager and press enter to continue (i=ignore, q=quit*) :i
warning: Ignoring running package manager. Some package operations may fail.


CHECKING FOR NETWORK CONNECTION
-------------------------------
Network connection present.


RUNNING PRE-PACKAGE COMMANDS
----------------------------
warning: An error occurred running 'sudo dpkg --configure -a'
sudo dpkg --configure -a (Pre-depend step 1)
warning: An error occurred running 'sudo apt-get install --yes --force-yes -f'
sudo apt-get install --yes --force-yes -f (Pre-depend step 2)
warning: An error occurred running 'sudo apt-get update'
sudo apt-get update (Pre-depend step 3)


DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --yes --force-yes libcupsys2 build-essential build-essential python2.5-dev libcupsys2-dev cupsys-bsd libusb-dev libtool libjpeg62-dev openssl libsnmp9-dev python-qt3 python-reportlab libsane-dev python-imaging libsane'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? y
Running 'sudo apt-get install --yes --force-yes libcupsys2 build-essential build-essential python2.5-dev libcupsys2-dev cupsys-bsd libusb-dev libtool libjpeg62-dev openssl libsnmp9-dev python-qt3 python-reportlab libsane-dev python-imaging libsane'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? 
error: Aborted.

warren@warren-desktop:~/Desktop$ 

Thanks for your time
biddy

---

### Post by Yellow Pasque on 2007-12-05
Did you have any other package management programs like synaptic open at the time?

What happens when you try and sudo ap-get install those packages yourself?

---

### Post by breggol on 2008-02-02
Same error over here with 7.10.

Any solution yet?

---

### Post by o.besner on 2008-02-06
Same problem.

What I found out is that you can install the packages yourself with Synaptic. Just install everything with the same name... it works !

---

### Post by suejacobson on 2008-05-05
Ok, so I am trying to install what my husband gave me on my parent's computer and I have no idea what I'm doing....

My error message is:
A package manager 'apt-get' appears to be running. Please quit the package manager and press enter to continue (i=ignore, r=retry*, q=quit) :

I saw where someone said:
What I found out is that you can install the packages yourself with Synaptic. Just install everything with the same name... it works !

can you walk me through that?

---

