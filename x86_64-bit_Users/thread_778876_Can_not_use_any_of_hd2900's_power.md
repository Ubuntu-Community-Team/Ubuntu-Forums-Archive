---
title: "Can not use any of hd2900's power"
date: 2008-05-02
forum: x86 64-bit Users
---

### Post by zaraki1311 on 2008-05-02
Hi, I have a Hd2900, with a amd athlon 5000+ black edition O.C to 3.01, and 4gb of ram, i have been trying to use any of the fancy graphical options or even just get out of the defaults that ubuntu installs with, but i can not. even after installing the ati drivers for their site, then i try to change the resolution the colours go to hell and so does the text, and then i try to use the fancy appearance stuff it tells me something to the effect that my gpu isn't powerful enough:confused:, so does anyone know how i might deal with this?

---

### Post by ASULutzy on 2008-05-02
Have you tried using Envy to install your drivers for you?

Some things that may be helpful, open up a terminal by going to applications, then accessories, then terminal.

type```
gksudo gedit /etc/X11/xorg.conf
```and paste what's in that file here.
Also from a terminal type```
glxinfo
``` and paste the output here.
Finally from a terminal type```
fglrxinfo
``` and again paste the output here.

There are probably other things that would be useful to look at, but that'd probably be the best place to start.

---

