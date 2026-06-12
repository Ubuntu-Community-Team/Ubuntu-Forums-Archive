---
title: "[SOLVED] wine + wow + ATI x850x graphic problems"
date: 2008-06-08
forum: Wine
---

### Post by chuugokujin on 2008-06-08
Hi,
I did everything this guide says and I still have problem to run the game properly.

1) I can successfully enter the game and choose my character.The game starts fast but only 2D contents shows, like the login, password textbox, and all the icons such as "login", "Quit". All 3D contents are black, or blue. After loading into the world, the action bars there, but all 3D things are blue.

2) My graphic flashes badly, it evens shows my Desktop icons when game is running.

here is my WTF.config, please help me:

SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET locale "enUS"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x1024"
SET gxRefresh "60"
SET gxCursor "0"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET pixelShaders "1"
SET movie "0"
SET expansionMovie "0"
SET Gamma "1.000000"
SET lastCharacterIndex "6"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET Sound_OutputDriverName "System Default"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET farclip "477"
SET specular "1"
SET particleDensity "1.000000"
SET groundEffectDensity "24"
SET groundEffectDist "70"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET realmName "Eredar"
SET gameTip "1"
SET uiScale "1"
SET showPartyDebuffs "0"

---

### Post by thisismalhotra on 2008-06-09
This will help;

[http://ubuntuforums.org/showthread.php?t=770939](http://ubuntuforums.org/showthread.php?t=770939)

---

### Post by chuugokujin on 2008-06-09
Thank you very much for reply!

The first problem is solved! Could you tell me how I can fix the second one as well? My graphics flashes badly, my desktop graphics flashes in and out, this is my screen shot:

[http://img128.imageshack.us/my.php?image=screenshotpb2.png](http://img128.imageshack.us/my.php?image=screenshotpb2.png)

> **thisismalhotra said:**
> This will help;

[http://ubuntuforums.org/showthread.php?t=770939](http://ubuntuforums.org/showthread.php?t=770939)

---

### Post by thisismalhotra on 2008-06-10
> **chuugokujin said:**
> Thank you very much for reply!

The first problem is solved! Could you tell me how I can fix the second one as well? My graphics flashes badly, my desktop graphics flashes in and out, this is my screen shot:

[http://img128.imageshack.us/my.php?image=screenshotpb2.png](http://img128.imageshack.us/my.php?image=screenshotpb2.png)

I exactly know this problem as I had the same with my laptop with Ati Xpress Radeon 200m,but I am sorry could not fix it till date  6 months now .. had to switch back to XP :(

Try Winehq website but I did not have any luck waiting to see if Wine 1.0 release will fix it. You may tru updating to rc4... can you confirm that it only happens indoor and not outdoor.

Also turn compiz off while running the game.

EDIT: I think this one SET readEULA "1"

But the keyboard and mouse freeze up still is not concerned with this ... but try anyways. Also see if there is some settings of that sort in wincfg.

---

### Post by chuugokujin on 2008-06-10
> **thisismalhotra said:**
> I exactly know this problem as I had the same with my laptop with Ati Xpress Radeon 200m,but I am sorry could not fix it till date  6 months now .. had to switch back to XP :(

Try Winehq website but I did not have any luck waiting to see if Wine 1.0 release will fix it. You may tru updating to rc4... can you confirm that it only happens indoor and not outdoor.

Also turn compiz off while running the game.

EDIT: I think this one SET readEULA "1"

But the keyboard and mouse freeze up still is not concerned with this ... but try anyways. Also see if there is some settings of that sort in wincfg.

lol, unfortunately it remains same even if I updated to wine-1-rc4, and put  SET readEULA "1" overthere.
and, yeah, it happens anytime anywhere no matters indoor or outdoor.
I guess I will have to wait one day until they solve this problem then, switch back to XP.

Thanks for the effort&#65281;

---

### Post by thisismalhotra on 2008-06-11
Did you turn compiz off??

try SET readEULA "0"

---

### Post by wakingrufus on 2008-06-11
[http://ubuntuforums.org/showthread.php?t=824713](http://ubuntuforums.org/showthread.php?t=824713)

this should be the same problem.  disable compiz by going to System - Preferences - Visual Effects, and set the option to "none".

---

### Post by chuugokujin on 2008-06-12
To both of you,
I SET readEULA "0" and it doesn't work, it still flashes.

and I can't turn off Compiz cuz I don't find System->Preferences->Visual Effect, I don't have such option in Preferences.

very weired!

---

### Post by thisismalhotra on 2008-06-12
> **chuugokujin said:**
> To both of you,
I SET readEULA "0" and it doesn't work, it still flashes.

and I can't turn off Compiz cuz I don't find System->Preferences->Visual Effect, I don't have such option in Preferences.

very weired!

If you are running ubuntu/gnome right click on the desktop and select change background image or wallpaper. Than click on viual effects tab and turn it off/none.

or

System->Preferences-> Appearance -> Visual Effect

or

run (try other 2 first)

```
metacity --replace
```

---

### Post by chuugokujin on 2008-06-12
> **thisismalhotra said:**
> If you are running ubuntu/gnome right click on the desktop and select change background image or wallpaper. Than click on viual effects tab and turn it off/none.

or

System->Preferences-> Appearance -> Visual Effect

or

run (try other 2 first)

```
metacity --replace
```

All the problem is solved now! The flashing has gone by turning off compiz.

Thanks a LOT for all of you guys.

---

### Post by thisismalhotra on 2008-06-13
Can you make the thread solved please

---

### Post by chuugokujin on 2008-06-13
> **thisismalhotra said:**
> Can you make the thread solved please

Sry, what a nub I am! lol

---

