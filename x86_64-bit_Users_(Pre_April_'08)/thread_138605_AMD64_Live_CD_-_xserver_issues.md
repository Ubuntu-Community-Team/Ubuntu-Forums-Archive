---
title: "AMD64 Live CD - xserver issues"
date: 2006-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by whiskeyclone on 2006-03-02
Hey, I'm trying to get Breezy to run on my AMD64 Turion Laptop, but having no joy. 

I've taken a gander around the forums and I'm guessing its the ATI driver issue. Tried with i386 and Kubuntu live CDs and not a burn issue - because I have the same issue with them  (I've got a Raedon Mobililty Xpress 200M ATI card in there).

The Error message is "There is a problem with your X server (graphical interface), and it may not be setup correctly."

I tried changing the settings using sudo dpkg-reconfigure xserver-xorg but they all seemed to be correct (all bar the resolution which was too high) but that fixed nothing. Tried changing Driver to Vesa/VGA (no Vega option as [this]("http://ubuntuforums.org/showthread.php?t=128435&highlight=live+amd+xserver") post suggests - assumed it was vga)

I had a different problem with 5.04 - it would get as far as the splash screen (after I got dumpped to terminal and had to prompt it with startx) but it died after making the startup noise.

I've had Gentoo running on this machine fine before from a live CD - but I really want to have a distro installed to dual boot and I think I want that distro to be  Ubuntu - but I want to play with it on the Live CD first. 

Is there a way of installing the ATI drivers when using the live cd because everything is stored on the RAM? The machine has no active internet connection - but I do have access to a Flash drive.

Any ideas short of partitioning and installing, then installing the drivers from terminal? 

Thanks - any sorry if this has been answered, I spent some time last night searching for this problem but couldn't spot a solution. 

Its probably an easy fix which as a noob I'm complicating for myself. 

Cheers.

---

### Post by ruudiculus on 2006-03-13
> Is there a way of installing the ATI drivers when using the live cd because everything is stored on the RAM? The machine has no active internet connection - but I do have access to a Flash drive.

Yes, you can do this in theory (I have never verified, sorry) but you'll need to do it every time you startup with the live cdrom.

As far as your ATI driver is concerned: I've got the same card on a HP 64bit laptop and I've managed to get things running grahically. You might want to try and use my HowTo on this (click on the link below)

Yet, when I run programs like **3ddesk** and **glxgears** there doesn't seem much 3d acceleration and the Xwindow manager tends to fall back into some default screen setting. Well, when you've got your graphics up, you might help me (and others) with that...

Good luck!

---

