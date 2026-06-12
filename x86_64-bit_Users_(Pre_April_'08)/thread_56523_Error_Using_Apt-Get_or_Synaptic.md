---
title: "Error Using Apt-Get or Synaptic"
date: 2005-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by huckleberry on 2005-08-12
First time UBUNTU and linux user (sort of, I dabbled in linux about 5 years ago).  Currently use a UNIX system at work so I know my way around a terminal.

I am having errors when I try to install packages.   Here is the error I get:

[INDENT]Preconfiguring packages ...
Selecting previously deselected package numlockx.
(Reading database ... 71675 files and directories currently installed.)
Unpacking numlockx (from .../numlockx_1.0-12_amd64.deb) ...
Setting up locales (2.3.2.ds1-20ubuntu14) ...
Generating locales...
  en_US.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8...memory exhausted
dpkg: error processing locales (--configure):
 subprocess post-installation script returned error exit status 1
Setting up numlockx (1.0-12) ...
Errors were encountered while processing:
 locales
E: Sub-process /usr/bin/dpkg returned an error code (1)[/INDENT]

Also have  a few other bugs.  Kernel panic every so often on boot, gnome freezes forcing a hard restart, synaptic bugs out on errors like those above.


System Desciption (newly built computer):
AMD 3200+
Abit A8N NForce 4 Ultra Mobo
MSI GF 6600GT
1Gb Corsair XMS
160Gb Seagate Barracude SATA 

Any help would be apprciated.

Sincerely,

---

