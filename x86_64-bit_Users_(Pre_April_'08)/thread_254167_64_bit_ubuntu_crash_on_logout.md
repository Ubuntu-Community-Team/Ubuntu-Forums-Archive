---
title: "64 bit ubuntu crash on logout"
date: 2006-09-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by daniminas on 2006-09-09
Hi. First, sorry my english, i'm Uruguayian.  I been installed the 64 bit ubuntu, and everything works verry good :).. but when i want to log out, shutdown, restart, etc.. the computer crash... I can't switch to the console too.:confused: 

Please help, and thanks in advance

---

### Post by Kilz on 2006-09-09
> **daniminas said:**
> Hi. First, sorry my english, i'm Uruguayian.  I been installed the 64 bit ubuntu, and everything works verry good :).. but when i want to log out, shutdown, restart, etc.. the computer crash... I can't switch to the console too.:confused: 

Please help, and thanks in advance

What video card do you have?

---

### Post by daniminas on 2006-09-09
i've a ASRock 775i65g motherboard..  is that? :(

---

### Post by Kilz on 2006-09-09
> **daniminas said:**
> i've a ASRock 775i65g motherboard..  is that? :(

Im more interested in finding out what graphics you have. Is it ATI or nividia, or something else?

---

### Post by daniminas on 2006-09-11
an Intel 865G chipset.. :-k

---

### Post by phunkizm on 2006-09-11
I'm having a similar problem, with AMD Athlon 64 and a ATI Radeon Express 200 video card.  When trying to log out, shutdown, or restart, the screen goes blank and it looks like the power was shut off.  But the computer stays on, forcing me to hold down the power button to turn it off.  I've done some searching on this problem and only found one solution which was so brief that i didn't want to try it until learning more.  (The solution was to add add "AlwaysRestartServer=true" to the gdm.conf file.)  
This is a rather annoying bug.. and although I love Ubuntu so far, I'm tempted to wipe it clean again and find a new distro that won't include this problem!

---

### Post by Kilz on 2006-09-11
> **phunkizm said:**
> I'm having a similar problem, with AMD Athlon 64 and a ATI Radeon Express 200 video card.  When trying to log out, shutdown, or restart, the screen goes blank and it looks like the power was shut off.  But the computer stays on, forcing me to hold down the power button to turn it off.  I've done some searching on this problem and only found one solution which was so brief that i didn't want to try it until learning more.  (The solution was to add add "AlwaysRestartServer=true" to the gdm.conf file.)  
This is a rather annoying bug.. and although I love Ubuntu so far, I'm tempted to wipe it clean again and find a new distro that won't include this problem!

The reason I asked for the video card from the orignal poster was because I also have a radon express 200. The problem has nothing to do with Ubuntu, but the drivers from ATI. The problem is the 8.25.18 drivers that are in the repositories. You might want to upgrade the video drivers with the ATI driver installer. Its presently at 8.28.8, here is a link to a good howto for [upgrading them.]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually")

I dont know what the orignal posters problem is, but I think its along the same lines. They might want to look for newer graphics drivers.

---

### Post by kuja on 2006-09-11
An intel chipset eh? What driver are you using for video right now. It should be midway down your /etc/X11/xorg.conf file.

---

### Post by Extol11 on 2006-09-12
> **daniminas said:**
> i've a ASRock 775i65g motherboard..  is that? :(

I have the exact same mother board and it does the same thing. I'm using the integrated graphics card and it is the 865G chipset. Any tips on how to solve this problem?

---

### Post by daniminas on 2006-09-12
> **Extol11 said:**
> I have the exact same mother board and it does the same thing. I'm using the integrated graphics card and it is the 865G chipset. Any tips on how to solve this problem?
This is my chipset/motherboard, and i've the **phunkizm** problem.. :(

---

### Post by daniminas on 2006-09-15
> **Kilz said:**
> The reason I asked for the video card from the orignal poster was because I also have a radon express 200. The problem has nothing to do with Ubuntu, but the drivers from ATI. The problem is the 8.25.18 drivers that are in the repositories. You might want to upgrade the video drivers with the ATI driver installer. Its presently at 8.28.8, here is a link to a good howto for [upgrading them.]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually")

I dont know what the orignal posters problem is, but I think its along the same lines. They might want to look for newer graphics drivers.

I been trying that howto, but now i get a error at the startup and i cant open the Desktop, i get something like a 'Cannot open screen", or no device...

Please Help, i like ubuntu but at this point i don't know what i have to do.. :(

---

### Post by Kilz on 2006-09-15
> **daniminas said:**
> I been trying that howto, but now i get a error at the startup and i cant open the Desktop, i get something like a 'Cannot open screen", or no device...

Please Help, i like ubuntu but at this point i don't know what i have to do.. :(

When I posted that I hoped you would understand that it was to fix the persons who I responded to's problem. Not yours. You have now installed a video driver not made for your system.
Type in the following command

```
sudo dpkg-reconfigure xserver-xorg
```
It will ask a series of questions, one of them is

```
For the X Window System graphical user interface to operate correctly, it is necessary to select a video card driver for the X server.                                                                        

Drivers are typically named for the video card or chipset manufacturer, or for a specific model or family of chipsets.                             

Select the desired X server driver.  
```

From the list below I'm guessing the answer will be i810 change it from fglrx. Then agree to the rest of it.

---

### Post by daniminas on 2006-09-15
and some idea how to fix the original problem? anybody?.. :(

---

### Post by BIGtrouble77 on 2006-09-15
I have this problem with my laptop.  Try this, it fixed it for me:
```

sudo gedit /boot/grub/menu.lst
```
From there, remove all of the instances of 'SPLASH'.  Save the file and reboot (it will probably crash again).

When you boot up again it will boot in text mode.  The good news is that shutting down will probably work now.

Realize that everytime you update the kernel you'll have to remove SPLASH again.

---

### Post by daniminas on 2006-09-16
Thanks, but i been trying with the AlwaysRestartServer on the gdm.conf and nothing.. with the splash on menu.lst and nothing, and with the Kilz HOW-TO and still nothing... 

Xorg tellmee this about the graphic controller: 'Intel Corporation 82865G Integrated Graphics Controller'... i just want to start tu use Ubuntu normally, because all work verry good except 'this' problem.... :(

---

### Post by daniminas on 2006-09-17
I was reading abour ATI AND NVDIA on this forum... but i don't know what to do.. please some help :rolleyes:

---

### Post by Kilz on 2006-09-17
> **daniminas said:**
> I was reading abour ATI AND NVDIA on this forum... but i don't know what to do.. please some help :rolleyes:

Here is the situation in a nutshell. You dont have ATI or Nivida, you have intel graphics. 
Do not try to install ATI or nivida drivers as it will only make your system unusable. You could buy a ATI or nvidia card, and solve the problem that way. But that costs money.
Right now my sugestion if you dont want to buy a card is to file a bug report and wait and see. Also keep looking , maybe there is a fix someone doesnt know about here.
I did take a look at Intels site, there is a linux download foe this chipset. It may not work,[ but its worth a try. ]("http://downloadfinder.intel.com/scripts-df-external/T8Clearance.aspx?url=/8203/eng/i915Graphics.tar.gz&agr=Y&ProductID=1044&DwnldID=8203&lang=eng") It even has a install script. I dont know if I would use it, but its up to you.

---

### Post by kuja on 2006-09-17
As per buying a card, that does cost money, however, you could get say, an nvidia 6200 for <$40(USD). Not too bad a price.

---

### Post by Kilz on 2006-09-17
> **kuja said:**
> As per buying a card, that does cost money, however, you could get say, an nvidia 6200 for <$40(USD). Not too bad a price.

I agree, the nivida would be the better choice. It has the best linux support.

---

### Post by daniminas on 2006-09-18
> **Kilz said:**
> Here is the situation in a nutshell. You dont have ATI or Nivida, you have intel graphics. 
Do not try to install ATI or nivida drivers as it will only make your system unusable. You could buy a ATI or nvidia card, and solve the problem that way. But that costs money.
Right now my sugestion if you dont want to buy a card is to file a bug report and wait and see. Also keep looking , maybe there is a fix someone doesnt know about here.
I did take a look at Intels site, there is a linux download foe this chipset. It may not work,[ but its worth a try. ]("http://downloadfinder.intel.com/scripts-df-external/T8Clearance.aspx?url=/8203/eng/i915Graphics.tar.gz&agr=Y&ProductID=1044&DwnldID=8203&lang=eng") It even has a install script. I dont know if I would use it, but its up to you.

Ok, first at all, thanks for all the help :). I will try with that driver, and if not work i report the file bug.. However, if work i will post: 'it work!, ubuntu rocks!' :)

Daniel

---

### Post by daverobev on 2006-09-19
Right, I'm not sure whether my issue is the same as this, but it certainly sounds the same.

I have an AsRock 775i65G with nVidia 6600 GTS, C2Duo/1.8GHz and I am getting full system lockups when a)coming out of screen saver or b) trying to shut down.

I'm using the nVidia drivers.

Doing the 33 or so updates tonight has not resolved this (I've not been on this machine lately, so I can't really say whether it was having these exact problems before - I suspect not, though I was getting lockups doing something or other, but not trying to Restart!).

A side issue is that my USB keyboard doesn't seem to work with GRUB anymore either.

I'm a semi-noob, I can probably try stuff with a little help, but "oh just reconfigure your psybox kron hash daemon with multiroot vnodes" will make me go..huh?

I'm guessing I have the same prob as the OP, I'm just able to express it better :)

Everything *was* working fine. But full system lockups make me cry :-/

TIA,

Dave

---

### Post by Kilz on 2006-09-19
> **daverobev said:**
> Right, I'm not sure whether my issue is the same as this, but it certainly sounds the same.

I have an AsRock 775i65G with nVidia 6600 GTS, C2Duo/1.8GHz and I am getting full system lockups when a)coming out of screen saver or b) trying to shut down.

I'm using the nVidia drivers.

Doing the 33 or so updates tonight has not resolved this (I've not been on this machine lately, so I can't really say whether it was having these exact problems before - I suspect not, though I was getting lockups doing something or other, but not trying to Restart!).

A side issue is that my USB keyboard doesn't seem to work with GRUB anymore either.

I'm a semi-noob, I can probably try stuff with a little help, but "oh just reconfigure your psybox kron hash daemon with multiroot vnodes" will make me go..huh?

I'm guessing I have the same prob as the OP, I'm just able to express it better :)

Everything *was* working fine. But full system lockups make me cry :-/

TIA,

Dave

Since you have a nvidia card and the orignal poster has intel graphics I'm not so sure its the same problem. But it may be in the same area. You say you are using nvidia drivers, how did you install them? What instructions did you follow?

---

### Post by daverobev on 2006-09-20
I downloaded them from nVidia, I think, ran the run and then changed my xorg.conf to use "nvidia" not "nv" - but I'm sure that that bit is NOT the issue as that worked fine a couple of weeks back when I was using the machine daily - specifically, moving the mouse after the screensaver had come up did definately not cause a crash.

I set the cursor to software (HWCursor=false or somesuch) but again, that was ages ago (I had a flickery cursor before), so I'm *fairly* sure its not that.

Can I ask, what would coming OUT of screensaver and hitting "Restart" (this is after doing all the updates last night, just before I posted the previous message - I'm in the UK) have to do with the graphics card?

Could it be something to do with the clock? I'm losing or gaining a lot of time with the software clock - I'm guessing due to the speedstep stuff in the Conroe. Could it be that, or at least related to it?

Can anyone point me at log files - I have a rough understanding of the filestructure, but log locations....nah.

I'm racking my brain trying to think what else was giving me a lockup a couple of weeks back, something to do with transferring files - connecting to a Windows share, I think, using SMB.

Stuff that works: firefox, banshee, etc. Banshee keeps playing while the screensaver is up but moving the mouse causes it to stop as the system locks.

Any ideas about why grub is no longer picking up my keyboard?!? It works in the BIOS, and I can log in, I'm just stuck with GRUB...

I'm really not convinced its a graphics thing, but more than willing to test :)

---

### Post by kick6 on 2006-09-20
> **daverobev said:**
> I downloaded them from nVidia, I think, ran the run and then changed my xorg.conf to use "nvidia" not "nv" - but I'm sure that that bit is NOT the issue as that worked fine a couple of weeks back when I was using the machine daily - specifically, moving the mouse after the screensaver had come up did definately not cause a crash.

I set the cursor to software (HWCursor=false or somesuch) but again, that was ages ago (I had a flickery cursor before), so I'm *fairly* sure its not that.

Can I ask, what would coming OUT of screensaver and hitting "Restart" (this is after doing all the updates last night, just before I posted the previous message - I'm in the UK) have to do with the graphics card?

Could it be something to do with the clock? I'm losing or gaining a lot of time with the software clock - I'm guessing due to the speedstep stuff in the Conroe. Could it be that, or at least related to it?

Can anyone point me at log files - I have a rough understanding of the filestructure, but log locations....nah.

I'm racking my brain trying to think what else was giving me a lockup a couple of weeks back, something to do with transferring files - connecting to a Windows share, I think, using SMB.

Stuff that works: firefox, banshee, etc. Banshee keeps playing while the screensaver is up but moving the mouse causes it to stop as the system locks.

Any ideas about why grub is no longer picking up my keyboard?!? It works in the BIOS, and I can log in, I'm just stuck with GRUB...

I'm really not convinced its a graphics thing, but more than willing to test :)

Is the screensaver you're running 3d?

---

### Post by daverobev on 2006-09-21
Hmm, not sure - I have it set on "random" and I haven't specifically downloaded and installed any 3d screensavers, though I do know it has the molecular models and so on running...and they used to work, with the nvidia drivers installed.

Does log out call something in 3d, then?

---

### Post by daniminas on 2006-11-02
After all this time sice the original post i'm still with the problem and i cant shutdown, restart, logout normally my ubuntu x64... :( 

I'm waiting for some magic solution wich can make me back to Ubuntu.. now, ive installed the 32bit edition wich works fine but slowly, but if i've a 64bit pc i want to use ubuntu 64... :(

---

### Post by mnorayr on 2006-11-16
Hi, I have exactly the same problem: 
64 bit ubuntu edgy crashes whenever I try to logout/restart/shutdown. The PC is a DELL precision workstation with dual 64 bit xeons, 4 gig RAM and ATI X850XT graphics card.
 I have the latest sti drivers (fglrx) and opengl works. 
 Please help, I really would like to keep ubuntu, but it's not possible if every time I want to logout I need to pull the plug ...](*,) :(

---

### Post by kuja on 2006-11-16
The fglrx drivers have historically been full of problems. One of the being that at least with some versions of the fglrx drivers it won't let you logout, restart, shutdown, or switch vts.

---

### Post by cwhitt on 2007-01-11
There seem to be a few different types of problems with logout and/or shutdown.  If you have an Intel chipset with onboard video, the problem may be caused by kernel panics when the X server is being shut down.  Don't know about a fix, but a good workaround was posted here:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34697](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34697)

You need to change a setting in your BIOS Advanced -> CPU Configuration -> Execute Disable Function to ENABLED.  Somehow this prevents the shutdown of the X server from causing a kernel panic.

Cheers

---

### Post by daniminas on 2007-02-04
Thanks to cwhitt for the solution.. and to all for the help... 

 I'm a happy x64 user now :D

---

### Post by Lonthong on 2007-02-05
I just did a fresh Edgy 64 install with Ati latest driver v. 8.33.06. Laptop = BenQ P41, Turion X2, Ati X1100. I had also log out problem (only log out, shut down & reboot work properly). What I mean by 'problem' is black screen & keyboard seemed to freeze.

This trick solved my issue:
sudo gedit /etc/gdm/gdm.conf-custom
Add:    AlwaysRestartServer=true  under [DAEMON]

Hope this can be of help people having problemw ith Ati cards

---

### Post by kurisutofuaa on 2007-02-06
> **cwhitt said:**
> There seem to be a few different types of problems with logout and/or shutdown.  If you have an Intel chipset with onboard video, the problem may be caused by kernel panics when the X server is being shut down.  Don't know about a fix, but a good workaround was posted here:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34697](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34697)

You need to change a setting in your BIOS Advanced -> CPU Configuration -> Execute Disable Function to ENABLED.  Somehow this prevents the shutdown of the X server from causing a kernel panic.

Cheers

How do you access the BIOS Advanced?

---

### Post by rieske on 2007-02-22
thanks, Lonthong, your post helped me solve the same problem on 32 bit arch.

---

