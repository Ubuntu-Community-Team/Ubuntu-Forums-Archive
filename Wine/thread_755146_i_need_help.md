---
title: "i need help"
date: 2008-04-14
forum: Wine
---

### Post by Slayer225 on 2008-04-14
i need help i want to install and execute a online chat application called x-fire and wine doesnt support it. What other emulator programs are there for ubuntu??

---

### Post by cogadh on 2008-04-14
***_W_***ine ***_I_***s ***_N_***ot an ***_E_***mulator. 

Your only option for running Windows software in Linux, other than Wine, is to set up a virtual machine running Windows (VMWare and VirtualBox are the best IMO). However, there is or was an X-fire compatibile plugin for Gaim, I'm sure there are other native applications that can be used to do the same thing as X-Fire.

---

### Post by schtufbox on 2008-04-14
X-fire plugin for gaim/pidgin here: [http://www.fryx.ch/xfire/]("http://www.fryx.ch/xfire/")

---

### Post by Poyntz on 2009-06-08
> **Slayer225 said:**
> ...and wine doesnt support it.

The latest wine does support the latest xfire. It's just a bit dodgy and can crash if you take a step in the wrong place.

Install the latest wine:
```
sudo apt-get update && sudo apt-get install wine
```

Download winetricks:
```
cd; wget kegel.com/wine/winetricks
```

Install the following apps:
```
cd; sh winetricks ie6 && sh winetricks allfonts && sh winetricks comctl32 && sh winetricks comctl32.ocx
```

Please install the latest xfire from [www.xfire.com](www.xfire.com)

Run:
```
wine <xfire installer app>.exe
```
- follow the install process.

In order to run xfire without it crashing, please try my tutorial here:
[http://ubuntuforums.org/showthread.php?t=1181645&highlight=winetricks](http://ubuntuforums.org/showthread.php?t=1181645&highlight=winetricks)

All the best

---

