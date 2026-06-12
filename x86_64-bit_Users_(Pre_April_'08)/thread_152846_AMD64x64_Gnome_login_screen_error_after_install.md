---
title: "AMD64/x64 Gnome login screen error after install"
date: 2006-03-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by smiley2billion on 2006-03-30
Hello all,

I tried searching on here for an answer to this question but didn't have any luck finding one :(

I recently got a new AMD Athlon 64 X2 4400+ and an Evga motherboard to go along with it.  I've installed and played with Windows XP x64 and it works fine, now I'm ready to go back to my Ubuntu ways x64 style. But here's the issue:

Everything about the install seems to go fine... right up until I reboot for the first time to what appears to be the gnome login screen, except I can't see it.  The screen is all garbled and you can't really make out anything at all excpet for the brown color.  My first guess would be that it's an nvidia (Evga 6800 GS OC PCIe) driver problem.  The issue with this is I haven't the first clue about how to get a new driver for it.  I know how to use the terminal and I'm not afraid to, but where do I go from what appears to be a jacked up log-in screen?  Please note that this happens when Ubuntu is fully installed and should be ready for me to log-in. I've done lots of 32bit (and a few 64bit for my friends) installs of ubuntu before.  I'm also using the pressed CD sent to me from Ubuntu, so I'm pretty sure it's not an issue with the media being bad (I've tried a few different discs as well of the x64 version as well).

I hope I've given enough info, if not, please req. more.  Also, just out of lazyness does anyone have a link to a good guide about using the "32bit wrapper" method of getting 32bit binaries to run on a 64bit setup? Is that even necessary anymore? This is my first 64bit setup. TIA!

PS.  I have NOT tried to install the 32bit version on this box, so it *might* not be completely tied to it just being a 64bit install.

---

### Post by smiley2billion on 2006-03-30
After more digging around on here I think I found my answer:

From Jason_25:

"This is a very common problem with the older versions of the nv driver. The 6600 isn't supported by it. CTRL-alt-f1 will get you to the terminal. Then type
Code:

sudo dpkg-reconfigure xserver-xorg

and enter your password. Choose sane options until you get to the driver section. Instead of nv, choose vesa. Then
Code:

sudo /etc/init.d/gdm restart

That will get you going until you get into the gui."

---

