---
title: "Can't get live CD to finish boot"
date: 2006-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by mike-in-nc on 2006-05-29
Hello, all--

I am interested in Linux, though I have never installed or configured a Linux system.  I have used it as an OS when doing some work on a remote supercomputer.  I am trying the Ubuntu 5.10 live CD.  Machine is an Athlon 64 3200 with an ASUS A8V Deluxe mainboard.  Video is a Matrox Millennium G550, digital output at 1280 x 1024 to a Viewsonic LCD.

This system is now running Windows XP Professional.

The live CD starts the boot.  It goes through the blue and brown screens & there is some brief music (Gnome startup music?)  However, even after a long wait (15 mins), there is no desktop, just a black screen.  At that point if I press the reset button, I get a character-mode screen that says something like "Starting runlevel 2..." which shows some checks & then stalls on "Checking battery...".

Any hints on getting this running, or is it a lost cause?

Mike

---

### Post by H.E. Pennypacker on 2006-05-30
No, it's not a lost cause.  It's most likely a bad download or a bad burn, as in my case.  What's happening to you is similar to what's happening to me.  After you download the Live CD, make sure to check md5sums.  That at least eliminates a bad download.  If that works out, try burning.  If the second burn does not work, something's going on at the point of the burn.  Try burning using another computer to see if the problem lies with your computer.  It's a process of elimination.

---

### Post by mike-in-nc on 2006-05-30
> H.E. Pennypacker:  It's most likely a bad download or a bad burn, 
Thanks for the idea.  Tne MD5 sum is OK.  I'll try the existing CD on another machine.  If no go, I'll try re-burning, as you suggested. Either way, I'll learn something.

Mike

---

### Post by mike-in-nc on 2006-05-30
I couldn't try the CD at work because the machines there are i386 and the CD is AMD64.  Duh!  

However, I burned and tried an i386 live CD at home, booting into expert mode, which gave a little more information.  Same symptoms.  The reported problem is that the X Server can't be started.  However, the graphics card & monitor are both detected correctly, so it's hard to know what the problem could be.  Is there some issue with having the monitor hooked up through the digital (DVI) connection, rather than the VGA connection?

Mike

---

### Post by mike-in-nc on 2006-05-31
Got this to work this evening after downloading 6.06.  At first, same symptoms. Then, I went into the BIOS and changed the AGP aperture from 64Mb to 128Mb. Upon starting the PC with the 6.06 disk, I changed the graphics resolution to 1280 x 1024 and let the boot go ahead.  I did get a GNOME desktop & functioning system this time. Can't say which of the three changes was the most important, but I suspect the aperture setting.

Mike

---

### Post by H.E. Pennypacker on 2006-05-31
Great! :) Thanks for following up on this.

---

