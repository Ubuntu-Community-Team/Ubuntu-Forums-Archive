---
title: "Installing Flash Player on Ubuntu 7.10"
date: 2008-11-24
forum: x86 64-bit Users
---

### Post by theemperor on 2008-11-24
Hi I am using Ubuntu 7.10. Since I will be consuming lot of Flash content as part of my job, I need to install flash player. Pls suggest how to install flash player in my machine. 

I am not a techie. Hence pls help me on this

Thanks

Bijoy

---

### Post by __Ryan__ on 2008-11-24
Open a terminal and enter the following:
```

sudo aptitude install flashplugin-nonfree
```

---

### Post by chunchengch on 2008-11-24
[COLOR="Red"]$ sudo apt-get install flashplugin-nonfree[/COLOR]

---

### Post by theemperor on 2008-11-24
Hi,

I have tried Both sudo aptitude install flashplugin-nonfree and sudo apt-get install flashplugin-nonfree.

Following is the error messege. I have downloaded .tar.gz and .deb version of flash player. Where do i need to keep this files...?

user@user-desktop:~$ sudo aptitude install flashplugin-nonfree
[sudo] password for user:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "flashplugin-nonfree"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done    
  
user@user-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree
user@user-desktop:~$ 

Thanks

Bijoy

---

### Post by chunchengch on 2008-11-24
[COLOR="Red"]$ sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
$ sudo apt-get install flashplugin-nonfree[/COLOR]

---

### Post by theemperor on 2008-11-24
Hi, I tried and installed all the packages and ran Install command.

It still says the package is not found.

Following is the error.
=============================================================
user@user-desktop:~$ sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
[sudo] password for user:
--18:11:09--  [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 223 [text/plain]

100%[====================================>] 223           --.--K/s             

18:11:10 (44.22 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [223/223]

user@user-desktop:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_IN
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_IN
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_IN
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release [11.7kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release          
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages [8541B]
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages [3154B]           
Fetched 23.6kB in 5s (4651B/s)                           
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3494B of archives.
After unpacking 49.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Install these packages without verification [y/N]? y
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free medibuntu-keyring 2008.04.19 [3494B]
Fetched 3494B in 0s (6011B/s)           
Selecting previously deselected package medibuntu-keyring.
(Reading database ... 88046 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.19_all.deb) ...
Setting up medibuntu-keyring (2008.04.19) ...
OK

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_IN
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_IN
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_IN
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Fetched 189B in 2s (80B/s)
Reading package lists... Done
user@user-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree

===================================================================

---

### Post by __Ryan__ on 2008-11-24
I believe that the flash-plugin is in the multiverse which you have to have enabled.

System -> Administration -> Software Sources

Select the multiverse checkbox and then try installing the plugin again.

---

### Post by theemperor on 2008-11-24
Hi, I have selected the Multiverse checkbox and ran the command.

This is the result.

=================================================================
user@user-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: nspluginwrapper (>= 0.9.91.4-2ubuntu1) but it is not going to be installed
E: Broken packages

==========================================================================

---

### Post by zionstation on 2008-11-24
Hi,I'm not sure whether this is too late for or not. 
You'd go to: 
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Adobe Flash Player

Adobe Flash Player Logo
Download Adobe Flash Player
Adobe Flash Player
Linux, x86

Different operating system or browser?

Browser: Firefox, Mozilla, Seamonkey

Learn more | System requirements | Distribute Flash Player | Installation instructions

Adobe Flash Player version 10.0.12.36
.tar.gz for Linux (x86) | 3.7MB

Download time estimate: 5 minutes @ 56K modem

Agree and install now

By clicking the "Agree and install now" button,
you agree to the Software License Agreement.

Adobe Flash Player version 10.0.12.36
.rpm for Linux (x86) | 3.8MB

Download time estimate: 5 minutes @ 56K modem

Agree and install now

By clicking the "Agree and install now" button,
you agree to the Software License Agreement.

Adobe Flash Player version 10.0.12.36
YUM repository definition | 4KB

Download time estimate: 1 minutes @ 56K modem

Agree and install now

By clicking the "Agree and install now" button,
you agree to the Software License Agreement.

Adobe Flash Player version 10.0.12.36
.deb for Ubuntu 8.04+ | 3.8MB

Download time estimate: 5 minutes @ 56K modem

Agree and install now

By clicking the "Agree and install now" button,
you agree to the Software License Agreement.

---

### Post by theemperor on 2008-11-24
Hi, 

I have download these from Adobe and tried. My machine is x86 64 architecure and Flash player 10 doesn't support 64 bit i believe. Is there any alternative?

Thanks

Bijoy

---

### Post by chunchengch on 2008-11-24
[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by aysiu on 2008-11-24
You can follow these instructions to install Flash 10 for 64-bit:
[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install)

---

### Post by theemperor on 2008-11-24
Thanks a lot. This was really helpful for me

Bijoy

---

### Post by keenboy on 2009-01-28
Flash player simply doesn't work on 7.10!!

I have tried every possible method with no luck. It work great on 8.04, not like that's any help though.

---

