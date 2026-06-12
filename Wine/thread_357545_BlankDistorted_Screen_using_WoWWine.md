---
title: "Blank/Distorted Screen using WoW/Wine"
date: 2007-02-09
forum: Wine
---

### Post by BrokenMemories on 2007-02-09
Okay I've installed Wine  using the ubuntu HowTo as well as checked out several HowTo in this forum. Wine is working fine as far as I can tell. My problem is when I try to run wow.

I'm running Ubunto 6.10 + Beryl. However in an effort to run wow the windows manager is currently Metacity.

I can run the launcher.exe no problems, but when WoW launches I get a window (currently running in window mode), hear the music no problems but can't see the start screen/login etc. Its either black or very distorted.

Hardware is P4 532 3ghz, 1gb ram, ATI Radeon X800 256mb.
config file as follows.
```
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraView "0"
SET cameraDistanceMaxFactor "2"
SET profanityFilter "0"
SET ChatBubblesParty "1"
SET guildMemberNotify "1"
SET minimapZoom "0"
SET minimapInsideZoom "0"
SET SoundZoneMusicNoDelay "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET autoSelfCast "1"
SET assistAttack "1"
SET soundMaxHardwareChannels "12"
SET weatherDensity "0"
SET DesktopGamma "1"
SET gxTripleBuffer "1"
SET accountName "BrokenMemories"
SET gxWindow "1"
SET lastCharacterIndex "3"
SET expansionMovie "0"
SET checkAddonVersion "0"
SET CombatLogRangeCreature "50"
SET gxApi "opengl"
SET ffxDeath "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "100"

```

Device settings for Gfx card are:
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X800 (R430 UO)"
	Driver		"radeon"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
	BusID		"PCI:1:0:0"
EndSection
```

If anyone has any idea on whats going wrong it would be great to get this working. I'm still quite new to the Linux scene so any help would be appreciated.

Cheers
~BM~

---

### Post by Sammi on 2007-02-10
If you have tried running WoW in both OpenGL and d3d mode, then this is probably related to your ATI video card. Sadly ATI only have crappy drivers available for Linux.

But you should look through this excellent resource for installing and configuring ATI drivers. It might help: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

And your not running Xgl are you?

---

### Post by BrokenMemories on 2007-02-10
Not sure what Xgl is sorry. I do know that beryl can run under Xgl or AIGLX (or something). I had the AIGLX one installed however I've uninstalled Beryl.

I've now installed the fglrx drivers. I can load WoW and log in. However about 3s after I enter the game world the entire computer  freezes and only my mouse works. I disabled addons but this didnt seem to do anything.

Not really sure whats wrong.

xorg.conf still has the following, Should it be <Driver		"fglrx">? Just wondering.

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X800 (R430 UO)"
	Driver		"radeon"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
	BusID		"PCI:1:0:0"
EndSection
```

Cheers
~BM~

---

### Post by BrokenMemories on 2007-02-10
Okay I've managed to get it working thanks to the awesome help posted by jameslov found here:
[http://www.ubuntuforums.org/showthread.php?t=312482&page=13](http://www.ubuntuforums.org/showthread.php?t=312482&page=13)

Third or 4th post down on teh page. Looks like it was a ATI driver problem and need to set some options. 

Cheers,
~BM~

---

### Post by firestrife2382 on 2007-12-14
that link doesn't work :(

---

