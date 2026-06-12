---
title: "[SOLVED] screen flickering in kotor2"
date: 2008-07-19
forum: Wine
---

### Post by Adahn on 2008-07-19
the suspects:
hardy, 8.47 ati drivers using envy, wine 1.1.1

Install went fine, using .isos ripped from my discs. Patched game, then installed cracked exe and HD movies

I initially had sound no sound ingame, but somehow fixed them (using alsa now).

I can run/play the game in a virtual window at any resolution, but there is random screen flickering. I've tried setting vsync on/off both in game and forced in drivers.

If I try to run the game w/o virtual desktop emulation I'll get 'out of range' errors on the monitor, regardless of resolution settings in game config.

I'm not using any custom .dlls.

edit:
the ingame movies don't flicker, but also don't run very well, as if my system is too slow.

---

### Post by Akingboy on 2008-07-19
System --> Settings --> Appearance (Or whatever it is in english. 4th lowest option) --> Visual Effects --> Nothing = Fixed!

---

### Post by Adahn on 2008-07-19
Fixed indeed!
Thank you!

---

### Post by ajgreeny on 2008-07-19
I think you may need to reset all your compiz settings if you use that way of turning off compiz and have used custom settings from Advanced Desktop Effects.  Much simpler to turn it off temporarily using compiz-switch from [here]("http://forlong.blogage.de/article/pages/Compiz-Switch").  One click to turn them on, the next click to turn off.  All settings stay exactly as you left them.

---

### Post by Adahn on 2008-07-19
> **ajgreeny said:**
> I think you may need to reset all your compiz settings if you use that way of turning off compiz and have used custom settings from Advanced Desktop Effects.  Much simpler to turn it off temporarily using compiz-switch from [here]("http://forlong.blogage.de/article/pages/Compiz-Switch").  One click to turn them on, the next click to turn off.  All settings stay exactly as you left them.

Thanks for the tip.

---

### Post by Fabled One on 2011-04-23
Also try disabling multi-core rendering.

---

