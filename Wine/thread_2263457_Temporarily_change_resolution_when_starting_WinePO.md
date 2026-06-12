---
title: "Temporarily change resolution when starting Wine/POL"
date: 2015-02-01
forum: Wine
---

### Post by IdoSC on 2015-02-01
Hi there,

I'm trying to play a game where the only graphics-related option I can modify is resolution, through WINE.
Here's the deal: I have 2 monitors. My standard resolution is 1280x1024. I'm using POL and configured WINE to start in an emulated desktop with the resolution of 1280x1024. 

The game was too slow (old GPU and heavy game), so I tried setting the resolution in-game to 1024x768. It worked great, except it went to Window mode, and out of full-screen.

So I tried setting WINE's virtual desktop to 1024x768 first. It obviously didn't help, since the virtual desktop no longer appeared "full-screen" (or otherwise, it didn't span all over my actual desktop, since the resolutions mismatched).

I did solve it by setting my actual PC's resolution to 1024x768, and then the game remained in full screen when starting it.

_**So heres what I want to achieve:**_ I want to make this process automated, by a bash script or any way possible. Whenever I start the game (the WINE application, the POL profile), the resolution would be changed to 1024x768, preferably on both monitors (keeping them mirrored), or otherwise it could be just one monitor of my choice. Upon exiting the WINE session, the resolution would be reverted to 1280x1024, mirroring the monitors.

Is this achievable somehow? Thanks in advance.

---

### Post by TheFu on 2015-02-01
xrandr is the shell + X/Windows command that can be used to change screen resolutions.  The device connection will need to be provided by the command to control each.

run **xrandr** alone while sitting on the box (not remote).  xrandr works on the X-server for the local machine even if you are connected remote. I can't check it now ... I'm remote and only see "Screen 0" - which is almost certainly NOT the answer for either of your screens. Something like DFP1 or DFP2 or CRT1 ... sorry - don't remember.  Anyway - yours will probably be different.

---

