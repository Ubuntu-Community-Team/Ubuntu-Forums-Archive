---
title: "PlayOnLinux and wine games heavy video lag"
date: 2012-12-02
forum: Wine
---

### Post by jccantele49 on 2012-12-02
Hello,

I'm experiencing an issue where all of the games I'm trying in PlayOnLinux are un-usably laggy. I've spent hours upon hours trying to troubleshoot this issue in the IRC channel with no luck.

The laptop is using nvidia-current version 304, with bumblebee. The laptop is a Samsung Series 7 Chronos (NP700Z7C-SP01US). The laptop has a Geforce 650M with 2 gigs of video memory.

My PlayOnLinux version is set to 1.5.18.

I've tried installing and re-installing the video drivers, and i've tried tweaking every feature I can imagine, with still no luck.

What should I do?

---

### Post by dak0 on 2012-12-03
Hello,

You have no problem running games on windows ?

---

### Post by jccantele49 on 2012-12-03
Windows works fine, yeah.

---

### Post by holastickboy on 2012-12-03
> **jccantele49 said:**
> Hello,

I'm experiencing an issue where all of the games I'm trying in PlayOnLinux are un-usably laggy. I've spent hours upon hours trying to troubleshoot this issue in the IRC channel with no luck.

The laptop is using nvidia-current version 304, with bumblebee. The laptop is a Samsung Series 7 Chronos (NP700Z7C-SP01US). The laptop has a Geforce 650M with 2 gigs of video memory.

My PlayOnLinux version is set to 1.5.18.

I've tried installing and re-installing the video drivers, and i've tried tweaking every feature I can imagine, with still no luck.

What should I do?

A quick search on the net shows that the laptop uses an Intel integrated graphics chip in the processor, as well as the nvidia Geforce 650m for when you need more power.

Have you activated the nvidia chip for the rendering? You can usually change what the active rendering chip is in the nvidia-settings (optimus  is the name nvidia uses for their hybrid graphics). Other than that, the 650m shouldnt be giving you much trouble.

Also, what game are you trying to play? Might need some tweaks, that's all ;)

---

### Post by jccantele49 on 2012-12-03
Thanks Holastickboy,

Those are along the same lines I was thinking.

I was aware of the dual GPU (hence, Bumblebee). But I'm unsure of how I can determine whether the nvidia GPU is kicking when I'm in game?

As far as tweaks go, I've tried every tweak imaginable from appdb for Borderlands and Diablo 3, with no luck. And my machine is way over spec for both games, and they perform fine in Windows.

---

### Post by wildmanne39 on 2012-12-03
*Thread moved to **Wine**.*

---

### Post by LillyDragon on 2012-12-03
Are you using Unity, btw? It really cuts into performance on some games or emulators with onboard chipsets. OpenArean/Quake III and Urban Terror hiccup like crazy, and ZSNES skips over half the frame rate. I prefer XFCE for games, it's far less fuss with fullscreen applications and even booting games is incredibly snappy.

---

### Post by jccantele49 on 2012-12-04
The problem happens with Unity, xfce, and Cinnamon

---

### Post by jccantele49 on 2012-12-05
any ideas? for bumblebee?

---

### Post by holastickboy on 2012-12-05
I wish I knew how to do it. Problem is that my laptop doesnt use an Nvidia GPU. It does, however, use an ATI HD5470, but it's not supported on Linux (never works) so I can't even test that for you. Anyone else have experience with switchable graphics?

---

### Post by Tweak42 on 2012-12-06
> **jccantele49 said:**
> any ideas? for bumblebee?

I don't have a optimus laptop yet, but have you tried [Primus]("http://www.webupd8.org/2012/11/primus-better-performance-and-less.html")

---

### Post by jccantele49 on 2012-12-07
Tweak42, your link helped me figure out the problem inadvertently! I wasn't using the "optirun" command to launch games. I didn't know that was required to use the GPU.

Btw, Primus looks awesome :D

---

