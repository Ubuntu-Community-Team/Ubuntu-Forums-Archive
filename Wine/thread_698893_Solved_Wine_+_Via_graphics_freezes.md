---
title: "Solved: Wine + Via graphics freezes"
date: 2008-02-16
forum: Wine
---

### Post by scottopoly on 2008-02-16
Ok, so I had teh problem where ANY wine command freezes the laptop. Run wine in console, I would see it started to create .wine, then the mouse would not even move.

Essentially this is the fix that worked for me: [https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)
That is, I changed to the drivers from Viaarena (mine are for the CLE266 class of cards, I have an Averatec 3200 series, It has Via Unichrome S3 something something. xorg.conf called it VT8378, could be correct, who knows)

Also this thread tipped me off to the answer, though he has a different workaround: [http://ubuntuforums.org/showthread.php?t=593043](http://ubuntuforums.org/showthread.php?t=593043)

For the record, I tried (these are package names from synaptec) xserver-xorg-video-via, xserver-xorg-video-openchrome, and xserver-xorg-video-unichrome, and here are the results: 

**-via:** (this is the one that came installed by default)
glxinfo: segfaults right after it prints "GL_EXT_texture_lod"
glxgears: about 490 fps
wine: hard freeze
enabling visual effects in gnome: fails

**-unichrome:**
everything exactly the same as -via. hmm.
[B]
-openchrome:[/B]
glxinfo: hard freeze
glxgears: hard freeze
wine: hard freeze
vis effects: didn't bother
[B]
drivers from Viaarena:[/B]
glxinfo: works!
glxgears: 450 fps (hmm)
wine: works!
vis effects: nope.
BUT, anytime openGL anything is invoked (wine, glxinfo, or glxgears), I get the following list of warnings. Oh well, Rome wasn't built in a day.
```
libGL warning: 3D driver claims to not support visual 0x22
libGL warning: 3D driver claims to not support visual 0x23
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x25
libGL warning: 3D driver claims to not support visual 0x26
libGL warning: 3D driver claims to not support visual 0x27
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x29
libGL warning: 3D driver claims to not support visual 0x2a
libGL warning: 3D driver claims to not support visual 0x2b
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x2d
libGL warning: 3D driver claims to not support visual 0x2e
libGL warning: 3D driver claims to not support visual 0x2f
libGL warning: 3D driver claims to not support visual 0x30
libGL warning: 3D driver claims to not support visual 0x31
```

Edit: using Gutsy 7.10 here

---

### Post by scottopoly on 2008-02-16
And I just gotta say whoa cool!! I just installed a small program in Wine and it works!! Holy ****!! That's so cool. I've never used wine before. I thought it would be like hard and complicated and ****.

---

### Post by scottopoly on 2008-02-17
But then VIDEO doesn't work!! :evil::evil::evil::evil:
I am frustrated by linux.

So I try to reinstall the old via driver in synaptic. Things crashed. Now I'm in some weird state where:
glxinfo: works, but direct rendering no.
glxgears: they turn about 1 or 2 fps, but reports 100ish fps
wine: works
videos: works.

So, wtf. I can't have it all. Linux, go home.

---

### Post by mandlar on 2008-03-28
I'm having the same problem: Wine keeps crashing anytime I try to run anything with it on my Averatec 3250.  I'm running 7.04.

Have you had any further luck?

---

### Post by scottopoly on 2008-03-30
Actually, I switched back to windows :popcorn:

One of the biggest reasons was stand-by mode not working. 

As far as wine and gfx drivers, well there's a lot of info above to get you going. I got wine working, but then couldn't watch videos. (That's what I meant when I said "VIDEO" wasn't working). I'm honestly not sure what driver or lack thereof was in use at that last stage. I think videos might have worked there too. 

Good job on the averatec. It's a nice computer!

---

