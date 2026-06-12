---
title: "WoW and Wine, Black boxes on login screen glitch..."
date: 2008-11-25
forum: Wine
---

### Post by Espionage724 on 2008-11-25
Ubuntu 8.10
Intel 950GMA
Crossovers with latest Wine

```
SET SoundOutputSystem "1"
SET SoundBufferSize "232"
SET ffxDeath "0"
SET ffxGlow "0"
SET ffxspecial "0"
SET M2UseShaders "1"
SET fixedfunction "1"
SET gxapi "opengl"
SET pixelShaders "1"
SET SmallCull "0.07"
SET trilinear "0"
SET useWeatherShaders "0"
SET weatherDensity "0"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET locale "enUS"
SET movie "0"
SET showToolsUI "1"
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
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "177"
SET particleDensity "1.000000"
SET gxVSync "0"
SET baseMip "1"
SET spellEffectLevel "0"
SET environmentDetail "0.5"
SET accountName "Espionage10203"
SET realmName "Korialstrasz"
SET gameTip "2"
SET mouseSpeed "0.5"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET VoiceActivationSensitivity "0.39999997615814"
```

---

### Post by Eviljim on 2008-11-25
Change

SET M2UseShaders "1"

to

SET M2UseShaders "0"


and see what happens.

---

### Post by Espionage724 on 2008-11-25
M2USeShaders isn't used in patch 3.0.3 anymore. M2UseShaders, pixelshaders, vertexshaders are not used but are replaced by one command called "fixedfunction" which if 1, disables all pixelshader, shader, vertexshader stuff. I tried it on and off and black boxes still exist :(

---

### Post by Eviljim on 2008-11-25
Doesnt look like fixedfunction is used either..


> 
Notes from the 3.0.3 patch that may affect you:

Bug Fixes

o Fixed an issue that was affecting terrain rendering on GeForce 3 and 4 Ti cards. Those that added the command Set fixedfunction 1 to their config.wtf file should remove it to avoid a decrease in performance.

---

### Post by Espionage724 on 2008-11-25
I can't recall me having this problem when I was using normal wine instead of crossovers but then again crossovers made me an automatic config.wtf file. I will try to delete it and start fresh.

---

### Post by Espionage724 on 2008-11-25
Nope still broken.....

---

### Post by Eviljim on 2008-11-26
Check this thread out, I know its a little old now, but there may be a few gems of info in there for you.

[http://ubuntuforums.org/showthread.php?t=801394&highlight=intel+950]("http://ubuntuforums.org/showthread.php?t=801394&highlight=intel+950")

---

### Post by deadseraphim on 2008-12-06
I'm also having this exact same problem, also with an Intel integrated graphics card (Dell Inspiron 530, Ubuntu 8.04 preloaded).

---

### Post by Falkin on 2008-12-11
Exact same problem with an Mobile Intel 945 express

---

### Post by whiteychs on 2009-07-25
I hate to bring up old threads, but did anyone find a fix?

I'm having the same problem on my Lenovo S10 netbook with Intel GMA 950 chipset.

---

### Post by zhugo on 2009-08-18
Well i did not find yet how to change the Config.wft file to make it work , but if i lauch from command line with wine Wow.exe -d3d & it work's ... It lease i dont get the black login and errors 

:) 

Ps i use a acer aspire one with the onboard intel 950 graphic card

---

### Post by SolarOnline on 2009-08-18
This thread at WINEHQ should help troubleshoot all errors as it lists the problem you can encounter and confirmed fixes.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421)

It's up to date with Patch 3.2 - "Call of the Crusade"

---

