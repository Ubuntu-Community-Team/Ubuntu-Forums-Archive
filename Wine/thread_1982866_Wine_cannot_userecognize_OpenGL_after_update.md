---
title: "Wine cannot use/recognize OpenGL after update"
date: 2012-05-19
forum: Wine
---

### Post by Orpheon on 2012-05-19
I've used wine for a very long time, and one of the things I've used it  for was for a small game made in game maker which I like very much.
Today, an update came through, wanting to update opengl. I accepted, and restarted the system as was required.
Wine is now incapable of running that game (Which is 2d, btw). I tried running it in the console, with this output: [URL="http://pastebin.com/ckAS7G7z"]http://pastebin.com/ckAS7G7z
[/URL] (The missing sound server is normal and on purpose. That is not the problem)
```
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D8 is not available without OpenGL.
```I first went to the IRC, here is what I got from there: [http://pastebin.com/uRd6q7G0](http://pastebin.com/uRd6q7G0)

OpenGL native works fine, my own programs in it had no problem running. I then found this: [http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html](http://www.noobslab.com/2011/09/nvidia-drivers-for-ubuntu-1110-oneiric.html)
and followed it, because for some reason I didn't have nvidia-current.

Didn't fix it.

Subsequent visits to IRC and googling revealed that maybe I was lacking a proper 32 bit opengl, so I tried completely uninstalling wine (and deleted the .wine and stuff directories), and reinstalling as many things I could find that had anything to do with opengl. Then reinstalling wine.

Didn't fix it.

I even tried getting a copy of a libgl.so which I am not sure whether it's 64- or 32-bit I once used for my code and put it in the /usr/lib32, in hope that it would answer wine's summons.

Didn't fix it.

So now I'm sort of stuck. Does anyone have any idea what could be doing this, and more importantly, how to fix it?


PS: I'm on a Ubuntu 12.04 64-bit, nvidia, wine version 1.4.

---

### Post by oldos2er on 2012-05-19
Moved to Wine.

---

### Post by Orpheon on 2012-05-19
Ok.

Also bumping (again).

---

### Post by Tweak42 on 2012-05-21
I had a problem with wine like this back when running 11.10  Here's a thread that may point you in the right direction:   

[http://forum.winehq.org/viewtopic.php?p=66842&sid=4a823d1aad88dd9925d5a4747eb4d94b](http://forum.winehq.org/viewtopic.php?p=66842&sid=4a823d1aad88dd9925d5a4747eb4d94b)

---

### Post by cwwilson721 on 2012-05-22
It's EASY:

INSTALL THE UBUNTU NVIDIA "ADDITIONAL DRIVERS"

Nvidia doen't include the OpenGL stuff anymore, but the OS Driver does.

Why make it hard?

Uninstall any of the stuff you've already done, and reboot, then install them.

Easy.

Uninstalling/reinstalling wine has NOTHING to do with OpenGL working on your system (wine is a PROGRAM, that calls OpenGL functions that the SYSTEM provides thru graphics "drivers")

---

