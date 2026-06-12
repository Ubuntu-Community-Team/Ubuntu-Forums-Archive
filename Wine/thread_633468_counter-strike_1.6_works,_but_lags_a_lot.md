---
title: "counter-strike 1.6 works, but lags a lot"
date: 2007-12-06
forum: Wine
---

### Post by flippykid on 2007-12-06
Well I am not sure why counter-strike 1.6 seems to lag so much, when I play dust2 I get around 20 - 30 fps, while when I used to use windows xp I would get a good 80 - 90 fps. I´m not sure why it´s doing this but I´m hoping someone here knows, I have an ati radeon 9000 pro 128 mb, with a 1.79 ghz intel single core. I installed steam and counter-strike properly, and I can run it with no problem other then lag. I´m running using alsa sound and opengl ingame at 800 - 600 resolution. If there is anything I missed tell me and I will add it on.

---

### Post by boast on 2007-12-06
and compiz is not running, correct?

---

### Post by Nehallyn on 2007-12-07
I'm not sure if it will work, but you can try tweaking the CS:S config:

[http://www.overclock.net/faqs/119786-how-adjust-many-css-cvars-better.html](http://www.overclock.net/faqs/119786-how-adjust-many-css-cvars-better.html)

Of course, make a backup of any existing config first!

---

### Post by flippykid on 2007-12-07
> **Nehallyn said:**
> I'm not sure if it will work, but you can try tweaking the CS:S config:

[http://www.overclock.net/faqs/119786-how-adjust-many-css-cvars-better.html](http://www.overclock.net/faqs/119786-how-adjust-many-css-cvars-better.html)

Of course, make a backup of any existing config first!

Thanks for the help, but I use counter-strike 1.6, not source =/, but thanks again

> **boast said:**
> and compiz is not running, correct?

Nope, It´s 100% off, but I still get lag, I´m not sure why though.

---

### Post by boast on 2007-12-08
for winecfg, is ALSA set to hardware emulation?


Do you get expected rates when doing glxgears?

---

### Post by chris062689 on 2007-12-08
After upgrading to .50, I had terriable FPS, try downgrading to .49 or even .46

---

### Post by mo0n_sniper on 2007-12-08
yes anything newer than 0.9.46 has a terrible lag in counter strike.I filled a bug report and someone told me to do some testing bun i am away from home and i can't right now

see:
[http://bugs.winehq.org/show_bug.cgi?id=10582](http://bugs.winehq.org/show_bug.cgi?id=10582)

---

### Post by nawitus on 2007-12-08
Are you using WINEDEBUG="fixme-all" which should increase FPS.

---

### Post by flippykid on 2007-12-08
> **nawitus said:**
> Are you using WINEDEBUG="fixme-all" which should increase FPS.

Alright, how do I make sure it launches with that? like what should it look like? I´m not sure since I have never really done this before.

> **mo0n_sniper said:**
> yes anything newer than 0.9.46 has a terrible lag in counter strike.I filled a bug report and someone told me to do some testing bun i am away from home and i can't right now

see:
[http://bugs.winehq.org/show_bug.cgi?id=10582](http://bugs.winehq.org/show_bug.cgi?id=10582)

How do i uninstall the new version of wine? Because I can´t seem to uninstall it, I just don´t know how to.

---

