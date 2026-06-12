---
title: "World of Warcraft Problems"
date: 2007-12-06
forum: Wine
---

### Post by Aruza on 2007-12-06
I Have read multiple how tos on how to install wow in wine and i have gotten the install down and the only way that i can get it to run without having it log me out/restart is to add the -opengl modifier. when i do this wow will run but its dark and there appears to be no textures.

if anyone has any suggestions please help! i am so sick of windows

Thanks,
Aruza

__________________________________________________
HP dv6000 laptop
1.6Ghz Core 2 Duo
2Gb 667Mhz RAM
160Gb Hard Drive

---

### Post by Faud on 2007-12-07
Hi and welcome to the forums. Please post your graphics card and your config.wtf file.
Thanks.

---

### Post by doodger on 2007-12-07
i never used -opengl, i just wined wow naturally.

When i come back home i'll post my wtf file, hopefully it can help! :)

---

### Post by Aruza on 2007-12-07
The laptop has a Intel 945 chipset and my config.wtf file is as follows:

SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x1024"
SET gxMultisampleQuality "0.000000"
SET fullAlpha "1"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET shadowLevel "0"
SET trilinear "1"
SET frillDensity "32"
SET farclip "537"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
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
SET gxVSync "0"
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
SET gxWindow "1"
SET autoDismountFlying "1"
SET statusBarText "1"
SET ShowVKeyCastbar "1"
SET UnitNameNPC "1"
SET autoSelfCast "1"
SET UnitNameOwn "1"
SET ChatBubbles "0"
SET guildMemberNotify "1"
SET scriptErrors "1"
SET M2UseShaders "0"
SET gxMaximize "1"
SET coresDetected "2"
SET Sound_VoiceChatInputDriverName "Realtek HD Audio Input"
SET Sound_VoiceChatOutputDriverName "Realtek HD Audio output"
SET Sound_OutputDriverName "Realtek HD Audio output"
SET ChatMusicVolume "0"
SET ChatSoundVolume "1"
SET ChatAmbienceVolume "0"
SET Sound_EnableMusic "0"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "0.60000002384186"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET OutboundChatVolume "2.5"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET Sound_EnableAmbience "0"
SET PushToTalkButton "LCTRL"
SET readTerminationWithoutNotice "-1"
SET CombatLogRangeParty "200"
SET CombatLogRangePartyPet "200"
SET CombatLogRangeFriendlyPlayers "200"
SET CombatLogRangeFriendlyPlayersPets "200"
SET CombatLogRangeHostilePlayers "200"
SET CombatLogRangeHostilePlayersPets "200"
SET CombatHealing "0"
SET videoOptionsVersion "1"
SET spellEffectLevel "6"
SET checkAddonVersion "0"
SET cameraView "4"
SET groundEffectDist "70"
SET CombatDamage "0"
SET xpBarText "1"
SET autojoinPartyVoice "0"
SET Sound_VoiceChatOutputDriverIndex "1"
SET Sound_OutputDriverIndex "1"
SET SoundOutputSystem “1&#8243; 
SET SoundBufferSize “150&#8243; 
SET gxApi “OpenGL”





Thanks,
Aruza

---

### Post by Faud on 2007-12-07
There are some slight varations in our config.wtf files. Are you running on ALSA drivers? and what happens when you just start with wow.exe, not adding -opengl ?

---

### Post by Aruza on 2007-12-07
Im new to linux so im not sure what you mean by ALSA drivers but when i start up wow without using the -opengl the screen flashes, then the colors go weird and i get logged out, the computer doesnt restart because i dont see the HP bios splash screen, i just get logged out.

Please please help!
and thanks to all those who have replied!
Aruza

---

### Post by Faud on 2007-12-07
ALSA are drivers in your audio tab of winecfg. You remember how when you were installing the game and it came to the point where you had to do the registery tweak? And then you go into winecfg and set it up for your desktop size and emulate desktop and all of that? ALSA is under the audio tab.

---

### Post by Aruza on 2007-12-07
i do remember that now. The howto that i read said to use the OSO? drivers. thats what i am using.

---

### Post by Aruza on 2007-12-10
I solved the texture problem, now everything looks good. I added the following lines to my WTF file.

SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"

Thanks to everyone that helped out!
Aruza

---

### Post by eugne on 2007-12-31
Hello,
I try to play WoW on my ubuntu 7.10 with wine 0.9.54
If I launch WoW with the -d3d option, everything is OK except my fps rate : 4 fps max in shattrath, no more than 8 fps everywhere outside
If I launch WoW with the -opengl option, my fps rate is 30 average in shattrath (120 max outside) but I have no 3d texture : no pnj, no player, no ennemy, no element like the mailbox appear on my screen. Here is a [screenshot of what I have when trying to play with -opengl]("http://www.hiboox.com/lang-fr/image.php?img=vwe6bi2q.png")

---

### Post by Faud on 2007-12-31
Well your first problem is that your a rogue........:lolflag: Im just kidding, Im just kidding

Post your config.wtf file and we'll take a look at it

---

### Post by TolTime on 2007-12-31
if i post mine could i get a little help?:-?

---

### Post by Ferrat on 2008-01-01
> **eugne said:**
> Hello,
I try to play WoW on my ubuntu 7.10 with wine 0.9.54
If I launch WoW with the -d3d option, everything is OK except my fps rate : 4 fps max in shattrath, no more than 8 fps everywhere outside
If I launch WoW with the -opengl option, my fps rate is 30 average in shattrath (120 max outside) but I have no 3d texture : no pnj, no player, no ennemy, no element like the mailbox appear on my screen. Here is a [screenshot of what I have when trying to play with -opengl]("http://www.hiboox.com/lang-fr/image.php?img=vwe6bi2q.png")

with 0.9.54? 0.9.52 just came out? ;) 

Have you tried an earlier version of wine? =) 

[http://ubuntuforums.org/showthread.php?p=4050910#post4050910](http://ubuntuforums.org/showthread.php?p=4050910#post4050910)

this might help :)

---

### Post by eugne on 2008-01-02
> **Ferrat said:**
> with 0.9.54? 0.9.52 just came out? ;) 

Have you tried an earlier version of wine? =) 

[http://ubuntuforums.org/showthread.php?p=4050910#post4050910](http://ubuntuforums.org/showthread.php?p=4050910#post4050910)

this might help :)

Hello,

Yes, I made a mistake, it's wine 0.9.52 :oops:
In the meanwhile, someone told me the solution of my problem was exposed [here]("http://www.wowwiki.com/Linux/Wine/Troubleshooting#ATI_no_Object_Textures.2FModels") 
Thanks to everyone :)

---

