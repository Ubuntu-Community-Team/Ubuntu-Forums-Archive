---
title: "quake wars resolution problem"
date: 2007-11-19
forum: Wine
---

### Post by ZERO_SHIFT on 2007-11-19
[CENTER]:confused:When changing my resolution settings the game restarts but I am still stuck with the old resolution, any ideas?:confused:
:confused::-|:-?8-[:o:mrgreen:
[/CENTER]

---

### Post by mbradlcu on 2007-11-21
couple questions:
can you change your resolution out side the game?
if so can you attach your /etc/X11/xorg.conf,,
and what vid hardware are you using.

thanks!

---

### Post by Sockerdrickan on 2007-11-21
Might be an unsupported resolution?
btw nice formatting in OP lol

---

### Post by amisus on 2008-01-24
I'm also having a resolution problem with this game.  I'm running Gutsy, and the native resolution is 1280X800.  I can't change the resolution here -- if I go to System--->Preferences to change it, it says it has changed it, but it hasn't

In the game, the resolution is set to a default of 640X480, and I cannot change the resolution because some of the screen is cut off.  The "apply" button is off screen, so I can select a new setting, but I can't apply that setting.

Anyone have an idea of how to remedy this?

---

### Post by Velociraptor on 2008-01-24
Not sure what your problem is, but have you tried turning off 3d desktop effects/compiz? I had problems with the demo because of this, and couldn't also move the mouse.

---

### Post by amisus on 2008-01-24
No, compiz isn't involved.  Before launching the game, I switched to Metacity.

---

### Post by mbradlcu on 2008-01-24
I forget how to set the specific resolution in the xorg.conf,, never seems to work when I just add eg: 1280x1024,,, anyway at least you can edit your ~/.etqwcl/etqwconfig.cfg

change the lines to look like the following for a windowed 1024x768 resolution,, at least from that point you can change the resolution.
seta r_fullscreen "0"
seta r_mode "4"

---

### Post by amisus on 2008-01-24
Thanks!  I was able to sort it out by editing that cfg file.

---

### Post by Virus666 on 2012-03-13
> **mbradlcu said:**
> I forget how to set the specific resolution in the xorg.conf,, never seems to work when I just add eg: 1280x1024,,, anyway at least you can edit your ~/.etqwcl/etqwconfig.cfg

change the lines to look like the following for a windowed 1024x768 resolution,, at least from that point you can change the resolution.
seta r_fullscreen "0"
seta r_mode "4"

That worked. Thanks...

---

### Post by ubudog on 2012-03-13
Back to sleep thread.

---

