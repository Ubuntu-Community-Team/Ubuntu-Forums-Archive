---
title: "Ground Texture Issues in WoW"
date: 2008-05-20
forum: Wine
---

### Post by dur on 2008-05-20
I've just recently installed WoW 2.4.2 under Wine 1.0-rc1 in Ubuntu 8.04. It runs very well, except for one little problem. The ground textures are all miscoloured, like so:

[http://img143.imageshack.us/my.php?image=screenshotii6.png](http://img143.imageshack.us/my.php?image=screenshotii6.png)

Has anyone else experienced this issue before? If so, do you know what can be done to solve this? Thanks. Here are all my specs:

Intel Celeron processor 1.7GHz
2GB DDR RAM
Intel X3100 integrated graphics chipset (with latest driver version from ubuntu repositories)

Ubuntu Hardy Heron
Wine v. 1.0-rc1

Here is my WoW Config.wtf:

```
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET SmallCull "0.070000"
SET DistCull "350.000000"
SET frillDensity "8"
SET farclip "177"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET movie "0"
SET expansionMovie "0"
SET realmList "us.logon.worldofwarcraft.com"
SET ffxDeath "0"
SET ffxGlow "0"
SET UIFaster "2"
SET readTerminationWithoutNotice "-1"
SET coresDetected "1"
SET gxCursor "0"
SET videoOptionsVersion "1"
SET textureFilteringMode "0"
SET checkAddonVersion "0"
SET Gamma "1.000000"
SET showToolsUI "1"
SET Sound_VoiceChatInputDriverName "dsnoop:0"
SET Sound_VoiceChatOutputDriverName "System Default"
SET Sound_OutputDriverName "System Default"
SET patchlist "us.version.worldofwarcraft.com"
SET baseMip "1"
SET spellEffectLevel "0"
SET groundEffectDist "70"
SET weatherDensity "0"
SET realmName "Mal'Ganis"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET gameTip "4"
SET uiScale "1"
SET shadowLOD "0"
SET gxApi "opengl"
SET M2UseShaders "0"
SET gxWindow "1"
SET accountName "dagothurreturns"
SET Sound_VoiceChatInputDriverIndex "1"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET DesktopGamma "1"
SET lod "1"
SET showNewbieTips "0"
SET UberTooltips "0"
```

Again, thanks in advance!

---

### Post by dur on 2008-05-25
No one has any ideas?

---

### Post by pissedoffdude on 2008-05-26
Intel's graphics cards don't work so well with opengl due to their drivers. So you should try running in d3d mode. Try removing this line from your config.wtf: ```
SET gxApi "opengl"
```

---

