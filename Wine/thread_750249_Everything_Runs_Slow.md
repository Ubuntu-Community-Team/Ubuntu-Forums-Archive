---
title: "Everything Runs Slow"
date: 2008-04-09
forum: Wine
---

### Post by Commander Bosko on 2008-04-09
Hi guys,
  First time Linux user here. I'm running Ubuntu 7.10, using a dual boot with Windows XP. Ubuntu runs fine, but every time I try to run something with Wine, it runs so slow, that it's unusable.  

  It's odd because I have a good computer able to run most games at full quality on windows. If this is a common question I apologize, but I searched and nothing seemed relevant to my problem. Any help is appreciated. 

  Thanks:)

---

### Post by Weichpudding on 2008-04-09
Precisely what applications do run slow in Wine? It's important to know because if you are trying to run games the performance can greatly differ from Windows.

Oh, and some specs plus installed drivers would be good to know, too.

---

### Post by Commander Bosko on 2008-04-09
Lol, yea that probably would have helped.

  K, I have a 3 GHz Pentium 4, with 2 GB of ram.

  My video card is the ATI Radeon X300/X550/X1050 Series, on a side note, when I first loaded up Ubuntu, it told me that my video card was a restricted device, but it installed the driver and I have never been told anything again.
  
  It is a Dell, which I don't think would make a difference but couldn't hurt.

  Also the 2 games I tried running were Warcraft 3 and Guild Wars.

---

### Post by Commander Bosko on 2008-04-09
Bump

---

### Post by POW R TOC H on 2008-04-09
> **Commander Bosko said:**
> Hi guys,
  First time Linux user here. I'm running Ubuntu 7.10, using a dual boot with Windows XP. Ubuntu runs fine, but every time I try to run something with Wine, it runs so slow, that it's unusable.  

  It's odd because I have a good computer able to run most games at full quality on windows. If this is a common question I apologize, but I searched and nothing seemed relevant to my problem. Any help is appreciated. 

  Thanks:)

If you have Windows XP along with linux, then it's better to play on windows. I have a separate hard disk (only 15Gb) , always set to primary master, with a cut-down version of windows on it. When I want to play games, I restart with that hard disk as primary, and boot from it... But i managed to play Sam&Max with Wine just fine! :D

---

### Post by Commander Bosko on 2008-04-09
I know I could just play in windows, but I'm doing this as kind of an experiment, unsuccessful thus far.

---

### Post by Commander Bosko on 2008-04-10
bump

---

### Post by Commander Bosko on 2008-04-10
Ok I am getting a LOT of this error.

fixme:d3d:set_tex_op Unhandled texture operation WINED3DTOP_MODULATEALPHA_ADDCOLOR

Any ideas on how to fix this?

---

### Post by FrozenFox on 2008-04-10
Warcraft 3 needs to be loaded in opengl mode. Tack   -opengl   to the end of the command or shortcut you use to run it. It will run significantly better that way. As for GW, i have no idea.

Please also tell us the info received from running the command fglrxgears (I think thats the ati command.. i might have the lettering slightly off, so if you get 'no such command', sorry about that).

As for those 'fixme' errors, dont worry about them. Wine will always spit out errors on every program, because it's awesome at reporting problems like that. Dealing with them is more for people advanced with the usage of wine, ie using native windows DLL files instead of the wine ones when wine tells them its having a problem with a given program. Even if the program works 100% flawlessly in wine, it will still show errors or fixmes in the terminal. Judge a program by how well it runs in actuality, not what stuff wine tells you isn't perfect yet :)

---

### Post by aoanla on 2008-04-10
According to the AppDB entry for Guild Wars, there are no problems with it in the latest version of Wine (indeed, one report claims that it may even be better than in Windows!).

I suggest you upgrade Wine to the latest version (if you search on the forums here, you'll quickly see how to do that), and see if that improves matters.

---

### Post by Commander Bosko on 2008-04-10
First off, thanks for the replies guys! :)

K, all my expierementing has been done with Wine 0.9.58.  And with glxgears, I ended it after a little while because it seemed to be endless, this is what I got.

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
27392 frames in 5.0 seconds = 5455.004 FPS
27566 frames in 5.0 seconds = 5513.192 FPS
26858 frames in 5.0 seconds = 5363.656 FPS
29498 frames in 5.0 seconds = 5893.103 FPS
29405 frames in 5.0 seconds = 5864.004 FPS
29367 frames in 5.0 seconds = 5848.850 FPS
29527 frames in 5.0 seconds = 5897.484 FPS
29507 frames in 5.0 seconds = 5899.921 FPS
29713 frames in 5.0 seconds = 5919.988 FPS
29614 frames in 5.0 seconds = 5902.295 FPS
29658 frames in 5.0 seconds = 5915.842 FPS
29596 frames in 5.0 seconds = 5909.844 FPS
29509 frames in 5.0 seconds = 5899.511 FPS
27816 frames in 5.0 seconds = 5546.725 FPS
27119 frames in 5.0 seconds = 5418.922 FPS
29032 frames in 5.0 seconds = 5784.803 FPS
28357 frames in 5.0 seconds = 5669.403 FPS
29643 frames in 5.0 seconds = 5908.186 FPS
29507 frames in 5.0 seconds = 5897.576 FPS
28621 frames in 5.0 seconds = 5711.936 FPS
29327 frames in 5.0 seconds = 5864.024 FPS
29327 frames in 5.0 seconds = 5855.244 FPS
X connection to :1.0 broken (explicit kill or server shutdown).

Hope that helps.

---

### Post by Commander Bosko on 2008-04-10
Also you were right, the -opengl tag on Warcraft 3 made it run perfectly, however the mouse screws up from time to time.  But Guild Wars still dosn't work

---

### Post by Commander Bosko on 2008-04-11
Bump?

---

### Post by Commander Bosko on 2008-04-11
I think I'm just going to give up on gaming with Linux.  It appears to be more complicated for it to be worth it.

---

### Post by Commander Bosko on 2008-04-15
Update... I can't just give up, I'm just too damn tenacious.  However I've come to the conclusion that it's my ATI graphics card.  Games run on linux without wine run even worse... so either I'm screwed and cant run any 3d games on linux, OR I will have to pray that they update my drivers.

---

### Post by badrunner on 2008-04-15
Both warcraft 3 and guildwars should perform very very well under wine (i have both here and they work great).

However, there are quite a few problems with the proprietary ati linux driver, and a lot of wine users have problems with this card.

Does running "glxinfo" at a terminal print a line that says "Direct Rendering: Yes", if not then you dont have 3d hardware acceleration working (should be enabled through the restricted drivers manager in Sytem->Administraion).

---

### Post by Commander Bosko on 2008-04-15
It says 

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

I've enabled the restricted driver.  Is there another way to fix this?

---

### Post by badrunner on 2008-04-15
> **Commander Bosko said:**
> It says 

direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

I've enabled the restricted driver.  Is there another way to fix this?

If it says that then hardware rendering isnt enabled, if the restricted driver manager thinks the fglrx (i think thats the driver for ati) driver is being used then, then there must be a problem with you xorg.conf, unfortunately i cant help more with that as i dont have an ati card in any of my machines.

You could try running this to see if it prints more info:

```
LIBGL_DEBUG=verbose glxinfo
```

But i have no idea what that might show.

You might be best starting a forum post in one of the other forums, possibly "General Help" or "Hardware and Laptops", and if you have success resolving the 3d issue, you might find guild wars starts working well.

Just to double check, are you passing "-dx8 -dsound" to the guild wars command, i was never able to get it to work well without those.

---

### Post by Commander Bosko on 2008-04-15
I'll try posting in another forum, also 

```
LIBGL_DEBUG=verbose glxinfo
```

didn't give me any new information.  Also I always ran GW with those tags.

---

### Post by flaggh on 2008-04-19
The only advice I can give is to ditch the ATI card and pick up something a little more linux friendly.  I have wasted days trying to get Direct Rendering to work with my ATI card and finally gave up, and although I'm no expert, I'm not a total noob.  

If that advice doesn't sit well with you, at least remember to backup your xorg.conf file before you screw around with it,

---

