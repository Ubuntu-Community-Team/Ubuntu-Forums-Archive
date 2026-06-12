---
title: "Shaiya relic of mystra working"
date: 2012-07-10
forum: Wine
---

### Post by vanquishedangel on 2012-07-10
This is my setup that has shaiya working very well with good fps on a good, but crappy card. 

First my system specs:
HP DC5750
AMD Athalon x2 2.5 ghz
8 gig memory
Graphics card: Saffire ATI Radeon HD 6450
OS: Lubuntu 64 bit newest (12.04)
Wine: wine 1.4

I used all software from the repos, and for wine I run "sudo apt-get build-dep wine wine1.2 wine1.3 wine1.4" I also have playonlinux installed for ease

you should be able to figure out how to install and use playonlinux quite easily so that I will not go over in this post

however I will tell you what i installed into wine and how I set it up to get it running.

Here is what I installed:
corefonts
d3dx9
d3dx8
d3dx10 (my graphics card supports it)
d3dx11 (my graphics card supports it)
gdiplus

Here is how my wine registry is set up: (under HKEY_CURRENT_USER/Software/Wine/Direct3D)

DirectDrawRenderer gdi
Multisampling disabled 
OffscreenRenderingMode fbo 
UseGLSL disabled 
VertexShaderMode hardware 
VideoMemorySize (your video memory amount)1024 
VideoDriver (for ati cards only)ati2dvag.dll 
VideoPciDeviceID (for ati card radeon HD 6450, google to find how to get yours)0x6779 
VideoPciVendorID (for ati cards only, google to find yours)0x1002

I used gdi because the game works well with it, even saw a boost in fps from it compared to opengl

Settings for shaiya:
run in windowed mode (helps with lag and disconnect)
All others set to max
Resolution 1024x768

I installed the game directly from the shaiya website. If you run an old modem or have bad disconnect issue I adapted my  txqueuelen to 500 instead of 1000 (not sure if/how this will work for every one so avoid it)( if you want to try it, googl to find out how) to pick windowed mode for shaiya you need to run CONFIG.exe, you cant pick that option in game.

Deleting aeria ignite helps as well as disabling the p2p client in shaiya (akami)

Also after all things installed set wine to use windows 98 mode, it increased fps and stabilized. shaiya wont install if you do that before install. fps was real slow when set above 98 for some reason.

youtube video here:
[http://www.youtube.com/watch?v=8ke-d0mDAtA&feature=youtu.be](http://www.youtube.com/watch?v=8ke-d0mDAtA&feature=youtu.be)

Also an issue I have run into is when maintenance is happening it seems to freeze computer, but if you wait long enough it gives error message.

---

