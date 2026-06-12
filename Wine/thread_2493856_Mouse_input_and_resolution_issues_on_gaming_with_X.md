---
title: "Mouse input and resolution issues on gaming with X11 fractional scale enabled"
date: 2023-12-27
forum: Wine
---

### Post by cardidi on 2023-12-27
Hi,

I'm using Ubuntu 23.10 now. I have 2 4K monitors that one of them is 27 inch (Main display) and another one is 23 inch. So I enable x11 fractional scale and set 175% and 200% for 27 inch and 23 inch display.

I install some games from Steam (Civilization VI and City:Skylines) and Heroic Game Launcher (CONTROL) with Proton installed.

CONTROL (yeah, the name of game) feels great with a tiny issue that resolution system reported is larger than my physics resolution (Given is 4434x2468), and I can turn it to 3880x2160(4k) without any issue on full-screen mode. No-border mode force to render at 4434x2468.

But Civilization and Skyline is bad, they offers me 3880x2160 (4k) as the biggest resolution. So here has 2 behaviours:

 - If I choose to use that resolution on full-screen mode all UI elements looks as normal, but I can't click on them in their visual position. The way to click on UI is to offset cursor a liitle bit from it's visual position. 
 - If I choose to use taht resolution on window mode, window is smaller than my monitor, but everything runs ok.

I known that fractional scale on x11 is rendering screen in a higher resolution (render_resolution = monitor_resolution x 2 / fraction_scale_factor) and downscale into target resolution, but I still not figure out what's goingon. So if someone met same situation like me? How do you fix it?

---

