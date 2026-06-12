---
title: "No Live CD with Amd 64bit"
date: 2007-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by derby007 on 2007-11-16
I just got my shiny new PC, Dell Inspiron 531, Amd 64 3800+ dual core, 2G ram, ATI Radeon X1300 Pro graphics(aaaagh!!->threads on this device do not make good reading!), 250G hd. I got it for a good price, ie. less than a quarter of the price i paid for my PC 10 years ago, which is now not worth €1. 
Anyway, it has vista premium, which is interesting.... but.......I installed Gobuntu( i386 GutsyAlternate version ) with no real hassle, i had to edit xorg.conf to use VESA driver. 
I then tried to install the 64bit Live Gutsy cd, but it hung (no matter what I tried) at : 'running scripts, (rc.local)', or something, I think this is where it tries to go into the graphical mode, or loading GDM or X windows...( know what I mean :) )
So......I'm guessing I'm having a graphics problem, ATI raises its ugly head again. My ultimate aim is to get Compiz-fusion, MythTV working.

Can anybody help ?

---

### Post by elliotjreed on 2007-11-16
I have the same PC, and can't get it to run the AMD64 Live CD...

I would like to know how too! As I want the best out of my PC!

---

### Post by derby007 on 2007-11-16
I wonder is it a bug, i thought the new Gutsy had ATI support. 

Q. for you: whats the AMD Live! about (concerning the processor), I noticed it is mentioned in the Bios set-up. 
Is it to do with the following: [URL="http://www.amdlive.com/gb-en/about.aspx/[/URL]
Quote from website: A smarter entertainment PC for all the screens in your digital life. Enhance your digital entertainment experience by connecting all the screens in your life. An AMD LIVE! PC is the ultimate digital entertainment upgrade, enabling you to access your favourite photos, music, TV and films wherever you are — directly from your main PC, without slowing it down.

---

### Post by Jouke74 on 2007-11-16
For an install I suggest the AMD64 alternate CD. Then install in text mode. To run the live CD you probably need to start in save graphics mode, at least that worked for me (X1600 Raedon). The problem is that my AMD64 Live CD hangs when it wants to start the partitioning of my harddrive during install. Not a time when you want to have a possible hang. That's why I switched to the alternate CD.

---

### Post by derby007 on 2007-11-16
I'm going to try the Alternate CD tonite. 
I did try the 'safe' mode with the Live CD, & other options, but to no avail....... :(

---

### Post by tybalt on 2007-11-16
Hi,
I had that problem with previous versions of AMD64 (edgy and dapper), and could finally start the live system by adding the parameters: vga=771 noapic nolapic

With these, i could start the live cd, and perform a complete installation. Nevertheless, the system never worked (unable to boot).  :(

Gutsy release solved the problem for me. :)
My system has a different processor and motherboard, in any case: AMD64Athlon 3500+ and Asus M2N4-SLI.

Hope this helps. Good luck.

---

### Post by derby007 on 2007-11-17
Yeah, the 64bit Alternate CD worked again, similar to Gobuntu, ie. had to tweak my xorg.conf. The installed xorg.conf had no 'Module' section, ie. no 'vbi', 'glx', 'dri', etc. I then went into the restricted drivers option on the 'menu' but it complained it wanted 'xorg-driver-fglrx', but while right-clicking on this .deb file to install, it asked me to insert the CD again, (to update some libraries), and now I can run the restricted driver. 
So, I'll try to install compiz-fuzion tonite (or does it come with Gutsy?mmmm) & see if 3D works.......

By the way notice the improvement with 'glxgears' after the new driver install:
Before: glxgears>
3331 frames in 5.0 seconds = 659.664 FPS
3306 frames in 5.1 seconds = 649.214 FPS
3390 frames in 5.2 seconds = 657.287 FPS
3277 frames in 5.0 seconds = 654.026 FPS

After: glxgears>
17852 frames in 5.0 seconds = 3570.349 FPS
17946 frames in 5.0 seconds = 3589.194 FPS
17780 frames in 5.0 seconds = 3555.970 FPS

Also: I now have direct rendering, 
glxinfo>
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes

---

