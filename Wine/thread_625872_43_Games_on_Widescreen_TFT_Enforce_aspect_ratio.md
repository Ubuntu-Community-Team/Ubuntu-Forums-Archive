---
title: "4:3 Games on Widescreen TFT: Enforce aspect ratio?"
date: 2007-11-28
forum: Wine
---

### Post by *malagant* on 2007-11-28
Is is possible to run Games (for example Warcraft III) which do not support widescreen resolutions, on a widescreen TFT with an aspect ratio of 4:3? So that i have black borders on the left and right? I have an nVidia graphic card (Geforce 6800GT) and the windows driver has an option for this. Maybe it is possible with Linux too?

Ubuntu 7.10
Wine 0.9.49
latest nvidia driber (100.14.19)

---

### Post by cogadh on 2007-11-28
Use the Wine "Emulate virtual desktop" function and set it to a 4:3 resolution that will fit on your monitor. You won't get black borders on the side, but the game will run normally.

In Windows, I know the Nvidia driver has an option for setting a fixed aspect ratio that will force a 4:3 resolution with the black borders on the side, but I'm not sure if you can do that with the Linux driver. You might want to check through the Nvidia Linux driver readme for details on how you might do that:
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/index.html)

---

### Post by *malagant* on 2007-11-29
> **cogadh said:**
> Use the Wine "Emulate virtual desktop" function and set it to a 4:3 resolution that will fit on your monitor. You won't get black borders on the side, but the game will run normally.

Playing in "windowed mode" would be ok, but i need a way to prevent my mouse from leaving the virtual desktop, Otherwise, i cannot really navigate in the game.

> In Windows, I know the Nvidia driver has an option for setting a fixed aspect ratio that will force a 4:3 resolution with the black borders on the side, but I'm not sure if you can do that with the Linux driver. You might want to check through the Nvidia Linux driver readme for details on how you might do that:
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/README/index.html)

I cannot find something similar :/

---

### Post by MrHippocampus on 2007-11-29
If your monitor is connected via DVI you should be able to do this, if you run nvidia-settings (it should be in the applications menu somewhere, if not you can run it from a terminal), and then select DFP-0 (or something starting with DFP) from the box on the left hand side. Here you can select the GPU scaling method which should do what your asking for, "Aspect Ratio Scaled" is probably the one you want.

---

### Post by *malagant* on 2007-11-29
[X] Force Full GPU Scaling
[X] Aspect Ratio Scaled

works fine, thank you.

---

### Post by hugh on 2007-12-20
Found this solution via Google and it worked great. Thanks.

---

### Post by kaustikos on 2011-12-27
Is there a similar solution for non-nvidia graphics. I'm especially interested in Intel built-in cards. Please, explain in for me.

---

### Post by cwwilson721 on 2011-12-28
99 times out of a hundred, there is a setting ON THE MONITOR that does this.

Look for something in the 'Aspect' area (All monitor menus are different, just look for it)

---

### Post by boddhisatva on 2012-06-07
Thanks for this info! I've been playing stretched games on wine for ages, and it's so easy to fix this!

---

