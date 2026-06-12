---
title: "Wine// World of Warcraft HELP ME!!!"
date: 2008-05-29
forum: Wine
---

### Post by deathface on 2008-05-29
ok so, i followed all of the directions, i did the regedit, i did the wineconfig, i set the gxapi and even tried the death and glow so here is the problem. I also have my restricted drivers in use and they work fine.

everything loads and runs at the right speed but the background is black and there are no graphics. I am able to log in but my character is not there and once again the background is black but all of the windows and fonts are fine.

I have an N Series Fujitsu Lifebook with a X600 Mobility Radeon, here is my error report
```
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21ecac,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3413
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f2c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f528,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f518,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f144,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:imm:ImmGetDefaultIMEWnd (0x20024 - (nil) 0x7f0227e0 ): semi-stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:reg:GetNativeSystemInfo (0x37402b24) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmAssociateContextEx (0x20024, (nil), 16): stub
archive Data\patch.MPQ opened

archive Data\enUS\patch-enUS.MPQ opened

archive Data\enUS\patch-enUS-2.MPQ opened

archive Data\patch-2.MPQ opened

archive Data\common.MPQ opened

archive Data\enUS\locale-enUS.MPQ opened

archive Data\enUS\speech-enUS.MPQ opened

```

PLEASE HELP so I can get Windows the F off my computer

Thanks in advance


PS I just tried to get rid of the config.wtf and the background worked but the textbars didn't hahaha this is so strange. if you need anymore information from me let me know, i was going to post my xorg.conf but i didn't know if it was necessary

---

### Post by Faud on 2008-05-29
are you using an ATI graphics card ?
If so you need to add a line to your config.wtf file and it will fix that. Cant remember what it is at the moment but its all over these forums, just give it a look.

---

### Post by Trance56k on 2008-05-30
post your wtf config file from WoW directory.

---

### Post by DoktorSeven on 2008-05-30
> preloader: Warning: failed to reserve range 00000000-60000000

Please see [Preloader Page Zero Problem](http://wiki.winehq.org/PreloaderPageZeroProblem) (and [Launchpad bug #114025](https://bugs.launchpad.net/wine/+bug/114025)) for more information and a fix.

---

### Post by thisismalhotra on 2008-05-30
Here this will help

[http://ubuntuforums.org/showthread.php?t=770939](http://ubuntuforums.org/showthread.php?t=770939)

---

### Post by deathface on 2008-05-30
thank you so much for your replies, i sometimes have a hard time wording things the right way to search through forums for answers. I have gotten very far, the video works, the sound works, everything looks good, BUT (theres always a catch it seems) My Desktop flashes every secound or so through Wow. I tried logging in (which was successful // graphics and all) even as it continued to flicker. I have found a forum here and there that addresses the issue but never a solution. After I finish this I am going to write a long essay on how to do WOW in WINE on ubuntu with ATI mobility cards.

here was my steps

loaded and then upgraded wine (9.61)


copied the WOW folder from a mounted drive

did the regedit

got and loaded my envy drivers

installed the linux addon (and allowed unupdated addons ((which it claimed the addon the be)) to run)

loaded the four WIN32 files (msvcp60,riched20,mfc42,riched32)

my rendering is YES



as far as I can read this works for the entire world but me :mad:
If you have encountered this problem then help a brother out. I searched for the answer and yes there are suggestive posts about it but no concrete solution.




I found this config.wtf and after just adding lines wasn't working I loaded this one which does exactly the same thing (flickering desktop)

```
SET ffxGlow "0"
SET locale "enUS"
SET hwDetect "0"
SET UIFaster "2"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1440x900"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET gxApi "opengl"
SET SmallCull "0.010000"
SET DistCull "500.000000"
SET farclip "777"
SET movie "0"
SET expansionMovie "0"
SET Gamma "1.000000"
SET readTOS "1"
SET readEULA "1"
SET realmList "us.logon.worldofwarcraft.com"
SET gameTip "72"
SET uiScale "0.83999997377396"
SET mouseSpeed "1"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "2"
SET autoSelfCast "1"
SET ShowTargetCastbar "1"
SET guildMemberNotify "1"
SET weatherDensity "3"
SET readScanning "-1"
SET readContest "-1"
SET cameraView "5"
SET ffxNetherWorld "0"
SET profanityFilter "0"
SET EnableSoundWhenGameIsInBG "1"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "0.60000002384186"
SET AmbienceVolume "1"
SET SoundNumChannels "128"
SET SoundOutPutSystem "2"
SET SoundBufferSize "157"
SET gxCursor "0"
SET useWeatherShaders "0"
SET SoundUseHardware "1"
SET timingTestError "0"
SET patchlist "us.version.worldofwarcraft.com"
SET gxVSync "0"
SET minimapInsideZoom "0"
SET showToolsUI "1"
SET CombatLogRangeCreature "2000"
SET coresDetected "1"
SET Sound_VoiceChatInputDriverName "dsnoop:0"
SET Sound_VoiceChatOutputDriverName "dmix:0"
SET Sound_OutputDriverName "dmix:0"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.30000001192093"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "0.5"
SET Sound_MusicVolume "0.20000000298023"
SET Sound_AmbienceVolume "0.30000001192093"
SET OutboundChatVolume "2.5"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET EnableVoiceChat "1"
SET PushToTalkButton "LSHIFT"
SET Sound_EnableSoundWhenGameIsInBG "1"
SET readTerminationWithoutNotice "-1"
SET CombatLogRangeParty "2000"
SET CombatLogRangePartyPet "2000"
SET CombatLogRangeFriendlyPlayers "2000"
SET CombatLogRangeFriendlyPlayersPets "2000"
SET CombatLogRangeHostilePlayers "2000"
SET CombatLogRangeHostilePlayersPets "2000"
SET DesktopGamma "1"
SET M2UsePixelShaders "1"
SET M2UseShaders "0"
SET videoOptionsVersion "1"
SET pixelShaders "1"
SET textureFilteringMode "5"
SET movieSubtitle "1"
SET groundEffectDist "140"
SET minimapZoom "0"
SET xpBarText "1"
SET playerStatusText "1"
SET partyStatusText "1"
SET petStatusText "1"
SET targetStatusText "1"
SET deselectOnClick "0"
SET assistAttack "1"
SET ShowVKeyCastbar "1"
SET UnitNameOwn "1"
SET UnitNameNPC "1"
SET lod "1"
SET shadowLevel "0"
SET groundEffectDensity "64"
SET specular "1"
SET ffxDeath "0"
SET gxRefresh "60"
SET Sound_OutputDriverIndex "1"
```

Here is my xorg.conf which I added a suggested line to (didn't change performance at all)

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option		"UseFastTLS"	"2"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```


if your on Azemythst (dont know how to spell it cause MY SCREENS FLICKERING) ill give you 5g for the solution

thank you for your fast replies

---

### Post by deathface on 2008-05-31
if anyone knows of a post which revolves around this problem please share, i am really lost

---

