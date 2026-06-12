---
title: "Blank screen at login time!"
date: 2006-01-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hygelac on 2006-01-06
I'm fairly new to Kubuntu and have been trying to get my graphics card to work (ATI Radeon Xpress 200M).  My computer is an HP zv6000, so I have been following the wiki ([https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard)) for help; the computer at the bottom of the page (HP Pavilion zv6000 series) being of the same model as mine.  I have also been following the forum thread that the wiki links to concerning the graphics card.

The first problem I have is referenced in that thread.  There is an error message in Xorg.0.log and X does not load, leaving me in shell.  As the thread advises, I comment-out the Load  "int10" line of the "Module" section of xorg.conf.  This causes an even worse problem.  Linux loads but instead of seeing a graphical login or the shell login that I was seeing, I see a completely blank screen (I do not see X begin loading before this)!

So, can someone please help me with this?  For now, I have restored the old "ati" driver until "fglrx" is actually working; (I had to do this by running the Damn Small Linux liveCD and changing xorg.conf, since I had no way of interracting with Kubuntu) but I really want to get this graphics card running!

:confused:

---

