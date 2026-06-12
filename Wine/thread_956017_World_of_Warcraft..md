---
title: "World of Warcraft."
date: 2008-10-22
forum: Wine
---

### Post by Milkium on 2008-10-22
Hey guys.
World of Warcraft in Wine doesn't seem to be working properly for me. I do have it set so that it opens in windowed mode. 

Every time I try to open WoW, I usually make it to the news/updates window. But when I click "PLAY", the screen just goes bezerk and...well, it looks like the attached picture I have at the end of this post.

Even after closing WoW, my screen stays like this, and I have to reboot.

Here's my config.wtf file. What's the problem here?


```
SET hwDetect "0"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.070000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "177"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxWindow "1"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET realmList "us.logon.worldofwarcraft.com"
SET soundMaxHardwareChannels "12"
SET locale "enUS"
SET readTerminationWithoutNotice "-1"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "1"
SET videoOptionsVersion "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET gxCursor "0"
SET DesktopGamma "1"
SET Gamma "1.000000"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET spellEffectLevel "0"
SET groundEffectDist "70"
SET gameTip "22"
SET uiScale "1"
SET M2UseShaders "0"
SET realmName "Burning Legion"
SET gxColorBits "24"
SET gxDepthBits "24"
SET textureFilteringMode "0"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "0.69999998807907"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET baseMip "1"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.39999997615814"
SET EnableVoiceChat "1"
SET weatherDensity "0"
SET shadowLOD "0"
SET installType "Retail"
SET expansionMovie "0"
SET portal "us"
SET mouseSpeed "0.5"
SET gxWindow "1"
```

Thanks. :)
**EDIT:** I should also mention that this happened only after I got my new monitor. With my old CRT this didn't happen. This has only happened with my new flat panel widescreen monitor.

---

### Post by wownerd87 on 2008-10-22
Well I think I might be having a similar problem,ny news thing comes up fine, but when I start wow, there is like a black square by my mouse and everything freezes except the mouse and i can hear the login music but i just see the desktop, but everything is frozen so i have to reboot. Sound similar?

---

### Post by wownerd87 on 2008-10-22
Hey I fixed my problem by adding this to my config.wtf Try it


> SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"

---

### Post by Milkium on 2008-10-23
> **wownerd87 said:**
> Hey I fixed my problem by adding this to my config.wtf Try itUnfortunately that didn't work. :(
But thanks for trying.

---

### Post by Karilex on 2008-10-23
not sure if you already tried but add this

SET M2UseShaders "0"

---

### Post by Flynn555 on 2008-10-23
have a lookie

[http://ubuntuforums.org/showthread.php?t=579378&highlight=Howto+WoW+wine](http://ubuntuforums.org/showthread.php?t=579378&highlight=Howto+WoW+wine)

---

### Post by Milkium on 2008-10-23
> **Karilex said:**
> not sure if you already tried but add this

SET M2UseShaders "0"Tried that. :(

---

### Post by Milkium on 2008-10-23
> **Flynn555 said:**
> have a lookie

[http://ubuntuforums.org/showthread.php?t=579378&highlight=Howto+WoW+wine](http://ubuntuforums.org/showthread.php?t=579378&highlight=Howto+WoW+wine)Thanks for the link. I'll take a look at it when I get home later.

@prematurebaby: No thanks. I'm a huge pirate, and I think that the law is on to me. I'm going to stay low for a while.

---

### Post by Milkium on 2008-10-23
> **Flynn555 said:**
> have a lookie

[http://ubuntuforums.org/showthread.php?t=579378&highlight=Howto+WoW+wine](http://ubuntuforums.org/showthread.php?t=579378&highlight=Howto+WoW+wine)Couldn't get help from that. But thanks for the link.

Anyone else?

---

### Post by Eviljim on 2008-10-24
Looks like a driver issue. If you are using an Ati card try version 8.4 or 8.10.

---

### Post by Milkium on 2008-10-24
Is 8.10 buggy?
I'm using Ubuntu 8.04, and pretty much all is well. 
Wouldn't want anything bad to happen.

---

### Post by Milkium on 2008-10-24
bump.

---

### Post by Milkium on 2008-10-25
bump.

---

### Post by Catholicnerd on 2008-10-25
I'm using 8.10, and aside from crashing about every fifteen minutes or so, WoW works great for me.  What I had to do to get it working was disable pixel shader support in winecfg, and then run WoW in windowed mode.  You'll need to close your minimap every time you enter the game, or the screen will just go berserk again.  Not a perfect situation, but at least it works.](*,)

---

### Post by Milkium on 2008-10-27
I disabled pixel shader support, and I have set to run in windowed mode, yet it still doesn't work.

---

### Post by Eviljim on 2008-10-27
> Is 8.10 buggy?

Probably. All I can tell you is that with my 2600XT card and pre 3.0 patch only driver version 8.4 worked fine.

When the latest patch hit, driver V8.4 didnt work and I had to try 8.10, which runs fine in fullscreen (as before)and a decent graphic detail.

---

### Post by Milkium on 2008-10-27
Hm. I'll create a new thread with a few more elaborations, as I didn't really make too many here.

---

