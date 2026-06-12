---
title: "gutsy 7.10 AMD64 install hangs"
date: 2008-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by gunninks on 2008-01-22
I am trying to install gutsy amd64 and my system hangs after i choose to run the live cd, it says loading kernel and the screen goes blank, keyboard does not responed. 
I have tried using the safe graphics mode aswell as the alternate cd.
mdsum says the download is fine also i have tried multiple cd's.

fyi 32bit gutsy works just fine.

my rig is as follows:
AMD64 3200
Asus A8N-E
2gig dual chanel corsar ram
ATI Pci-E x700 pro
2 seagate 120gig pata
1 WD 200gig sata2

If there is any other info needed to help me solve please tell me.

I would just run the 32bit however i want to try and get the best performance posible.

Thanks.

---

### Post by Perfect Storm on 2008-01-22
Maybe this is your problem (+solution) [http://ubuntuforums.org/showthread.php?t=672603&highlight=blank+screen](http://ubuntuforums.org/showthread.php?t=672603&highlight=blank+screen)

---

### Post by prince_niceguy on 2008-01-22
seems there is some issue with the ati cards and live cd... i used alternate cd to install and it worked smoothly.... try that out... it is not that difficult and instead of graphical installer you will be inputting everything through keyboard... quite easy...

---

### Post by XplOzIOn on 2008-01-22
> **gunninks said:**
> I am trying to install gutsy amd64 and my system hangs after i choose to run the live cd, it says loading kernel and the screen goes blank, keyboard does not responed. 
I have tried using the safe graphics mode aswell as the alternate cd.
mdsum says the download is fine also i have tried multiple cd's.

fyi 32bit gutsy works just fine.

my rig is as follows:
AMD64 3200
Asus A8N-E
2gig dual chanel corsar ram
ATI Pci-E x700 pro
2 seagate 120gig pata
1 WD 200gig sata2

If there is any other info needed to help me solve please tell me.

I would just run the 32bit however i want to try and get the best performance posible.

Thanks.

Yes there is a problem with Ubuntu live CD and 64Bit and ATI cards. My screen went blank too, it wasent reading the CD or anything. Just blank window. I rebooted and choosed the option to check if the CD was OK, it hanged for like 10 minutes (BLACK SCREEN) and then it continued loading the Live session. After that it installed without any problems!

Maybe theres something wrong with 64Bit and ATI cards that makes the Live CD dumb??

---

### Post by ubun_two on 2008-01-22
I am experiencing a similar issue, but I don't use ATI card.  

I can make it work under 32bit, but it does complain about video card after going through grub initially, and goes into vga mode (until I manually install driver).

My machine:
Intel Quadcore (Q6600)
Abit IP35 Pro Mobo
512MB nVidia 8800GT
4GB RAM (Geil 4x1GB)
2 SATA HD (400GB + 500GB) - one is Seagate, other is Western Digital

---

### Post by XplOzIOn on 2008-01-22
I believe is mostly a combination of HARDWARE that causes this random black screen.

For people having this problem ill suggest using Alternate CD

---

### Post by gunninks on 2008-01-23
Thank you for everyones input. I will try and work some more on this in the coming days but as for right now i haven't the time. There has been a tragedy in the family so please dont think i have not followed through with your suggestions. Thank you for your time and i will let everyone know my progress.

As to the previous poster telling me to try the alt install cd, i have and it didnt work. I will look over all the suggestions and try each of them until we come up with a fix.

---

### Post by gambrjl on 2008-01-23
Is pretty much everyone with an ATI card having the blank screen with the Live CD problems?  or is it intermittent?

I'm putting together a new rig tonight with a Quad Core Q660, Asus P5k mobo and an ATI 2500HD graphics card.  Should I even try the live CD or just go directly to the alternate??  I don't mind text based installs, just curious

---

### Post by Haister on 2008-01-23
I pretty much had the same problem with the live install with ATI graphic card.  I downloaded and burned a DVD installation disk which is about 4 gig and the install went without a hitch!

---

### Post by gambrjl on 2008-01-23
> **Haister said:**
> I pretty much had the same problem with the live install with ATI graphic card.  I downloaded and burned a DVD installation disk which is about 4 gig and the install went without a hitch!

DVD installation disk??  meaning you burned the 700M install iso to a DVD disk instead of a CD-R and it worked?

---

### Post by Haister on 2008-01-23
no 4gig image, this is pretty much the full blown software! the link is below.

[http://ubuntu-cdimage.datahop.it/releases/gutsy/release/](http://ubuntu-cdimage.datahop.it/releases/gutsy/release/)

---

### Post by gambrjl on 2008-01-23
> **Haister said:**
> no 4gig image, this is pretty much the full blown software! the link is below.

[http://ubuntu-cdimage.datahop.it/releases/gutsy/release/](http://ubuntu-cdimage.datahop.it/releases/gutsy/release/)

Oh.. cool, thanks.  I'll keep that in mind

---

### Post by wedesoft on 2008-01-23
After hours of installation nightmare I got my ATI PCI-Express AX700 LE working on an AMD64 (Biostar iDeq Shuttle PC). Using the **old** ATI driver did the trick for me. I installed the driver according to reference [1] (see below).
It was not a straightforward process for me, but I guess I could have done it like this:
[list]
[*]Boot graphically
[*]Change *splash* to *nosplash* in **/boot/grub/menu.lst** to avoid blank screens
[*]remove kdm from boot process (using program **serviceconfig**)
[*]Download **ati-driver-installer-8-01-x86.x86_64.run** from here: [http://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-01-x86.x86_64.run"]https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-01-x86.x86_64.run](http://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-01-x86.x86_64.run"]https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-01-x86.x86_64.run)
[*]Install some build-tools: *sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms*
[*]Build the packages: *sh ati-driver-installer-8-01-x86.x86_64.run --buildpkg Ubuntu/gutsy*
[*]I am not sure wether *DISABLED_MODULES="fglrx"* in **/etc/default/linux-restricted-modules-common** is really needed (as explained in reference [1])
[*]Install the packages: *sudo dpkg -i xorg-driver-fglrx_8.452.1-1*.deb fglrx-kernel-source_8.452.1-1*.deb fglrx-amdcccle_8.452.1-1*.deb*
[*]Run *sudo aticonfig --initial*
[*]Run *sudo aticonfig --overlay-type=Xv*
[*]Edit **/etc/X11/xorg.conf**
```

Section "Device"
	[...]
#       Driver          "ati"
	Driver		"fglrx"
	Option		"VideoOverlay"		"on"
	Option		"OpenGLOverlay"		"off"
	[...]
EndSection
[...]
Section "Extensions"
	Option	"Composite"	"Enable"
	Option	"XVideo"	"Enable"
EndSection

```
[*]After rebooting you need to manually start X11 (*startx*) or kdm (*/etc/init.d/kdm start*)
[*]I have installed *compiz* and I can start it from within X11: *compiz --replace*. You need to change the whitelist and blacklist as explained in reference [1].
[*]Unfortunately XVideo does not seem to run. For playing videos I either need to kill *compiz* (*killall compiz.real && sleep 3 && ( kwin & )*) or run the respective player using X11-output (e.g. *mplayer -vo x11 -zoom ...* or *xine -V xshm ...*)
[/list]
I hope I haven't forgotten any step. I tried so many things. Check the reference below for further information.
It's still not perfect (XVideo problems) and once I have entered graphics mode I cannot restore text-mode any more (blank screen).

[list=1]
[*][http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually)
[/list]

**Update:** I now have problems building and running programs which are using libc++-6 and OpenGL. The old ATI driver is linked against libc++-5 and this causes conflicts. If anyone knows an easy fix, please let me know.

**Update:** I have tested the next driver version (ati-driver-installer-8-02-x86.x86_64.run) and it has the same issue since it also links against libc++-5

---

