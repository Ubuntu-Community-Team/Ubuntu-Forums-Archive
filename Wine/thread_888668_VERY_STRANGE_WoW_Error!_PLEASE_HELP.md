---
title: "VERY STRANGE WoW Error! PLEASE HELP"
date: 2008-08-13
forum: Wine
---

### Post by Anatashinu on 2008-08-13
I have Ubuntu 8.04
I have WoW BC 2.4.3
This is my Config.wtf:

[PHP]SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
SET Basemip "0"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "500.000000"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET expansionMovie "0"
SET realmList "us.logon.worldofwarcraft.com"[/PHP]

Also in that folder is RunOnce.wtf. Here it is:
[PHP]

SET readTOS "-1"

SET readEULA "-1"

SET readScanning "-1"

SET readContest "-1"

SET readTerminationWithoutNotice "-1"
[/PHP]

My Server:

I'm trying to login to WoWscape at logon.wowscape.net

My Problem:
Whenever I open WoW, it goes to the Terms of Use. I try to scroll down, but the cursor freezes. The animations don't.
It will not let me exit the game in any way. I cannot switch between desktops. I cannot do anything. I have to restart my computer.

People, Please Help!

Thanks!

-Anatashinu

---

### Post by Anatashinu on 2008-08-13
The Solution:

Have your realmlist in config.wtf be the same as in realmlist.wtf

---

