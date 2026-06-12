---
title: "gentoo install through ubutnu"
date: 2008-09-12
forum: x86 64-bit Users
---

### Post by shao on 2008-09-12
Hi, uhmmm... I dint know where else to post this so, if I shouldn't be doing this here I'm sorry. Anyway I'm trying to install Gentoo and I've  followed the instructions from this page 

[http://abhinay.wordpress.com/2008/07/17/install-gentoo-when-other-linux-running/]("http://abhinay.wordpress.com/2008/07/17/install-gentoo-when-other-linux-running/")

and it tell's me to add lines to make.conf:
```
make.conf

Set CFLAGS, CXXFLAGS

CFLAGS="-O2 -march=nocona -pipe"
CXXFLAGS="${CFLAGS}"

also add these lines to make.conf
MAKEOPTS="-j3"

VIDEO_CARDS="i810 vesa"

INPUT_DEVICES="keyboard mouse synaptics evdev"

```

and then
```
GENTOO_MIRRORS="http://gentoo.cites.uiuc.edu/pub/gentoo/ \
                http://gentoo.osuosl.org/ \
                http://gentoo.chem.wisc.edu/gentoo/"
SYNC="rsync://rsync.gentoo.org/gentoo-portage"

```

so I go on to the following command which gives me this

```
bin/bash-2.05b# env-update
!!! No closing quotation in //etc/make.conf
!!! Incorrect multiline literals can cause this. Do not use them.
bin/bash-2.05b# 
```

any help?

---

### Post by estamand on 2008-09-13
Change your

GENTOO_MIRRORS="http://gentoo.cites.uiuc.edu/pub/gentoo/ \
                [http://gentoo.osuosl.org/](http://gentoo.osuosl.org/) \
                http://gentoo.chem.wisc.edu/gentoo/"

to

GENTOO_MIRRORS="http://gentoo.cites.uiuc.edu/pub/gentoo/"

See if that works.

---

### Post by shao on 2008-09-13
nope, this is my make.conf now 
```
bin/bash-2.05b# cat make.conf
# These settings were set by the catalyst build script that automatically built this stage
# Please consult /etc/make.conf.example for a more detailed example
CFLAGS="-Os -pipe"
CHOST="i386-gentoo-linux-uclibc"
CXXFLAGS="-Os -pipe
Set CFLAGS, CXXFLAGS

CFLAGS="-O2 -march=nocona -pipe"
CXXFLAGS="${CFLAGS}"

also add these lines to make.conf
MAKEOPTS="-j3"

VIDEO_CARDS="i810 vesa"

INPUT_DEVICES="keyboard mouse synaptics evdev"

GENTOO_MIRRORS="http://gentoo.cites.uiuc.edu/pub/gentoo/"
```

and still the output is 
```
bin/bash-2.05b# env-update
!!! Invalid token (not "=") -march
!!! ParseError: Invalid token (not '='): //etc/make.conf: line 8 in //etc/make.conf
!!! Incorrect multiline literals can cause this. Do not use them.
```

---

### Post by Neo0351 on 2008-09-13
I'd recommend you start over with you're install.  Next after you get the stage3 tarball and portage follow the official guide to install starting where you left off.  The guide you linked seems very incomplete.  Also do yourself a favor and print out the output of 
```
lspci -k
```
This will tell you what hardware you have and the modules you are using to get it working if you decide to build your kernel.  Here's the link to the gentoo handbook [http://www.gentoo.org/doc/en/handbook/index.xml](http://www.gentoo.org/doc/en/handbook/index.xml)
Hope this helps

---

### Post by shao on 2008-09-13
ok sooo, i strating over and this is lspci
```
$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

and I have a HP pavillon dv600

---

### Post by estamand on 2008-09-15
You`ve got a different problem now.  Look at your make.conf. You are missing a "

bin/bash-2.05b# cat make.conf
# These settings were set by the catalyst build script that automatically built this stage
# Please consult /etc/make.conf.example for a more detailed example
CFLAGS="-Os -pipe"
CHOST="i386-gentoo-linux-uclibc"
CXXFLAGS=**"-Os -pipe"**
Set CFLAGS, CXXFLAGS

CFLAGS="-O2 -march=nocona -pipe"
CXXFLAGS="${CFLAGS}"

also add these lines to make.conf
MAKEOPTS="-j3"

VIDEO_CARDS="i810 vesa"

INPUT_DEVICES="keyboard mouse synaptics evdev"

GENTOO_MIRRORS="http://gentoo.cites.uiuc.edu/pub/gentoo/"

---

### Post by eurgain on 2008-09-15
The lines that read:

 Set CFLAGS, CXXFLAGS

and

 also add these lines to make.conf

appear to be missing the leading # character to make them into comments.  You do not want bash to try to interpret these!

Two other things... you are building a 32-bit system for a 64-bit machine: is that what you want?  The intel driver has now replaced the i810 for most purposes.

BTW, after using Gentoo for years alongside Ubuntu and SuSE, I have very recently dumped Gentoo.  It seems to have become mired in infighting and politics.  I now use Ubuntu, and if I feel like compiling something, I use apt-build.

A

---

