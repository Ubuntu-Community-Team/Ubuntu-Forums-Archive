---
title: "Upgrade questions, 32-bit to 64-bit"
date: 2007-11-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by c-m on 2007-11-14
Hi,

I am about to upgrade from an old XP2500 to a C2D system. As such I was considering running Ubuntu 64-bit instead of the 32-bit operating system.

My questions in upgrading is:

1) will i still have access to the large amount of software I did previously in the reposetories? In particular VLC, firefox, Openoffice, amarok etc..

2) Is all the hardware supported in the 32-bit kernal currently supported in the 64-bit system? I'm concerned that I will loose the use of my Nexus-S dvb-s card.

---

### Post by John.Michael.Kane on 2007-11-14
> **c-m said:**
> Hi, I am about to upgrade from an old XP2500 to a C2D system. As such I was considering running Ubuntu 64-bit instead of the 32-bit operating system.
I will try to answer your questions as best possible

> **c-m said:**
> My questions in upgrading is:
1) will i still have access to the large amount of software I did previously in the repositories? In particular VLC, firefox, Openoffice, amarok etc..
Yes there should be no issue finding the same apps you used under 32bit. As for the apps you listed look below.

[vlc]("http://packages.ubuntu.com/gutsy/graphics/vlc") Architecture available amd64
[firefox]("http://packages.ubuntu.com/gutsy/web/firefox") Architecture available amd64
[openoffice]("http://packages.ubuntu.com/gutsy/editors/openoffice.org") Architecture available amd64
[amarok]("http://packages.ubuntu.com/gutsy/kde/amarok") Architecture available amd64

> **c-m said:**
> 2) Is all the hardware supported in the 32-bit kernel currently supported in the 64-bit system? I'm concerned that I will loose the use of my Nexus-S dvb-s card.
Most hardware supported under the 32bit kernel should have the same support under the 64bit kernel. 

You may also want to read the thread below.
[Please Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

Hope this helps.

---

### Post by dezoete on 2007-11-14
Hi

I'm a newbee, but my experience is as follows:

Computer: AMD64 dual 2G with XP 

I tried Ubuntu 7.10 64bit, but had problems running my windows 32 bit programs
I changed to  7.10 32bit version, and had no problems. and no change in speed

Advice: Don't use 64bit version.

---

### Post by John.Michael.Kane on 2007-11-14
> **dezoete said:**
> Hi

I'm a newbee, but my experience is as follows:

Computer: AMD64 dual 2G with XP 

I tried Ubuntu 7.10 64bit, but had problems running my windows 32 bit programs
I changed to  7.10 32bit version, and had no problems. and no change in speed

Advice: Don't use 64bit version.

You can't tell someone a particular architecture should not be used because of "problems" you may have had on your particular hardware. 

Their hardware setup might be completely different then yours thus their problems if any would be either none or different, and in this case the OP is planing on running Intel hardware thus his setup might fall into the category of  no problems or different problems

Also I take it you asked for help in this section of the forum. regarding any issues you have had with 64bit?

---

### Post by c-m on 2007-11-14
I don't have any specific reason to run 64-bit over 32-bit, but if I am going to run 64-bit i'd rather do it now, since i'll be doing a fresh install anyway.


I will be running the following hardware:

C2D E6300 1.8ghz
2gb ddr
Ausus P5B mothboard (on board sound, sata etc..)
Nvdia Geforce 6200    (to be upgraded to an ATI HD 2600)
22" LCD monitor 1680x1050
Nexus-s DVB-S card for recieving satellite


In addition to the software I mentioned I also need regular use of GIMP and Scribus

---

### Post by John.Michael.Kane on 2007-11-14
> **c-m said:**
> I don't have any specific reason to run 64-bit over 32-bit, but if I am going to run 64-bit i'd rather do it now, since i'll be doing a fresh install anyway.


I will be running the following hardware:

C2D E6300 1.8ghz
2gb ddr
Ausus P5B mothboard (on board sound, sata etc..) 
Nvdia Geforce 6200    (to be upgraded to an ATI HD 2600)
22" LCD monitor 1680x1050
Nexus-s DVB-S card for recieving satellite


In addition to the software I mentioned I also need regular use of GIMP and Scribus

[scribus]("http://packages.ubuntu.com/gutsy/graphics/scribus") Architecture available amd64
[gimp]("http://packages.ubuntu.com/gutsy/graphics/gimp") Architecture available amd64

Looking over the above hardware, and doing a forum search there where users who had issues with the p5b with regards to the on-board audio, and usb.
[http://ubuntuforums.org/showthread.php?p=3607822&highlight=P5B#post3607822](http://ubuntuforums.org/showthread.php?p=3607822&highlight=P5B#post3607822)
[http://ubuntuforums.org/showpost.php?p=3006497&postcount=24](http://ubuntuforums.org/showpost.php?p=3006497&postcount=24)
[http://ubuntuforums.org/search.php?searchid=31254581](http://ubuntuforums.org/search.php?searchid=31254581)

Note: I'm not sure if Gutsy kernel has resolved the issues above. So you might want to take the above issues into account if you are planing on buying the p5b.

The Geforce 6200 is supported.

The  ATI HD 2600 is unknown, and most forum members would tell you that ati can be a pain to get working properly.

C2D E6300 1.8ghz Should be seen fine by the kernel.

2gb ddr Should be recognized without issue.

22" LCD monitor 1680x1050 You should have no issues getting xorg to run at the resolution.

Also further searching regarding the Nexus-s DVB-S seems to bring up at least one Ubuntu forums member who has it working.
[http://www.uluga.ubuntuforums.org/showpost.php?p=651429&postcount=263](http://www.uluga.ubuntuforums.org/showpost.php?p=651429&postcount=263)

Hope this helps.

---

### Post by c-m on 2007-11-14
my search has shown mixed results regarding the P5B in ubuntu. 

I already have the board so, will giv eit a shot, if not its only 30mins or so to reinstall.

Thanks

---

### Post by Yellow Pasque on 2007-11-14
> **dezoete said:**
> I'm a newbee, 
I tried Ubuntu 7.10 64bit, but had problems running my windows 32 bit programs
I changed to  7.10 32bit version, and had no problems. and no change in speed

Advice: Don't use 64bit version.
The solution was probably something simple like installing the ia32-libs package. Pleae don't come into the 64-bit forum, claim to be a n00b, and then advise people not to use a 64-bit distro. We have enough of the 64-bit FUD on these forums.

Thanks.

---

### Post by vuco on 2007-11-14
> **c-m said:**
> Hi,

1) will i still have access to the large amount of software I did previously in the reposetories? In particular VLC, firefox, Openoffice, amarok etc..



I have an Ubuntu 64bit box. When I was using Feisty, I couldn't run Flash inside Firefox. I tried
many tricks, including editing configuration files by hand with no success. I googled until
I find one solution: download a 32bit Firefox and install Flashplayer on it. This solved my
problem. Now I upgraded to Gutsy 64bit. Flash still didn't install on Firefox. I didn't tried hard
to solve the problem with the 64bit Firefox, I just download the 32bit FF and installed Flash.

So if someone knows how to run a 64bit Firefox with the Flashplayer plugin please, tell us.

Luis Otavio Furquim

---

### Post by rsambuca on 2007-11-14
If you are using Gutsy, then you have three easy methods of installing the Flash plugin with the 64bit Firefox:

1.  Go to a site that uses Flash.  You will be prompted to install the flash plugin.  Select "yes".
2.  Open a terminal and enter 'sudo apt-get install flashplugin-nonfree'.  You may have to enable your universe and multiverse repositories first.
3.  Open Synaptic Package Manager and select 'flashplugin-nonfree'.  Press 'apply' to install.

---

### Post by Random-penguin on 2007-11-14
I would encourage you to at least have a go with the 64-bit install and see how far you get...especially if you're doing a fresh install. I went for the plunge last night and everything I need seems to work (including nvidia graphics compiz dvd playback and google earth) :)

---

