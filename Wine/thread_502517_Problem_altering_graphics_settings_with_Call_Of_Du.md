---
title: "Problem altering graphics settings with Call Of Duty 2 in Wine"
date: 2007-07-16
forum: Wine
---

### Post by punky on 2007-07-16
I managed to get COD2 installed and multiplayer runs fine.

However it starts in 640x480 mode (my linux desktop runs in 1024), When I alter the resolution (or anything else like reset to optimum settings, DirectX or textures), and click apply, the game just quits out.

Does anyone know what's going on or suggest anything so I can debug this?

I've tried running it in terminal to see if it throws any error messages up, but I can't seem to get it working via terminal (have to click the shortcuts it created)

Cheers :)

---

### Post by ominousluv on 2007-08-17
I am having the same problem, and I cannot figure it out.

---

### Post by Moustacha on 2007-08-17
open /path/to/install/Call of Duty 2/main/players/yourplayername/config.cfg (or config_mp.cfg for mp) and edit the settings in there.
find "seta r_mode" and change it to the resolution you want
eg
seta r_mode "1440x900"
or
seta r_mode "1024x768"

---

### Post by punky on 2007-08-19
Thanx for the tip. I have tried altering the config file. It changes, but it crashes right at the end of loading the level.

I'm guessing its a graphics driver/card problem (works fine in XP though).

I'm using an x1600XT

---

### Post by Moustacha on 2007-08-19
might be because of ati drivers, they seem to cause a lot of other problems. I'm using a 7600GT and it runs perfect. Have you got the latest wine also, 0.9.42?

---

