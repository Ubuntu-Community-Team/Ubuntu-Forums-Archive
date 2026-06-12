---
title: "Black Screen, GRUB issues, and Confusion..."
date: 2008-03-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Equiflux on 2008-03-07
_Intro:_
I've searched through these forums for a little while now and even posted twice regarding my, soon to be mentioned, problems but found only a few bits of information that may help me; nothing that I feel will fully help me get completely through this situation. Basically, I just built a new system and I can't get Ubuntu Studio working in it. I just want to get it working and get on with my life; I feel so "home sick" not using Ubuntu. Need assistance ASAP.

_Issues at a glance:_
[LIST]
[*][Solved] GRUB does not display a menu on/after initial boot up.
[*]After displaying the Ubuntu Studio usplash, my screen just goes black because no signal is sent to my monitor.
[*]Xubuntu somewhat works, Ubuntu Studio does not at all. (Except for the usplash anyway)
[/LIST]

_System Specs:_
> 
[LIST]
[*]CPU: AMD Phenom 9500
[*]Mobo: MSI K9A2 Platinum
[*]GFX: NVIDIA 9600 GT
[*]HDD: 250GB SATA
[*]RAM: 2GB DDR2 1066
[/LIST]

*note: I'm trying to use Ubuntu Studio 7.10*

---

_A bit more In-depth:_
**GRUB:** It does not display a menu for me to choose between Ubuntu, memtest, etcetera. Is this normal if Ubuntu is my only OS?

**Black Screen:** After booting and going through the usplash, my entire screen goes black and displays the "No Signal" message. This happens with both the 32bit and 64bit versions.
[LIST]
[*]While trying to install the 32bit version Ubuntu Studio, I get an error saying "No installable Kernel Found in APT sources" When I just continue anyway and *attempt* to boot, I get an X.org error saying that no screen is found. It *does* at least display something past the usplash.
[*]Ubuntu Studio 64bit fully installs with no problems. However, when I try to boot it, nothing happens past the loading/boot/usplash screen.
[*]Same goes with trying to boot Live Xubuntu CD's and trying to install in graphical mode(I have to install Xubuntu using the alternative installation). The Linux Kernel just loads, a few lines of text appear at the top and bottom of my screen, I'm not sure what the text says but I will check if it is necessary, and then the screen goes black. 
[/LIST]
**Xubuntu 64bit** - sort of works. Past the usplash the screen goes black for a few moments and then a small window appears. (At this point I am in 800x600 but my monitor is 1024x768 ) The window says something to do with my graphics card or something and asks me to make some quick configurations like choosing display devices and restricted drivers. I can actually log in and do stuff, it recognized the 4 cores, all the RAM, etc. The only thing that is wrong now is that I am still in 800x600 at this point. I think something's up with my Graphics Card and the Drivers.

---

Anyways, thats my problem. I can try to provide some more information about the problems if necessary, so work with me here.

Thanks!

---

### Post by archmage258 on 2008-03-08
Hi; I dont have too much experience with the your other issues; but I do know that on my laptop I have the same load issue.  I was able to fix it by changing some of the settings in my /boot/grub/menu.lst. Specifically the hiddenmenu option, just comment it out with a # and viola; you have your load screen.  Hope that helps! :)

---

### Post by Equiflux on 2008-03-08
Alright thanks. I'll update my first post. Is there a way I can use the shell immediately after boot-up?

I found a possible solution:
[QUOTE=llamafier]I'm in the _**exactly**_ same position! (800x600 sucks) It seems the problem is that there are no linux drivers available for this card yet. It is just too new. :(

I was searching around and found [this](http://forums.nvidia.com/index.php?showtopic=60737):

[http://forums.nvidia.com/index.php?showtopic=60737](http://forums.nvidia.com/index.php?showtopic=60737)

so apparently [these](ftp://download.nvidia.com/XFree86/Linux-x86/171.05/) drivers will work:

[ftp://download.nvidia.com/XFree86/Linux-x86/171.05/](ftp://download.nvidia.com/XFree86/Linux-x86/171.05/)

I just have no idea how to install them, and I'm using the 64bit version so that probably will complicate things. :([/QUOTE]

But how would I go about installing this with no GUI or Shell?

---

### Post by Equiflux on 2008-03-09
Okay, I think I'm close to getting drivers installed and fixing all of this, but can anyone tell me how to:

-End my x.org server
-Get the kernel source for Ubuntu Studio's kernel
-Make a "source tree" for it, if that made any sense, so that the NVIDIA driver installer and find it and build whatever it needs to build.

---

