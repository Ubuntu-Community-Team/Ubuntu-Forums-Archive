---
title: "Cannot boot LiveCD"
date: 2007-09-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by danieljay on 2007-09-12
So I purchased new parts to build a PC and now am trying to install Ubuntu Feisty 64bit on the machine. I can get to the screen that asks if you want to install, install with safe graphics, memory test,... However, when I select anything to install Ubuntu all I get is a blank black screen and the monitors go into power saving mode.

I am running the Asus M2N32-SLI Delux with the AMD 6400+ X2 processor.
I have an MSI NX8600GTS-T2D256E-OC GeForce 8600GTS 256MB 128-bit GDDR3 PCI Express x16 graphics card. (I am running this with dual monitors)
One 500GB SATA hard drive on SATA1 and a DVD burner running on SATA2.
Along with 2GB of ram.

I am currently posting from the machine running Windows XP Pro so I know that the machine works but cannot boot to install Ubuntu.

Is there some kind of boot switch that I need to add in order to boot and install?

---

### Post by cleric23 on 2007-09-13
I was having the same problem (still did not fix it). My monitor went blank too, but I noticed disk activity. The system actually was booting, I just didnt see it. Try the safe grafics mode and then just wait until you see the GUI, just my booting was blank.

I unfortunately still have no idea how to fix this (instead of just deactivating boot splash, which worked for me, but the framebuffer still doesnt work, so I boot with a very low resolution)..

Hope that helps

---

### Post by dabl on 2007-09-13
Is this a laptop? If so, probably there's trouble with the power-saving/battery-saving stuff.  There are boot "switches" that you need to use -- I have a desktop so I'm not real expert at it. Something like "noapic" and "nolapic" and "noacpi".  :)

---

### Post by danieljay on 2007-09-13
This is a brand new desktop that I have put together.

I will try and letting it sit for a while longer to see if things will bring my screens back.

---

### Post by danieljay on 2007-09-13
I finally got Gutsy installed. I ended up using the alternate CD and I also unplugged the power cord on my graphics card. Possibly could have gotten away with not unplugging the power but things worked. I also then used Envy to install the nvidia drivers.

---

