---
title: "medieval 2 Pixel shader direct 3d problem"
date: 2007-12-06
forum: Wine
---

### Post by doodger on 2007-12-06
oki, the game is installed, its no cd patched, now the problem is that it wont start :(

sudo wine medieval2.exe

Then a popup apears saying: This program requires graphic cards with pixelshader 1.1 or better. 

the error in the terminal is :

err:wine_d3d:DllMain VideoMemorySize is 0 but must be >0
fixme:win:EnumDisplayDevicesW ((null),0,0x34ae0c,0x00000000), stub!

This is bugging me, my graphic card meet requirement. 

Anyone could help?

---

### Post by cogadh on 2007-12-06
NEVER USE SUDO OR A ROOT ACCOUNT TO RUN WINE!!!!

From the WineHQ FAQ:
> NEVER run Wine as root. Doing so gives Windows programs (and viruses) full access to your computer and every piece of media attached to it. Running with sudo also has these same risks but with the added bonus of breaking the permission on the users ~/.wine folder in the process. If you have run Wine with sudo you need to sudo rm -rf ~/.wine and then run winecfg to set wine back up. You should run Wine as the normal user you use to login.
As for your other problems (after you have fixed the "sudo" issue), you need to first make sure that pixel shader support is enabled on the Graphics tab in winecfg. Then you need to make a registry edit to set the actual VRAM of your video card. See the Wine [Useful Registry Keys](http://wiki.winehq.org/UsefulRegistryKeys) page for details.

---

### Post by doodger on 2007-12-06
ORLY? I sometime use sudo for wine, i tought it made the software go faster(Noob error) I really, really, really cant supress .wine, ill just hope everything goes well.

As for the d3d problem, ill post when i get my sister off my computer.

---

### Post by doodger on 2007-12-06
Its still doing the same pop up, but one message is gone, the remaining one is 
fixme:win:EnumDisplayDevicesW ((null),0,0x33ae0c,0x00000000), stub!

Got an idea?:confused:

HO and how do i see my memory card vram?

---

### Post by cogadh on 2007-12-07
The "fixme" messages that Wine produces are just developer notes about missing or incomplete functions in Wine. They usually mean nothing to an end user and most applications will still run despite them. That particular message is pretty common and shouldn't impact the game at all (note I said "shouldn't").

As for your remaining issues, it would help to know what version of Wine you are using and what video card you have.

---

### Post by doodger on 2007-12-07
hmm, im using wine from the repository, the latest one.

as for my Graphic card, i use nVidia Corporation NV18 [GeForce4 MX 4000]

---

### Post by cogadh on 2007-12-07
If its from the default Ubuntu repositories, it is not the latest one. Those repositories have 0.9.46, while the latest is 0.9.50. To get the latest, follow the instructions here:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

However, the GeForce 4 MX series of cards do not have pixel shader capabilities, only the GeForce 4 Ti series had that ability (in the GeForce 4 generation). From the GeForce FX (technically GeForce 5) generation forward, all Nvidia cards have pixel shader capability. Your machine does not meet the minimum requirements for the game with a GeForce 4 MX, so it will not work, regardless of Wine.

---

### Post by doodger on 2007-12-07
argh dang. Well thx aniway. I'll just use OSX Boot camp i guess :)

---

