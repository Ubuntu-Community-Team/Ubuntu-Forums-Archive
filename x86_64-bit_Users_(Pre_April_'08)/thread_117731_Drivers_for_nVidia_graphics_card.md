---
title: "Drivers for nVidia graphics card"
date: 2006-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by gbullit on 2006-01-15
My hardware:
MSI  K8N Neo4, AMD Athlon 64, Corsair 2x512 DDR400 Dual Channel, Gainward FX 6600 GT 256 Mb PCI-express, Maxtor S-ATA 160 Gb, 17” TFT screen
OS Kubuntu 5.10 using KDE desktop
How do I install drivers for my graphics card ? I am rather new to Linux and is there a way to install the drivers in packet manager, so I just can download and install the drivers? Help would be much appreciated, thnx :smile:

---

### Post by MartinG on 2006-01-15
See the Unofficial Guide:

[http://makuchaku.info/amnesty/#installnvidiadriver](http://makuchaku.info/amnesty/#installnvidiadriver)

(Although this is the Ubuntu guide, it's the same for Kubuntu.)

---

### Post by scunc_dvl on 2006-01-15
I believe this guide is for the drivers that come free (as in nonproprietary) with ubuntu--the nvidia glx drivers. 

For my nvidia card (geforce 6600LE), the free drivers (version 7667 I think) simply do not work, and for myself I have to use the VESA drivers until I install the latest drivers from NVidia's website (Which is okay but it does involve installing some packages, setting up, and possible bug fixing..)

tseliot wrote a howto on it here -- [http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

Method 1 is pretty much the same as the one in the guide, using the 7667 drivers (which, if nothing's wrong with them, you probably shouldn't change them.. )

Method 2 is the one that involves the Nvidia driver installer from the Nvidia website (NVIDIA-Linux-x86_64-1.0-8***-pkg2.run ). What it all boils down is doing everything to help this installer do its work (installing all the necessary packages, exporting the name of the correct version of the compiler)

Note I would omit the steps involving changing any settings in text files, as recent installers like 8174 and 8178 seem to be able to change your settings just fine on their own. 

*(What they -cannot- do is load the proper kernel modules and etc., this is why removing + installing the right packages is so important. And additionally, method 2 boils down to getting rid of -all- the old nvidia stuff to make the installer's stuff work right)*

Heh I wish it wasn't that complicated :???:

---

### Post by gbullit on 2006-01-17
Hi again. In SuSE you can install the Nvidia drivers in YAST => Online Update => Installed & Installable patches, that's it, YAST download and install the drivers, no problem, 3D acceleration works. Being rather new to Linux, method 2 seem to be a bit farfetched, to say the least, isn't there an easier way to do this?:(

My hardware:
MSI  K8N Neo4, AMD Athlon 64 3500+, Corsair 2x512 DDR400 Dual Channel, Gainward FX 6600 GT 256 Mb PCI-express, Maxtor S-ATA 160 Gb, 17” TFT screen

---

### Post by MartinG on 2006-01-17
[QUOTE=gbullit]Hi again. In SuSE you can install the Nvidia drivers in YAST => Online Update => Installed & Installable patches, that's it, YAST download and install the drivers, no problem, 3D acceleration works. Being rather new to Linux, method 2 seem to be a bit farfetched, to say the least, isn't there an easier way to do this?:([/QUOTE]
Yes, but I think you'll find that Yast only installs the 7667 drivers, as in "Method 1".  If you want cutting edge, I don't think Yast is any better.  Anyway, if you prefer it, you can use SUSE rather than Ubuntu -- it's a free world, and both are Linux.

---

### Post by gbullit on 2006-01-17
Thanks MartinG for the "help" which was nonexistent.
When it comes to what distro to use, don't you think that's up to me to decide? When I asked for help, I presumed that someone would show up and give me help about the topic in question, not giving their personal view on what distro to use, thanks and keeping that in mind , spare me your thought about distros.
regards
GB

---

### Post by chadwick359 on 2006-01-17
I don't actually know what version of the drivers Yast installs nowadays, but MartinG is correct, in Ubuntu, that is really the only way to install the latest and greatest Nvidia drivers, unless you update to Dapper, which has the 8000 series in repositories already.

---

### Post by MartinG on 2006-01-17
> **gbullit]Thanks MartinG for the "help" which was nonexistent.
When it comes to what distro to use, don't you think that's up to me to decide? When I asked for help, I presumed that someone would show up and give me help about the topic in question, not giving their personal view on what distro to use, thanks and keeping that in mind , spare me your thought about distros.
regards
GB[/QUOTE]Oops, I seem to have offended you, and I'm not sure how.

I *did* give you help by pointing you to the instructions to install the proprietary drivers, which are all most people need.  It might not have been what you wanted, but it was help nonetheless.  scunc_dvl augmented this by pointing to the howto which covers not just this in a different way (tseliot's method 1), but also the more cutting edge install of later drivers (method 2). (BTW, scunc_dvl possibly misled you in that the unofficial guide covers the installation of the proprietary drivers, not the free ones.)  So, I suggest you *have* had help.

As to the distro issue, nobody mentioned any distro until *you*, not I, suggested that SUSE is better than Ubuntu on this point said:**
> method 2 seem to be a bit farfetched, to say the least, isn't there an easier way to do this?
No, there isn't, and frankly the way you expressed this suggested that you think those who developed it have not tried hard enough. Which is partly why nobody except two of us have responded to your posts.  The help you have had is all there is on this topic.

I'm sorry if this forum hasn't given the answers you want; but then we are all just ordinary users, not paid support staff.

---

### Post by metoo on 2006-01-18
May be I'm missing something, but nvidia drivers are available as a package for breezy.

Use synaptic as a graphical package manager:
install the linux-restricted-modules-2.6... package for your kernel.
You get the name of the kernel you are running with: uname -r (typed in a console)
Then search in synaptic for 'nvidia'
Install nvidia-glx, nvidia-settings and whatever you want/need more.
nvidia-settings can be run by typing 'nvidia-settings' in a console.

However, this will give you 7667 drivers. Not the latest. Since 6996(?) I can play UT2k4 fine in amd64 but I have a agp card. There were people with problems with 6600 chips and pci-e. But if these 7667 works for you, there should be no need to upgrade to the latest 8xxx. Improvements were mainly on the sli and 7xxx-series card sides.

As a side note: the forums search function will (may be already has) give you this info as well. Use it first before posting new questions. If a solution exists, it is even faster and more convenient for you.

If you cannot see the packages I mentioned, then you have to update your /etc/apt/sources.list .
I'm not sure where the restricted stuff is in, but your list should contain: main restricted universe multiverse
See other posts or the wiki for hints to enhance the sources.list . You could then get the latest kde or openOffice 2.01 as well, which has nothing to do with the nvidia drivers ! :-)

---

### Post by martinbriscoe on 2006-01-24
Hello

Arnieboy suggested I call in here my problem is described below, It looks to me as if I have to follow method 2? but it looks very complex and scary for a newbie - is there an easier way as everything was working before running automatix

Thanks

Martin

>>>>
Me:
After running automatix my boot up time has increased from 1 to 3 minutes. The computer appears to hang after it begins 'starting hardware abstraction layer' the screen goes blank apart from a white dash top left then after a minute or more the computer comes back to life and the ubuntu screen appears.

I have uninstalled most things using the advice in this (Automatix removal) thread. Any idea whats going on and how to resolve the problem?
<<<

>>>
arnieboy
appears to be video card related. what is your video card?
<<<

>>>
Me
The XP driver is: nvidia geforce mx/mx400
<<<

>>>
Arnieboy:
yes this problem indeed is card related. I would suggest you refer to the following thread and ask for help. Tell them u have the nvidia-glx drivers in the repositories installed (which automatix installs.. nothing fancy other than that). mention your card details and they will help u on that further from there.
One of my team members maintains that thread.
<<<<

END

---

### Post by MartinG on 2006-01-25
Before getting into Method 2, have you tried running through Method 1? Did it throw up any messages?

If the answers are yes and no, please clarify:
What packages have you got installed which include "nvidia" in their name, or "restricted-modules"?
Is there a file in /etc/init.d that includes "nvidia" in its name?

---

### Post by martinbriscoe on 2006-01-25
Martin, thanks for responding

>>
have you tried running through Method 1? Did it throw up any messages?
<<

it shows:- 
nvidia-glx is already the newest version.
nvidia-settings is already the newest version.
linux-restricted-modules-2.6.12-10-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded

>>
What packages have you got installed which include "nvidia" in their name, or "restricted-modules"?
<<

Synaptic shows the following installed
restricted modules 2.6.12.4-11.1 and 2.6.12.4-11
nvidia-glx 1.0.7667-obuntu25
nvidia-kernel-common 1.0.7667+1
nvidia-settings 1.0.3ubuntu6
xserver-xorg-driver-nv 6.8.2-77

>>
Is there a file in /etc/init.d that includes "nvidia" in its name?
<<

Yep its called nvidia-glx 
 
---
Ooops I have just noticed that this thread is in an amd64 forum. I have an x86 machine - If I am in the wrong place I apologise. but any advice appreciated

Martin

---

### Post by MartinG on 2006-01-25
OK, you seem to have all the necessary packages in place, so it's down to configuration.  Let's try reconfiguring X. This uses a ncurses based screen. Enter```
sudo dpkg-reconfigure xserver-xorg
```Work your way through the questions, choosing nvidia at the right point, and then try it again (you probably need to reboot to see if the timing has improved.)

If (only if) that doesn't work, we'll try switching to the free driver.  To do that, edit /etc/X11/xorg.conf and in the section "Device" change the Driver line entry from "nvidia" to "nv".  Reboot (or just restart X).

If that works (which it surely should?), we'll re-install the Nvidia drivers.

First uninstall the following (listed in your last post):[INDENT] restricted modules 2.6.12.4-11.1 and 2.6.12.4-11
 nvidia-glx 1.0.7667-obuntu25
 nvidia-kernel-common 1.0.7667+1
 nvidia-settings 1.0.3ubuntu6[/INDENT]
Then reboot and try Method 1 again.

---

### Post by martinbriscoe on 2006-01-26
>>>
Let's try reconfiguring X. This uses a ncurses based screen. Enter```
sudo dpkg-reconfigure xserver-xorg
```Work your way through the questions, choosing nvidia at the right point, and then try it again (you probably need to reboot to see if the timing has improved.)
<<<

Martin

I am eternally grateful. This has solved my problem and my boot up is back to normal. Xorg asked me to select nv, which I did. 

What exactly does this mean? I assume the nv driver not exactly state of the art but does it matter?  My pc isnt either, I dont need fancy graphics as I dont play games. As long as I can use gimp and other std packages I'm happy.
What would you do? 

Many thanks
Martin

---------

If (only if) that doesn't work, we'll try switching to the free driver.  To do that, edit /etc/X11/xorg.conf and in the section "Device" change the Driver line entry from "nvidia" to "nv".  Reboot (or just restart X).

If that works (which it surely should?), we'll re-install the Nvidia drivers.

First uninstall the following (listed in your last post):[INDENT] restricted modules 2.6.12.4-11.1 and 2.6.12.4-11
 nvidia-glx 1.0.7667-obuntu25
 nvidia-kernel-common 1.0.7667+1
 nvidia-settings 1.0.3ubuntu6[/INDENT]
Then reboot and try Method 1 again.[/QUOTE]

---

### Post by MartinG on 2006-01-26
[QUOTE=martinbriscoe]I am eternally grateful. This has solved my problem and my boot up is back to normal. Xorg asked me to select nv, which I did. 

What exactly does this mean? I assume the nv driver not exactly state of the art but does it matter?  My pc isnt either, I dont need fancy graphics as I dont play games. As long as I can use gimp and other std packages I'm happy.
What would you do? [/QUOTE]The nv driver was developed by the open source community, by reverse engineering the nvidia chip(s). The nvidia drivers are written by nvidia themselves and released free to the community -- but they are closed source.  Some people refuse on principle to use closed source stuff, and certainly the Debian community won't include it in their base distributions; it is however easily accessed by those of us who want it.

The practical difference is that the nv driver doesn't support glx and transparency; glx you need for most games, transparency etc. for fancy effects (I have non-focused windows semi-transparent, which greys them out, and drop shadows, which enhances the active window -- but it's all non-functional eye candy!).  They all require a bit of processing power, so given what you say about your computer and your needs the nv driver is fine, and you can feel open source virtuous at the same time :)

If you do ever decide you want any of these enhancements, then try Method 1 again, but first remove all the packages I've referred to and the /etc/init.d/nvidia-glx file, so as to start from scratch.

Best wishes

---

