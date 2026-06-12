---
title: "World of Warcraft/DRI problem"
date: 2008-11-25
forum: Wine
---

### Post by Termagant on 2008-11-25
I installed WoW using Wine, and it worked, except the graphics were really strange and broken.

So I followed these instructions: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_1:_Install_the_driver_the_Ubuntu_Way](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_1:_Install_the_driver_the_Ubuntu_Way)

That also seems to have worked, except for one thing... when I open World of Warcraft now, the screen is black except for the cursor (the graphics on the cursor are better now, at least!). The quit button is still in the expected place, so I can close the program by clicking where I know it to be.

In any case, I'm totally stumped. Has anybody else had this problem, or have any idea how to fix it?

Thanks in advance for any help.

---

### Post by Eviljim on 2008-11-25
Try adding 

SET M2UseShaders "0"


to your Config.wtf file.

---

### Post by Termagant on 2008-11-25
> **Eviljim said:**
> Try adding 

SET M2UseShaders "0"


to your Config.wtf file.

Hm, I tried doing that, and it didn't seem to work. Darn. :( Thank you, though.

---

### Post by Eviljim on 2008-11-25
What graphics card are you using?


If it is ATi

add

SET gxAPI "OpenGL"
SET ffxGlow "0"
SET ffxDeath "0"


And see what happens.


Also could you post your config.wtf file here please?

---

### Post by Termagant on 2008-11-25
> **Eviljim said:**
> What graphics card are you using?


If it is ATi

add

SET gxAPI "OpenGL"
SET ffxGlow "0"
SET ffxDeath "0"


And see what happens.


Also could you post your config.wtf file here please?

That worked! Thank you so much! I'm so excited. :D

---

### Post by Eviljim on 2008-11-25
Good job, glad to be of help.

---

### Post by Termagant on 2008-11-26
Well, I thought it worked, but there seems to be one more problem.

Everything worked fine until I entered a new subzone, and then the text started shearing like crazy and flashing all over the screen. It's always text that's supposed to be on the screen, like the subzone text over the minimap, the quest text, the date from the calendar icon, etc.

Once I log out, it does it at the character selection screen as well. Next time I log in, it seems to work again, until I try again to go into a new subzone.

Anyway, does anybody have any suggestions on how to try and fix this? It's really frustrating to be so close and still have it not work!

EDIT:

And here is my Config.wtf file, in case that is helpful:

SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x768"
SET gxRefresh "60"
SET hwDetect "0"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.070000"
SET DistCull "500.000000"
SET trilinear "1"
SET farclip "397"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET realmList "us.logon.worldofwarcraft.com"
SET gxMultisampleQuality "0.000000"
SET readEULA "1"
SET realmName "Maelstrom"
SET mouseSpeed "0.80000001192093"
SET MusicVolume "0.20000000298023"
SET SoundVolume "0.30000001192093"
SET MasterVolume "0.60000002384186"
SET gameTip "10"
SET AmbienceVolume "0.30000001192093"
SET readScanning "-1"
SET readContest "-1"
SET Gamma "0.500000"
SET uiScale "1"
SET locale "enUS"
SET soundMaxHardwareChannels "12"
SET timingTestError "0"
SET spellEffectLevel "3"
SET patchlist "us.version.worldofwarcraft.com"
SET showToolsUI "1"
SET coresDetected "2"
SET Sound_VoiceChatInputDriverName ""
SET Sound_VoiceChatOutputDriverName "NoSound Driver"
SET Sound_OutputDriverName "System Default"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET readTerminationWithoutNotice "-1"
SET videoOptionsVersion "1"
SET Sound_VoiceChatInputDriverIndex "1"
SET Sound_VoiceChatOutputDriverIndex "1"
SET showPartyDebuffs "0"
SET SlideBarConfig "anchor=right;position=247.31430864284"
SET installType "Retail"
SET portal "us"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET VoiceActivationSensitivity "0.39999997615814"
SET gxFixLag "0"
SET M2UseShaders "0"
SET gxAPI "OpenGL"
SET ffxGlow "0"
SET ffxDeath "0"
SET gxTripleBuffer "1"
SET baseMip "1"
SET weatherDensity "1"

---

### Post by Termagant on 2008-11-27
Nobody has any idea how to fix this? Darn.

UDPATE: I solved this by checking the long WoW thread. Wish I'd checked it earlier!

---

