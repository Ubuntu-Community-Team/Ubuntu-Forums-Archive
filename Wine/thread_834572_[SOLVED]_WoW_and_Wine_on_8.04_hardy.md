---
title: "[SOLVED] WoW and Wine on 8.04 hardy"
date: 2008-06-19
forum: Wine
---

### Post by kennster on 2008-06-19
well i was running gusty and it worked fine and now i uninstalled and reinstalled 8.04 version of ubuntu and well Wine dosent seem to load the textures right  here is what my config folder looks like

```

SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET locale "enUS"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1600x1024"
SET gxRefresh "51"
SET gxMultisample "1"
SET gxMultisampleQuality "0.000000"
SET videoOptionsVersion "1"
SET pixelShaders "1"
SET movie "0"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET farclip "777"
SET specular "1"
SET particleDensity "1.000000"
SET realmName "Proudmoore"
SET gxWindow "1"
SET windowResizeLock "1"
SET textureFilteringMode "3"
SET expansionMovie "0"
SET DesktopGamma "1"
SET Gamma "1.000000"
SET groundEffectDist "120"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET gameTip "30"
SET uiScale "0.89999997615814"
SET useUiScale "1"
SET gxFixLag "1"
SET mouseSpeed "0.85000002384186"
SET profanityFilter "0"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET autoDismountFlying "1"
SET assistAttack "1"
SET stopAutoAttackOnTargetChange "1"
SET autoSelfCast "1"
SET lootUnderMouse "1"
SET showTargetOfTarget "1"
SET questFadingDisable "1"
SET enableCombatText "1"
SET combatTextFloatMode "3"
SET fctCombatState "1"
SET fctDodgeParryMiss "1"
SET fctDamageReduction "1"
SET fctRepChanges "1"
SET fctReactives "1"
SET fctFriendlyHealers "1"
SET fctLowManaHealth "1"
SET fctEnergyGains "1"
SET fctHonorGains "1"
SET fctAuras "1"
SET showChatIcons "1"
SET ShowTargetCastbar "1"
SET ShowVKeyCastbar "1"
SET Sound_OutputQuality "2"
SET Sound_EnableReverb "1"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET Sound_ZoneMusicNoDelay "1"
SET Sound_EnableSoundWhenGameIsInBG "1"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET checkAddonVersion "0"
SET cameraDistanceMaxFactor "2"
SET gxTripleBuffer "1"
SET lod "1"
SET spellEffectLevel "7"
SET weatherDensity "3"
SET ffxGlow "0"
SET shadowLevel "0"
SET groundEffectDensity "56"

```
and from what i know i have envyNG so i think i have the right graphics drivers if you want a screen shot of whats happen ill be happy to post

---

### Post by kennster on 2008-06-19
bump!

---

### Post by kennster on 2008-06-19
fixed it my self SET gxApi "opengl" was missing :D

---

