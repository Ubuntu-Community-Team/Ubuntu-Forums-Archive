---
title: "Can't get HL2 working"
date: 2008-06-09
forum: Wine
---

### Post by agentsmith23 on 2008-06-09
So I installed steam using PlayOnLinux and that went well. Steam seems to work fine I can login and it brings up all of my games. So i selected HL2 single player and had it downloaded and installed. That seemed to work find also. Now when I try to start HL2 it beings up that valve logo and goes to the screen with the blury background thanit closes and I get this error:    "Engine Error" 
"Platform Error: module failed to initialize"

Please help!
If more info is needed please let me know.

---

### Post by agentsmith23 on 2008-06-09
Bump! Anyone?

---

### Post by kevin11951 on 2008-06-09
what are your computer conditions; 
hardware? *
wine version? *
drivers for video card that you installed? 
did you use envy? 
what version of ubuntu? *
did you fresh install, or upgrade?

just some key info, the most important are stared.

---

### Post by agentsmith23 on 2008-06-09
> **kevin11951 said:**
> what are your computer conditions; 
hardware? *
wine version? *
drivers for video card that you installed? 
did you use envy? 
what version of ubuntu? *
did you fresh install, or upgrade?

just some key info, the most important are stared.

Hardware
Toshiba Satellite P205D-S7436
Turion64 X2 Processor TK-53
2GB PC2-5300 DDR2
ATI Radeon Xpress 1200 128MB-319MB dynamically allocated w/FGLRX drivers installed manually not with envy.
hardy heron upgrade

---

### Post by kevin11951 on 2008-06-09
> **agentsmith23 said:**
> Hardware
Toshiba Satellite P205D-S7436
Turion64 X2 Processor TK-53
2GB PC2-5300 DDR2
ATI Radeon Xpress 1200 128MB-319MB dynamically allocated w/FGLRX drivers installed manually not with envy.
hardy heron upgrade

two things that jumped out are: UPGRADE, and manually installed drivers.

unless someone else tells you otherwise, i would do a fresh install and use envy to install drivers... half life 2 has a platinum rating! there is no way it shouldn't work... [http://appdb.winehq.org/objectManager.php?sClass=version&iId=2890](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2890)

---

### Post by QUILz on 2008-06-10
Have you tried testing any other games requiring 3D acceleration?

---

### Post by agentsmith23 on 2008-06-10
I have played Urban Terror. I know it doesn't use wine but it works fine. I will try to install some other games that will use wine and see how that goes.

I'm installing painkiller right now. I will let you know how that goes in a few minutes.

---

### Post by ktulu77 on 2008-07-05
I have exactly the same problem : Platform error : module failed to initialize. I am on a fresh install of ubuntu 8.04-1 x386 and I am using PlayOnLinux.

I have an Nvidia card and the 3d acceleration works well.

I have this problem with wine 0.9.58 and 1.0. It is the same problem.

---

### Post by izach on 2008-07-07
This is not a linux problem.  This problem occurs on windows as well.

I don't know what it is, but reinstalling Steam fixes it.

---

### Post by Sleaka J on 2008-07-07
Tried turning off the Steam In-game Community? That's the module that failed to initialise. It doesn't work in Wine.

---

### Post by brianfantastic on 2009-02-12
> **izach said:**
> This is not a linux problem.  This problem occurs on windows as well.

I don't know what it is, but reinstalling Steam fixes it.

Does reinstalling steam work on linux, or just windows?
HOw do you turn off the community thing?

---

### Post by lovinlinux on 2009-02-13
> **Sleaka J said:**
> Tried turning off the Steam In-game Community? That's the module that failed to initialise. It doesn't work in Wine.

this worked great, now im up and running. thanks :P

---

