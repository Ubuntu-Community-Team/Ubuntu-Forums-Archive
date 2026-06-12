---
title: "WoW on HP DV6000 with Ubuntu 8.04 and Wine 0.9.60"
date: 2008-05-02
forum: Wine
---

### Post by Aruza on 2008-05-02
I am running Ubuntu 8.04 and Wine 0.9.60 on my HP DV6000.
I am trying to run WoW on said laptop and when i run wow it will run and i can login but my screen looks like the following. Notice the icons that dont load correctly.

[IMG]http://www.bloodshedcoven.com/joestempfolder/ss.png[/IMG]

Any help would be awesome!
Thanks
Aruza

---

### Post by thisismalhotra on 2008-05-02
Do you have ATi video card ... can you give details spec of your PC pls.
Also, did you try to do all the fixes here...

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

If you can post you config.wtf and xorg.conf pls...

---

### Post by situz on 2008-05-02
add this to your config.wtf file:
>  Set UIFaster "2"

that should fix your problem ;)

---

### Post by Aruza on 2008-05-03
ok adding the Set UIFaster "2" worked for having the UI load correctly but im still getting massive lag. Is that just because its running in wine or is there other config that i have to do?

thisismalhotra i do not have the ATI graphics i have the intel version.
the following is my config.wtf

SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x800"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET fullAlpha "1"
SET SmallCull "0.070000"
SET DistCull "350.000000"
SET trilinear "1"
SET frillDensity "32"
SET farclip "177"
SET pixelShaders "1"
SET particleDensity "0.400000"
SET unitDrawDist "300.000000"
SET movie "0"
SET DesktopGamma "1"
SET Gamma "1.000000"
SET readTOS "1"
SET readEULA "1"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "0.60000002384186"
SET realmList "us.logon.worldofwarcraft.com"
SET realmName "Magtheridon"
SET gameTip "6"
SET AmbienceVolume "0.60000002384186"
SET uiScale "0.69999998807907"
SET useUiScale "1"
SET mouseSpeed "1"
SET cameraYawMoveSpeed "200"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "2"
SET cameraSmoothStyle "0"
SET profanityFilter "0"
SET EnableMusic "0"
SET showGameTips "0"
SET ShowTargetCastbar "1"
SET readScanning "-1"
SET readContest "-1"
SET expansionMovie "0"
SET spamFilter "0"
SET minimapInsideZoom "0"
SET CombatLogRangeCreature "200"
SET CombatDeathLogRange "200"
SET minimapZoom "0"
SET patchlist "us.version.worldofwarcraft.com"
SET EnableErrorSpeech "0"
SET lod "1"
SET showToolsUI "1"
SET autoDismountFlying "1"
SET statusBarText "1"
SET ShowVKeyCastbar "1"
SET autoSelfCast "1"
SET ChatBubbles "0"
SET guildMemberNotify "1"
SET scriptErrors "1"
SET M2UseShaders "0"
SET MasterSoundEffects "0"
SET cameraView "4"
SET coresDetected "2"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET Sound_OutputDriverName "System Default"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_EnableAmbience "0"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET EnableVoiceChat "1"
SET PushToTalkButton "LCTRL"
SET readTerminationWithoutNotice "-1"
SET Sound_EnableMusic "0"
SET UnitNameNPC "1"
SET weatherDensity "0"
SET videoOptionsVersion "1"
SET CombatLogRangeParty "200"
SET CombatLogRangePartyPet "200"
SET CombatLogRangeFriendlyPlayers "200"
SET CombatLogRangeFriendlyPlayersPets "200"
SET CombatLogRangeHostilePlayers "200"
SET CombatLogRangeHostilePlayersPets "200"
SET CombatHealing "0"
SET Sound_EnableSFX "0"
SET Sound_EnableAllSound "0"
SET groundEffectDist "70"
SET textureFilteringMode "0"
SET gxFixLag "0"
SET MaxLights "1"
SET gxWindow "1"
SET baseMip "1"
SET spellEffectLevel "0"
SET cameraPitchMoveSpeed "100"
SET cameraPitchSmoothSpeed "45"
SET lootUnderMouse "1"
SET questFadingDisable "1"
SET fctCombatState "1"
SET fctLowManaHealth "1"
SET fctHonorGains "1"
SET fctAuras "1"
SET showNewbieTips "0"
SET showPartyDebuffs "0"
SET enableCombatText "1"
SET fctDodgeParryMiss "1"
SET fctRepChanges "1"
SET hidePartyInRaid "1"
SET showPartyBuffs "1"
SET autoLootCorpse "1"
SET checkAddonVersion "0"
SET UnitNamePlayerPVPTitle "0"
SET UnitNameEnemyPlayerName "0"
SET UnitNameEnemyPetName "0"
SET UnitNameEnemyCreationName "0"
SET UnitNameFriendlyPlayerName "0"
SET UnitNameFriendlyPetName "0"
SET UnitNameFriendlyCreationName "0"
SET UnitNameCompanionName "0"
SET gxMaximize "1"
SET windowResizeLock "1"
SET gxApi "opengl"
SET ffxDeath "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET ffxGlow "0"
SET lastCharacterIndex "1"
SET UIFaster "2"

thanks for your help so far guys!
Aruza

---

### Post by situz on 2008-05-03
have you done the registry fps boost for wine? 

[http://ubuntuforums.org/showthread.php?t=303509](http://ubuntuforums.org/showthread.php?t=303509)

---

### Post by Aruza on 2008-05-06
Ok i have tried Tweak 1 and i didnt notice an improvement. \
Tweak 2 i make the loader as specified but when i double clicked to run it didnt do anything except give me a prompt at which i selected run.

any thoughts?

i also noticed that even at the login screen my mouse is very laggy and choppy

---

