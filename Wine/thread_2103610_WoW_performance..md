---
title: "WoW performance."
date: 2013-01-10
forum: Wine
---

### Post by Zirts on 2013-01-10
Hi,

Im running a 
MD Athlon(tm) II P340 Dual-Core Processor × 2    @ 2.22 GHz
ATI Radeon HD 5650 With  12.11 Beta proprietary driver.
RAM 4 GB

So I ran WoW MoP from Wine today and FPS was at 14, and the settings were a lot lower than on Windows. (Can run it almoust ultra on windows with good FPS)

So my question:  Is it normal? Should I tweak the game a bit more? I have only changed in-game options tough. 
Or is the driver bad? Should I go with the stable release?

---

### Post by mastablasta on 2013-01-11
it could be the driver, it could be wine needing some extra tweaks, it could be the desktop effects causing the lag or it could simply be that the version of the game is not compatible with linux. hard to say from your data...

---

### Post by rudeboyskunk on 2013-01-11
When I played WoW several years ago I would run it under wine and get ~30fps (with the lowest settings possible).  If you go to wowwiki, they have a page for setting it up under wine that gives you little tweaks you can do.

Also, Blizzard *may* be releasing WoW (or another one of their games) this year for Linux, so you could just not pay them until the Linux version is out...

---

### Post by Zirts on 2013-01-11
Fair enought, I guess I will just wait a bit then for the official GNU/Linux port :)

Thanks for the replies!

---

### Post by holastickboy on 2013-01-11
You definitely won't get the same performance as under Windows, but you can definitely work at improving performance.  

1) Make sure it's using the OpenGL renderer instead of DirectX9. You can do this by adding SET gxAPI "opengl" to your config.wtf file in the WTF folder of your wow installation, or by adding it to the end of your Wine launch command (eg: wine wow.exe -opengl)

2) I like to also put SET ffxGlow "0" in my config.wtf, it removes the glow around everything, but increases performance.

3) For nvidia users, you can launch the game to take advantage of dual cores with the LD_PRELOAD command, but unfortunately you are stuck to one core usage if you're with AMD (unless you want to try hacked WINE versions, which are a hit and miss).

4) Turn down effects on Wow, particularly shadows, particles, and water quality. Won't look as nice, but it will work.

Other than that, you're going to need a lot more grunt to get it working at Ultra settings. I'm surprised you can even do that on Windows, my Phenom 2 x4 3.2ghz and Nvidia GTX 460 OC don't like that setting, and they are a great deal more powerful than the setup you posted.

---

### Post by Zirts on 2013-01-12
Thank you for the reply! The opengl setting fixed it but there is something weird now...  my game caps at 30 FPS, even tough game settings show that it should be able to go till 60 if possible :D    But even then the screen runs smooth so I'm happy.

---

### Post by holastickboy on 2013-01-13
> **Zirts said:**
> Thank you for the reply! The opengl setting fixed it but there is something weird now...  my game caps at 30 FPS, even tough game settings show that it should be able to go till 60 if possible :D    But even then the screen runs smooth so I'm happy.

In the advanced tab, ensure that it is not limiting the background and foreground frame rates (just uncheck the boxes).  Ensure Vsync is off, as well as in Unity (download and install unsettings, and then turn off vsync for Unity, which can cap your frame rate).  Good to hear it's working for you though!

Btw, there are other tweaks that might help you.  Here is my config.wtf, see if anything in there helps you!  Notice that the max fore and background fps are set in this one.  After turning off vsync in my nvidia settings, as well as in my unity settings, I am now running wow at 100+fps (though most of the settings are turned down, as I prefer smoothness to prettiness).

```

SET readTOS "1" 
SET readEULA "1" 
SET readScanning "-1" 
SET readContest "-1" 
SET locale "enUS" 
SET showToolsUI "1" 
SET accounttype "MP" 
SET readTerminationWithoutNotice "-1" 
SET installLocale "enUS" 
SET hwDetect "0" 
SET videoOptionsVersion "5" 
SET gxApi "OpenGL" 
SET gxWindow "0" 
SET gxMaximize "0" 
SET graphicsQuality "2" 
SET Gamma "1.000000" 
SET Sound_MusicVolume "0.40000000596046" 
SET Sound_AmbienceVolume "0.60000002384186" 
SET farclip "600" 
SET particleDensity "40" 
SET rippleDetail "1" 
SET reflectionMode "0" 
SET environmentDetail "50" 
SET shadowTextureSize "2048" 
SET SSAOBlur "1" 
SET terrainLodDist "300" 
SET wmoLodDist "300" 
SET terrainTextureLod "1" 
SET worldBaseMip "1" 
SET componentTextureLevel "0" 
SET weatherDensity "1" 
SET ffxDeath "0" 
SET ffx "0" 
SET ffxGlow "0" 
SET M2UseShaders "0" 
SET pixelShaders "1" 
SET SmallCull "0.07" 
SET specular "0" 
SET trilinear "0" 
SET useWeatherShaders "0" 
SET enterWorld "1" 
SET maxFPS "0" 
SET maxFPSBk "0" 
SET mouseSpeed "1" 
SET ChatMusicVolume "0.29999998211861" 
SET ChatSoundVolume "0.39999997615814" 
SET ChatAmbienceVolume "0.29999998211861" 
SET VoiceActivationSensitivity "0.39999997615814" 
SET Sound_EnableMusic "0" 
SET realmName "Earthen Ring" 
SET gameTip "23" 
SET projectedTextures "1" 
SET textureFilteringMode "0"
```

---

### Post by Zirts on 2013-01-13
Managed to get a constant 48 FPS with turning vsync off and unchecking the FPS cappers. Pretty much of a perfcect now for me as I like some graphics too on my screen :D   Many thanks !

---

