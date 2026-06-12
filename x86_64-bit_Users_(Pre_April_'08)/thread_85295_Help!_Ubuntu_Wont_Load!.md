---
title: "Help! Ubuntu Wont Load!"
date: 2005-11-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by nlella89 on 2005-11-02
first let me say.

Kudos to ubuntu, i thought i would get through this with no problems for installtion (and i did, it just wont start up)



k, when i start my computer, it shows the ubuntu logo and says loding everything and after the bar reaches the top, i get an ms dos type error that says could not start Xserver (your Graphical User Interface)

and i went in and saw what was wrong. heres what it gave me (please excuse typos, i did this by hand)

Window System Version 6.8.2(Ubuntu 6.8.2-77 2005101017489 root @ crested.warthogs.hbd.com.
Release Date 9 Feb 2005-7                       F]
X Protocol version 11, Revision 0, Release 6.8.2
Build OS: Linux 2.6.8.1 X86_64 [ELF]
Current OS:Linux Ubuntu 2.6.12-9-amd64-generic #1 Mon Oct 10 13:27:39 BST 2005 X86_64

Module Loader Present
OS Kernel: Linux ver 2.6.12-9-amd64-generic (buldd@king)(gcc version 3.4.5 20050809 (prerelease)(ubuntu 3.4.4-6ubuntu 8)) #1 Mon Oct 10 13:27:39 BST 2005

it shows the markers (didnt copy thoes down..)

(==)Log file:"/var/log/xorg.0.log" Time wed 2 nov 2 7:52:58
(==)Using Config file:"/etc/x11/xorg.conf"
Skipping
"usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o": no symbol found
Skipping
"usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o": no symbol found
Skipping
"usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o": no symbol found
(EE)no devices found
Fatal server error: no screens found




i would appriciate it if someone would help. heres some background info

ATI RADEON X700
Seagate 80GB barracuda
Chaintech nForce4 (integrated network it was detected)
NEC CD/DVD drive
Corsair 2GB ram
AMD ATHALON64 300+

everythings custom built.


when i tried to partition, i did it manually and heres what i did
60GB /  (this is the root)
100MG /boot bootable (Do i even need this, i tried it without it and the same error occured)
3.3GB /swap swap area (it wouldnt let me do 4GB :( i hope its okay and my ram wont go over and cause lag because of not enough swap area)

and when it asks what size i want to use, i select 1024X768 or whatever that size is.

i already did sudo dpkg-reconfigure xserver-xorg and i still had that error.

i would appriciate any help

---

### Post by Teroedni on 2005-11-02
Write

sudo nano /etc/X11/xorg.conf

You get a text file
Scrool down to where it stands section device
and then you se a subsection driver     "xxx"     i write xxx since i dont know what you hav there. SAnyway remove whatever stands there and put in either ati or vesa

after you done that
press ctrl+0 
thebn you save your file

---

### Post by Teroedni on 2005-11-02
Then restart and you should be able to get into Ubuntu
and then its get easier to fix the problem(i guess you want 3d)

---

### Post by jvictor on 2005-11-02
It maybe easier if you could post ur machine config, at least graphics card, and mobo..

---

### Post by queenorych on 2005-11-02
What video driver are you using?  I know if you install nvidia's driver using their installer it writes over files it should not.  ATI is probably worse.  Anyway try reinstalling the problamatic files
something like
apt-cache -S usr/X11R6/lib/modules/extensions/libGLcore.a
apt-get install (flag to reinstall) "package found above"

either that or pul out aptitude and reinstall the entire X system.

---

### Post by nlella89 on 2005-11-02
[QUOTE=Teroedni]Write

sudo nano /etc/X11/xorg.conf

You get a text file
Scrool down to where it stands section device
and then you se a subsection driver     "xxx"     i write xxx since i dont know what you hav there. SAnyway remove whatever stands there and put in either ati or vesa

after you done that
press ctrl+0 
thebn you save your file[/QUOTE]


umm. it opens something thats totally blank



[QUOTE=jvictor]It maybe easier if you could post ur machine config, at least graphics card, and mobo..[/QUOTE]


what?



[QUOTE=queenorych]What video driver are you using?  I know if you install nvidia's driver using their installer it writes over files it should not.  ATI is probably worse.  Anyway try reinstalling the problamatic files
something like
apt-cache -S usr/X11R6/lib/modules/extensions/libGLcore.a
apt-get install (flag to reinstall) "package found above"

either that or pul out aptitude and reinstall the entire X system.[/QUOTE]

didnt work

whats aptitude and how do i reinstall the entire x system?

---

### Post by ToastedToad on 2005-11-02
$ sudo dpkg-reconfigure xserver-xorg

Make sure you have the horizontal and verticle refresh rates for your monitor, select the proper video driver, and just answer the questions as well as you can. If you are not sure, then select the default answer.  It should get you really close.

---

### Post by Teroedni on 2005-11-03
[QUOTE=nlella89]umm. it opens something thats totally blank

sudo nano /etc/X11/xorg.conf

Make sure to writeX11 not x11
It is case sesitive

---

### Post by nlella89 on 2005-11-03
[QUOTE=Teroedni][QUOTE=nlella89]umm. it opens something thats totally blank

sudo nano /etc/X11/xorg.conf

Make sure to writeX11 not x11
It is case sesitive[/QUOTE]


i am....

---

### Post by korakde on 2005-11-05
Hi all,
I am having the exact same problem as nella. Has anyone got any further with diagnosing the problem. My config:
AMB64, 3000+ 939pin
Motherboard: MSI RS482M2-IL with integrated ATI Radeon Xpress200 graphics

---

### Post by skylark on 2005-11-05
/etc/X11/xorg.conf should exist. What does "ls -la /etc/X11/xorg.conf" result in? 

If you get a "No such file or directory" response then something has gone horribly wrong... otherwise you should be able to follow the directions Teroedni gave you (or ToastedToad's advice should also work).

---

### Post by Elendil on 2005-11-05
It is really good to get advice from all you guys, but....is there actually someone out there with a PCI-E based ATI card, that got UBUNTU 5.10 to start up correctly I wonder?
If so how about helping us out here? It appears very much like the issue at hand affects ALL ATI X-hundred cards. I myself own a X800XT and have the exact same problems.
Help is more than needed.....


Mark

---

### Post by Teroedni on 2005-11-06
OK i gues that you tried a live cd before install?
If not .Can you burn a live boot cd .
you find them here [http://se.releases.ubuntu.com/5.10/](http://se.releases.ubuntu.com/5.10/)

Then boot with the live cd

We should then be able to extract more information from xorgs logs and such.
Hope thats sounds ok

---

### Post by skylark on 2005-11-06
[QUOTE=Elendil]It is really good to get advice from all you guys, but....is there actually someone out there with a PCI-E based ATI card, that got UBUNTU 5.10 to start up correctly I wonder?
If so how about helping us out here? It appears very much like the issue at hand affects ALL ATI X-hundred cards. I myself own a X800XT and have the exact same problems.
Help is more than needed.....
[/QUOTE]
I'm running Ubuntu 5.10 on an AMD64 machine with a "Gigabyte ATI Radeon X300SE RX30S128D 128MB PCI-Express DVI/D-Sub TV-Out" card (yes low range, but I'm cheap, it's fanless and I don't play games). I've had no real problems with it at all (nor in 5.04).

---

### Post by uniko on 2005-11-06
I had  the same problem as there were no xorg.conf after install. I have an agp ati 9600xt btw, so it&#347; not limited to pci-e cards. I solved the problem by doing

```
sudo apt-get reinstall xserver-xorg

sudp dpkg-reconfigure xserver-xorg
```

I chose ati drivers at this time, I installed fglrx drivers later. Hope this helps.

---

### Post by Aphorism on 2005-11-12
Teroedni has already posted the solution here, and it is the one with the least amount of problems.  As far as I know, the ONLY solution for this is to switch the driver to "vesa", and not use the "ati" driver without turning off accelleration.

In this case, judging from the level of the poster, Toroedni's suggestion is probably the easiest...


Click APPLICATIONS->ACCESSORIES->TERMINAL

In the terminal, type:

sudo gedit /etc/X11/xorg.conf

Click SEARCH->FIND and type "ati".  It should find a line that looks like this...

Driver		"ati"

Simply change the "ati" to "vesa" and reboot.


Good luck.

---

### Post by ThiAm on 2005-11-14
Hi,

I encountered exactly the same frustrating issue "No screen found" error message on a awfull grey screen... and I solved it by implementing Teroedni's proposed solution... I run Ubuntu on a AMD64 - Sempron 1600 MHz.

Thanks a lot for effective support ! :D

---

### Post by cpinfdp on 2005-11-14
I tried the live cd of Ubuntu and Kubuntu, niether of which would load Xserver.  I am running a X700 .  I have also tried to reconfigure the Xserver to use vesa, vga, ati, but it doesn't start after the reconfiguration.  

I have seen a fix where they have a 'patch' of PCI Id's for the new ATI cards, but I was hoping that their might be a modifier to the live command that would let me at least load it and try it.

---

### Post by victor_c26 on 2005-11-23
[QUOTE=cpinfdp]I was hoping that their might be a modifier to the live command that would let me at least load it and try it.[/QUOTE]

This is what I want to know. I've been trying to boot Ubuntu for a while with the live cd, but most (if not all) advice on the forums is for the install.

Is there anyway one can load Ubuntu with a live cd? VESA pre-load command? Anything?

---

### Post by jluquette on 2005-11-28
I get the exact same error message too.  I tried that reinstall X thing and it didn't work for me either.  BTW, it happens with either Live or Install.
See my response to Korakde here: [http://www.ubuntuforums.org/showthread.php?p=526294#post526294](http://www.ubuntuforums.org/showthread.php?p=526294#post526294)

I'm using a new GigaByte GA-K8N51GMF-9 (mATX) MB with onboard NVidea GeForce graphics and no extra add-on video card (no add-on cards at all actually).
AMD 64 3700+ CPU
1 GB Corsair memory
19" ViewSonic vm910 LCD monitor

---

### Post by trilliji on 2006-03-25
I've been seeing this ubuntu error forever, just replace the "ati" driver with "radeon" in the xorg.conf and everything will work fine. Then you can install the fglrx driver at your leisure.

---

