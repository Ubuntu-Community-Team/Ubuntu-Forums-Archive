---
title: "No sound with WoW &amp; Wine"
date: 2007-12-25
forum: Wine
---

### Post by mjkelly on 2007-12-25
I'm pretty Linux literate, using it for over 10 years now actually, and im at a loss with this problem. I just cant get sound in WoW with Wine. I've searched up and down for a solution too with no such luck.

I am using an USB 5.1 sound card and alsa correctly identifies it and runs it properly.
lsusb: Bus 001 Device 005: ID 0c45:1677 Microdia 
aplay -l: **** List of PLAYBACK Hardware Devices ****
card 0: Audio [USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The soundcard is relatively new and OSS will NOT detect it. I needed the latest version of ALSA to get it to run at all..

Wine is version 0.9.51
Alsa is version 1.0.15 compiled from source, not repositories

When i run winecfg, warcraft 3 with wine, or world of warcraft i get the following same errors corresponding to alsa:

err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on USB Audio, disabling mixer

War3 plays sound just fine right out of the box, and winecfg's audio panel tests the audio just fine with alsa. However, WoW does not want to run any sound and since wine tests sound fine, and war3 and frozen throne both play sound correctly, i think its a WoW problem. And i have tried all the different options in the bottom of the audio tab in winecfg about hardware emulation and the like.






I'm just going to add some more errors i get when i run WoW, i dont think any of them are relevant to this issue however. Also, i'll include my config.wtf.
WoW errors:
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on USB Audio, disabling mixer
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed84,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34ecac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f2a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f40c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f580,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x1b2c00) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1b2fd0) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x34efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f124,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x7

Config.WTF
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET fullAlpha "1"
SET SmallCull "0.010000"
SET DistCull "500.000000"
SET shadowLevel "0"
SET trilinear "1"
SET frillDensity "48"
SET farclip "597"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET anisotropic "16"
SET movie "0"
SET movieSubtitle "1"
SET mouseSpeed "1.5"
SET Gamma "0.900000"
SET readTOS "1"
SET readEULA "1"
SET profanityFilter "0"
SET MusicVolume "0"
SET SoundVolume "0.20000000298023"
SET MasterVolume "0.20000000298023"
SET realmList "us.logon.worldofwarcraft.com"
SET weatherDensity "3"
SET cameraYawMoveSpeed "210"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceA "7.182460"
SET cameraPitchA "19.000000"
SET cameraYawA "2.000000"
SET cameraDistanceB "15.610087"
SET cameraPitchB "26.399998"
SET cameraYawB "3.100004"
SET cameraDistanceC "50.000000"
SET cameraPitchC "16.500000"
SET cameraYawC "4.0000000"
SET cameraPitchD "16.500000"
SET cameraYawD "0.000000"
SET cameraDistanceMaxFactor "2"
SET realmName "Alterac Mountains"
SET gameTip "17"
SET AmbienceVolume "0"
SET uiScale "1"
SET autoSelfCast "1"
SET scriptMemory "112640"
SET minimapInsideZoom "0"
SET soundMaxHardwareChannels "6"
SET gxMaximize "1"
SET readScanning "-1"
SET readContest "-1"
SET SoundNumChannels "128"
SET expansionMovie "0"
SET minimapZoom "0"
SET gxTripleBuffer "1"
SET cameraView "4"
SET accountName "bansheetk"
SET EnableSoundWhenGameIsInBG "1"
SET SoundZoneMusicNoDelay "1"
SET SoundUseHardware "0"
SET EnableErrorSpeech "0"
SET EnableAmbience "0"
SET patchlist "us.version.worldofwarcraft.com"
SET UberTooltips "0"
SET UnitNameOwn "1"
SET guildMemberNotify "1"
SET showToolsUI "0"
SET spellEffectLevel "3"
SET coresDetected "2"
SET lod "1"
SET baseMip "1"
SET Sound_VoiceChatInputDriverName "SoundMAX Digital Audio"
SET Sound_VoiceChatOutputDriverName "SoundMAX Digital Audio"
SET Sound_OutputDriverName "SoundMAX Digital Audio"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "0.40000000596046"
SET Sound_MusicVolume "0.10000000149012"
SET Sound_AmbienceVolume "0.40000000596046"
SET ffxGlow "0"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET UnitNamePlayer "0"
SET UnitNamePlayerPVPTitle "0"
SET checkAddonVersion "0"
SET readTerminationWithoutNotice "-1"
SET deselectOnClick "0"
SET videoOptionsVersion "1"

---

### Post by mjkelly on 2007-12-25
I tried editing the original post to correct this but twice it wouldnt let me.

I removed the USB device and now im using only the onboard intel sound card. So its not an Alsa issue like i thought it was.

Wine and games under Wine play sound just fine with my onboard sound and Alsa. Why wont WoW play any sound?

---

### Post by Hoaxe on 2007-12-25
did you take a look at wineconfig.

i just had the problem since i unfroze my account after like 6 months i think? 

lot's of new stuff and wow is the only reason i use wine. the new wine config panel is what i'm looking at now, under the audio tab probably what you are looking for...

hope it helps

EDIT: 
yeah this is what worked for me

in the wine config panel thingy under audio, deselct OSS and selet ALSA instead
apply changes

close and re-open WOW

should have a full orchestra playing

---

### Post by Mad-Halfling on 2007-12-28
I'm getting this same issue, I have tried just enabling ALSA but that doesn't make any difference.  The odd thing is that it was all working up until a short while ago.  Even after Blizz messed about with all the sound programming, I still managed to get it working using W2K as the WINE windows version, but then the sound disappeared again.  When I go into the WoW sounds setup there are no sound output devices available.  Anyone else found any other solutions to this?

Here's my config (the 1st 3 lines are what I have added to try to force the sound to use alsa)

SET ffxDeath "0"
SET SoundOutputSystem "6"
SET SoundBufferSize "150"
SET soundMaxHardwareChannels "12"
SET locale "enGB"
SET hwDetect "0"
SET gxRefresh "50"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET doodadAnim "0"
SET SmallCull "0.040000"
SET DistCull "350.000000"
SET MaxLights "1"
SET frillDensity "32"
SET farclip "357"
SET particleDensity "0.300000"
SET baseMip "1"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET gxResolution "1280x800"
SET gxCursor "0"
SET M2UseShaders "0"
SET Gamma "1.000000"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "0.9"
SET ffx "0"
SET AmbienceVolume "0.60000002384186"
SET uiScale "0.95999997854233"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "1"
SET gameTip "50"
SET minimapInsideZoom "0"
SET mouseInvertPitch "1"
SET expansionMovie "0"
SET profanityFilter "0"
SET timingTestError "0"
SET ShowTargetCastbar "1"
SET minimapZoom "0"
SET weatherDensity "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxTripleBuffer "1"
SET showToolsUI "1"
SET cameraView "5"
SET EnableSoundWhenGameIsInBG "1"
SET mouseSpeed "1.3999999761581"
SET coresDetected "2"
SET readTerminationWithoutNotice "1"
SET Sound_VoiceChatInputDriverName "Microphone (Conexant High Definition Audio)"
SET Sound_VoiceChatOutputDriverName "Internal Speaker/Headphone (Conexant High Definition Audio)"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET useUiScale "1"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_EnableSoundWhenGameIsInBG "1"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET autoSelfCast "1"
SET videoOptionsVersion "1"
SET pixelShaders "1"
SET spellEffectLevel "6"
SET groundEffectDist "70"
SET Sound_NumChannels "64"
SET scriptErrors "1"
SET checkAddonVersion "0"
SET CombatLogRangeCreature "50"
SET Sound_EnableErrorSpeech "0"

---

### Post by Candid357 on 2007-12-28
I am having the same problem... The graphics work fine, and I too am no new-to-linux user.(3 years now) we just got WoW and the sound does not work. I tried fixing it myself, and there has been nothing I can do. I looked over all the howto's and again nothing. Has anyone an idea?

---

### Post by Ripfox on 2007-12-29
I had no sound after getting the free Burning Crusade 10 days, but when I went into winecfg and checked the box "driver emulation" in the Audio tab it worked then.

Good luck hope it does the trick!

---

### Post by Nik0n on 2009-01-25
I might have a fix for you guys. I am some what new to Linux but im not a noob by any means. 

Anyway, My problem was the Windows version selected in wine.

I copied the wow folder from my windows drive because i didnt want to install the all 3 games. I have vista so i set it to vista for the version
but for some reason it will only work for XP for me.

hope it helps

---

