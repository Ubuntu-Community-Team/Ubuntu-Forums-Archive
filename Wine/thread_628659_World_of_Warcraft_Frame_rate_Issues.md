---
title: "World of Warcraft Frame rate Issues"
date: 2007-12-01
forum: Wine
---

### Post by Sephrik on 2007-12-01
Well I'm sure this has been touched upon before, but I've searched and I can't find anyone with the exact same issue.

Anyway the problem is that the frame rate seems to be a bit jumpy, at one point going from 4 - 60 at one point, depending on the perspective I'm looking at, I've taken a few screens to help explain it (the framerate is at the bottom of the screen shot) : 

This is a typically low frame rate (however it does jump from 4-10 fps)
[[IMG]http://img131.imageshack.us/img131/5679/lowframeratebi1.th.jpg[/IMG]](http://img131.imageshack.us/my.php?image=lowframeratebi1.jpg)

Getting a bit Higher as I start to look at the sky
[[IMG]http://img47.imageshack.us/img47/8444/framerategoingdownpg8.th.jpg[/IMG]](http://img47.imageshack.us/my.php?image=framerategoingdownpg8.jpg)

40-60 As I look at the sky:
[[IMG]http://img124.imageshack.us/img124/4162/frameratehigh2ys9.th.jpg[/IMG]](http://img124.imageshack.us/my.php?image=frameratehigh2ys9.jpg)

Also for some reason when I shake the camera around the frame rate can double O_o.

Here's a copy of my config.wtf file:
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "50"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET SmallCull "0.070000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "177"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET expansionMovie "0"
SET realmList "hswow.servegame.com"
SET readTerminationWithoutNotice "-1"
SET coresDetected "2"
SET videoOptionsVersion "1"
SET showToolsUI "1"
SET patchlist "us.version.worldofwarcraft.com"
SET gxApi "opengl"
SET realmName "Hades"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET Gamma "1.000000"
SET Sound_VoiceChatInputDriverName "dsnoop:0"
SET Sound_VoiceChatOutputDriverName "dmix:0"
SET Sound_OutputDriverName ""
SET Sound_MasterVolume "0.69999998807907"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.60000002384186"
SET Sound_AmbienceVolume "0.69999998807907"
SET groundEffectDist "70"
SET gameTip "49"
SET uiScale "1"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET Sound_ZoneMusicNoDelay "1"
SET spellEffectLevel "0"
SET gxCursor "0"
SET weatherDensity "0"
SET ffxDeath "0"
SET ffxGlow "0"
SET gxVSync "0"
SET textureFilteringMode "0"
SET accountName "Piers"
SET baseMip "1"
SET lastCharacterIndex "1"
SET minimapInsideZoom "2"
SET DesktopGamma "1"


3ghz Processor
Half a gig of ram
Nvida 5200 FX Geforce

Any ideas on how to get the frame rate a bit more stable and higher?

---

### Post by cogadh on 2007-12-01
Did you create a registry entry in Wine to set your correct video card memory?

---

### Post by Ren Höek on 2007-12-02
Actually it is not unnormal to get different frame rates depending on what is rendered.
If you look up only a few triangles have to pass the rendering pipeline. Looking at a bunch of other characters/npcs your graphic card has much more to do.

In this [**wiki**]("http://www.wowwiki.com/Linux/Wine") you can find a registry tweak, wich worked well for me.
Maybe also a newer driver could increase frame rate. What graphic card are you using? And with wich drivers?

Edit: Like I noticed you mentioned already "Nvida 5200 FX Geforce"...

---

### Post by Sephrik on 2007-12-03
Thanks for the replies guys, the frame rate is just playable most of the time (7-10 fps, outdoors), I guess I might have to live with it...Or dual boot T_T.

@Ren Höek Sorry I forgot to mention that I've already tried that registry tweak, though it did boost my frame rate a bit.

---

### Post by Ferrat on 2007-12-03
To be honest I think your real bottleneck is in your RAM, 512 is minimum (early releases says 256, but blizz realized that it was too little). 

If possible upgrade to 1GB or more

---

### Post by fbmx24 on 2007-12-04
I would highly suggest adding more ram. When I run wow with wine i get 68-75 fps. While my video card is better it is mainly the ram that helps the most. I have 2gb and the game runs using around 1gb. So I would get more ram and the game will play fine. 
     Also make sure you have the newest version of wine. I was getting around 20 fps lower with the older version.

---

