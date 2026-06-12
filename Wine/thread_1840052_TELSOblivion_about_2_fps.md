---
title: "TELS:Oblivion about 2 fps"
date: 2011-09-06
forum: Wine
---

### Post by ahiung on 2011-09-06
Sorry, I think this is not new topic. But, I can't find the exact answer in other post, so I need the exact answer in this post. Thanks.

My laptop is BenQ Joybook s42
VGA NDIVIA 9600M GT
Intel Core 2 Duo
Ubuntu 10.10
Wine 1.3.26 (Which the WineHQ says best for Oblivion)
Game: The Elder Scrolls: Oblivion (+patch 1.2, and GOTY)

Problem:
1. Can't skip the intro at begining(Minor)
2. No sound at menu(Minor)
3. Extremely low FPS in game(Fatal)

The effort I did were:
-Change some registries based on the OBLIVION topic in other post
-Set all LOW quality
-Turn off all effects
-I try to do -opengl command, but I'm not sure that I need to do that
-checked all the Installation steps, Which I found nothing wrong.

Thank you for helping me, I hope for the exact answer.:)

---

### Post by disabledaccount on 2011-09-07
Have You installed proprietry nVidia drivers?
I have 30(worst case)/70-150FPS(most of the time) in TES3 on HD5670 with medium/high settings, wine 1.3.26, D3D renderer. TES3 has essentially the same engine with very little improvements.

---

### Post by buzzmandt on 2011-09-08
> **tomazzi said:**
> Have You installed proprietry nVidia drivers?
I have 30(worst case)/70-150FPS(most of the time) in TES3 on HD5670 with medium/high settings, wine 1.3.26, D3D renderer. TES3 has essentially the same engine with very little improvements.

Just curious. What is this d3d renderer you speak of. Might help me with my ddo issues

---

### Post by disabledaccount on 2011-09-08
D3D = DirectX3D, the default built-in renderer.
I can post all settings/overrides (not much to tweak) that I'm using to launch the game, but not now - I think in 3-4 hours, when I return home.

I'm using retail version with Bloodmoon and Tribunal included, version: 1.6.1820

---

### Post by buzzmandt on 2011-09-08
> **tomazzi said:**
> D3D = DirectX3D, the default built-in renderer.
I can post all settings/overrides (not much to tweak) that I'm using to launch the game, but not now - I think in 3-4 hours, when I return home.

I'm using retail version with Bloodmoon and Tribunal included, version: 1.6.1820

Oh. The built in one. I thought u were refering to an addon

---

### Post by disabledaccount on 2011-09-08
So...
To run game only one dll override is needed in wine 1.3.26: msvcrt.dll
To fix sound problems alsa should be updated to 1.0.24 (from ppa) - this however will cause pulseaudio equalizer to not work on games, because wine will send audio streams directly to alsa.
Changing keyboard controls inside the game will cause freeze or crash.
I'm running it in single core mode on PhenomII x3 with CPU clk forced to constant 2.1GHz (max is 3.2)

```
export WINEPREFIX="$HOME/wine-Morrowind"
CDPATH="$WINEPREFIX/drive_c/TES3-Morrowind/"
export WINEDEBUG=-all
cd "$CDPATH"
schedtool -a 0x1 -n 0 -e wine "$CDPATH/Morrowind.exe"
#stupid gamma workaround on exit
xgamma -s 0 -gamma 1.0
exit 0
```

some example screenshots attached (weather effect)

:)

---

