---
title: "Glx error with nvidia-driver"
date: 2007-04-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mr. Sandman on 2007-04-15
After I installed the Nvidia-driver with a script Envy and made some modifications in xorg.conf, d.i. BusID:

Section "Device"
Identifier "NVIDIA Corporation NV34 [GeForce FX5200]"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "NvAGP" "0"
Option "RenderAccel" "Off"
Option "IgnoreDisplayDevices" "DFP,TV"
Option "NoRenderExtension" "Off"
Option "AllowGLXWithComposite" "Off"
EndSection

([http://www.albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_2](http://www.albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_2))

... I get this message:vanaggel@hapee:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x7a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

Can anybody help me with this?

Edgy Eft and XFX Geforce fx5200 AGP

---

### Post by Rospo Zoppo on 2007-04-15
If you use envy you don't have to edit xorg.conf, envy does it!

---

### Post by Mr. Sandman on 2007-04-15
> **Rospo Zoppo said:**
> If you use envy you don't have to edit xorg.conf, envy does it!

Yes I do!
AGP
See 3/4 off the page ([http://www.albertomilone.com/latest_....html#METHOD_2](http://www.albertomilone.com/latest_....html#METHOD_2))

Bye

---

### Post by Rospo Zoppo on 2007-04-15
That link doesn't exist...

---

### Post by BLTicklemonster on 2007-04-15
I was running the nvidia-glx from the non third party repos as found in synaptic.

BUT, what I just did was made sure I still had the nvidia.run drivers from nvidia's web site, booted to recovery, then installed. I was told that because I was "whatever reason it gave me" that it might not work, and I was given a choice to stop installation, or go ahead. Well, you know me... I went ahead anyway, and I'm back to normal. Well, ab-normal, but I can run glxinfo and everything is fine.

---

### Post by Mr. Sandman on 2007-04-15
> **Rospo Zoppo said:**
> That link doesn't exist...

Another try:  [http://www.albertomilone.com/latest_nvidia_udsf_edgy.html](http://www.albertomilone.com/latest_nvidia_udsf_edgy.html)

---

### Post by Mr. Sandman on 2007-04-15
> **BLTicklemonster said:**
> I was running the nvidia-glx from the non third party repos as found in synaptic.

BUT, what I just did was made sure I still had the nvidia.run drivers from nvidia's web site, booted to recovery, then installed. I was told that because I was "whatever reason it gave me" that it might not work, and I was given a choice to stop installation, or go ahead. Well, you know me... I went ahead anyway, and I'm back to normal. Well, ab-normal, but I can run glxinfo and everything is fine.

So you´re trying to say I must install nvidia-glx from de Synaptic-packages. (sorry my bad Englisch, im Dutch)

I also vond in my first post, Option "AllowGLXWithComposite "Off"
When I turned it "On" X dusn't start.

I shall try youre option later on. It's Bedtime in Holland!  :)

---

### Post by BLTicklemonster on 2007-04-15
No, I was using the synaptic version of nvidia-glx and had problems. what I did was download and install the version from nvidia.com from booting into recovery mode.

---

### Post by Mr. Sandman on 2007-04-16
> **BLTicklemonster said:**
> No, I was using the synaptic version of nvidia-glx and had problems. what I did was download and install the version from nvidia.com from booting into recovery mode.

Okay, thanks!

---

