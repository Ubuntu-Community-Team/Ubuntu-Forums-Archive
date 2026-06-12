---
title: "Having issues setting up DX9/11 in WINE for use with Steam"
date: 2018-08-04
forum: Wine
---

### Post by midgote on 2018-08-04
Hi, all! I've recently come into possession of a new laptop (X201T if anyone's wondering - quite the lovely little device imo) and the first thing I did to it was install Lubuntu to my SSD along with the latest version of WINE from WINEHQ. However, when I installed Steam to test if my personal favorite game was able to run (which it was able to do on the inferior L512 that I have, at least in the past), it failed to start, with the following error message

"Failed to initialize graphics.
Make sure you have DirectX 11 installed, have up to date
drivers for your graphics card and have not disabled
3D acceleration in display settings.
InitializeEngineGraphics failed"

I've looked around online for any drivers that I may need for my iGPU and any tips to get it to run properly, but even after installing literally every library possible for WINE and installing the latest firmware, I'm still having troubles. Note that I've tested this game on the same computer, but running Win7, and it works perfectly fine, so I know that it's not a hardware issue. Any advice?

---

### Post by dj--alex on 2018-09-23
DX10\11 games requires DXVK to run

DX9 must work with any drivers and systems. if al ok

---

