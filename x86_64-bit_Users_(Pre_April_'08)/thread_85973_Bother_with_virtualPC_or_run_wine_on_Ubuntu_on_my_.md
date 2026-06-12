---
title: "Bother with virtualPC or run wine on Ubuntu on my ibook?"
date: 2005-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by boegeskov on 2005-11-03
I apologize for posting a request so similar to many others on the post, but I'm completely new to the mac work and the linux world.  I use my pc for webdesign, and there are some programs (such as swish) that I would like to run on my ibook, but I really dont want to bother with virtual PC.  From what i've been able to gather here at the forum, my other option would be to simply install ubuntu on my ibook (which i would like to do anyway) and use wine.  Any advice here?  Any help would be much appreciated, I'm glad to find such a community based operating system..this is what attracted me most, good software and good communtiy support.  Cheers.

---

### Post by ltmon on 2005-11-03
Wine is a tricky deal at best.  It's improving, but they are chasing a very difficult target.

Sometimes it works better than others, and often you need to screw around with configuration files to get a certain program to work.  Unless you have heard definite confirmation that the programs you wish to use work with wine, then I wouldn't bet the farm on it.

You could have a look at Codeweavers Crossover Office, which is a commercial version of wine.  They officially support a whole bunch of programs, so if it's on their list you wouldn't have to spend hours playing with wine configurations to get what you need to work properly.  Of course that costs $$, but it's not very expensive. 

L.

---

### Post by andrego on 2005-11-04
Your best (only) option is to use VirtualPC (or other x86 PC emulation/virtualization software such as BOCHS) to run Windows applications. 

Wine is a win32 (windows API) re-implementation for Linux and other Unix systems.  It is designed to run x86 binaries on x86 unix.  (Windows executables are compiled for x86 processors)  Since your iBook is PPC based, you won't be able to run Windows binaries under PPC linux.

Note that once apple makes the switch to x86, it will be possible to run Windows programs directly under MacOS X Intel using Crossover Office (comercial wine).

---

### Post by boegeskov on 2005-11-04
I see, thanks for the help.  It astounding that I actually understand your reply after this morning in the forum.  I've learned a great deal about how mac, windows and linux actually operate simply from trying to solve this problem, this is exciting, being the newb i am.  thanks again for the help. Cheers.

---

### Post by dombleu on 2006-01-06
[QUOTE=andrego]Your best (only) option is to use VirtualPC (or other x86 PC emulation/virtualization software such as BOCHS) to run Windows applications. 
[/QUOTE]

did some1 actually got Bochs working under linux PPC? I tried it this afternoon and all I got was a window in wich I could see something that looks like a frozen PC on startup.

I'm sure there is somthing do to about it.

Any experience?

Edit: ok, solved. The documentation on bochs site got my installation running. Sorry about that. Pretty slow, but running well....

---

### Post by Typhoon on 2006-01-08
[QUOTE=dombleu]did some1 actually got Bochs working under linux PPC? I tried it this afternoon and all I got was a window in wich I could see something that looks like a frozen PC on startup.

I'm sure there is somthing do to about it.

Any experience?

Edit: ok, solved. The documentation on bochs site got my installation running. Sorry about that. Pretty slow, but running well....[/QUOTE]

I think you should try qemu - in my experience it is much quicker than Bochs.

Cheers,
Typhoon

---

### Post by dombleu on 2006-01-08
Hmmmm, ok great. It works. Fast enough I think. But i'm unable to set the display at a decent resolution. It seems to be stuck at 640x768. 

Apparently you can higher resolutions with "bochs vga extensions". But the documentation doesn't tell much about how to achive those resolutions.

Is there some limitations on PPC host?

---

### Post by nicodds on 2006-01-09
[QUOTE=dombleu]Hmmmm, ok great. It works. Fast enough I think. But i'm unable to set the display at a decent resolution. It seems to be stuck at 640x768. 
[/QUOTE]

You just have to change the resolution of your guest OS.

I'm using a Windows 2000 installation via QEMU on my iBook at 800x600, while in Ubuntu I'm using 1024x768, but I can also use the same resolution as the host, just by changing it on the guest.

> 
Is there some limitations on PPC host?

You can't use resolutions bigger than that of the host.

Nico

---

### Post by Ptero-4 on 2006-01-09
Use qemu. Stay away from M$ V$PC at all costs.

---

### Post by dombleu on 2006-01-09
The only choice I got in my *marvelous* installation of win98, when popping the display properties dialog is 640x480. That's it. Maybe I could just try a copy of win2k instead. Or install a different video driver in win98, but what driver?

Windows is far from being my main os. But to have accessible the 3 main OSes on the market on a single machine is about the end of all compatibility concerns.

I currently run Mac on linux with Tiger. And would be more than pleased to have a direct PC emulation on Linux. 

I already tried to get VirtualPC on mol, but I think was asking too much. It doesn't work.

Easy things are dull aren't they?

---

### Post by dombleu on 2006-01-09
The only choice I got in my *marvelous* installation of win98, when popping the display properties dialog is 640x480. That's it. Maybe I could just try a copy of win2k instead. Or install a different video driver in win98, but what driver?

Windows is far from being my main os. But to have accessible the 3 main OSes on the market on a single machine is about the end of all compatibility concerns.

I currently run Mac on linux with Tiger. And would be more than pleased to have a direct PC emulation on Linux. 

I already tried to get VirtualPC on mol, but I think was asking too much. It doesn't work.

Easy things are dull aren't they?

---

### Post by nicodds on 2006-01-11
[QUOTE=dombleu]The only choice I got in my *marvelous* installation of win98, when popping the display properties dialog is 640x480. That's it. Maybe I could just try a copy of win2k instead. Or install a different video driver in win98, but what driver?[/QUOTE]

Strange. The driver is that for the video card emulated by qemu, as stated on the man page,  [B]Cirrus CLGD 5446 PCI VGA card or dummy VGA card with Bochs VESA extensions (hardware level, including all non standard modes)
[/B] and the right driver should be choosed automatically at installation time. Maybe the problem is at this point.

Nico

---

