---
title: "Can't seem to install 7.04 (garbled screen)"
date: 2007-05-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by jenny9580 on 2007-05-04
Allow me to preface this post with the fact that I am very much a Linux newbie.. I've been trying to get it installed so I can learn more about it. Once I can get it installed, I expect to set up  camp in the newbie forum for awhile.. but getting it installed has been the hard part so far. :/

I have tried to find information on this problem to no avail.. I really hope this isn't a double post of a known thing.

This is my hardware config:
Athlon 64 3000+
Asus A8N-E motherboard (NForce4 chipset)
NVidia 7800GT
Dell 2007WFP DVI (1680x1050)
2gb ram
2x SATA2 drives
1x IDE cd-dvd drive

I've tried installing Linux on it multiple times, and the same problem seems to show up every time, regardless of the distro. I think one was Fedora x64 because it came with a school textbook, another was an older version of Ubuntu x64 that I'd downloaded.

I pop in the CD, and select install. It plays a sound, gets to what I'm guessing is a splash screen, but it is all tan and garbled looking. Nothing happens after that point - I can move around the cursor (which looks fine), but that's about it.. it just stays there forever. If I select the "safe gfx" option (#2 I think), it will boot up and it goes all the way to the desktop. From there, I can do whatever I want (use the Web and poke around menus).

I once attempted to install using command-line stuff so I wouldn't have a splash screen (this may have been with Fedora), but once I rebooted I got the garbled screen again and couldn't get past it.

I'm not sure how to get this to work.. is it possible that my video card has something wrong with it, or am I missing a setting somewhere? I've been reading about issues getting 1680x1050 resolutions to work.. could it be related? Are there any known issues with NForce or SATA2? I'm really at a loss as to where to go next with this.. I don't really know enough to troubleshoot it properly.

---

### Post by dabl on 2007-05-04
I'd say "video-related" is the category that your situation goes in.

I would use the "Alternate" installation CD, and when you get to the beginning of the xserver configuration script, the first screen asks if you would like to have it auto-detect your graphics card, you should say "no", and then the next screen puts up a list of graphics systems/vendors, and on that one you should choose "vesa", and then you can proceed with your keyboard, mouse, and screen configurations, choosing the default settings unless you have knowledge of a special setting that one of them needs.  On the screen settings, pick only a couple of resolutions that you think you'll want (and that your monitor or LCD supports), like 1280x1024 and 1024x768 -- go ahead and try 1680x1050 along with the others.

Alternatively, if you have your system installed but it only works in text mode, you can accomplish the same thing in the console by entering ```
sudo dpkg-reconfigure xserver-xorg
```  You will get the same configuration script.  When it is finished, enter ```
startx
``` and you should get a GUI desktop.

Once you have a functioning GUI, you'll be able to search for further information about your hardware combination, versus needed xorg.conf settings.  I personally have a GeForce 7900 GS PCI card that must be a lot like your 7800, but it is on an Intel motherboard with Intel processor, so I don't know the fine points of your Asus mobo.  I would encourage you (once you've got a VESA display system working) to try running the Envy script installer for Nvida and ATI, downloadable from here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

No guarantees, but he says it works for Feisty.

HTH:)

---

### Post by jenny9580 on 2007-05-04
Thank you.. I will try that when I get home from work. :) Luckily it's a fast connection here so I can grab the alternate CD here. :)

---

### Post by jenny9580 on 2007-05-04
I tried to install with the alt cd.. I allowed it to automatically set up partitions so I wouldn't break anything.. I didn't notice anything interesting during the install. Picked keyboard, timezone, username.. that was about it. When I reboot, it just says "Error loading operating system" and won't do anything else. It never got to a point where I could tell it to detect my video settings.. any ideas?

---

### Post by ronocdh on 2007-05-04
> **jenny9580 said:**
> I tried to install with the alt cd.. I allowed it to automatically set up partitions so I wouldn't break anything.. I didn't notice anything interesting during the install. Picked keyboard, timezone, username.. that was about it. When I reboot, it just says "Error loading operating system" and won't do anything else. It never got to a point where I could tell it to detect my video settings.. any ideas?
Are there other OSes on this computer? Were you trying to dual boot? Do you get the GRUB screen, and then once you choose Ubuntu, it throws the error?

---

### Post by jenny9580 on 2007-05-04
nevermind this post..

It looks like I've gotten it working well enough that I can now migrate over to the Newbie forum.. thanks so much for all of the help. :)

---

