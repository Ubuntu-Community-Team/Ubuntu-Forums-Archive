---
title: "Gnome won't start..."
date: 2008-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by kohlrak on 2008-04-07
I installed ubuntu this weekend. Had some trouble with drivers (plan on fixing them if i ever get gnome to start), and one time i had to shut down and had to hold down the power button (forget why). Next thing i know, i boot it up again, and low and behold the screen resizes and stuff, but gnome isn't there. It's just black, and i can type stuff in. It's like the terminal, only i can't send any commands. I figured that i could easily just delete the linux swap and the other ubuntu partition and re-install it and that'd fix it. Well, it didn't quite fix it. Fresh new install of ubuntu does not fix the problem. I don't know what to say other than that and that i have a Vostro 1000 by dell. Does anyone have any ideas?

SOLVED:

Bad ati drivers... don't know why it didn't happen the first time. Just use dpkg-reconfigure kserver-xorg as either sudo or root. Set driver to vesa, then use restricted drivers menu to enable it again (which should be a good version).

---

