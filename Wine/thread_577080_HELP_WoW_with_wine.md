---
title: "HELP: WoW with wine"
date: 2007-10-15
forum: Wine
---

### Post by -gabe-noob- on 2007-10-15
Ok so I've followed the guide, and I've downloaded WoW and TBC on my computer. there is one problem though, When I run WoW it shows the cinematic for TBC then shuts down and returns to the desktop. I'm using ubuntu 7.04 and the lates version of Wine.

When I start from terminal this is what I get 


gabe@gabe-laptop:~$ wine "C:\Program Files\World of Warcraft\WoW.exe"
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d020000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d020000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ede4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ed18,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f328,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f05c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f724,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x12c630) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x12fc68) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x33f05c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
Mesa 6.5.2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22

Common dieing for some wow action

---

### Post by Faud on 2007-10-15
Have you tried running it in OpenGL mode ?

---

### Post by -gabe-noob- on 2007-10-15
Can't theres no config.wtf  because I have not been able to start it successfully.

---

### Post by ajackson on 2007-10-15
What is stopping you from creating the config.wtf yourself?

---

### Post by -gabe-noob- on 2007-10-15
Because I'm a noob with Ubuntu and just computers in general and have no Idea how lol and on the guide it says that you must have a successful launch for it to appear if it is not originally there.

---

### Post by Faud on 2007-10-15
Here is a copy of my config.wtf file. You can just copy it if you want. I run in opengl with alsa drivers. I play just fine with in-game voice chat working as it should. Good luck

```

SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "500.000000"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET expansionMovie "0"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET gameTip "93"
SET gxApi "opengl"
SET ffxGlow "0"
SET Gamma "1.000000"
SET mouseSpeed "1"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "0.80000003576279"
SET MasterSoundEffects "0"
SET EnableMusic "0"
SET EmoteSounds "0"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "1"
SET ChatBubbles "0"
SET autoDismountFlying "1"
SET SoundListenerAtCharacter "0"
SET AmbienceVolume "0.60000002384186"
SET deselectOnClick "0"
SET ShowTargetCastbar "1"
SET ShowVKeyCastbar "1"
SET UnitNamePlayer "0"
SET minimapZoom "0"
SET minimapInsideZoom "0"
SET profanityFilter "0"
SET timingTestError "0"
SET scriptErrors "1"
SET readScanning "-1"
SET readContest "-1"
SET coresDetected "2"
SET checkAddonVersion "0"
SET Sound_OutputDriverName "dmix:0"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.30000001192093"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "0"
SET Sound_MusicVolume "0"
SET Sound_AmbienceVolume "0"
SET OutboundChatVolume "2.5"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET cameraView "3"
SET guildMemberNotify "1"
SET Sound_VoiceChatInputDriverName "dsnoop:0"
SET Sound_VoiceChatOutputDriverName "dmix:0"
SET TargetNearestDistance "52.000000"
SET Sound_EnableMusic "0"
SET Sound_EnableErrorSpeech "0"
SET Sound_EnableEmoteSounds "0"
SET PushToTalkButton "NUMPADMINUS"
SET readTerminationWithoutNotice "-1"
SET autojoinPartyVoice "0"
SET lastCharacterIndex "6"
SET Sound_EnableAllSound "0"

```
I told out my account name and relam but the rest is  there for ya.

---

### Post by -gabe-noob- on 2007-10-15
Copied that into the terminal because thats what i thought I was supposed to do and I got this.


gabe@gabe-laptop:~$ SET locale "enUS"
bash: SET: command not found
gabe@gabe-laptop:~$ SET hwDetect "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET gxColorBits "24"
bash: SET: command not found
gabe@gabe-laptop:~$ SET gxDepthBits "24"
bash: SET: command not found
gabe@gabe-laptop:~$ SET gxResolution "800x600"
bash: SET: command not found
gabe@gabe-laptop:~$ SET gxRefresh "60"
bash: SET: command not found
gabe@gabe-laptop:~$ SET gxMultisampleQuality "0.000000"
bash: SET: command not found
gabe@gabe-laptop:~$ SET gxFixLag "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET fullAlpha "1"
bash: SET: command not found
gabe@gabe-laptop:~$ SET SmallCull "0.040000"
bash: SET: command not found
gabe@gabe-laptop:~$ SET DistCull "500.000000"
bash: SET: command not found
gabe@gabe-laptop:~$ SET trilinear "1"
bash: SET: command not found
gabe@gabe-laptop:~$ SET frillDensity "24"
bash: SET: command not found
gabe@gabe-laptop:~$ SET farclip "500.000000"
bash: SET: command not found
gabe@gabe-laptop:~$ SET specular "1"
bash: SET: command not found
gabe@gabe-laptop:~$ SET pixelShaders "1"
bash: SET: command not found
gabe@gabe-laptop:~$ SET particleDensity "1.000000"
bash: SET: command not found
gabe@gabe-laptop:~$ SET unitDrawDist "300.000000"
bash: SET: command not found
gabe@gabe-laptop:~$ SET movie "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET expansionMovie "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET readTOS "1"
bash: SET: command not found
gabe@gabe-laptop:~$ SET readEULA "1"
bash: SET: command not found
gabe@gabe-laptop:~$ SET showToolsUI "1"
bash: SET: command not found
gabe@gabe-laptop:~$ SET realmList "us.logon.worldofwarcraft.com"
bash: SET: command not found
gabe@gabe-laptop:~$ SET patchlist "us.version.worldofwarcraft.com"
bash: SET: command not found
gabe@gabe-laptop:~$ SET gameTip "93"
bash: SET: command not found
gabe@gabe-laptop:~$ SET gxApi "opengl"
bash: SET: command not found
gabe@gabe-laptop:~$ SET ffxGlow "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET Gamma "1.000000"
bash: SET: command not found
gabe@gabe-laptop:~$ SET mouseSpeed "1"
bash: SET: command not found
gabe@gabe-laptop:~$ SET MusicVolume "0.40000000596046"
bash: SET: command not found
gabe@gabe-laptop:~$ SET SoundVolume "1"
bash: SET: command not found
gabe@gabe-laptop:~$ SET MasterVolume "0.80000003576279"
bash: SET: command not found
gabe@gabe-laptop:~$ SET MasterSoundEffects "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET EnableMusic "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET EmoteSounds "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET cameraYawMoveSpeed "180"
bash: SET: command not found
gabe@gabe-laptop:~$ SET cameraYawSmoothSpeed "180"
bash: SET: command not found
gabe@gabe-laptop:~$ SET cameraDistanceMaxFactor "1"
bash: SET: command not found
gabe@gabe-laptop:~$ SET ChatBubbles "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET autoDismountFlying "1"
bash: SET: command not found
gabe@gabe-laptop:~$ SET SoundListenerAtCharacter "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET AmbienceVolume "0.60000002384186"
bash: SET: command not found
gabe@gabe-laptop:~$ SET deselectOnClick "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET ShowTargetCastbar "1"
bash: SET: command not found
gabe@gabe-laptop:~$ SET ShowVKeyCastbar "1"
bash: SET: command not found
gabe@gabe-laptop:~$ SET UnitNamePlayer "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET minimapZoom "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET minimapInsideZoom "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET profanityFilter "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET timingTestError "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET scriptErrors "1"
bash: SET: command not found
gabe@gabe-laptop:~$ SET readScanning "-1"
bash: SET: command not found
gabe@gabe-laptop:~$ SET readContest "-1"
bash: SET: command not found
gabe@gabe-laptop:~$ SET coresDetected "2"
bash: SET: command not found
gabe@gabe-laptop:~$ SET checkAddonVersion "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET Sound_OutputDriverName "dmix:0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET ChatMusicVolume "0.30000001192093"
bash: SET: command not found
gabe@gabe-laptop:~$ SET ChatSoundVolume "0.30000001192093"
bash: SET: command not found
gabe@gabe-laptop:~$ SET ChatAmbienceVolume "0.30000001192093"
bash: SET: command not found
gabe@gabe-laptop:~$ SET Sound_MasterVolume "1"
bash: SET: command not found
gabe@gabe-laptop:~$ SET Sound_SFXVolume "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET Sound_MusicVolume "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET Sound_AmbienceVolume "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET OutboundChatVolume "2.5"
bash: SET: command not found
gabe@gabe-laptop:~$ SET InboundChatVolume "1"
bash: SET: command not found
gabe@gabe-laptop:~$ SET VoiceActivationSensitivity "0.40000003576279"
bash: SET: command not found
gabe@gabe-laptop:~$ SET cameraView "3"
bash: SET: command not found
gabe@gabe-laptop:~$ SET guildMemberNotify "1"
bash: SET: command not found
gabe@gabe-laptop:~$ SET Sound_VoiceChatInputDriverName "dsnoop:0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET Sound_VoiceChatOutputDriverName "dmix:0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET TargetNearestDistance "52.000000"
bash: SET: command not found
gabe@gabe-laptop:~$ SET Sound_EnableMusic "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET Sound_EnableErrorSpeech "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET Sound_EnableEmoteSounds "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET PushToTalkButton "NUMPADMINUS"
bash: SET: command not found
gabe@gabe-laptop:~$ SET readTerminationWithoutNotice "-1"
bash: SET: command not found
gabe@gabe-laptop:~$ SET autojoinPartyVoice "0"
bash: SET: command not found
gabe@gabe-laptop:~$ SET lastCharacterIndex "6"
bash: SET: command not found
gabe@gabe-laptop:~$ SET Sound_EnableAllSound "0"

---

### Post by Faud on 2007-10-15
The config.wtf file is a file that only WoW uses. So. create a new text document. Copy the what I gave you into the text document. Name the text document config.wtf.

Then go to places->home folder.  Hit "show hiddend files" Then go to the .wine folder, then c drive then programs then World of Warcraft then either account folder or wtf folder (dont remember Im at work) then add the config.wtf file to the WTF folder. Close everything and give it a go.

---

### Post by -gabe-noob- on 2007-10-15
Sorry that I'm such a noob, what do you mean by text document, like an open office page?

---

### Post by Faud on 2007-10-15
You should be able to just right click on your desktop and hit create document.

---

### Post by -gabe-noob- on 2007-10-16
Ok so I installed WoW following the guide. at first I was having problems with the game shutting after the cinimatic so I created a config.wtf file and that solved that problem (the config.wtf was from another person) now it kinda works, when I get to the loggin screen the computer is horribly laggy and much of the screen is blacked out with triangular shapes. Edit: I also have 2 config.wtf files, would this be the problem? and how can I delete one.

Thank you for any replies I'm dieing to play some WoW here and I don't wanna go back to windows!

P.S. this is the config.wtf file

SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "500.000000"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET expansionMovie "0"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET gameTip "93"
SET gxApi "opengl"
SET ffxGlow "0"
SET Gamma "1.000000"
SET mouseSpeed "1"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "0.80000003576279"
SET MasterSoundEffects "0"
SET EnableMusic "0"
SET EmoteSounds "0"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "1"
SET ChatBubbles "0"
SET autoDismountFlying "1"
SET SoundListenerAtCharacter "0"
SET AmbienceVolume "0.60000002384186"
SET deselectOnClick "0"
SET ShowTargetCastbar "1"
SET ShowVKeyCastbar "1"
SET UnitNamePlayer "0"
SET minimapZoom "0"
SET minimapInsideZoom "0"
SET profanityFilter "0"
SET timingTestError "0"
SET scriptErrors "1"
SET readScanning "-1"
SET readContest "-1"
SET coresDetected "2"
SET Sound_OutputDriverName "dmix:0"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.30000001192093"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "0"
SET Sound_MusicVolume "0"
SET Sound_AmbienceVolume "0"
SET OutboundChatVolume "2.5"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET cameraView "3"
SET guildMemberNotify "1"
SET Sound_VoiceChatInputDriverName "dsnoop:0"
SET Sound_VoiceChatOutputDriverName "dmix:0"
SET TargetNearestDistance "52.000000"
SET Sound_EnableMusic "0"
SET Sound_EnableErrorSpeech "0"
SET Sound_EnableEmoteSounds "0"
SET PushToTalkButton "NUMPADMINUS"
SET readTerminationWithoutNotice "-1"
SET autojoinPartyVoice "0"
SET lastCharacterIndex "6"
SET Sound_EnableAllSound "0"
SET locale "enUS"

2nd config.wtf file

SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "500.000000"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET expansionMovie "0"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET gameTip "93"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET Gamma "1.000000"
SET mouseSpeed "1"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "0.80000003576279"
SET MasterSoundEffects "0"
SET EnableMusic "0"
SET EmoteSounds "0"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "1"
SET ChatBubbles "0"
SET autoDismountFlying "1"
SET SoundListenerAtCharacter "0"
SET AmbienceVolume "0.60000002384186"
SET deselectOnClick "0"
SET ShowTargetCastbar "1"
SET ShowVKeyCastbar "1"
SET UnitNamePlayer "0"
SET minimapZoom "0"
SET minimapInsideZoom "0"
SET profanityFilter "0"
SET timingTestError "0"
SET scriptErrors "1"
SET readScanning "-1"
SET readContest "-1"
SET coresDetected "2"
SET Sound_OutputDriverName "SigmaTel STAC9200"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.30000001192093"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "0"
SET Sound_MusicVolume "0"
SET Sound_AmbienceVolume "0"
SET OutboundChatVolume "2.5"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET cameraView "3"
SET guildMemberNotify "1"
SET Sound_VoiceChatInputDriverName "dsnoop:0"
SET Sound_VoiceChatOutputDriverName "dmix:0"
SET TargetNearestDistance "52.000000"
SET Sound_EnableMusic "0"
SET Sound_EnableErrorSpeech "0"
SET Sound_EnableEmoteSounds "0"
SET PushToTalkButton "NUMPADMINUS"
SET readTerminationWithoutNotice "-1"
SET autojoinPartyVoice "0"
SET lastCharacterIndex "6"
SET Sound_EnableAllSound "0"
SET locale "enUS"

Edit:adding specs

1 gig ram
intel dual core 
and an intel chipset 945 gm I belive for the graphics card.

---

### Post by -gabe-noob- on 2007-10-16
Ok so I installed WoW following the guide. at first I was having problems with the game shutting after the cinimatic so I created a config.wtf file and that solved that problem (the config.wtf was from another person) now it kinda works, when I get to the loggin screen the computer is horribly laggy and much of the screen is blacked out with triangular shapes. Edit: I also have 2 config.wtf files, would this be the problem? and how can I delete one.

Thank you for any replies I'm dieing to play some WoW here and I don't wanna go back to windows!

P.S. this is the config.wtf file

SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "500.000000"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET expansionMovie "0"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET gameTip "93"
SET gxApi "opengl"
SET ffxGlow "0"
SET Gamma "1.000000"
SET mouseSpeed "1"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "0.80000003576279"
SET MasterSoundEffects "0"
SET EnableMusic "0"
SET EmoteSounds "0"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "1"
SET ChatBubbles "0"
SET autoDismountFlying "1"
SET SoundListenerAtCharacter "0"
SET AmbienceVolume "0.60000002384186"
SET deselectOnClick "0"
SET ShowTargetCastbar "1"
SET ShowVKeyCastbar "1"
SET UnitNamePlayer "0"
SET minimapZoom "0"
SET minimapInsideZoom "0"
SET profanityFilter "0"
SET timingTestError "0"
SET scriptErrors "1"
SET readScanning "-1"
SET readContest "-1"
SET coresDetected "2"
SET Sound_OutputDriverName "dmix:0"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.30000001192093"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "0"
SET Sound_MusicVolume "0"
SET Sound_AmbienceVolume "0"
SET OutboundChatVolume "2.5"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET cameraView "3"
SET guildMemberNotify "1"
SET Sound_VoiceChatInputDriverName "dsnoop:0"
SET Sound_VoiceChatOutputDriverName "dmix:0"
SET TargetNearestDistance "52.000000"
SET Sound_EnableMusic "0"
SET Sound_EnableErrorSpeech "0"
SET Sound_EnableEmoteSounds "0"
SET PushToTalkButton "NUMPADMINUS"
SET readTerminationWithoutNotice "-1"
SET autojoinPartyVoice "0"
SET lastCharacterIndex "6"
SET Sound_EnableAllSound "0"
SET locale "enUS"

2nd config.wtf file

SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "500.000000"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET expansionMovie "0"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET gameTip "93"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET Gamma "1.000000"
SET mouseSpeed "1"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "0.80000003576279"
SET MasterSoundEffects "0"
SET EnableMusic "0"
SET EmoteSounds "0"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "1"
SET ChatBubbles "0"
SET autoDismountFlying "1"
SET SoundListenerAtCharacter "0"
SET AmbienceVolume "0.60000002384186"
SET deselectOnClick "0"
SET ShowTargetCastbar "1"
SET ShowVKeyCastbar "1"
SET UnitNamePlayer "0"
SET minimapZoom "0"
SET minimapInsideZoom "0"
SET profanityFilter "0"
SET timingTestError "0"
SET scriptErrors "1"
SET readScanning "-1"
SET readContest "-1"
SET coresDetected "2"
SET Sound_OutputDriverName "SigmaTel STAC9200"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.30000001192093"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "0"
SET Sound_MusicVolume "0"
SET Sound_AmbienceVolume "0"
SET OutboundChatVolume "2.5"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET cameraView "3"
SET guildMemberNotify "1"
SET Sound_VoiceChatInputDriverName "dsnoop:0"
SET Sound_VoiceChatOutputDriverName "dmix:0"
SET TargetNearestDistance "52.000000"
SET Sound_EnableMusic "0"
SET Sound_EnableErrorSpeech "0"
SET Sound_EnableEmoteSounds "0"
SET PushToTalkButton "NUMPADMINUS"
SET readTerminationWithoutNotice "-1"
SET autojoinPartyVoice "0"
SET lastCharacterIndex "6"
SET Sound_EnableAllSound "0"
SET locale "enUS"

Edit:adding specs

1 gig ram
intel dual core
and an intel chipset 945 gm I belive for the graphics card.

---

### Post by hikaricore on 2007-10-17
[B]Stop making duplicate threads.
Stop making so many wow threads: [http://ubuntuforums.org/showthread.php?t=577303](http://ubuntuforums.org/showthread.php?t=577303)

I can keep merging them if need be.  But likely I'll just close them if it happens again.[/B]

Best of luck, but seriously, 3 threads is not going to make it any eaiser to get help.

---

