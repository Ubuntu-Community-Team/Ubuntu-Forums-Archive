---
title: "World Of Warcraft on Ubuntu 7.04 w/ Monile Intel 915 Graphics"
date: 2007-06-23
forum: Wine
---

### Post by Sl1k on 2007-06-23
Hello,

I cant seem to find any good information on how to fix this, I installed WoW fine, Installed Burning Crusade, Did all the Patches and followed all the guides to fix the Config.WTF file and Edited the registry to add the DisabledExtensions string, 

Now when I run WoW I can get to the Menu screen and login but the Graphics are all messed up, and its very choppy... 

I ran GLxgears and got this:

5530 frames in 5.0 seconds = 1105.816 FPS
5533 frames in 5.0 seconds = 1106.440 FPS
5067 frames in 5.0 seconds = 1013.247 FPS
5535 frames in 5.0 seconds = 1106.907 FPS
5537 frames in 5.0 seconds = 1107.277 FPS

I have an Acer Aspire 9400 w/2Ghz Proc and 2Gigs of Ram with the Intel 915 Chipset, Iv been at this for days now anyone know how I can finally get WoW to run??

Its ran perfect on XP btw.

Thanks.

---

### Post by Sl1k on 2007-06-23
Getting a little more progress using D3D mode but game crashes once I try and logon to Realm, I can load the Client and see my toons perfectly fine just crashs once finished loading world... and the terminal reads as follows:

Mesa 6.5.2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22


Anyone have any Ideas?


Prior to this with Opengl I could login to world just gfx were all fubard...

---

### Post by zyth on 2007-08-12
Set your VideoRam to something bigger in your xorg.conf.  I had this same issue until I set mine to 196608 (192mb) but really, 64mb or better should be fine, just remember it needs to be in kb not mb.  I think xorg only allocates 16mb by default or something.

---

### Post by stretchilism on 2007-10-17
i am having a similar problem, but with warcraft three, so i assume it's the same thing. how do i modify the allocation? i've found the file and am lost

---

### Post by Castar on 2008-02-07
In the Device Section, add if it's not there or modify 

"LinearAlloc" "65536"

this will give you 64MB for your video card.

---

### Post by jacob01 on 2008-02-07
what would i have to add to allocate more mem to an intel x3000  in 7.10?? there is no device section

---

### Post by emieczko on 2008-02-25
> **Castar said:**
> In the Device Section, add if it's not there or modify 

"LinearAlloc" "65536"

this will give you 64MB for your video card.

I'm a newb, so bear with me...

I tried adding the line above to my xorg.conf file and ended up with no GUI...  Basically right after Grub loads it dumps out to the terminal, i.e. never gets to Gnome.

I was able to use VI from the command line to edit xorg.conf and remove the new line.  That got me back to a usable system, but still no WoW.

Any ideas?

---

