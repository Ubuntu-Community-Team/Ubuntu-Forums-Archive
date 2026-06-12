---
title: "GREAT WoW framerate with Catalyst 8.10, but at a price."
date: 2008-10-21
forum: Wine
---

### Post by Catholicnerd on 2008-10-21
Hi everyone.  I've got a Radeon Mobility X1270 in my laptop, and I've just installed Echoes of Doom.  Strangely enough, my framerate is* amazing.*But the improved performance seems to have come with a pricetag: the World of Warcraft window flickers horribly.  I've tried everything I can think of to get rid of the problem.  Here's my config.wtf file:

SET gxApi "OpenGL"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET locale "enUS"
SET expansionMovie "0"
SET movie "0"
SET showToolsUI "1"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.80000001192093"
SET Sound_AmbienceVolume "1"
SET farclip "397"
SET particleDensity "1.000000"
SET spellEffectLevel "6"
SET groundEffectDensity "24"
SET gxWindow "1"
SET mouseSpeed "0.5"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET realmName "Hyjal"
SET gameTip "6"
SET VoiceActivationSensitivity "0.39999997615814"
SET gxMultisample "2"

Any advice?  Thanks a million.

---

### Post by Catholicnerd on 2008-10-21
Well, I realized that I'd forgotten to turn off desktop effects, so THAT issue is resolved.  But now when I enter major cities the graphics go completely bonkers and WoW crashes.  Anyone else have that problem?

---

### Post by trxDraxon on 2008-10-21
From what i've heard its a problem with the ATI driver and the wow minimap.  Try minimizing your minimap

---

### Post by Etrruugo on 2008-10-21
Thanks! Bump!&#12288;He wiped the dust off and gently wrapped it in brown paper. Then he placed the parcel in Reuben's hands.&#12288;&#12288;Racing home, Reuben burst through the front door. His mother was scrubbing the kitchen stove. &#8220;Here, Mum! Here!&#8221;Reuben exclaimed as he ran to her side. He placed a small box in her work roughened hand.&#12288;&#12288;She unwrapped it carefully, to save the paper. A blue-velvet jewel box appeared. Dora lifted the lid, tears beginning to blur her vision.&#12288;&#12288;In gold lettering on a small, almond-shaped brooch was the word Mother.&#12288;&#12288;It was Mother's Day, 1946.&#12288;&#12288;Dora had never received such a gift; she had no finery except her wedding ring. Speechless, she smiled radiantly and gathered her son into her arms.Thsale is a professional, loyal and reliable wow gold supplier online, we pioneered selling cheap wow gold. Welcome to thsale buy world of warcraft gold Buy Cheap WoW Gold, World of Warcraft Gold, Please look here! We are a Great MMORPG company. wow money and wow items,which is very cheap WOW Gold&#65281;All US Server 24.99$/1000G on sell! Cheap wow gold,rs powerleveling,wow power leveling,Buy Cheapest/Safe/Fast WoW US EU Gold Power leveling ---------------------------------------------------**  [Pet products](http://www.lovelonglong.com),     [dog bed](http://www.lovelonglong.com),   [pet supply](http://www.lovelonglong.com)    [wow power level](http://www.powerleveling-wow.com/siteMap.asp),     [WoW Power Leveling](http://www.powerleveling-wow.com),**

---

### Post by ABE3K on 2008-11-03
Also, don't forget to add this registry key to wine

[HKEY_CURRENT_USER\Software\Wine\OpenGL]

"DisabledExtensions"="GL_ARB_vertex_buffer_object"

---

