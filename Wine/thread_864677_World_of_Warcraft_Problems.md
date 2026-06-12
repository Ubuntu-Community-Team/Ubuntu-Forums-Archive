---
title: "World of Warcraft Problems"
date: 2008-07-19
forum: Wine
---

### Post by FLCL on 2008-07-19
Alright, so i've been having to switch back and forth on my drives to play and it's a very big hassel so i thought i would take a shot at running WoW on ubuntu. It installed fine from the discs, but when i try to run the game, problems. The first window with news and whatnot before you launch the game runs fine,then ill click play, and get this.

[[IMG]http://img369.imageshack.us/img369/4538/screenshotyg8.th.png[/IMG]](http://img369.imageshack.us/my.php?image=screenshotyg8.png)

The background is not loading, and if i click send error, it freezes up and i hear the story going in the background but no visual. Please help. D:

---

### Post by Bios Element on 2008-07-20
I had a similar problem to this some time back. I never did figure out the error but My best guess would be something to do with missing .dll files.

---

### Post by merlyn on 2008-07-20
Could you provide some information about your setup please.

For example your hardware, particularly your video card & which drivers you use.

Also a copy of the following files may prove useful,

1. ~/.wine/drive_c/Program Files/World of Warcraft/WTF/Config.wtf 
2. /etc/X11/xorg.conf

Also are you running Compiz?

The marbling on one of the window frames in your screenshot reminds me of a problem I had some time ago when I had the "Reflection" effect enabled under Compiz.

The error message displayed is in "Windows speak" and indicates a memory access error of some kind. 

I wouldn't be overly concerend about that at this stage, unless you are also getting a number of "Seg faults" while running Linux.

Also you may want to browse through [this thread]("http://ubuntuforums.org/showthread.php?t=579378"), (which is quite lengthy), as it has uselful information throughout on troubleshooting WoW under wine.

Cheers.

---

### Post by flytripper on 2008-07-20
sounds like it doesnt like direct x. make a config.wtf file in your wtf folder inside the Wow folder and put ```
SET gxApi "OpenGl"
```.After that give it a whizz.

---

### Post by FLCL on 2008-07-21
Yeah, it was the directx problem, tweaked the config.wtf file and it works fine, EXCEPT, i have one major problem, my mouse.. it's very sluggish and not streamlined like it would be on any other window. I tried tweaking the config file with:
SET ffxDeath "0"
SET ffxGlow "0"

but that seemed to make it worse, it wasnt so much for the mouse, but i thought i would give it a shot. Does anyone know how to fix my mouse issue? I really want to get this working fine so i dont have to keep swapping hard drives :/

---

### Post by fuzzychicken364 on 2008-07-21
> **flytripper said:**
> sounds like it doesnt like direct x. make a config.wtf file in your wtf folder inside the Wow folder and put ```
SET gxApi "OpenGl"
```.After that give it a whizz.

where do i find the WTF file, i just switched from vista so im not too sure about those kind of files.

---

### Post by Mahinva on 2008-07-21
To find the config.wtf file, you will want to first go into your World of Warcraft folder. From there, you will go into your WTF folder. You should find a Config.wtf file. Let me point out that in a fresh install of the game, the Config.wtf file is created sometime after logging in for the first time. This means, if you get hung up the moment you start the game for the first time, you may not have a Config.wtf file.

FLCL: The reason why your mouse (and even mine) is so sluggish is because when we run OpenGL, we do not have the ability to turn on the "Hardware Cursor" option. This means the game has to draw a cursor. If you get to stand in a corner of a room (or a spot where your fps is rather high) you may notice that your mouse is not sluggish. If you run the game in d3d (Direct3D) mode, you will have the ability to select Hardware Cursor, but many people either have lower fps, or various graphical glitches. For example, a lot of my textures are broken if I am outside a building when running in d3d mode. Hence, I run it in OpenGL.

I have heard that the Mac version of the game has Hardware Cursor in OpenGL mode, but for whatever reason, Blizzard doesn't/can't program/make it work for PC.

---

### Post by fuzzychicken364 on 2008-07-21
ok thanks alot

---

### Post by FLCL on 2008-07-22
Ohh, that makes sense, thanks for the info.

---

### Post by Mahinva on 2008-07-22
You're both very welcome. :D

---

### Post by Zhiro on 2008-08-02
Alright.  I have a new problem to see if anyone can solve it:

I'm running WoW with the latest patch and latest Wine (0.60 I believe?).  Anyway, after I went through the Ubuntu forums on how to download/install Wine and get WoW working (like adding things into WTF file) I got WoW to work, BUT, it only works in places other than Shatt.  I would suspect it affects all BC content, but I haven't been able to check that out for sure yet.  I have logged in and can play well in Ironforge (the only other place I've checked so far) on multiple characters.  I can interact with the interface and everything.  

When I'm in Shattrath, everything seems fine, I can type into chat and whatnot, but as soon as I move or turn the camera or anything, WoW freezes up and even freezes my computer.  I need to use the power button because things like Ctrl + F4 or Ctrl + F7 don't even work.  Here's my WTF:

SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x800"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET lodDist "80.000000"
SET SmallCull "0.070000"
SET DistCull "450.000000"
SET farclip "177"
SET particleDensity "1.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET realmList "us.logon.worldofwarcraft.com"
SET soundMaxHardwareChannels "12"
SET locale "enUS"
SET realmName "Aggramar"
SET expansionMovie "0"
SET mouseSpeed "1"
SET Gamma "0.500000"
SET MusicVolume "1"
SET SoundVolume "1"
SET MasterVolume "1"
SET ffx "0"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "2"
SET gameTip "20"
SET AmbienceVolume "0.69999998807907"
SET uiScale "1"
SET spellEffectLevel "0"
SET weatherDensity "0"
SET UnitNamePlayerGuild "0"
SET UnitNamePlayerPVPTitle "0"
SET gxWindow "1"
SET gxMaximize "1"
SET DesktopGamma "1"
SET patchlist "us.version.worldofwarcraft.com"
SET lod "1"
SET minimapZoom "0"
SET useWeatherShaders "0"
SET minimapInsideZoom "0"
SET fullAlpha "1"
SET unitDrawDist "300.000000"
SET baseMip "1"
SET showToolsUI "1"
SET profanityFilter "0"
SET gxTripleBuffer "1"
SET trilinear "1"
SET cameraView "2"
SET CombatLogRangeCreature "50"
SET MasterSoundEffects "0"
SET EnableMusic "0"
SET EmoteSounds "0"
SET SoundListenerAtCharacter "0"
SET coresDetected "2"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET Sound_OutputDriverName "System Default"
SET ChatMusicVolume "0"
SET ChatSoundVolume "0"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "1"
SET Sound_AmbienceVolume "1"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET readTerminationWithoutNotice "-1"
SET EnableMicrophone "0"
SET Sound_ZoneMusicNoDelay "1"
SET Sound_EnableSoundWhenGameIsInBG "1"
SET autoDismountFlying "1"
SET autoSelfCast "1"
SET guildMemberNotify "1"
SET ShowTargetCastbar "1"
SET videoOptionsVersion "1"
SET textureFilteringMode "0"
SET pixelShaders "1"
SET groundEffectDist "70"
SET playerStatusText "1"
SET targetStatusText "1"
SET assistAttack "1"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET showTargetOfTarget "1"
SET questFadingDisable "1"
SET removeChatDelay "1"
SET enableCombatText "1"
SET fctCombatState "1"
SET fctReactives "1"
SET fctHonorGains "1"
SET fctAuras "1"
SET hidePartyInRaid "1"
SET showPartyDebuffs "0"
SET UnitNameEnemyPlayerName "0"
SET UnitNameEnemyPetName "0"
SET UnitNameEnemyCreationName "0"
SET UnitNameFriendlyPetName "0"
SET UnitNameFriendlyCreationName "0"
SET UnitNameCompanionName "0"
SET screenEdgeFlash "0"
SET accountName "zhiro"
SET CombatLogRangeParty "50"
SET CombatLogRangePartyPet "50"
SET CombatLogRangeFriendlyPlayers "50"
SET CombatLogRangeFriendlyPlayersPets "50"
SET CombatLogRangeHostilePlayers "50"
SET CombatLogRangeHostilePlayersPets "50"
SET checkAddonVersion "0"
SET Sound_NumChannels "64"
SET shadowLOD "0"
SET Sound_EnableAllSound "0"

I would get my /etc/whatever file, but I don't know how to.  Anyone have any suggestions?  I'm running on an nVidia card, but I don't know the specifications because I can't find that either (I'm relatively new to Ubuntu =P).  ANY help would be much appreciated, thank you!

-Zhiro

P.S. I don't run it under OpenGL because when I do the text goes away and buttons don't show up plus I have that white minimap thing going on.

---

### Post by aoanla on 2008-08-02
Well, for a start, the latest Wine release is 1.1.2, not 0.9.60. At the very least, it would be worth upgrading to the stable release 1.0.0, just in case that fixes something.

However, the fact that you think 0.9.60 is the latest release strongly implies to me that you're using the default repositories for all your installs.
This means that your nVidia driver is probably a bit old, and might stand upgrading. 

(Some general background for you, since you said you're new:
  most linux distributions, including Ubuntu, host the additional software you can install in internet-accessible repositories, which are what Synaptic connects to to install stuff. For reasons of stability and security, the versions of the software packages in the official repositories are generally fixed (apart from security fixes) - so if a new version of the software comes out, it won't necessarily be added to the repository for the current version of Ubuntu. (The next release of Ubuntu,of course, would include newer versions of the packages in its repositories).
Unfortunately, this means that the official repository copies of software with fast release cycles - like Wine - often lag behind the current state of the art.
The source for newer Wine releases is wine.budgetdedicated.com - the site includes instructions on adding their repository to Ubuntu's list of places to get software. 
The source for newer releases of nVidia's drivers is [http://www.nvidia.com/page/drivers.html](http://www.nvidia.com/page/drivers.html)  
)

---

### Post by flytripper on 2008-08-02
also if you posted your system specs that would be telling of the possible reasons too. As for the mouse, i suspect you have and older type system? maybe a mid to low graphics card? the mouse is rendered by software so any lag (chug)on screen  is also translated to the mouse cursor. You are not alone with the whole Shattrath thing.I get 20 fps max then i portal to IF and boom!! 60 fps!! Its **_very_** poorly designed.They recently made a change to the way its rendered and loaded..(not sure which patch)so it loads in bits. ever tried to get inside the portal area and stopped in mid flight for a few seconds?. You could also try reducing the distance at which the camera can see, this greatly improves the frame rate as it reduces the size of the box your gpu has to render in 3d. You can tell which zones were designed by the better modelers... by the fps.

---

### Post by Zhiro on 2008-08-02
So I got the hardinfo thing, which specs would actually be helpful?  I'll post basics if that helps:

Processor: 2x Intel(R) Core(TM)2 Duo CPU T5550 @ 1.83GHz
Memory: 2066MB (389MB used)
Operating System: Ubuntu 8.04
OpenGL Renderer: Mesa DRI Intel(R) 965GM 4.1.3002 x86/MMX/SSE2
X11 Vendor: The X.Org Foundation
Audio Adapter: HDA-Intel - HDA Intel

It's a brand new XPS M1330 laptop from Dell.  I ordered it with Ubuntu preloaded so I would hope that it has good stuff on it.

Update on WoW though.  I discovered that when I run it with OpenGL it CAN work in Shattrath, but there's no text and the buttons are half-imaged or imageless.  Without OpenGL the screen is perfect, but I can't work in Shatt (or on a FP.  I tried to fly out of IF to Menethil to test it and it locked up again).  It looks like it might be a videocard thing but again I'm a noob, so anything would be helpful =).

P.S. I downloaded Wine 1.1.2, thank you =)

---

### Post by aoanla on 2008-08-02
Built in Intel graphics solutions are generally a bit useless, in Windows as well as in Linux. And, as mentioned, Shattrath *is* well known for being a bit horribly designed, especially for lower end graphics cards.

Still, I think there are some work-arounds for the OpenGL thing - I know I've seen the minimap and button issue mentioned by people before...

---

### Post by zeifertstc on 2008-12-02
Don't know if anybody is still watching this post, but I've managed to solve most of these problems with a guide available in the Ubuntu Community Section of the site. [https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft") I've done everything in this guide after the alternative installation method: Alternative 1 (Copy from Windows)

I've modified the config.wtf file with the top 4 options (disregarding the ones about sound as it didn't affect me), fixing the login screen and the character select screen. After logging in, it looked like things were going to run fine. However I ran into a similar situation with the text disappearing and the white mini-map. This was mostly fixed by entering a simple registry key, also in the guide under the heading "Registry configuration". 

This only leaves us with one problem that I have yet to fix and am still looking for possible solutions to. The mini-map being white while inside a building/instance/interior path to instance. So far, I haven't gotten any word of any possible work-a-rounds. I'll try to keep this post updated if I get any answers from anywhere else.

---

