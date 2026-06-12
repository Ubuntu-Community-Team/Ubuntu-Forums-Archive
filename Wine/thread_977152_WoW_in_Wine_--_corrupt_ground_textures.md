---
title: "WoW in Wine -- corrupt ground textures"
date: 2008-11-09
forum: Wine
---

### Post by AyndiG on 2008-11-09
Hi!
I am new to Linux and installed Ubuntu 8.04 on both my desktop and laptop. It works beautifully on the desktop; WoW looks better than it did in Windows =)

However, my laptop is the backup WoW computer, and is not running well at all. The ground textures (and sometimes the buff graphics) have lines of bright colors running through them, or they appear striped. The ground in Goldshire, for example, has a couple stripes of green colors and some black and purple, while the ground in IF looks almost normal, but has a blocky line pattern extending from around my character. The texture problems in Goldshire causes more of an fps drop than the texture problems in IF.

Its a pretty old Dell Inspiron 1100, but ran WoW in windows decent enough. I've tried all the troubleshooting tips I could find, but they haven't fixed the ground texture problems.

I will post the cfg file below, just need to switch to the laptop to copy it =)

---

### Post by AyndiG on 2008-11-09
Here are the contents of my config file:

> SET M2UseShaders "0"
SET Pixelshaders "0"
SET gxApi "OpenGL"
SET locale "enUS"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "1"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET textureFilteringMode "0"
SET movie "0"
SET expansionMovie "0"
SET Gamma "1.000000"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "397"
SET particleDensity "1.000000"
SET spellEffectLevel "0"
SET realmName "Hyjal"
SET gameTip "5"
SET gxWindow "1"
SET mouseSpeed "0.5"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET VoiceActivationSensitivity "0.39999997615814"
SET lastCharacterIndex "5"
SET uiScale "0.63999998569489"
SET useUiScale "1"

---

### Post by AyndiG on 2008-11-12
As an extra note - the laptop uses an intel graphics chip (i830). I've tried hunting for updated drivers for it, but havent found any linux ones. 

I dont have  a means of uploading my own screenshots, but I found one that shows what my textures are doing in areas like elwynn or any place where its a relatively repetitve ground tetxure over a large area.

[IMG]http://img237.imageshack.us/img237/7800/wowtexturebug1ry6.png[/IMG]

This image, which shows the known Nvidia graphical glitch, is the closest thing I can find to the other issue, except that in addition to buff graphics and everything being screwed up, theres also a colorful line pattern around my character in place of shadows. Since they appear somewhat similar in game, I did try adding the 'fixes' to my config file for the nvidia bug, but they didn't help anything.

[IMG]http://img413.imageshack.us/img413/2215/geforce6700gtgfxbuget3.jpg[/IMG]

I hope that helps someone help me =x 
I would really like to get this running by midnight tonight ;)

---

### Post by Tea4all on 2008-11-12
Try changing your config to:

SET locale "enUS"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "1"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET textureFilteringMode "0"
SET movie "0"
SET expansionMovie "0"
SET Gamma "1.000000"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "397"
SET particleDensity "1.000000"
SET spellEffectLevel "0"
SET realmName "Hyjal"
SET gameTip "5"
SET gxWindow "1"
SET mouseSpeed "0.5"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET VoiceActivationSensitivity "0.39999997615814"
SET lastCharacterIndex "5"
SET uiScale "0.63999998569489"
SET useUiScale "1"

---

