---
title: "ATI Radeon/WoW, Need Help"
date: 2008-10-23
forum: Wine
---

### Post by mikegmcb on 2008-10-23
I've already set up WoW on a Ubuntu PC before with an Nvidia card, but my laptop that has an ATI video card is causing such a problem. I cannot get past TOS on -opengl. It crashes when I hit the second accept. I run in d3d and can't really do much. I don't have any idea why it crashes, and I don't know if I can get a log if the computer freezes up like that, so if I can, let me know and I'll post it here if it would be of any value. I have the following on this laptop:

-Ubuntu Hardy 8.01 (I recall that's the most updated... whatever the most updated is...)
-AMD X2 64 Bit
-ATI Radeon 3100 (256MB)
-3GB RAM
-Fully Patched/Manually Installed World of Warcraft.

I have done the following modifications.
-OpenGL Registry & WTF/Config modification for it.
-Both ffxGlow and ffxDeath changes in WTF/Config.
-Turned off Pixel Shaders (Which turns back on, by the way.

I also get this nice error VIA terminal (I run everything terminal) when I run that I don't get running my nVidia box:
```
system.reg is not a valid registry file
userdef.reg is not a valid registry file
user.reg:829: Malformed key '[Software\\Classes\\CLSID\\{25E609E4-B259-11CF-BFC7-444553540000}\\InProc'
user.reg:829: Error creating key '[Software\\Classes\\CLSID\\{25E609E4-B259-11CF-BFC7-444553540000}\\InProc'
user.reg is not a valid registry file

```

Config.wtf:

```
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET farclip "450.000000"
SET specular "1"
SET particleDensity "1.000000"
SET accountName "mikegmcb"
SET movie "0"
SET expansionMovie "0"
SET realmList "us.logon.worldofwarcraft.com"
SET readTerminationWithoutNotice "-1"
SET coresDetected "2"
SET videoOptionsVersion "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET groundEffectDensity "24"
SET gxApi "opengl"
SET ffxGlow "0"
SET ffxDeath "0"
SET portal "us"
SET installType "Retail"
SET patchlist "us.version.worldofwarcraft.com"
SET mouseSpeed "0.5"
SET Gamma "1.000000"
SET lastCharacterIndex "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET realmName "Dalaran"
SET gameTip "2"
SET VoiceActivationSensitivity "0.39999997615814"

```

I used Envy to set up my ATI Drivers. "Direct rendering: yes"

I'm starting to lose a little hope here... I got it fine on my other box, am I doing something wrong? I know ATI cards are a pain to set up... but is it supposed to be this much of a pain? Any help for this would be great.

---

### Post by Eviljim on 2008-10-24
Change 

SET readTOS "1"
SET readEULA "1"

to 

SET readTOS "0"
SET readEULA "0"

and see what happens. If not try -1 instead.

You will also need SET M2UseShaders "0"

---

