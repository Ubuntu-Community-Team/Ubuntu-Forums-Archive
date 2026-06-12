---
title: "WoW Issue(s)"
date: 2008-07-04
forum: Wine
---

### Post by Le-Froid on 2008-07-04
For some reason, I can't log on to already created chars without my computer freezing on me. Also, when I make a new character everything looks sort of..weird and there is only text for about ~3 seconds.

Here is my config.wtf:

```
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1152x864"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET doodadAnim "0"
SET SmallCull "0.010000"
SET DistCull "350.000000"
SET MaxLights "1"
SET frillDensity "8"
SET farclip "237"
SET particleDensity "0.400000"
SET baseMip "1"
SET movie "0"
SET expansionMovie "0"
SET readTOS "1"
SET readEULA "1"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET coresDetected "2"
SET videoOptionsVersion "1"
SET pixelShaders "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET spellEffectLevel "6"
SET realmName "Ghostlands"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET cameraPitchMoveSpeed "125"
SET cameraPitchSmoothSpeed "45"
SET gameTip "70"
SET DesktopGamma "1"
SET Gamma "1.000000"
SET groundEffectDist "70"
SET uiScale "0.84999996423721"
SET profanityFilter "0"
SET cameraYawMoveSpeed "250"
SET ChatBubblesParty "1"
SET UnitNameOwn "1"
SET questFadingDisable "1"
SET showNewbieTips "0"
SET scriptErrors "1"
SET useUiScale "1"
SET showChatIcons "1"
SET checkAddonVersion "0"
SET autoClearAFK "0"
SET mouseSpeed "1"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "1"
SET fctCombatState "1"
SET fctLowManaHealth "1"
SET fctHonorGains "1"
SET fctAuras "1"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_EnableAmbience "0"
SET Sound_EnableMusic "0"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET Sound_EnableSFX "0"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET gxWindow "1"
SET lastCharacterIndex "2"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"

```

I also attached a picture of what it does look like after logging on to a *new* character

---

### Post by Le-Froid on 2008-07-05
Bump :(

---

### Post by dserver on 2008-07-05
Edit: Sorry, I just saw that you already have this added.

For the graphical problem, try adding
```
SET gxApi "opengl"
SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxColorBits "24"
SET gxDepthBits "24"
```
to your /World of Warcraft/wtf/Config.wtf file.

---

### Post by pissedoffdude on 2008-07-07
What kind of video card do you have?  Be sure that you have installed the latest drivers for it.

---

### Post by Le-Froid on 2008-07-07
> **pissedoffdude said:**
> What kind of video card do you have?  Be sure that you have installed the latest drivers for it.

I believe it is "Intel Corporation 82G965 Integrated Graphics Controller".

---

### Post by piousp on 2008-07-08
Check out [this]("http://www.wowwiki.com/Linux/Wine/Troubleshooting") site

---

### Post by Le-Froid on 2008-07-08
> **piousp said:**
> Check out [this]("http://www.wowwiki.com/Linux/Wine/Troubleshooting") site

I've already tried everything there :(
Everything I tried there (and on the ubuntu help articles) ends up crashing my computer.

---

### Post by pissedoffdude on 2008-07-09
> **Le-Froid said:**
> I believe it is "Intel Corporation 82G965 Integrated Graphics Controller".

Unfortunately, intel's linux drivers aren't very great right now.  You're options would be to either run WoW in d3d mode or use windows.  To run in d3d mode, remove ```
SET gxApi "opengl"
```

---

### Post by Le-Froid on 2008-07-09
> **pissedoffdude said:**
> Unfortunately, intel's linux drivers aren't very great right now.  You're options would be to either run WoW in d3d mode or use windows.  To run in d3d mode, remove ```
SET gxApi "opengl"
```

Guess I'll just use my vista partition :(
System crashes without the opengl mode..although it seems everything with WoW crashes my system :p

---

