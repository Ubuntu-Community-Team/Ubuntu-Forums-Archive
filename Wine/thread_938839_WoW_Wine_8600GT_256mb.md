---
title: "WoW Wine 8600GT 256mb"
date: 2008-10-05
forum: Wine
---

### Post by Delvien on 2008-10-05
I am at a loss (literally :P)  I cannot seem to branch above 25 ish FPS in heavily populated areas in World of Warcraft. Windows gives me 60+. The hardware is the same, and wine does a good job with it, but am I missing something?

Running in OpenGL mode.

Tried the regedit hack (didn't actually affect frame rate)

Using WINEDEBUG=all flag ( and tried without, no affect)

Tried having wow run on separate X server, no change. 

Reduced settings (little affect)

No matter what I do I cannot seem to get my FPS higher in areas with more than 2 people.

All I find is the same suggestions over and over, nothing new. 

Anyone have some kind of tricky hack to make this run better?

Spec 1.8ghz Dual core 2 gigs of ram running at 667mhz, 7200 rpm drive, 8600GT 256mb running on GDDR3

Edit, even overclocked my Gfx card and it still doesn't change but 5-10 fps) which makes it 25-30. :(

---

### Post by Snipersnest on 2008-10-05
I have a 8500 GT .. not much difference in cards.  But I'm getting 20-80fps at all times with OpenGL and Wine.. Maybe the answer is in your config.wtf?   Heres mine.. I know some of it is in there twice but I'm to lazy to edit it out again. All I know is mine works great with it like this so I'm not touching it lol.

```

SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1" 
SET locale "enUS" 
SET weatherDensity "0" 
SET checkAddonVersion "0" 
SET screenEdgeFlash "0" 
SET M2UseShaders "0" 
SET vertexShaders "0" 
SET showfootprints "0" 
SET SkyCloudLayers "0"
SET Sound_EnableHardware "1" 
SET particleDensity "1.000000" 
SET gxFixLag "0" 
SET hwDetect "0" 
SET gxAPI "OpenGL" 
SET gxDepthBits "24" 
SET gxResolution "1440x900" 
SET gxRefresh "50" 
SET gxMultisampleQuality "0.000000" 
SET fullAlpha "1" 
SET SmallCull "0.010000" 
SET DistCull "500.000000" 
SET trilinear "1" 
SET frillDensity "24" 
SET farclip "777" 
SET specular "1" 
SET pixelShaders "1" 
SET unitDrawDist "300.000000" 
SET movie "0" 
SET expansionMovie "0" 
SET realmList "us.logon.worldofwarcraft.com" 
SET readTerminationWithoutNotice "-1" 
SET coresDetected "4" 
SET processAffinityMask "3" 
SET gxWindow "1" 
SET videoOptionsVersion "1" 
SET DesktopGamma "1" 
SET Gamma "1.000000" 
SET profanityFilter "0" 
SET showToolsUI "1" 
SET Sound_VoiceChatInputDriverName "System Default" 
SET Sound_VoiceChatOutputDriverName "System Default" 
SET Sound_OutputDriverName "System Default" 
SET ChatMusicVolume "0.30000001192093" 
SET ChatSoundVolume "0.40000000596046" 
SET ChatAmbienceVolume "0.30000001192093" 
SET Sound_MasterVolume "0.5" 
SET Sound_SFXVolume "0.20000000298023" 
SET Sound_MusicVolume "1" 
SET Sound_AmbienceVolume "0.80000001192093" 
SET Sound_EnableSoundWhenGameIsInBG "1" 
SET patchlist "us.version.worldofwarcraft.com" 
SET groundEffectDensity "24" 
SET groundEffectDist "140" 
SET realmName "Argent Dawn" 
SET cameraPitchMoveSpeed "115" 
SET cameraPitchSmoothSpeed "45" 
SET gameTip "91" 
SET OutboundChatVolume "1" 
SET InboundChatVolume "1" 
SET VoiceActivationSensitivity "0.40000003576279" 
SET EnableMicrophone "0" 
SET uiScale "0.81000000238419" 
SET guildMemberNotify "1" 
SET questFadingDisable "1" 
SET cameraDistanceMaxFactor "2" 
SET CombatHealing "0" 
SET minimapZoom "0" 
SET minimapInsideZoom "0" 
SET autoSelfCast "1" 
SET showPartyDebuffs "0" 
SET cameraYawMoveSpeed "230" 
SET cameraDistanceMax "50" 
SET useUiScale "1" 
SET lod "1" 
SET ffxGlow "0" 
SET ffxDeath "0" 
SET Sound_EnableErrorSpeech "0" 
SET Sound_NumChannels "64" 
SET xpBarText "1" 
SET scriptErrors "1" 
SET playerStatusText "1" 
SET CombatDamage "0" 
SET autoQuestWatch "0" 
SET alwaysShowActionBars "1" 
SET SlideBarConfig "anchor=right;position=204.47297185637" 
SET Sound_EnableMusic "0" 
SET cameraView "0" 
SET gxCursor "0" 
SET textureFilteringMode "0" 
SET baseMip "1" 
SET shadowLOD "0" 
SET targetStatusText "1" 
SET lockActionBars "1" 
SET lastCharacterIndex "1" 
SET gxColorBits "24"

```
Thats the config.wtf in your WTF folder . Maybe that will help. I took some of the settings in mine from the winehq site for the wow 2.4.3 page.

---

### Post by Eviljim on 2008-10-06
try changing

SET gxAPI "OpenGL"

to

SET gxAPI "d3d"


then see what happens.

---

### Post by Delvien on 2008-10-06
> **Eviljim said:**
> try changing

SET gxAPI "OpenGL"

to

SET gxAPI "d3d"


then see what happens.


D3D performance is poor, you can set the flag to -d3d or -opengl, you don't have to do it in the wtf config file.

---

### Post by Eviljim on 2008-10-06
Do you have an AGP graphics card or PCI-E?

---

### Post by Snipersnest on 2008-10-06
I just did what WineHQ said it currently can support.. thats why I edited my files.. mine works just fine without bothering with D3D. 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329)

As far as I know Cedega is really the only one supporting D3D with WoW at the moment.

---

### Post by Delvien on 2008-10-06
> **eviljim said:**
> do you have an agp graphics card or pci-e?


pci-e

---

### Post by luposolo on 2008-10-06
i notice running a seperate x server does not give you a performance boost ive tested it with css and cs but i havent tested it with native games yet

---

### Post by Delvien on 2008-10-06
An update to my gfx card made -d3d crash wow :D -opengl still works fine

---

### Post by luposolo on 2008-10-06
i just tested WoW on my linux box i have it running in opengl mode and im getting 50-80 fps in orgrimmar and i have compiz fusion running

---

### Post by Delvien on 2008-10-06
> **luposolo said:**
> i just tested WoW on my linux box i have it running in opengl mode and im getting 50-80 fps in orgrimmar and i have compiz fusion running

Specs?

what reso you running at?

---

### Post by luposolo on 2008-10-07
i have amd athlon 64 X2 dual core 4200+ 2.2ghz , 8800gts 320mb, 8gb of ram and my res is 1280 by 1024

---

### Post by Delvien on 2008-10-07
> **luposolo said:**
> i have amd athlon 64 X2 dual core 4200+ 2.2ghz , 8800gts 320mb, 8gb of ram and my res is 1280 by 1024


Faster proc, better gfx card, too much ram and lower reso, no wonder :p

---

### Post by pissedoffdude on 2008-10-07
Do you have the latest nvidia drivers?  Also try messing with the video settings inside the game.

---

