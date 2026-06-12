---
title: "Drops refesh rate to 50hz"
date: 2008-07-27
forum: Wine
---

### Post by senectus on 2008-07-27
After closing a game (Fallout 2) in wine it always drops the refresh rate back to 50hz, which is really annoying.

Is there any way I can tell WINE to put the screen back to 77Hz when it closes the game?

---

### Post by LinuxRocks713 on 2008-07-28
> **senectus said:**
> After closing a game (Fallout 2) in wine it always drops the refresh rate back to 50hz, which is really annoying.

Is there any way I can tell WINE to put the screen back to 77Hz when it closes the game?

System >> Preferences >> Screen Resolution

or use xrandr to fix it, though you must recompile the X Windowing System to include it (100% chance of failure).

---

### Post by senectus on 2008-07-29
Not really what I meant... I know how to manually later the refresh rate, but I want WINE to recognize that it changed the refresh rate and I want it to not do that.

I'm pretty sure it happens because the resolution that fallout2 runs at is lower than what I have gnome running at...

---

