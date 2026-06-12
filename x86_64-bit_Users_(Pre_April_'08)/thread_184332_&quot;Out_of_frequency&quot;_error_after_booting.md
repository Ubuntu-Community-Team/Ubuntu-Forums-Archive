---
title: "&quot;Out of frequency&quot; error after booting"
date: 2006-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Pukis_m on 2006-05-29
Hi,
I've just installed Ubuntu 5.10 from Install cd. The problem is:
when I start PC, everything goes well until login screen- then monitor shows some strnage colours and a small error box: "Out of frequency range..."

(I can login (I hear a confirmation sound after pressing ENTER))

The problem is that I can't access desktop in any way. 

Restarting in Recovery mode and typing in Bash : xorgconf or even xor (tab) didn't give any results. 

What should I do?

System: amd 64, Leadtek GF6600 (non GT) 128 mb and IIyama  LCD (1280x1024)

Thank you

---

### Post by FluffyElmo on 2006-05-29
Sounds like your refresh rate is too high for your monitor. Hit *Ctrl->Alt->F2* for a text login and then look at your xorg.conf. Back it up (*sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak*) and then edit it using nano (*sudo nano /etc/X11/xorg.conf*). 

If you post the file then I or someone else may be able to help. There may be easier ways as well, I tend to do things the manual way...

---

### Post by FluffyElmo on 2006-05-29
I have a system very similar to yours, AMD64, 6600GT and an 1280x1024 LCD so just realized my xorg.conf may be of help. It's a little convoluted since I sometimes use TV-Out, I've also eliminated all modes other than the two I use. 

In my system it boots to 1280x1024@75hz with just the LCD connected and boots to 2048x768@60hz with the Monitor and the TV-Out attatched. I also use the official Nvidia drivers downloaded from nvidia.com so if you're using the open source drivers it may not help.

If you've installed the Nvidia drivers it may be worth just trying my xorg.conf in place of your own. Good Luck!

---

### Post by Pukis_m on 2006-05-30
Thanks, but changin few lines didn't show any good results...

BTW: I've found out, that xorg.conf says that my video adapter is 6600 GT, while it is 6600 TD... Maybe just a minot problem...

---

### Post by Pukis_m on 2006-05-30
Here's copy of unmodified xorg-conf

Hope, this helps you (and me, in that way;))

---

