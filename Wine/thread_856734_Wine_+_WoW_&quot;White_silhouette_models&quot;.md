---
title: "Wine + WoW &quot;White silhouette models&quot;"
date: 2008-07-11
forum: Wine
---

### Post by SerpentKnights on 2008-07-11
Can somebody help me figure out how to fix the "white" character model and some object models? Basically the it's a white silhouette of the models. My graphic card is Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller. Direct rendering works. I also have OpenGL enabled in the Config.wtf file.

If need more info, just let me know what to do and I will do my best.

Thanks!

---

### Post by Tuxoid on 2008-08-14
yes, I have an intel 945gm, and in select areas of the game, the white models may be fixed by enabling character shadows (that is, if it's disabled).

You may still notice white models occasionally. You may also notice your minimap has turned white.

---

### Post by twinkletoes2007 on 2009-04-16
I've been having the "white problem" since I upgraded to the new 3.1 patch.

I'm using a Vaio PCG-384L (not sure the graphics card exactly)
Wine is using Windows XP
Hardware Acceleration : Emulation


this is what is in my config. wtf
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET locale "enUS"
SET movie "0"
SET showToolsUI "1"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET textureFilteringMode "0"
SET mouseSpeed "0.5"
SET Gamma "1.000000"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET Sound_OutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "400.000000"
SET particleDensity "0.60000002384186"
SET spellEffectLevel "0"
SET realmName "Azuremyst"
SET gameTip "18"
SET VoiceActivationSensitivity "0.39999997615814"
SET ffxDeath "0"
SET ffxSpecial "0"
SET M2UseShaders "0"
SET ffxGlow "0"
SET UIFaster "2"
SET lastCharacterIndex "3"
SET accounttype "LK"
SET baseMip "1"
SET environmentDetail "0.75"
SET weatherDensity "0"

Comp Fiz is off. I do have problems with Wine crashing, but I think that's my drivers. I didn't have this problem before the patch though. 
Any ideas? I can't find anything! Thank you!

This is what it looks like 
[http://i2.photobucket.com/albums/y25/Twinkletoes2007/Screenshot.png](http://i2.photobucket.com/albums/y25/Twinkletoes2007/Screenshot.png)

(take note how the NPC in the background and myself the gnome look fine) 
The white only affects other people I play with.

---

### Post by NightMKoder on 2009-04-16
Intel drivers have been known to suck (pre-GEM), but intel decided to do a revamp of the graphics stack in the kernel. The new drivers (in jaunty, UXA acceleration) are somewhat flaky for some, but personally I'm using it and...it's gotten a lot better.

Consider upgrading to jaunty and if you have a horrible performance decrease, try [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/349992](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/349992) (fix is halfway down).

Otherwise old intel drivers don't work too well, so you shouldn't expect much.

---

### Post by Tuxoid on 2009-06-07
I can confirm I have this exact problem, where NPCs and my character will display fine, but other players are white silhouettes. I can generally see their helms correctly, and I can see their mounts properly, but everything else is just pure white.

I have tried the fix listed at the launchpad link, and I'm using kernel 2.6.30-rc3, but their are no improvements for WoW at least.

Just to clarify, I am aware that with the fix, YMMV.

Has anyone figured out to how correct this, or is this still a mystery?

---

