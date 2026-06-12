---
title: "wow-white indoors"
date: 2008-10-21
forum: Wine
---

### Post by Beshaba on 2008-10-21
[SIZE="3"]Hi,

Ever since patch 3.0.2 I have a graphical issue.
Before the patch I used to play in opengl mode. Since the patch I've had to play in direct 3d, otherwise the login screen was black and none of the fields were present so I was unable to log in. 

I can now log in and run the game in direct 3d mode but the graphics are choppy and indoors many objects appear totally blank. All you see is a white block in the shape of the object. [/SIZE][/SIZE]

Any ideas? Does anyone knows what Blizzard has changed so that my old settings (which worked perfectly) no longer function?:confused:

Here are my config.wtf settings:

SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET locale "enUS"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET textureFilteringMode "0"
SET showToolsUI "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET Sound_OutputDriverName "System Default"
SET SmallCull "0.070000"
SET DistCull "350.000000"
SET farclip "1277"
SET particleDensity "1.000000"
SET spellEffectLevel "0"
SET realmName "Dalaran"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET gxCursor "0"
SET Gamma "1.000000"
SET groundEffectDist "70"
SET weatherDensity "0"
SET gameTip "41"
SET uiScale "0.63999998569489"
SET shadowLOD "0"
SET baseMip "1"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET Sound_EnableMusic "0"
SET Sound_MasterVolume "0.5"
SET Sound_SFXVolume "0.5"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.39999997615814"
SET showGameTips "0"
SET DesktopGamma "1"
SET UIFaster "2"
SET expansionMovie "0"
SET accountName (will not be released)
SET installType "Retail"
SET portal "us"
SET mouseSpeed "1.5"
SET environmentDetail "0.5"
SET Sound_EnableDSPEffects "0"[/SIZE][/SIZE]

---

### Post by Eviljim on 2008-10-22
Need to know your PC spec my friend.

Found this on the Technical Support Forum on WoW Europe

> i got this from blizz post and it worked great for me not one bit on lag glich at all now thanx blizz

bigwull


Graphical Issues in 3.0.2

Black textures

There is a known issue with some Nvidia Geforce and ATI Radeon graphics cards which causes certain textures in the game to appear black and could lead to crashes. One work around to resolve this is to navigate to your World of Warcraft directory and open the Config.wtf file in the WTF folder with Wordpad.
Add this line to the bottom:
SET FixedFunction &#8220;1&#8221;

If after restarting the game the textures still appear black, check with Nvidia or ATI for updated drivers for your card:

ATI: [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)
NVIDIA: [http://www.nvidia.com/Download/index.aspx](http://www.nvidia.com/Download/index.aspx)

Our development team are also actively working on this issue and hope to have a full solution implemented in a future patch. 

I know it says black textures, but its remarkably similar otherwise.

---

### Post by Beshaba on 2008-10-25
Sorry about forgetting the specs of my computer.
It's an Inspiron 530, graphic card  Intel Corporation 82633/G31 Express Integrate.
Let me know how I can give more specs if necessary.

I tried to modify the config.wtf file by using the information on wowwiki, but nothing improved.

Any clue?

---

### Post by gnl99 on 2008-10-26
related comments herelet's go to the forum Good Services[img]http://pic.piclib.net/sunvv/images/pic/new20_711.gif[/img]About all go to [wow gold](http://www.powerleveling-wowgold.com) Good Services ok![img]http://pic.piclib.net/sunvv/images/pic/16340.jpg[/img]sites where they can express&#65281;[china massage](http://www.chinamassage.org/)-china massage help you to power[body massage](http://www.massageinshanghai.org/)-massage vip service in shanghai[escorts shanghai](http://www.escortinshanghai.com/)-24-hour out call escort service in shanghai[massage](http://www.chinamassage.org/)-this service for  massage shanghai

---

### Post by Eviljim on 2008-10-27
Well Blizz have definately done something to the graphics engine for sure.

Pre 3.0 patch I was using V8.4 of ATi driver for my 2600XT card with no problems whatsoever.

Update to patch 3.0 and now the graphics have gone completely pear shaped. Updated to V8.10 of the ATi driver and now the graphics are back to normal - albeit a bit slower on fps.

I would recommend checking the intel site for any new drivers for your graphics card.

---

### Post by Beshaba on 2008-10-31
Ok, I am working on upgrading the drivers.

---

### Post by illepic on 2008-11-04
Notes from the 3.0.3 patch that may affect you:

Bug Fixes

o Fixed an issue that was affecting terrain rendering on GeForce 3 and 4 Ti cards. Those that added the command Set fixedfunction 1 to their config.wtf file should remove it to avoid a decrease in performance.

---

