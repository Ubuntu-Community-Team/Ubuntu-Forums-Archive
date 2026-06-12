---
title: "[SOLVED] Radeon HD 2400"
date: 2008-10-25
forum: x86 64-bit Users
---

### Post by Sponzenbroekske on 2008-10-25
Laptop Asus F8P
ATI RADEON HD 2400
Ubuntu 8.10 64bit
driver location: [http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

I want to install the driver for my video card.

```
yannick@asus:~/Desktop$ sh at*
Created directory fglrx-install.B16316
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.542...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................                                         
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.27-7-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.B16316 
```

As you can see I get an error, but I don't know hwo to solve it.

```
yannick@asus:~/Desktop$ lspci                     
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)      
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)         
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)         
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)         
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)         
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)         
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)                         
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)       
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)  
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
**[COLOR="Red"]01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400[/COLOR]**
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
08:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:03.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
08:03.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:03.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

```
yannick@asus:~/Desktop$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
yannick@asus:~/Desktop$ modprobe -v fglrx


```

If you want more info just ask :)

---

### Post by CowzRule on 2008-10-25
I used the following website for instructions on how to install those drivers.
[Installing the restricted drivers manually]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually")

---

### Post by jocko on 2008-10-26
> **Sponzenbroekske said:**
> Laptop Asus F8P
ATI RADEON HD 2400
Ubuntu [COLOR=Red]8.10[/COLOR] 64bit
driver location: [COLOR=Red][http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)
[/COLOR] 
I want to install the driver for my video card.



The driver on ATI's website does not work with the xorg version in intrepid.
Just use the restricted driver manager (System --> Administration --> Hardware drivers).
The driver in the intrepid repos is actually a beta version of ati's next release (8.11) and is the only driver that supports xorg 7.4.

---

### Post by Sponzenbroekske on 2008-10-26
> **CowzRule said:**
> I used the following website for instructions on how to install those drivers.
[Installing the restricted drivers manually]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually")

Worked like a charm :) Got it up and working in 5 min :) Thank You!

EDIT: And now I see, the title "installing ... Manually", I did it the ubuntu way, I hope this won't give any problems.

---

### Post by Sponzenbroekske on 2008-10-26
> **jocko said:**
> 
Just use the restricted driver manager (System --> Administration --> Hardware drivers).


That was the problem I had no driver there. But it is solved. Anyway thanks for your effort, its really appreciated :)

---

### Post by Zetheroo on 2008-11-07
> **Sponzenbroekske said:**
> Worked like a charm :) Got it up and working in 5 min :) Thank You!

EDIT: And now I see, the title "installing ... Manually", I did it the ubuntu way, I hope this won't give any problems.

So does that mean that the ATI drivers work in Intrepid?

---

### Post by Sponzenbroekske on 2008-11-10
> **Zetheroo said:**
> So does that mean that the ATI drivers work in Intrepid?

Yes it is up and running :), at least the driver for my card.

---

### Post by apollyon0810 on 2008-11-15
I have a Toshiba Satellite laptop with a Mobility Radeon HD 2400.  I have no problems with getting the driver to work with Ubuntu's restricted drivers manager.  I guess the only issue I suffer from is poor performance.  Compiz-Fusion works fine and all that, but it's just really laggy.  I dual boot Vista and Ibex.  Vista is NOTICEABLY faster.  Is this just an issue with the ATI chipset?  I know the Mobility HD2400 has some sort of "shared" video memory.  Does the Linux driver not take advantage of this?  Is there some sort of work-around?  I'd love to use Linux, but I just can't stand the slow performance.

Laptop is A215-S7472.

---

### Post by Sponzenbroekske on 2008-11-16
> **apollyon0810 said:**
> I have a Toshiba Satellite laptop with a Mobility Radeon HD 2400.  I have no problems with getting the driver to work with Ubuntu's restricted drivers manager.  I guess the only issue I suffer from is poor performance.  Compiz-Fusion works fine and all that, but it's just really laggy.  I dual boot Vista and Ibex.  Vista is NOTICEABLY faster.  Is this just an issue with the ATI chipset?  I know the Mobility HD2400 has some sort of "shared" video memory.  Does the Linux driver not take advantage of this?  Is there some sort of work-around?  I'd love to use Linux, but I just can't stand the slow performance.

Laptop is A215-S7472.

Funny , I never had poor performance, maybe you should try Hardy Heron. That will give you less trouble.
And else you can try Xubuntu with a ligther desktop-manager. I've heard that compiz is possible without any problems on XFCE4.
And there's a bigger Linux-world then Ubuntu :).

Vista faster then ubuntu, I've never heard that :s.

---

### Post by apollyon0810 on 2008-11-16
> **Sponzenbroekske said:**
> Funny , I never had poor performance, maybe you should try Hardy Heron. That will give you less trouble.
And else you can try Xubuntu with a ligther desktop-manager. I've heard that compiz is possible without any problems on XFCE4.
And there's a bigger Linux-world then Ubuntu :).

Vista faster then ubuntu, I've never heard that :s.


It's not just Ibex.  I've had the exact same issue with Hardy, multiple distros of Fedora, OpenSUSE, Mint, Gentoo, Sabayon, ect ect.  Always with the same poor performance.  Always ended up going back to Vista.  Sad, huh?

---

### Post by Sponzenbroekske on 2008-11-16
> **apollyon0810 said:**
> It's not just Ibex.  I've had the exact same issue with Hardy, multiple distros of Fedora, OpenSUSE, Mint, Gentoo, Sabayon, ect ect.  Always with the same poor performance.  Always ended up going back to Vista.  Sad, huh?

I see you don't have a lot of post, 6 to be exact and 2 of them here, maybe you could post an on thread with your problem to attract more skilled people.
Maybe its another piece of your hardware, cuz on mu ASUS F8P I don't have that problem

---

### Post by bodymind on 2008-11-24
do you still get GL windows flickering i intrepid?? 

i'm on hardy 8)

---

### Post by Sponzenbroekske on 2008-11-25
> **bodymind said:**
> do you still get GL windows flickering i intrepid?? 

i'm on hardy 8)

I never had that flickering :), my radeon is running nice on the fglrx driver :)

---

### Post by bodymind on 2008-11-25
> **Sponzenbroekske said:**
> I never had that flickering :), my radeon is running nice on the fglrx driver :)

i forgot to metion that it's only with compiz-fusion :\

my ati is this:
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400

i tried to install manually but all i got was a blank screen and 
"(WW) fglrx(0): Failed to open DRM connection" on Xorg.0.log... :confused:

now i'm using envy drivers... it stopped the flickering in totem... but i still get flickered in mplayer and games... that use openGL ](*,)](*,)

---

### Post by Sponzenbroekske on 2008-11-25
> **bodymind said:**
> i forgot to metion that it's only with compiz-fusion :\

my ati is this:
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400

i tried to install manually but all i got was a blank screen and 
"(WW) fglrx(0): Failed to open DRM connection" on Xorg.0.log... :confused:

now i'm using envy drivers... it stopped the flickering in totem... but i still get flickered in mplayer and games... that use openGL ](*,)](*,)


Ah yeah I got the flckering too, when I play a movie in a small screen, but when it is maximized I don't got that issue anymore, but I never made a big deal of it. And I'm using compiz too:)

---

### Post by SudoScience on 2008-11-30
Sorry to butt in, but does anyone else have problems with the 2400 in dual-screen mode with Catalyst Control Center? Mine tells me to restart, but then it erases my settings. So I just do it without restarting, which mostly works, but has some areas around the edges of the screen which freeze any motion... so yeah, not any major problems, just little annoying things.
Also: the label on my card says 2400PRO instead of 2400HD... is there a difference??? (I can't find anything on 2400PRO, so right now I'm assuming they're the same thing)
Sorry if these are newb questions, I'm pretty new at working Ubuntu.

---

### Post by SudoScience on 2008-11-30
Oh yeah, by the way, I also get the screen-flicker problem w/ Google Earth.

---

### Post by bodymind on 2009-01-06
> **SudoScience said:**
> Oh yeah, by the way, I also get the screen-flicker problem w/ Google Earth.

it flickers with every opengl or xv(mplayer) window...  :s but in  fullscreen works fine

---

