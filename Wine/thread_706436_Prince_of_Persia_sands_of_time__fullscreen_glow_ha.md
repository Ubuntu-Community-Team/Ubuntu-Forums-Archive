---
title: "Prince of Persia sands of time : fullscreen glow has vertical offset"
date: 2008-02-24
forum: Wine
---

### Post by oedipuss on 2008-02-24
The game runs nicely with wine 0.9.56, with one exception.
The fullscreen glow effect is displaced upwards about 1 cm. It is by no means a serious issue, but it seems like an easily fixable bug. 
Visually it looks like a faded and blurred version of the screen is copied about 1 cm above the normal screen, a bit hard to notice, but more easily seen in moving parts, such as the player model.
Changing the resolution doesn't affect the perceived distance, so I'm guessing it isn't a set amount of pixels.


I'm using a fresh wine 0.9.56 (made a new wineprefix for testing, default settings), with an nvidia 7600, latest drivers installed, in ubuntu gutsy. 
I remember seeing the exact same thing in some other game , a while back, but can't be more specific...

Can anyone else confirm it? Also, any ideas as to why and where this happens would be appreciated .

---

### Post by happyhamster on 2008-02-24
Yes, confirmed. Has been that way for quite a while too IIRC (at least since 0.9.51, probably much earlier). I believe the other Persia games show the same thing (Warrior Within and the Two Thrones).

I don't know what causes it, but the terminal shows zillions of "fixme:d3d..." messages. The only error I get is: "err:d3d_shader:shader_get_registers_used No texture bound to sampler 3"

I'm also using an Nvidia-card (7300gt) and the 169.09 driver.

---

### Post by oedipuss on 2008-02-24
Do you know what exactly this effect is ? I'd like to search wine's bug database for it, but other than fullscreen effect or glow I don't know how to describe it. 
Is it a pixel shader effect or something more specific ?

---

