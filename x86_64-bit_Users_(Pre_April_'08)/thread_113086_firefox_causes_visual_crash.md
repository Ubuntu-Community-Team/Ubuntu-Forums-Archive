---
title: "firefox causes visual crash"
date: 2006-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by OakRand on 2006-01-05
This one is somewhat hard to explain

Sometimes when using firefox it messes up the visual output. Colors and lines will appear all over the browsing window and when I shut it down the effects have perverted the screen. xterms or any other other windows get affected in the same way. The systems is still running but is pretty useless if I can't see anything.

Logging out fixes the problem.

Has any else had this?

I posted in the AMD 64 forum because that's what I'm using, and with the plethora of other problems regarding this architecture 's distro, I assumed it had something to do with it.

---

### Post by FluffyElmo on 2006-01-05
I haven't seen this myself though it sounds like an issue with Xorg. A few general questions that might help narrow down the problem.

What version of Firefox? What video card and motherboard chipset are you using? Also are there any errors in */var/log/Xorg.0.log* or */var/log/messages*?

---

### Post by OakRand on 2006-01-05
No error messages in /var/log/Xorg.0.log or /var/log/messages.

Firefox 1.0.7.

Motherboard: A8N-SLI Premium.

Videocard: nVidia GeForce 6200

---

### Post by FluffyElmo on 2006-01-05
There have been issues with Nvidia PCI-Express cards and amd64 in the recent past so I'd suggest updating your video driver to their latest release to see if it helps ([http://ubuntuforums.org/showthread.php?t=75074]("http://ubuntuforums.org/showthread.php?t=75074")).

If that doesn't help you may want to try posting at the Nvidia Linux forums ([http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14]("http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14")). 
A quick search of the forum doesnt turn up your exact problem but there are issues with similar hardware that might give you someplace to start. 

There should be a wider range of people there who could help since your problem is not necessarily Ubuntu specific but likely tied to Nvidia driver issues. 

Good Luck!

---

### Post by OakRand on 2006-01-05
Cheers.

I'll give those ideas a try and see what happens.

---

### Post by OakRand on 2006-01-16
Seems to have worked. Cheers.

---

### Post by FraM on 2006-02-11
I have the same problem on Ubuntu 5.10 AMD64.

The only solution it's shutting down X server and restarting it.
I've noticed that the problem affects only Firefox when opening a page with dinamic contents (such as Flash, that I haven't installed for known problems, or Java).

I cannot install official Nvidia driver since 8179 module is incompatible with kernel module API (7667). I use kernel 2.6.12-10.

Any idea?

---

### Post by FluffyElmo on 2006-02-11
I'm not sure if I understand the problem. If you install using the Nvidia installer (method two in the link from above [http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)) it will ask to uninstall the old kernel module (7667) and compile/install a new one.

If that doesn't work and you've installed the driver using Synaptic, maybe try uninstalling back to the vesa or nv drivers and then running the official installer?

---

### Post by FraM on 2006-02-12
[QUOTE=FluffyElmo]I'm not sure if I understand the problem. If you install using the Nvidia installer (method two in the link from above [http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)) it will ask to uninstall the old kernel module (7667) and compile/install a new one.
[/QUOTE]

Yes, I followed tseliot's guide, method 2. But X server didn't start because "kernel module API (7667) mismatch driver version (8179)". tseliot is still searching  a solution for this problem.
In the while he suggests to follow method 1.

I had the same problem on Ubuntu 5.04, both running nvidia-glx and Nvidia 7667 official driver.

---

