---
title: "[SOLVED] Driver question"
date: 2008-05-19
forum: x86 64-bit Users
---

### Post by HeavyP on 2008-05-19
My laptop have a bug on the bug tracker site, consequently, I am unable to hear any sound or use my wireless.

Can I browse the internet for linux driver? What are the alternatives?

I really want to fully convert to Ubuntu but I'm quite inexperience. Any help would be highly appreciated.

---

### Post by Sef on 2008-05-19
What are your system specs?

Possibly it will work in GNU/Linux.

---

### Post by HeavyP on 2008-05-20
I'm using Lenovo 3000 Y410. I have got a driver for my wireless adapter now (Intel 3945). Currently, working on installation.

---

### Post by John.Michael.Kane on 2008-05-20
Regarding your sound issue. You can try adding the following line, either to your /etc/modprobe.conf.

```
options snd-hda-intel index=0 model=lenovo
```

Regarding the wireless issue. Can please post the output, of the below command.

```
lshw -short -quiet
```

---

### Post by HeavyP on 2008-05-20
Sorry John.Michael.Kane I cannot find modprobe.conf on my system I already searched through but it doesn't exist

The following is the result I got from lshw

heavyp@heavyp-laptop:~$ lshw -short -quiet
WARNING: you should run this program as super-user.
H/W path       Device  Class       Description
==============================================
                       system      Computer
/0                     bus         Motherboard
/0/0                   memory      2038MiB System memory
/0/1                   processor   Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80G
/0/100                 bridge      Mobile PM965/GM965/GL960 Memory Controller Hu
/0/100/2               display     Mobile GM965/GL960 Integrated Graphics Contro
/0/100/2.1             display     Mobile GM965/GL960 Integrated Graphics Contro
/0/100/1a              bus         82801H (ICH8 Family) USB UHCI Controller #4
/0/100/1a.1            bus         82801H (ICH8 Family) USB UHCI Controller #5
/0/100/1a.7            bus         82801H (ICH8 Family) USB2 EHCI Controller #2
/0/100/1b              multimedia  82801H (ICH8 Family) HD Audio Controller
/0/100/1c              bridge      82801H (ICH8 Family) PCI Express Port 1
/0/100/1c.1            bridge      82801H (ICH8 Family) PCI Express Port 2
/0/100/1c.1/0          network     PRO/Wireless 3945ABG Network Connection
/0/100/1c.2            bridge      82801H (ICH8 Family) PCI Express Port 3
/0/100/1c.3            bridge      82801H (ICH8 Family) PCI Express Port 4
/0/100/1c.3/0  eth0    network     NetLink BCM5906M Fast Ethernet PCI Express
/0/100/1d              bus         82801H (ICH8 Family) USB UHCI Controller #1
/0/100/1d.1            bus         82801H (ICH8 Family) USB UHCI Controller #2
/0/100/1d.2            bus         82801H (ICH8 Family) USB UHCI Controller #3
/0/100/1d.7            bus         82801H (ICH8 Family) USB2 EHCI Controller #1
/0/100/1e              bridge      82801 Mobile PCI Bridge
/0/100/1e/6            bus         R5C832 IEEE 1394 Controller
/0/100/1e/6.1          system      R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
/0/100/1e/6.2          system      R5C592 Memory Stick Bus Host Adapter
/0/100/1e/6.3          system      xD-Picture Card Controller
/0/100/1e/6.4          generic     Illegal Vendor ID
/0/100/1f              bridge      82801HEM (ICH8M) LPC Interface Controller
/0/100/1f.2            storage     82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Control
/0/100/1f.3            bus         82801H (ICH8 Family) SMBus Controller

I already tried running in sudo but it doesn't work, the terminal turn blank.

Also, I have been working on my own to install drivers that I found on the internet.

For SoundCard I typed in google look for realtek linux driver and I got something like realtek-linux-audiopack-5.03. However, I couldn't get it to install. Here, is what happened

There are two files so I archieved them and post on the internet. Please take time to scan for viruses if you are using Windows because I'm using public computer.

[http://www.savefile.com/files/1564872](http://www.savefile.com/files/1564872)

And here is where I'm stuck on installing iwlwifi

Can't compile mac80211-10.0.4

[http://www.savefile.com/files/1564874](http://www.savefile.com/files/1564874)

Thank you for your help.
I really appreciate it.

:)

---

### Post by Yellow Pasque on 2008-05-20
Try OSS4
[http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2)

---

### Post by HeavyP on 2008-05-21
> **Temüjin said:**
> Try OSS4
[http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2)

Are you sure that my soundcard is in the list?

---

### Post by Yellow Pasque on 2008-05-21
> **HeavyP said:**
> Are you sure that my soundcard is in the list?
Yes, it's a standard HD Audio device implemented with a Realtek codec.

---

### Post by HeavyP on 2008-05-21
I see thanks, I'll try but I'd rather try this after I get my wifi working....

It's rather too complicate for me to run around and use a public computer to download file and install it on my laptop with a flash drive.

Can anyone please take a look on those files? 

Thanks

P.S. It used to work ocassionally on Ubuntu 7.0

---

### Post by Sef on 2008-05-21
> PRO/Wireless 3945ABG

> I see thanks, I'll try but I'd rather try this after I get my wifi working....

Is the [the driver]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&Inst=Yes&ProductID=2259&DwnldID=10315&strOSs=39&OSFullName=Linux*&lang=eng") that you downloaded here?

The file is tgz: > English: iwlwifi-1.0.0-1.tgz

If you are not sure how to install a .tgz package, read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by HeavyP on 2008-05-22
heavyp@heavyp-laptop:~/Desktop/iwlwifi-1.0.0-1$ make
Makefile:20: 
Makefile:21: WARNING: $SHELL not set to bash.
Makefile:22: If you experience build errors, try
Makefile:23: 'make SHELL=/bin/bash'.
Makefile:24: 
Kernel Makefile not found at '/lib/modules/2.6.24-16-generic/source'
make: *** [compatible/kversion] Error 1

This is what I got after trying to install that thing. It seems that I need to install mac80211 first, which I already tried and couldn't get it then. The detail of the installation can be checked on my previous posts.

---

### Post by HeavyP on 2008-05-23
Can anyone help me please, I'm really desperate to use Ubuntu :(

---

### Post by Yellow Pasque on 2008-05-23
It looks like you need the kernel headers package, i.e:
```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by HeavyP on 2008-05-23
heavyp@heavyp-laptop:~$ sudo apt-get install linux-headers-'uname -r'
[sudo] password for heavyp: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-uname -r
heavyp@heavyp-laptop:~$ 

Then? What now?

---

### Post by Yellow Pasque on 2008-05-23
You typo'd. The ' should be a ` (found on the ~ key). `uname -r` just substitutes the name of your kernel; you could also type out:
```
sudo apt-get install linux-headers-2.6.24-16-generic
```

---

### Post by HeavyP on 2008-05-23
D'oh!

Edit: Now what do I do now (T-T)

heavyp@heavyp-laptop:~$ sudo apt-get install linux-headers-2.6.24-16-generic
[sudo] password for heavyp: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.24-16-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
heavyp@heavyp-laptop:~$

---

### Post by Yellow Pasque on 2008-05-23
Hmmm. Try:
```
sudo apt-get build-dep linux-image-`uname -r`
sudo apt-get source linux-image-`uname -r`
```

---

### Post by HeavyP on 2008-05-24
heavyp@heavyp-laptop:~$ sudo apt-get build-dep linux-image-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/th.archive.ubuntu.com_ubuntu_dists_hardy_universe_source_Sources - open (2 No such file or directory)
heavyp@heavyp-laptop:~$ sudo apt-get source linux-image-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/th.archive.ubuntu.com_ubuntu_dists_hardy_universe_source_Sources - open (2 No such file or directory)
heavyp@heavyp-laptop:~$ 

Help!

---

### Post by Yellow Pasque on 2008-05-24
Are all of your software sources enabled? Go to System -> Administration -> Software Sources and make sure all of the options are checked.

---

### Post by HeavyP on 2008-05-24
After checking all available options this is what I get after closing the window```


Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
```

I already mounted the cdrom and tried to use sudo apt-cdrom add... but I still got the same result

Arghhhh..

Edit: Hang on this might work.... I'm re-running the previous commands and it's downloading something. Unfortunately this will have to wait cause my battery is running out.

Here's the result

> heavyp@heavyp-laptop:~$ sudo apt-get build-dep linux-image-`uname -r`
[sudo] password for heavyp: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  build-essential debhelper docbook-dsssl docbook-utils docbook-xsl dpkg-dev
  g++ g++-4.2 gawk gettext html2text intltool-debian jadetex kernel-wedge
  libc6-dev libosp5 libostyle1c2 libsgmls-perl libsp1c2 libstdc++6-4.2-dev
  libtimedate-perl linux-libc-dev openjade patch po-debconf sgmlspl sharutils
  sp tex-common texlive-base texlive-base-bin texlive-common texlive-doc-base
  texlive-fonts-recommended texlive-latex-base texlive-latex-recommended tipa
  transfig xmlto
The following packages will be upgraded:
  cpp gcc
2 upgraded, 39 newly installed, 0 to remove and 100 not upgraded.
Need to get 41.6MB/42.2MB of archives.
After this operation, 159MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-proposed/main linux-libc-dev 2.6.24-17.31 [694kB]
Get:2 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main libc6-dev 2.7-10ubuntu3 [2538kB]                                                                              
Get:3 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-proposed/main gcc 4:4.2.3-1ubuntu5 [5084B]                                                                         
Get:4 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main libstdc++6-4.2-dev 4.2.3-2ubuntu7 [1217kB]                                                                    
Get:5 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main g++-4.2 4.2.3-2ubuntu7 [3035kB]                                                                               
Get:6 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-proposed/main g++ 4:4.2.3-1ubuntu5 [1446B]                                                                         
Get:7 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main libtimedate-perl 1.1600-9 [30.1kB]                                                                            
Get:8 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main patch 2.5.9-4 [97.8kB]                                                                                        
Get:9 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main dpkg-dev 1.14.16.6ubuntu3 [559kB]                                                                             
Get:10 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main build-essential 11.3ubuntu1 [7070B]                                                                          
Get:11 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main html2text 1.3.2a-3build2 [91.3kB]                                                                            
Get:12 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main gettext 0.17-2ubuntu1 [2067kB]                                                                               
Get:13 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main intltool-debian 0.35.0+20060710.1 [31.6kB]                                                                   
Get:14 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main po-debconf 1.0.10 [232kB]                                                                                    
Get:15 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main debhelper 6.0.4ubuntu1 [516kB]                                                                               
Get:16 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main libosp5 1.5.2-3ubuntu3 [1095kB]                                                                              
Get:17 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main libostyle1c2 1.4devel1-18build1 [890kB]                                                                      
Get:18 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main openjade 1.4devel1-18build1 [338kB]                                                                          
Get:19 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main docbook-dsssl 1.79-5 [343kB]                                                                                 
Get:20 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main tex-common 1.10 [710kB]                                                                                      
Get:21 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main texlive-common 2007-13 [78.5kB]                                                                              
Get:22 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main texlive-doc-base 2007-3 [750kB]                                                                              
Get:23 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main texlive-base-bin 2007.dfsg.1-2 [2646kB]                                                                      
Get:24 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main texlive-base 2007-13 [6159kB]                                                                                
Get:25 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main texlive-fonts-recommended 2007-13 [7203kB]                                                                   
Get:26 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main texlive-latex-base 2007-13 [1223kB]                                                                          
Get:27 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main texlive-latex-recommended 2007-13 [1732kB]                                                                   
Get:28 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main tipa 2:1.3-10 [3195kB]                                                                                       
Get:29 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main jadetex 3.13-9 [234kB]                                                                                       
Get:30 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main libsgmls-perl 1.03ii-31 [29.2kB]                                                                             
Get:31 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main sgmlspl 1.03ii-31 [11.2kB]                                                                                   
Get:32 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main libsp1c2 1.3.4-1.2.1-47build1 [1477kB]                                                                       
Get:33 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main sp 1.3.4-1.2.1-47build1 [173kB]                                                                              
Get:34 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main docbook-utils 0.6.14-1 [73.2kB]                                                                              
Get:35 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main docbook-xsl 1.73.2.dfsg.1-2 [1339kB]                                                                         
Get:36 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main kernel-wedge 2.29ubuntu2 [40.0kB]                                                                            
Get:37 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main sharutils 1:4.6.3-1build1 [111kB]                                                                            
Get:38 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main transfig 1:3.2.5-rel-3 [589kB]                                                                               
Get:39 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main xmlto 0.0.18-5.1build1 [31.7kB]                                                                              
Fetched 41.5MB in 43min5s (16.1kB/s)                                                                                                                        
Extracting templates from packages: 100%
Preconfiguring packages ...
Selecting previously deselected package gawk.
(Reading database ... 96881 files and directories currently installed.)
Unpacking gawk (from .../gawk_1%3a3.1.6.dfsg-0ubuntu1_amd64.deb) ...
Preparing to replace cpp 4:4.2.3-1ubuntu3 (using .../cpp_4%3a4.2.3-1ubuntu5_amd64.deb) ...
Unpacking replacement cpp ...
Selecting previously deselected package linux-libc-dev.
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-17.31_amd64.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu3_amd64.deb) ...
Preparing to replace gcc 4:4.2.3-1ubuntu3 (using .../gcc_4%3a4.2.3-1ubuntu5_amd64.deb) ...
Removing old gcc doc directory.
Unpacking replacement gcc ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.3-2ubuntu7_amd64.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.3-2ubuntu7_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu5_amd64.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-4_amd64.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu3_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_amd64.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-3build2_amd64.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.17-2ubuntu1_amd64.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.35.0+20060710.1_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_1.0.10_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_6.0.4ubuntu1_all.deb) ...
Selecting previously deselected package libosp5.
Unpacking libosp5 (from .../libosp5_1.5.2-3ubuntu3_amd64.deb) ...
Selecting previously deselected package libostyle1c2.
Unpacking libostyle1c2 (from .../libostyle1c2_1.4devel1-18build1_amd64.deb) ...
Selecting previously deselected package openjade.
Unpacking openjade (from .../openjade_1.4devel1-18build1_amd64.deb) ...
Selecting previously deselected package docbook-dsssl.
Unpacking docbook-dsssl (from .../docbook-dsssl_1.79-5_all.deb) ...
Selecting previously deselected package tex-common.
Unpacking tex-common (from .../tex-common_1.10_all.deb) ...
Selecting previously deselected package texlive-common.
Unpacking texlive-common (from .../texlive-common_2007-13_all.deb) ...
Selecting previously deselected package texlive-doc-base.
Unpacking texlive-doc-base (from .../texlive-doc-base_2007-3_all.deb) ...
Selecting previously deselected package texlive-base-bin.
Unpacking texlive-base-bin (from .../texlive-base-bin_2007.dfsg.1-2_amd64.deb) ...
Selecting previously deselected package texlive-base.
Unpacking texlive-base (from .../texlive-base_2007-13_all.deb) ...
Selecting previously deselected package texlive-fonts-recommended.
Unpacking texlive-fonts-recommended (from .../texlive-fonts-recommended_2007-13_all.deb) ...
Selecting previously deselected package texlive-latex-base.
Unpacking texlive-latex-base (from .../texlive-latex-base_2007-13_all.deb) ...
Selecting previously deselected package texlive-latex-recommended.
Unpacking texlive-latex-recommended (from .../texlive-latex-recommended_2007-13_all.deb) ...
Selecting previously deselected package tipa.
Unpacking tipa (from .../tipa_2%3a1.3-10_all.deb) ...
Selecting previously deselected package jadetex.
Unpacking jadetex (from .../jadetex_3.13-9_all.deb) ...
Selecting previously deselected package libsgmls-perl.
Unpacking libsgmls-perl (from .../libsgmls-perl_1.03ii-31_all.deb) ...
Selecting previously deselected package sgmlspl.
Unpacking sgmlspl (from .../sgmlspl_1.03ii-31_all.deb) ...
Selecting previously deselected package libsp1c2.
Unpacking libsp1c2 (from .../libsp1c2_1.3.4-1.2.1-47build1_amd64.deb) ...
Selecting previously deselected package sp.
Unpacking sp (from .../sp_1.3.4-1.2.1-47build1_amd64.deb) ...
Selecting previously deselected package docbook-utils.
Unpacking docbook-utils (from .../docbook-utils_0.6.14-1_all.deb) ...
Selecting previously deselected package docbook-xsl.
Unpacking docbook-xsl (from .../docbook-xsl_1.73.2.dfsg.1-2_all.deb) ...
Selecting previously deselected package kernel-wedge.
Unpacking kernel-wedge (from .../kernel-wedge_2.29ubuntu2_all.deb) ...
Selecting previously deselected package sharutils.
Unpacking sharutils (from .../sharutils_1%3a4.6.3-1build1_amd64.deb) ...
Selecting previously deselected package transfig.
Unpacking transfig (from .../transfig_1%3a3.2.5-rel-3_amd64.deb) ...
Selecting previously deselected package xmlto.
Unpacking xmlto (from .../xmlto_0.0.18-5.1build1_amd64.deb) ...
Setting up gawk (1:3.1.6.dfsg-0ubuntu1) ...

Setting up cpp (4:4.2.3-1ubuntu5) ...

Setting up linux-libc-dev (2.6.24-17.31) ...
Setting up libc6-dev (2.7-10ubuntu3) ...
Setting up gcc (4:4.2.3-1ubuntu5) ...

Setting up libtimedate-perl (1.1600-9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.16.6ubuntu3) ...
Setting up html2text (1.3.2a-3build2) ...

Setting up gettext (0.17-2ubuntu1) ...

Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up po-debconf (1.0.10) ...

Setting up debhelper (6.0.4ubuntu1) ...
Setting up libosp5 (1.5.2-3ubuntu3) ...

Setting up libostyle1c2 (1.4devel1-18build1) ...

Setting up openjade (1.4devel1-18build1) ...

Setting up docbook-dsssl (1.79-5) ...

Setting up tex-common (1.10) ...

Creating config file /etc/texmf/texmf.d/05TeXMF.cnf with new version

Creating config file /etc/texmf/texmf.d/15Plain.cnf with new version

Creating config file /etc/texmf/texmf.d/45TeXinputs.cnf with new version

Creating config file /etc/texmf/texmf.d/55Fonts.cnf with new version

Creating config file /etc/texmf/texmf.d/65BibTeX.cnf with new version

Creating config file /etc/texmf/texmf.d/75DviPS.cnf with new version

Creating config file /etc/texmf/texmf.d/85Misc.cnf with new version

Creating config file /etc/texmf/texmf.d/90TeXDoc.cnf with new version

Creating config file /etc/texmf/texmf.d/95NonPath.cnf with new version

Creating config file /etc/texmf/updmap.d/00updmap.cfg with new version

Creating config file /etc/texmf/texmf.cnf with new version

Setting up texlive-common (2007-13) ...

Setting up texlive-doc-base (2007-3) ...
Running mktexlsr. This may take some time... done.

Setting up texlive-base-bin (2007.dfsg.1-2) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all.
	This may take some time... done.

Setting up texlive-base (2007-13) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all.
	This may take some time... done.
Running updmap-sys. This may take some time... done.

Setting up texlive-fonts-recommended (2007-13) ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.

Setting up texlive-latex-base (2007-13) ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.
Building format(s) --all --cnffile /etc/texmf/fmt.d/10texlive-latex-base.cnf.
	This may take some time... done.

Setting up texlive-latex-recommended (2007-13) ...
Running mktexlsr. This may take some time... done.

Setting up tipa (2:1.3-10) ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.

Setting up jadetex (3.13-9) ...
Replacing config file /etc/texmf/texmf.cnf with new version
Running mktexlsr. This may take some time... done.
Building format(s) --all --cnffile /etc/texmf/fmt.d/40jadetex.cnf.
	This may take some time... done.

Setting up libsgmls-perl (1.03ii-31) ...
Setting up sgmlspl (1.03ii-31) ...
Setting up libsp1c2 (1.3.4-1.2.1-47build1) ...

Setting up sp (1.3.4-1.2.1-47build1) ...

Setting up docbook-utils (0.6.14-1) ...

Setting up docbook-xsl (1.73.2.dfsg.1-2) ...

Setting up kernel-wedge (2.29ubuntu2) ...
Setting up sharutils (1:4.6.3-1build1) ...

Setting up transfig (1:3.2.5-rel-3) ...

Setting up xmlto (0.0.18-5.1build1) ...
Setting up libstdc++6-4.2-dev (4.2.3-2ubuntu7) ...
Setting up g++-4.2 (4.2.3-2ubuntu7) ...
Setting up g++ (4:4.2.3-1ubuntu5) ...

Setting up build-essential (11.3ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
heavyp@heavyp-laptop:~$ sudo apt-get source linux-image-`uname -r`
[sudo] password for heavyp: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 63.5MB of source archives.
Get:1 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-proposed/main linux 2.6.24-17.31 (dsc) [2211B]
Get:2 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-proposed/main linux 2.6.24-17.31 (tar) [59.1MB]
Get:3 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-proposed/main linux 2.6.24-17.31 (diff) [4415kB]                                                                   
Fetched 63.5MB in 2h30min42s (7023B/s)                                                                                                                      
gpg: WARNING: unsafe ownership on configuration file `/home/heavyp/.gnupg/gpg.conf'
gpg: Signature made Wed 30 Apr 2008 03:58:07 AM ICT using DSA key ID 8BF9EFE6
gpg: Can't check signature: public key not found
dpkg-source: extracting linux in linux-2.6.24
dpkg-source: unpacking linux_2.6.24.orig.tar.gz
dpkg-source: applying ./linux_2.6.24-17.31.diff.gz
heavyp@heavyp-laptop:~$ cd desktop
bash: cd: desktop: No such file or directory
heavyp@heavyp-laptop:~$ cd Desktop
heavyp@heavyp-laptop:~/Desktop$ ls
iwlwifi-1.2.25.gz  mac80211-10.0.4
heavyp@heavyp-laptop:~/Desktop$ cd mac80211-10.0.4
heavyp@heavyp-laptop:~/Desktop/mac80211-10.0.4$ ls
CHANGES  FILES  Makefile  modified  origin  ORIGIN_FILES  patches  pending  post  pre  README  scripts  stubs  TODO
heavyp@heavyp-laptop:~/Desktop/mac80211-10.0.4$ make patch_kernel

WARNING: $SHELL not set to bash.

If you experience build errors, try 'make SHELL=/bin/bash'.

Kernel Makefile not found at '/lib/modules/2.6.24-16-generic/source/'
If patch or script failed, check pre/ and post/ for current stage.
make: *** [compatible/modified] Error 1
heavyp@heavyp-laptop:~/Desktop/mac80211-10.0.4$ 

---

### Post by HeavyP on 2008-05-24
I still got no sound after installing OSS 4.0

```
heavyp@heavyp-laptop:~$ sudo ossdetect -v
[sudo] password for heavyp: 
Detected Intel High Definition Audio (ICH8)
Detected Generic USB audio device (BETA)
Detected OSS Transparent Virtual Mixing Architecture
heavyp@heavyp-laptop:~$ sudo ossinfo
Version info: OSS 4.0 (b1015/200803240317) (0x00040003) 
Platform: Linux/x86_64 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 (heavyp-laptop)

Number of audio devices:	6
Number of audio engines:	14
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: hdaudio0 Intel HD Audio interrupts=1226 (1227)
    HD Audio controller Intel HD Audio
    Vendor ID    0x8086284b
    Subvendor ID 0x17aa384e
     Codec  0: ALC262 (0x10ec0262/0x17aa3837)
     Codec  1: Unknown (0x10573055)
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual mixer


Mixer devices
 0: High Definition Audio ALC262 (Mixer 0 of device object 1)

Audio devices
HD Audio speaker                  /dev/oss/hdaudio0/pcm0  (device index 0)
HD Audio headphone                /dev/oss/hdaudio0/pcm1  (device index 1)
HD Audio spdif-out                /dev/oss/hdaudio0/spdout0  (device index 2)
High Definition Audio rec1        /dev/oss/hdaudio0/pcmin0  (device index 3)
High Definition Audio rec2        /dev/oss/hdaudio0/pcmin1  (device index 4)
High Definition Audio rec3        /dev/oss/hdaudio0/pcmin2  (device index 5)
heavyp@heavyp-laptop:~$ 

```

---

### Post by HeavyP on 2008-05-26
I will try this later on the next version....

Give up! Switching to Windows

---

