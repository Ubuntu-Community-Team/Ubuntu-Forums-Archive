---
title: "WoW with Wine(ATI RADEON XPRESS 200)"
date: 2008-05-26
forum: Wine
---

### Post by tictactoe on 2008-05-26
hello guys,i have been trying to get WoW working for quite a time....

MY Specs:
Pentium D 2.66Ghz
1GB RAM
ATI Radeon Xpress 200 in built card with 256MB memory
D101GGc mobo

wine version used : 0.959

here is my config.wtf file

SET ffxDeath "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
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
SET readTOS "-1"
SET readEULA "-1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET coresDetected "2"
SET videoOptionsVersion "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"

i tried using the **SET gxapi "opengl"(ignore the case)** too,but i got a black screen.....

here is the screenshot without using that line in config.wtf

[ATTACH]71639[/ATTACH]

also i followed these threads ,but couldnt change the outcome!!!
[http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
[http://www.ubuntuforums.org/showthread.php?t=303509](http://www.ubuntuforums.org/showthread.php?t=303509)

please help me out!!:(

---

### Post by strongboww on 2008-05-26
try turning pixel shaders off, some people said that it fixed a number of problems

do you actually start wow with -opengl?

---

