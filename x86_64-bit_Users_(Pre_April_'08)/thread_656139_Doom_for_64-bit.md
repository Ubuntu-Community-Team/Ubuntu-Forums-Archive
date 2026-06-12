---
title: "Doom for 64-bit"
date: 2008-01-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by BreathEasy on 2008-01-02
I suppose I could have asked this in the Games forum, but this question seems more appropriate here since it deals specifically with 64-bit systems.

I'm looking for a Doom port, available for Linux, which can be compiled on 64-bit systems. Doomsday currently doesn't compile in 64-bit, only 32-bit. Same for ZDoom. It's surprising how difficult it is to make it work in 64-bit. I'd settle for .deb packages, but I want something which uses recent technology too (ie. OpenGL, widescreen resolution support, etc). Any help?

---

### Post by SatanClaus on 2008-01-02
Try to use prboom it works fine with 64bit on Feisty with opengl.

---

### Post by BreathEasy on 2008-01-02
> **SatanClaus said:**
> Try to use prboom it works fine with 64bit on Feisty with opengl.
That did the trick. There's so many ports these days I didn't want to try them all. Thanks!

:guitar:

---

### Post by crjackson on 2008-01-02
> **SatanClaus said:**
> Try to use prboom it works fine with 64bit on Feisty with opengl.

Is prboom a full game, or something else needed to play?

---

### Post by BreathEasy on 2008-01-03
> **crjackson said:**
> Is prboom a full game, or something else needed to play?
Prboom is just an engine, like Doomsday, LXdoom and many other ports. They're all reimplementations of the original Doom game, but only contain the engine part; you need at least one additional .WAD from any of the old Doom games, which can include the shareware version of Doom.

Turns out, if you install prboom from the repositories, apt/synaptic will also install freedoom, which is basically just a .WAD file containing a free implementation of Doom using different art, sound and music. I suppose it's installed so that the engine has at least something to work with, but you can just add your own proper WADs afterwards.

---

### Post by khensucat on 2008-01-03
This sounds pretty interesting. I have the Doom Trilogy game here. So, I would install that, and then just drag the was files from the CD into the game directory?

---

