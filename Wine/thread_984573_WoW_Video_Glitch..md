---
title: "WoW Video Glitch."
date: 2008-11-16
forum: Wine
---

### Post by BlazinNightSkye on 2008-11-16
Ok, i know it is possible to make WoW work under linux with wine. I have gotten so close to getting it to work. I think my issue may be partly because i run a older dell inspiron E1705. It has an Intel Centrino duo, with that stupid graphics excelerator card. I did have WoW working under windows perfect. Currently i do have sound under wine, i have the latest version, and the latest patch for the game. These are my current settings under config.wtf:
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET locale "enUS"
SET expansionMovie "0"
SET movie "0"
SET showToolsUI "1"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET textureFilteringMode "0"
SET Sound_OutputDriverName "System Default"
SET farclip "400.000000"
SET specular "1"
SET particleDensity "1.000000"
SET spellEffectLevel "3"
SET installType "Retail"
SET patchlist "us.version.worldofwarcraft.com"
SET Gamma "1.000000"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET [[CVar "videoOptionsVersion|videoOptionsVersion]]"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET lastCharacterIndex "1"
SET realmName "Ravenholdt"
SET gameTip "3"
SET mouseSpeed "0.5"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET VoiceActivationSensitivity "0.39999997615814"
Here are my problems, i can login and select my char, but cannot move my character. The graphics are very clitchy and do not load correctly, there is some text defexts with the buttons on the login screen and char selector. I do have sound. I think part of it has to do with framerate, but not positive. This is my first try at running a game under wine. 
I also have some pictures. Just ask for them and i will send. Thanks.

---

### Post by nzrock95 on 2008-11-16
[https://help.ubuntu.com/community/WorldofWarcraft#Configuration]("https://help.ubuntu.com/community/WorldofWarcraft#Configuration")
Did you do any of that? Using OpenGL should fix those graphical issues. You probably don't need the last two under config.wtf if your sound is fine. If you have framerate issues, look at "Registry configuration" on that same page (I would add it anyway because it helps greatly).

Good luck!

---

### Post by BlazinNightSkye on 2008-11-16
I have done all of it, including the registry. And still having some graphical glitches, i am also under openGL.

---

### Post by BlazinNightSkye on 2008-11-16
> **nzrock95 said:**
> [https://help.ubuntu.com/community/WorldofWarcraft#Configuration]("https://help.ubuntu.com/community/WorldofWarcraft#Configuration")
Did you do any of that? Using OpenGL should fix those graphical issues. You probably don't need the last two under config.wtf if your sound is fine. If you have framerate issues, look at "Registry configuration" on that same page (I would add it anyway because it helps greatly).

Good luck!

But thank you!

---

### Post by nzrock95 on 2008-11-16
Hmm...can you describe these glitches in more detail? Or better yet, a screenshot?

Have you edited config.wtf since your first post? If so, can I see it?

---

### Post by BlazinNightSkye on 2008-11-16
> **BlazinNightSkye said:**
> Ok, i know it is possible to make WoW work under linux with wine. I have gotten so close to getting it to work. I think my issue may be partly because i run a older dell inspiron E1705. It has an Intel Centrino duo, with that stupid graphics excelerator card. I did have WoW working under windows perfect. Currently i do have sound under wine, i have the latest version, and the latest patch for the game. These are my current settings under config.wtf:
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET locale "enUS"
SET expansionMovie "0"
SET movie "0"
SET showToolsUI "1"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET textureFilteringMode "0"
SET Sound_OutputDriverName "System Default"
SET farclip "400.000000"
SET specular "1"
SET particleDensity "1.000000"
SET spellEffectLevel "3"
SET installType "Retail"
SET patchlist "us.version.worldofwarcraft.com"
SET Gamma "1.000000"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET [[CVar "videoOptionsVersion|videoOptionsVersion]]"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET lastCharacterIndex "1"
SET realmName "Ravenholdt"
SET gameTip "3"
SET mouseSpeed "0.5"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET VoiceActivationSensitivity "0.39999997615814"
Here are my problems, i can login and select my char, but cannot move my character. The graphics are very clitchy and do not load correctly, there is some text defexts with the buttons on the login screen and char selector. I do have sound. I think part of it has to do with framerate, but not positive. This is my first try at running a game under wine. 
I also have some pictures. Just ask for them and i will send. Thanks.

Here is a screenshot

---

### Post by nzrock95 on 2008-11-16
If that is still your config.wtf, then you need to add SET gxApi "opengl" to it. Try getting rid of that SET [[CVar "videoOptionsVersion... line and replacing it with SET gxApi "opengl".

Good luck!

---

### Post by BlazinNightSkye on 2008-11-16
> **nzrock95 said:**
> If that is still your config.wtf, then you need to add SET gxApi "opengl" to it. Try getting rid of that SET [[CVar "videoOptionsVersion... line and replacing it with SET gxApi "opengl".

Good luck!
 Ok i erased that line, added the openGL one, and i got the black. This screenshot is without OpenGL. Both are glitchy, i can move better under OpenGL but i cant press any buttons. I can at least somewhat see them without Open GL. this is my current config.wtf
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET locale "enUS"
SET expansionMovie "0"
SET movie "0"
SET showToolsUI "1"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET textureFilteringMode "0"
SET Sound_OutputDriverName "System Default"
SET farclip "777"
SET specular "1"
SET particleDensity "1.000000"
SET spellEffectLevel "3"
SET installType "Retail"
SET patchlist "us.version.worldofwarcraft.com"
SET Gamma "1.000000"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET lastCharacterIndex "1"
SET realmName "Ravenholdt"
SET gameTip "4"
SET mouseSpeed "0.5"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET VoiceActivationSensitivity "0.39999997615814"

Anymore ideas?

---

### Post by BlazinNightSkye on 2008-11-16
Maybe i need a better driver for my video card? (though its only the graphics accelerator that comes in dells that are non-gaming)

---

### Post by nzrock95 on 2008-11-16
Hmm...that is quite odd. I'm pretty much out of ideas.

My config.wtf is just about the same as yours. You could try adding SET gxTripleBuffer "1", but that might make it worse. Hey, worth a shot. Other than that...mess around with some of the in-game Video settings (lower settings, lower resolution, raise resolution, etc). Here's my config.wtf if you want to take a look.

```
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
SET gxResolution "1280x1024"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "397"
SET specular "1"
SET particleDensity "1.000000"
SET groundEffectDensity "24"
SET mouseSpeed "0.5"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET realmName "Grizzly Hills"
SET gameTip "7"
SET VoiceActivationSensitivity "0.39999997615814"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET accountName "evilelephant4224"
SET gxTripleBuffer "1"
SET lastCharacterIndex "1"
```

If you want to use it, keep your gxResolution and realmName (or just switch realms in-game).

Sorry 'bout that...good luck!

EDIT: Also, try playing in fullscreen mode. Many games run into problems when played in windowed mode.

---

### Post by BlazinNightSkye on 2008-11-17
I will give it a try, thank you. I didnt think to try full screen mode yet. I still think it has somthing to do with the graphics card. I will look more into that detail.

---

