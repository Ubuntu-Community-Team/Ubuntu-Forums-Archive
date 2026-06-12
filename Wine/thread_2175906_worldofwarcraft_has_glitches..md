---
title: "worldofwarcraft has glitches."
date: 2013-09-21
forum: Wine
---

### Post by cosmoshell on 2013-09-21
Trying to get world of warcraft pandoria working. Intel® Sandybridge Mobile  graphics.

I tried openGL, it loads perfectly then crashes after 3 seconds. so i cant play it.
SET gxApi "d3d" the graphics flicker, and colored mozacs flash over graphics, and theres clouds of glitchs where you cant see.


> SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET showToolsUI "1"
SET accounttype "MP"
SET readTerminationWithoutNotice "-1"
SET installLocale "enUS"
SET enterWorld "1"
SET hwDetect "0"
SET videoOptionsVersion "5"
SET gxWindow "1"
SET gxMaximize "1"
SET maxAnimThreads "3"
SET accountName "cosmoshell@gmail.com"
SET accountList "!GAME14513|WoW2|"
SET mouseSpeed "1"
SET Gamma "1.000000"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET VoiceActivationSensitivity "0.39999997615814"
SET Sound_EnableAllSound "0"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "200"
SET reflectionMode "0"
SET environmentDetail "50"
SET textureFilteringMode "0"
SET terrainLodDist "200"
SET realmName "Illidan"
SET gameTip "43"
SET checkAddonVersion "0"
SET rippleDetail "1"
SET shadowTextureSize "2048"
SET gxApi "d3d"
SET particleDensity "10"
SET wmoLodDist "100"
SET terrainTextureLod "1"
SET terrainMipLevel "1"
SET worldBaseMip "2"
SET weatherDensity "0"
SET ffxGlow "0"
SET ffxSpecial "0"

tried SET gxApi "d3dx11" SET gxApi "d3dx9"  

tried
sudo apt-get install driconf
Open driconf, go to the tab "image quality" and activate the S3TC texture compression, even if the software support is not available. (Default is "no" change to "yes")
did nothing. SET gxApi "OpenGL" 
performce is better, no flickering of tiles, but it has this cloudy glitches that make it so you cant see,

---

### Post by cosmoshell on 2013-09-22
fixed, needed to distupgrade.

---

