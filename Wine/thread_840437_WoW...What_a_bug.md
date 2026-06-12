---
title: "WoW...What a bug"
date: 2008-06-25
forum: Wine
---

### Post by Meatshield on 2008-06-25
Ok, well let me start off by saying that I've had WoW installed for the last two weeks with no problems. However I recently bought Burning Crusades and with that, my video started pausing every few seconds. I started to try to fix it, and now it crashes my system. I'll try to post a pic later, but it's like it splits the screen in mirror images and distorts it. It's a full-screen effect with no way to get out of it (including exiting WoW), so I'm forced to Ctrl+Alt+Backspace to get back to my desktop.

Here are my specs (if you haven't guessed by now, I'm using ATI :( )
Ati Mobility Radeon x1400 with ATI's 8.6 Proprietary Drivers
Kernal 2.6.24-19

Xorg.conf:
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option "Capabilities" "0x00000800"
	Option "UseFastTLS" "off"
	Option "KernelModuleParm" "locked-userpages=0"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "on"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

config.wtf:
```
SET locale "enUS"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET gxApi "opengl"
SET videoOptionsVersion "1"
SET pixelShaders "1"
SET movie "0"
SET showToolsUI "0"
SET Sound_OutputDriverName "System Default"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET SmallCull "0.070000"
SET DistCull "500.000000"
SET farclip "177"
SET particleDensity "1.000000"
SET spellEffectLevel "0"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
SET accountName "REMOVED"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET gxCursor "0"
SET DesktopGamma "1"
SET Gamma "1.000000"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET groundEffectDist "70"
SET realmName "REMOVED"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET gameTip "27"
SET CombatHealing "0"
SET scriptErrors "1"
SET minimapZoom "0"
SET minimapInsideZoom "0"
SET uiScale "1"
SET autoSelfCast "1"
SET questFadingDisable "1"
SET CombatLogRangeParty "50"
SET CombatLogRangePartyPet "50"
SET CombatLogRangeFriendlyPlayers "50"
SET CombatLogRangeFriendlyPlayersPets "50"
SET CombatLogRangeHostilePlayers "50"
SET CombatLogRangeHostilePlayersPets "50"
SET CombatLogRangeCreature "50"
SET shadowLOD "0"
SET profanityFilter "0"
SET xpBarText "1"
SET statusTextPercentage "1"
SET displayFreeBagSlots "1"
SET autoLootCorpse "1"
SET gxDepthBits "24"
SET expansionMovie "0"
SET gxVSync "0"
SET textureFilteringMode "0"
SET weatherDensity "0"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"


SET Sound_AmbienceVolume "0.60000002384186"
SET lod "1"
SET baseMip "1"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
```

If it helps isolate it, I can get the Launcher.exe and Photoshop CS2 running just fine, and as soon as I click continue on the Launcher it screws the screen up for me, regardless of whether it's in windowed mode or not.

*EDIT* Added a picture. Screencap won't even work in this mode. Had to bust out the camera.

---

### Post by tehpyrate on 2008-06-25
Did you turn off Visiual effects? 

It helped solve alot of my problems. When I tried to get WoW WINE Running

---

### Post by Meatshield on 2008-06-25
Yeah Compiz and such are all off, and I've done all the tweaks (registry edit, DLL file download, etc etc). The game worked for two weeks flawlessly, and now suddenly has this problem. Further tests also show this happens in all kernals, but stuff like glxgears runs flawlessly, so I'm still stumped.

---

### Post by soulcmdc on 2008-06-25
This is the exact same bug that I'm having, I posted it a couple of days ago: [http://ubuntuforums.org/showthread.php?t=838952](http://ubuntuforums.org/showthread.php?t=838952)
No responses yet.

---

### Post by reaby on 2008-06-26
i'm having same kind problem..
[http://ubuntuforums.org/showthread.php?t=840664](http://ubuntuforums.org/showthread.php?t=840664)

i suspect this has something to do with new ati drivers.

---

### Post by soulcmdc on 2008-06-26
> **reaby said:**
> i'm having same kind problem..
[http://ubuntuforums.org/showthread.php?t=840664](http://ubuntuforums.org/showthread.php?t=840664)

i suspect this has something to do with new ati drivers.

Reaby - you were exactly right.  This is a bug in the new drivers.  If you regress to 8.5, everything worked lovely.  For some reason or another the link on ATI's page to the 8.5 drivers is not functioning, [**Here** is a direct link]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-5-x86.x86_64.run")
Just running through the graphical installer fixed the problem.  Hope this helps everyone else with this issue.

---

### Post by reaby on 2008-06-27
thanks for the link to older drivers. all works fine now again.

---

