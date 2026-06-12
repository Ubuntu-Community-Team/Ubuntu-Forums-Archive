---
title: "WoW having weird lag every 2-5 sec"
date: 2008-01-06
forum: Wine
---

### Post by frostfire.dk on 2008-01-06
Hello fellow Ubuntu users

Im having some weird problems when playing wow
When i start the game it makes some weird lagg or glitches every 2-5 secs, it looks kinda like  a little lag spike every time, but its graphic related.
I have tryied almost every trick in the book
I have changed regedit
I have changed Config.wtf
i have changes Xorg.conf
I have changed craphic settings in the game
I have tryied with fresh install and tryied all the tricks again

Im running on a 
Intel Pentium M 2GHZ
1024 mb ram
ATI Mobility Radeon 9600 think its 256 or 512 mb ram cant remember

My Wine version is 0.9.52

My Config.WTF looks like this:

```
 SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enGB"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1400x1050"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET SmallCull "0.070000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "297"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET expansionMovie "0"
SET realmList "eu.logon.worldofwarcraft.com"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET coresDetected "1"
SET videoOptionsVersion "1"
SET lastCharacterIndex "6"
SET readTerminationWithoutNotice "1"
SET showToolsUI "1"
SET patchlist "eu.version.worldofwarcraft.com"
SET realmName "Ravencrest"
SET gameTip "4"
SET textureFilteringMode "0"
SET Gamma "1.000000"
SET Sound_VoiceChatInputDriverName "dsnoop:0"
SET Sound_VoiceChatOutputDriverName "dmix:0"
SET Sound_OutputDriverName "dmix:0"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET baseMip "1"
SET spellEffectLevel "0"
SET groundEffectDist "70"
SET weatherDensity "0"
SET uiScale "0.63999998569489"
SET UIFaster "2"
SET M2UsePixelShaders "1"
SET M2UseShaders "0"
SET gxCursor "0"
SET checkAddonVersion "0"
SET DesktopGamma "1"
SET useUiScale "1" 
```

And my Xorg.conf looks like this

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"Buttons"	"10"
	Option		"ButtonMapping"	"1 2 3 6 7 4 5"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option		"Capabilities" "0x00000800"
 	Option 		"UseFastTLS" "2"
 	Option 		"KernelModuleParm" "locked-userpages=0"
EndSection

Section "Monitor"
	Identifier	"Standard Skærm"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Monitor		"Standard Skærm"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection

Section "ServerFlags"
	Option	"AIGLX"	"on"
EndSection

Section "DRI"
	Mode 0666
EndSection


```

I hope omeone can help me cause it drives me crazy, and i really dont wanna be forces to use windoze

---

### Post by frostfire.dk on 2008-01-06
Please someone, im going crazy here

---

### Post by hikaricore on 2008-01-06
Please allow 24-48 hours before bumping your posts so that our users have time to offer their input.

Remember this is a volunteer community and patience is a must.

---

### Post by frostfire.dk on 2008-01-07
I finally got it working, by reinstalling the graphic driver, i have no idea what made it work but nm its working :D

And hikaricore im sorry i promise it wont happen again

---

### Post by oedipuss on 2008-01-07
This can happen if there are other applications using the cpu. I've had it too with various games, and it can be difficult to diagnose. Specifically, running deluge, or having system monitor open caused the little glitches periodically in many games, although neither seemed to use that much cpu. 
Try closing most other applications before running wow, and see if it helps.
It goes without saying that compiz/beryl must be off when running games.
 Also, you can try giving a higher priority to your wine proccess , with 'renice' , but you'd better look for some other post on how exactly to do that, and what proccesses to renice (wow.exe or wineserver or both, I can't remember)..

---

