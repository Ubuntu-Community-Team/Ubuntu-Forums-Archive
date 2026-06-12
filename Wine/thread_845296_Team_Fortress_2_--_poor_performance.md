---
title: "Team Fortress 2 -- poor performance"
date: 2008-06-30
forum: Wine
---

### Post by cereal killer on 2008-06-30
AMDx2 4200 (2.2 GHZ)
3 GB Ram
Geforce 8600 GT

Running on Hardy with Wine 1.0.

I run it on Windows maxed with perfect performance. I understand since Wine is an emulator it is a bit harsher on your specs like all emulators are. However even if I turn down the resolution and all the settings to the point that the game looks like it's 10 years old, it still runs poorly.

Any suggestions?

---

### Post by cogadh on 2008-06-30
***W***ine ***I***s ***N***ot an ***E***mulator. It is an alternate implementation of the Windows API, a completely different animal from an emulator.

As for your issue, TF2 usually needs to be run in DX8 mode for best performance in Wine (though not the best quality). Modify the game's launch options to include "-dxlevel 80" then try running it again.

---

### Post by cereal killer on 2008-06-30
Bah, it's simply not worth it. If I have to jump through all kinds of hoops to get a game to run at inferior performance then I won't bother.

I'm puzzled though, because Warcraft 3 Frozen Throne isn't listed on Platinum list, but it works PERFECTLY. TF2 is on a list above WC3 yet it runs poorly.

---

### Post by 12pcwormburner on 2008-09-27
Actually, its quite worth. 

Simply enter -dxlevel 81 (yes....81) and tada!!

TF2 runs great, I would say it ran perfect, except I can't adjust the gamma in game.

---

