---
title: "Regarding Wine and Proprietary drivers"
date: 2015-04-27
forum: Wine
---

### Post by mandarpowale on 2015-04-27
[COLOR=#141823][FONT=helvetica]I have an Asus HD7750 1GD5-V2 card and I am using AMD's Omega 14.12 drivers (proprietary). I have a few ported steam games (Dota 2 mainly) that run on my Ubuntu, I wanted to run Age of Mythology & Skyrim, so, it seems that I need Wine. But when I tried to install it , it said that my proprietary fglrx drivers need to be uninstalled. So what will happen if I proceed? Will I need to reinstall fglrx drivers once wine has been installed, or will I lost the ability to play my steam games?

Please reply asap

TIA

Mandar[/FONT][/COLOR]

---

### Post by ian-weisser on 2015-04-27
Windows drivers are not compatible with Linux. Period.
You need Linux drivers for your hardware.
Wine cannot use Windows drivers. Wine cannot use *any* drivers. Wine only knows about the hardware that the Linux OS makes available.

---

### Post by brian62 on 2015-04-28
> **mandarpowale said:**
> [COLOR=#141823][FONT=helvetica]I have a few ported steam games (Dota 2 mainly) that run on my Ubuntu, I wanted to run Age of Mythology & Skyrim, so, it seems that I need Wine. But when I tried to install it , it said that my proprietary fglrx drivers need to be uninstalled.[/FONT][/COLOR]

Whoa whoa, you are confused. In order to run Dota 2 on Linux, simply download Steam (either through repos or through Steam's website), install Steam, install Dota 2, and you should be good. You do **not**&#8203; need Wine to play Dota 2 on Linux.

---

