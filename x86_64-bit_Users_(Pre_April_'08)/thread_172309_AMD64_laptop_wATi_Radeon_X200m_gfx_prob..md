---
title: "AMD64 laptop w/ATi Radeon X200m gfx prob."
date: 2006-05-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by usernamed on 2006-05-08
Hi,

Having followed the excellent how-to elsewhere on these forums, I have installed the fglrx drivers for the integrated ATi graphics on my laptop's motherboard.

On the surface, everything appears to be working, if I type fglrxinfo I get the following output:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series SW TCL Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

```

I'm not seeing any errors in the X server log files and I'm not getting any output that suggests there is a problem.  However, a game (Darwinia) that runs happily at 25fps in Windows on the same hardware, is crawling along at 1fps in Linux.  

I'm able to run fgl_glxgears, and get approximately 160-190 FPS.  Can anyone else out there with the same graphics setup post what they're getting when they run fgl_glxgears?  Does the output I'm getting from fgl_glxgears suggest that 3d acceleration is working?  My experience with Darwinia would suggest that it isn't, but I don't have any other OpenGL software, and I don't have any prior linux experience with this gfx chip to compare it against.

Any assistance would be gratefully recieved!

---

