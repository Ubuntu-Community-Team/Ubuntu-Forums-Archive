---
title: "WOW with intel 945GM"
date: 2007-03-05
forum: Wine
---

### Post by Ripfox on 2007-03-05
I have Beryl working, also getting over 1000fps in glxgears, but i have NO idea which tutorial to use to get WOW working...I tried wine but it locks up my system...

ANY help is cool...

Peace

---

### Post by Sammi on 2007-03-06
Use the community WoW/Wine howto: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by hikaricore on 2007-03-06
One thing you may want to consider.  Most intel integrated drivers are lacking in comparison to their windows counterparts.

I've not had luck running WoW on serveral intel video systems I've had a chance to test on.

I'm not saying that you'll have no luck, some people manage to get by quite well, but just be aware that there are some specific issue with the intel drivers that may affect gameplay.

---

### Post by Ripfox on 2007-03-06
Well, now I can play in d3d mode, but man is it slow compared to windows....I think I may have to go back to dual-booting...

---

### Post by Ripfox on 2007-03-06
OK, Sweet...sorry about my moment of weakness...

If anyone has this Intel chipset, this is what I did, and it works fantastic!

Install the latest Wine

Copy all your WOW cds to a folder (overwriting as prompted)

Run winecfg from a terminal.
Change operating mode to Windows XP.
Click the Audio tab.
Make sure that OSS is selected for sound.
Click Apply.
Exit winecfg.

Install WOW with wine.

Go to your wine folder and go into your WOW folder.  Then to the WTF folder.  Edit the config.wtf.  Add these lines:

SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "d3d"
SET ffxGlow "0"

(for some reason, the intel integrated graphics chip does not like OpenGL.  Running the program in d3d mode works much better.)

After you login, select your character, and enter the game, hit Escape and reduce all video options to the minimum you can go.  Turn off weather effects, etc.  

With this configuration, I was actually able to run WOW with decent fps.

Hope this helps someone!

---

### Post by Sammi on 2007-03-07
I love success stories :D

And yes, a detailed explanation of what settings work for some specific hardware is always useful. Great work!

---

### Post by ELD on 2007-03-07
How on earth do u get 1k FPS in glxgears, i have the same chipset and im sure my FPS is much lower, how can i check?

---

### Post by Ripfox on 2007-03-07
glxgears -printfps
  

Do you have Beryl working? I can help if you don't. This laptop has been an adventure, but I have just about whooped it. :)

---

### Post by DiamondX on 2007-03-09
Thanks. I also have that card, in a dell e1505. I just followed your directions, and worked! I did everything except changing it to WinXP. But for some reason, both the system mouse pointer, and the WoW mouse pointer show up. Kind of irritating, but it still works.

Wait, just tried to enter the world, and it froze after loading. In the terminal, it said ```
intel_batchbuffer.c:145: intel_flush_inline_primitive: Assertion `intel->prim.primitive != ~0' failed.
```

---

### Post by hikaricore on 2007-03-09
> **DiamondX said:**
>  But for some reason, both the system mouse pointer, and the WoW mouse pointer show up. Kind of irritating, but it still works.

This is and always has been a known issue while running the game in direct 3d mode.  It is mentioned in every FAQ in existence and hundreds of time across this forum.  :P

---

### Post by Ripfox on 2007-03-09
> **DiamondX said:**
> Thanks. I also have that card, in a dell e1505. I just followed your directions, and worked! I did everything except changing it to WinXP. But for some reason, both the system mouse pointer, and the WoW mouse pointer show up. Kind of irritating, but it still works.

Wait, just tried to enter the world, and it froze after loading. In the terminal, it said ```
intel_batchbuffer.c:145: intel_flush_inline_primitive: Assertion `intel->prim.primitive != ~0' failed.
```

I failed to mention that I also did the tips at the end of this guide: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Only I don't know if some of them affect the d3d mode, but it's worth a shot. 

I have d3d mode working almost perfectly, I can play as fast as Windows, but the mouse thing is still there. Not too annoying though :)

You MUST change it to winxp, I am almost positive.

---

### Post by hikaricore on 2007-03-09
> **ripfox said:**
> I have d3d mode working almost perfectly, I can play as fast as Windows, but the mouse thing is still there. Not too annoying though :)

Personally if I were running in d3d mode, I would find a nice minimalistic set of cursor graphics for X that are semi transparent and set them as my cursor scheme.  This would make the mouse pointer less obvious and with time, you could mostly become oblivious to it.  :)  Just a thought.

---

### Post by Sl1k on 2007-06-23
I'm using the 915GM Chipset and tried what you said and now I can login and see my toon without messed up graphics but... when logging onto server teh game shuts down with this is the teminal:


Mesa 6.5.2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22

I tried using OpenGL methods which I was able to login but my gfx  where all garbbled.


I really really really wana get this working :(

---

### Post by Vicouss on 2007-09-23
A way I've found to remove that annoying mouse problem, of course there is still a downside though.


Also on a 945gm chipset

Running WoW in a window, on a wine virtual desktop...  Bringing mouse up to the top of the window, and returning it removes my secondary pointer.

Downside, if you like desktop integration or can't play in a window, (I haven't had a problem with it, plus 15-35 fps in Stormwind, which isn't great but playable..) Then it really doesn't work.

---

### Post by Ripfox on 2007-10-07
> **Sl1k said:**
> I'm using the 915GM Chipset and tried what you said and now I can login and see my toon without messed up graphics but... when logging onto server teh game shuts down with this is the teminal:


Mesa 6.5.2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22

I tried using OpenGL methods which I was able to login but my gfx  where all garbbled.


I really really really wana get this working :(

Dd you try turning OFF pixel shaders in winecfg? I had that error with Guild Wars and turning them off fixed it.

---

### Post by WeedGrinch on 2008-02-07
> **ripfox said:**
> OK, Sweet...sorry about my moment of weakness...

If anyone has this Intel chipset, this is what I did, and it works fantastic!

Install the latest Wine

Copy all your WOW cds to a folder (overwriting as prompted)

Run winecfg from a terminal.
Change operating mode to Windows XP.
Click the Audio tab.
Make sure that OSS is selected for sound.
Click Apply.
Exit winecfg.

Install WOW with wine.

Go to your wine folder and go into your WOW folder.  Then to the WTF folder.  Edit the config.wtf.  Add these lines:

SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "d3d"
SET ffxGlow "0"

(for some reason, the intel integrated graphics chip does not like OpenGL.  Running the program in d3d mode works much better.)

After you login, select your character, and enter the game, hit Escape and reduce all video options to the minimum you can go.  Turn off weather effects, etc.  

With this configuration, I was actually able to run WOW with decent fps.

Hope this helps someone!

Thanks a lot, it works perfect!

---

### Post by -gabe-noob- on 2008-02-07
I gotta try this, and see if the fps will get over 6.... WOOo and in the gears thing I get like 1.5 k.... weird

Does this work if u used online install? 

and I'm betting its not working on me because I'm trying cross over, so I'm gonna try with wine now, I can just coppy the files to wine directory right?

---

### Post by hikaricore on 2008-02-08
glxgears is a simple opengl test.
It is not meant to be a benchmark.


Anyway 1,500 frames per seconds is quite slow for glxgears.
I get roughly 16,000-20,000 on my high end system.

---

### Post by Resonance378 on 2008-02-08
> **Sl1k said:**
> I'm using the 915GM Chipset and tried what you said and now I can login and see my toon without messed up graphics but... when logging onto server teh game shuts down with this is the teminal:


Mesa 6.5.2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22

I tried using OpenGL methods which I was able to login but my gfx  where all garbbled.

I really really really wana get this working :(

Your answer lies with: 
> (for some reason, the intel integrated graphics chip does not like OpenGL. Running the program in d3d mode works much better.)

AKA: Intel OnBoard/Integrated Graphics Chipset will/does not work with OpenGL, therefore USE d3d (direct 3d) with WoW and Wine, then see how far you get.

---

### Post by hikaricore on 2008-02-08
The problem being that WINE converts Direct3D into OpenGL on the fly.

So using D3D mode often makes things worse.  >.<

---

### Post by Resonance378 on 2008-02-08
> **hikaricore said:**
> The problem being that WINE converts Direct3D into OpenGL on the fly.

So using D3D mode often makes things worse.  >.<

Mehah! *evil villan surprise voice*  You learn something new every day.

Is it that Intel has a bass akwards implementation of OpenGL or is it something to do with the way it supports D3D natively then?  I suppose that sort of information is in the Chip Whitesheets....

---

### Post by Resonance378 on 2008-02-08
> **Resonance378 said:**
> Mehah! *evil villan surprise voice*  You learn something new every day.

Is it that Intel has a bass akwards implementation of OpenGL or is it something to do with the way it supports D3D natively then?  I suppose that sort of information is in the Chip Whitesheets....

Which can be found ^^

[http://www.intel.com/design/mobile/specupdt/309220.htm](http://www.intel.com/design/mobile/specupdt/309220.htm)
[http://www.intel.com/design/mobile/datashts/309219.htm](http://www.intel.com/design/mobile/datashts/309219.htm)

[http://www.intel.com/design/mobile/datashts/309219.htm](http://www.intel.com/design/mobile/datashts/309219.htm)  This document... page 361 shows a nice diagram of the pipeline for graphics processing but really no clues as to HOW exactly it supports OpenGL or D3D...  then again I know little to nothing about support for those APIs on the die

---

### Post by -gabe-noob- on 2008-02-08
I can't get this to work 'cause wow crashed when I try to edit video settings... could it be like a turn around of not being able to edit in OpenGL mode?

---

### Post by -gabe-noob- on 2008-02-08
and also cause when I try to run in full screen there is about an inch of black space in between the top of the screen and the picture, meaning I cant see the bottum of the picture

---

### Post by hikaricore on 2008-02-09
> **-gabe-noob- said:**
> also I love how the forum mod makes some condesending remark with out even referencing the biggest part of my post...

I addressed the post in which i was replying to and attempted to explain the situation a little further.
 Making taunting remarks like this will just give me a reason to completely ignore you from this point on.  Best of luck.

--Aaron

---

### Post by -gabe-noob- on 2008-02-09
Sorry Hi... I had a realll bad day yesterday, mind posting your system specks :P i'm currently on the search for a new computer. 

(again real sorry man, I did come off as quite the ****

---

### Post by -gabe-noob- on 2008-02-09
here are the systems I'm looking at 

Specifications


    * 2.0GHz Intel Core 2 Duo
    * 2GB 667MHz DDR2 SDRAM - 2x1GB
    * 250GB Serial ATA Drive
    * SuperDrive 8x (DVD±R DL/DVD±RW/CD-RW)
    * Apple Mighty Mouse
    * Apple Keyboard (English) + Mac OS X
    * Accessory kit
    * 2.0GHz Intel Core 2 Duo
    * ATI Radeon HD 2400 XT with 128MB memory
    * 20-inch glossy widescreen LCD
    * AirPort Extreme
    * Bluetooth 2.0 + EDR
(macintosh, a bit pricy around 1.3k) 

Or 

Limbo 2440

An Ubuntu system with Compiz out-of-the-box


Selected options:
Processor:  	Core 2 Duo E4500 2.2 GHz
Memory:  	2 GB DDR2-533
Hard Disk:  	320 GB SATA2
Optical Drive:  	CD-RW / DVD-ROM (included)
Networking:  	Gigabit Ethernet (included)
Operating System:  	Ubuntu 7.10 Gutsy Gibbon (Gnome)
Video Card:  	NVIDIA 8500 GT 256 MB
Display:  	--
Speakers:  	--
Input devices:  	--
Warranty:  	1 Year (included)\
775 with monitor and keyboard+ mouse (looking for a surge protector)

---

### Post by Sammi on 2008-02-10
If you want to game in Linux, go for a Nvidia graphics card. They've got far the best driver implementation for Linux. 

ATI are getting better, but it'll probably be a year before they reach parity with Nvidia, so one should steer clear of them a little longer IMO. 

Intel's Linux drivers may be open source and pretty well integrated into Linux, but they are low quality non the less. Not good for gaming.

---

### Post by Ripfox on 2008-02-10
The intent of this thread is to help people with intel integrated graphics run WOW...:)

---

### Post by variableenigma on 2008-05-10
BUMP!

I am running Ubuntu Hardy Heron on a Dell Latitude D620 with an Intel VGA Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller.

I WAS running it with OpenGL, and it was working fine except for ONE little graphics problem- things (including my minimap, characters, and some objects) turn into white silhouettes whenever I went indoors. 

After reading this post, I changed it to d3d, but NOW, it crashes right after I select my character with this message: 
Error #132 (0x85100084) Fatal Exception


This is in my terminal window:
fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\common.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x32eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ec94,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f2c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a0,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x12e588) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x130150) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x32f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f144,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:reg:GetNativeSystemInfo (0x37402b24) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x32d194,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32d200,0x00000000), stub!
Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max temporary reg
Please report at bugzilla.freedesktop.org
Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org
of Warcraft\WoW.exe: intel_batchbuffer.c:145: intel_flush_inline_primitive: Assertion `intel->prim.primitive != ~0' failed.
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set


My config.wtf file looks like this:
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "d3d"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET lodDist "100.000000"
SET SmallCull "0.070000"
SET DistCull "350.000000"
SET frillDensity "8"
SET farclip "177"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET realmList "us.logon.worldofwarcraft.com"
SET soundMaxHardwareChannels "12"
SET locale "enUS"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET coresDetected "2"
SET videoOptionsVersion "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET patchlist "us.version.worldofwarcraft.com"
SET M2UseShaders "0"
SET ffxdeath "0"
SET ffxglow "0"
SET gxCursor "0"
SET textureFilteringMode "0"
SET Gamma "0.800000"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET lod "1"
SET baseMip "1"
SET spellEffectLevel "0"
SET groundEffectDist "70"
SET weatherDensity "0"
SET realmName "Llane"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET gameTip "28"
SET uiScale "1"
SET shadowLOD "0"
SET accountName "variableenigma"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_EnableAmbience "0"
SET Sound_EnableErrorSpeech "0"
SET Sound_EnableMusic "0"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET Sound_EnableEmoteSounds "0"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET checkAddonVersion "0"
SET scriptErrors "1"
SET UIFaster "2"
SET minimapZoom "0"
SET minimapInsideZoom "0"
SET gxTripleBuffer "1"


Help! I don't know a lot about this, so please make it newbie-friendly! haha Let me know what other information you may need, and I'll find it for you.

---

### Post by Ripfox on 2008-05-11
If you can get it to run in opengl then you would prefer that method...:)

---

### Post by pedro_orange on 2008-05-12
I find wow runs proper rubbish on built-in Intel graphics.
I've got an old Alienware Sentina with a built-in graphics card and when it was using Windows WoW ran crap on it. 
It works slightly better with Ubuntu/Wine, in OpenGL mode. (-opengl) Not at all in D3D.

But; I've got a desktop with an nVidia 8800 GTX. 
Now that works properly.

I don't think it's worth the time/hassle to be trying to get WoW working on em. If you wanna feed the WoW addiction get an nVidia or use Windoze :)

---

### Post by ForksHolder on 2008-05-12
Hello,

I have Intel 915GM witch is almost like yours.

I run it on D3D and it's running but with LOW fps.. About 3 FPS... :(
My computer is Compaq nc6220..

Any ideas?

---

### Post by Ripfox on 2008-05-12
Unfortunately I cannot really support this thread any longer as I have since sold my laptop with intel graphics on it. But, if you surf back to the original post, and try the things I did there, I did get a decent framerate out of this card. For the people who feel the need to pop in here and tell people to "buy an nvidia card" well that's an obvious solution isn't it? The people who sought out this thread are trying to make due with what they have and you cannot switch out your graphics card in your laptop. If you have something constuctive to say, well let's hear it...:confused:

---

### Post by anthony.phipps on 2008-08-22
my wow works fine, Lenovo Thinkpad R61 with Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller
here are my configurations:

Config.wtf
```
SET accountName "-"
SET autoClearAFK "0"
SET autoLootCorpse "1"
SET autoQuestWatch "0"
SET autoSelfCast "1"
SET cameraDistanceMax "50"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "67.5"
SET cameraView "0"
SET cameraYawSmoothSpeed "270"
SET ChatAmbienceVolume "0.30000001192093"
SET ChatBubblesParty "1"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET CombatDamage "0"
SET CombatHealing "0"
SET CombatLogPeriodicSpells "0"
SET coresDetected "2"
SET deselectOnClick "0"
SET DesktopGamma "1"
SET displayFreeBagSlots "1"
SET DistCull "500.000000"
SET expansionMovie "0"
SET farclip "477"
SET ffxDeath "0"
SET ffxGlow "0"
SET gameTip "1"
SET Gamma "1.000000"
SET groundEffectDensity "24"
SET guildMemberNotify "1"
SET gxApi "opengl"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxFixLag "0"
SET gxMultisampleQuality "0.000000"
SET gxRefresh "60"
SET gxResolution "1280x800"
SET gxWindow "1"
SET hidePartyInRaid "1"
SET hwDetect "0"
SET InboundChatVolume "1"
SET locale "enUS"
SET M2UseShaders "0"
SET minimapInsideZoom "0"
SET minimapZoom "0"
SET mouseInvertPitch "1"
SET movie "0"
SET OutboundChatVolume "1"
SET particleDensity "1.000000"
SET patchlist "us.version.worldofwarcraft.com"
SET PetMeleeDamage "0"
SET PetSpellDamage "0"
SET pixelShaders "1"
SET profanityFilter "0"
SET PushToTalkButton "RCTRL"
SET questFadingDisable "1"
SET readContest "-1"
SET readEULA "1"
SET readScanning "-1"
SET readTerminationWithoutNotice "-1"
SET readTOS "1"
SET realmList "us.logon.worldofwarcraft.com"
SET realmName "-"
SET scriptErrors "1"
SET showChatIcons "1"
SET showGameTips "0"
SET showNewbieTips "0"
SET showPartyBuffs "1"
SET showPartyPets "0"
SET showRaidRange "1"
SET ShowTargetCastbar "1"
SET showTargetOfTarget "1"
SET showToolsUI "1"
SET ShowVKeyCastbar "1"
SET SmallCull "0.040000"
SET Sound_AmbienceVolume "0.60000002384186"
SET SoundBufferSize "150"
SET Sound_EnableErrorSpeech "0"
SET Sound_EnableSoundWhenGameIsInBG "1"
SET Sound_MasterVolume "0.40000000596046"
SET Sound_MusicVolume "0"
SET Sound_OutputDriverName "System Default"
SET SoundOutputSystem "2"
SET Sound_SFXVolume "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET specular "1"
SET stopAutoAttackOnTargetChange "1"
SET UberTooltips "0"
SET uiFaster "0"
SET uiScale "0.95999997854233"
SET UnitNameCompanionName "0"
SET UnitNameFriendlyCreationName "0"
SET UnitNameFriendlyPetName "0"
SET UnitNameFriendlyPlayerName "0"
SET UnitNameNPC "1"
SET UnitNamePlayerGuild "0"
SET UnitNamePlayerPVPTitle "0"
SET useUiScale "1"
SET videoOptionsVersion "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET weatherDensity "3"
SET lastCharacterIndex "1"
SET gxCursor "0"
SET groundEffectDist "70"
```

/etc/X11/xorg.conf
```
# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 930B"
	Horizsync	30-81
	Vertrefresh	56-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	2560    1024
		Modes		"1280x1024@60"	
#"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1600x1200@65"	"1152x864@75"	"1600x1200@60"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
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
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "device" # 
	Identifier	"device2"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:0:2:1"
	Driver		"vesa"
	Screen	0
EndSection
Section "screen" # 
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" # 
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```

winecfg setup:
```
wow.exe
-Applications
--Windows version: Windows XP
-Graphics
--Allow the window manager to decorate the windows [checked]
--Allow the window manager to control the windows [checked]
--Vertex Shader Support: Hardware
--Allow Pixel Shader [checked]
--Screen resolution: 96dpi
-Audio
--Sound Drivers: ALSA Driver [checked]
--Hardware Acceleration: Full
--Default sample rate: 44100
--Default bits per sample: 16
--Driver Emulation [checked]
-Drives
--Click Autodetect...
```

My issues are:
-Minimap is white but shows icons
-When a patch is applied, i have to change SET readEULA and SET readTOS to 1 (from -1) or else the game freezes if i try to accept them ingame.

---

### Post by Ripfox on 2008-08-25
Thank you for that constructive post. :)

---

### Post by Tuxoid on 2008-09-24
Wow runs craptastically on my Intel 945gm in my LG P1 Laptop. I have the white minimap of death, when I go in a building, tunnel or cave, the exits and windows turn white.

My Config.wtf

```
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET locale "enUS"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET movie "0"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET SmallCull "0.070000"
SET DistCull "350.000000"
SET farclip "177"
SET particleDensity "1.000000"
SET realmName "Frostwolf"
SET expansionMovie "0"
SET gameTip "59"
SET accountName "bigscottie5"
SET Gamma "1.000000"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET weatherDensity "1"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET uiScale "1"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_MasterVolume "0.30000001192093"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.5"
SET OutboundChatVolume "2.5"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET lastCharacterIndex "1"
SET DesktopGamma "1"
SET ffxGlow "0"
SET ffxDeath "0"
SET gxWindow "1"
SET UIFaster "0"
SET M2UseShaders "0"
SET M2UsePixelShaders "0"
SET lod "1"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
SET Sound_EnableHardware "1"
SET gxDepthBits "24"
SET spellEffectLevel "0"
SET MultisampleQuality "0.000000"
SET questFadingDisable "1"
SET lockActionBars "1"
SET alwaysShowActionBars "1"
SET Sound_OutputQuality "2"
SET EnableVoiceChat "1"
SET PushToTalkButton "V"
SET textureFilteringMode "0"
SET groundEffectDist "10"
SET gxTripleBuffer "1"
SET gxApi "opengl"
```

My xorg.conf:

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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
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

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"Intel 945"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
	Vendorname	"Intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x800"
	Horizsync	31.5-50.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	800
		Modes		"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection
Section "device" #                                  
	Identifier	"device1"
	Boardname	"Intel 945"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	1
	Vendorname	"Intel"
EndSection
Section "screen" #                                  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #                                  
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

winecfg:

```
-Mimics: Windows XP
-no library overrides
--Graphics
-Stops mouse from leaving window
-allow window manager decoration
-allow window manager control
-Vertex Shaders: Hardware
-Pixel Shaders [UNCHECKED]
-96dpi screen resolution
--Audio
-ALSA and OSS
-16 Bits per sample
-44100 sample rate
-Full Hardware acceleration
-No driver emulation
```

I try to run Wow under direct3d, but I generally have a framerate below 10fps outdoors.

Anything I could do?

---

### Post by Sammi on 2008-09-26
Buy a computer that meets the minimum requirements to play the game?

---

### Post by bumpycat on 2008-09-28
I'm running Wow under Wine on a Lenovo Thinkpad R61e, with onboard Intel GM965/X3100 graphics. I went through the [Ubuntu Wow FAQ]("https://help.ubuntu.com/community/WorldofWarcraft"), and set gxAPI to d3d, and it worked!

Config.wtf as follows:

SET locale "enGB"
SET realmList "eu.logon.worldofwarcraft.com"
SET patchlist "eu.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxAPI "direct3d"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET M2UseShaders "0"
SET videoOptionsVersion "1"
SET textureFilteringMode "0"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET readTerminationWithoutNotice "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET Sound_EnableHardware "1"
SET SoundBufferSize "150"
SET SmallCull "0.080000"
SET DistCull "350.000000"
SET farclip "400.000000"
SET particleDensity "0.25"
SET realmName "Turalyon"
SET ffxDeath "0"
SET ffxGlow "0"
SET gameTip "8"
SET uiFaster "0"
SET weatherDensity "0"
SET checkAddonVersion "0"
SET screenEdgeFlash "0"
SET vertexShaders "0"
SET showfootprints "0"
SET SkyCloudLayers "0"
SET Gamma "1.000000"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"

---

### Post by anthony.phipps on 2008-10-01
i recommend that you delete your account name and realm name entries from your pasted config files for your own accounts sake.

---

### Post by Ripfox on 2008-10-01
> **Sammi said:**
> Buy a computer that meets the minimum requirements to play the game?

Again, this thread is to try and make it work for those stuck with this graphics. "Go buy a new computer" isn't helping anyone. I have had some success with this card and it's better to some people than nothing. Not everyone can afford to replace their computer...

---

### Post by Sammi on 2008-10-02
> **Ripfox said:**
> Again, this thread is to try and make it work for those stuck with this graphics. "Go buy a new computer" isn't helping anyone. I have had some success with this card and it's better to some people than nothing. Not everyone can afford to replace their computer...
That is exactly my point. He did have some success making it run, but was complaining that it was running with lower than 10 fps. It would be wrong of us to make everyone think that they can expect more than that. They can't. I am helping them understand this.

I do apologize for the dryness of my remark though. I could have formulated myself in friendlier terms, which is more in line with the general spirit of this forum.

---

### Post by kylet450 on 2008-10-02
lol

I did the same thing, but with gl

im gonna try what you did, cheers.

I get 7500 ( average ) on glx gears lol XD

---

### Post by Ripfox on 2008-10-03
> **Sammi said:**
> That is exactly my point. He did have some success making it run, but was complaining that it was running with lower than 10 fps. It would be wrong of us to make everyone think that they can expect more than that. They can't. I am helping them understand this.

I do apologize for the dryness of my remark though. I could have formulated myself in friendlier terms, which is more in line with the general spirit of this forum.

Thanks for the reply. I have gotten up to 25 fps on those cards though, so they can potentially expect more.

---

### Post by bleachworthy on 2008-10-03
I've got the 945GME in a E1505, just got wow installed, the game runs completely in OpenGL mode, but does not render anything properly, it's barely playable, however in D3D mode, it runs great, until the UI loads, and you enter the game, then there is a full system crash...

---

### Post by peabody on 2008-10-16
Just had to say that I got this working with the new patch, which seemed to really break the opengl renderer so I had to resort to d3d, but I had to do the following to the registry to get d3d mode working on my 945gm (seems to be because neither pbuffers or frame buffer objects are supported by the current intel driver in Hardy).

1. Open the registry with regedit
2. Go to HKEY_CURRENT_USER\Software\Wine\Direct3D
3. Make sure the keys there look like the following:

OffscreenRenderingMode backbuffer
PixelShaderMode        disabled
UseGLSL                enabled
VertexShaderMode       hardware

Close regedit, then run the game in d3d mode (put -d3d as a command line switch on the launcher).

I can still play the game, though framerates dropped about 5fps on average which has been truly painful in outdoor areas since I usually only got about 10-12fps on average there before using opengl.  Needless to say I move with the camera tilted to floor whenever I can.  Indoor areas and instances are still quite playable.

The upside has been that mouse cursor lag has completely disappeared and all graphical glitches that affected the OpenGL renderer are gone (white minimap, white walls and objects in some areas).

It's just a shame the game won't run better than that as average framerate in just about all areas of the game in windows is about 20.

---

### Post by KevNice on 2008-10-16
I am about to give up on this.. I have tried nearly every configuration of config.wtf, winecfg, all the advice in the ubuntu guide and troubleshooting section. I can get the game to run as long as I stay indoors. On one toon I tried to ride the flight path bird thing and it crashed moments after taking air, now I can't even log into that toon because it crashes immediately. I rolled a new toon and indoors everything seemed to be fine (of course the empty room he was in helped) but after stepping outside for about 10 seconds it crashed. Can't be sure but it seems the fps was too low and it couldn't keep up with the game, so just crashed.

Here's what my config looks like (on a Dell Inspiron 1520:

```
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "opengl"
SET ffxGlow "0"
SET UIFaster "2"
SET M2UseShaders "0"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET locale "enUS"
SET expansionMovie "0"
SET movie "0"
SET showToolsUI "1"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET textureFilteringMode "0"
SET accountName "-"
SET mouseSpeed "1.5"
SET Gamma "1.000000"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET Sound_OutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "177"
SET particleDensity "1.000000"
SET realmName "-"
SET gameTip "11"
SET VoiceActivationSensitivity "0.39999997615814"
SET spellEffectLevel "0"
SET groundEffectDist "70"
SET baseMip "1"
SET environmentDetail "0.5"
SET weatherDensity "0"
SET ffxDeath "0"
SET lastCharacterIndex "1"
```

I tried it in D3D also and it crashed right after the opening CGI.. couldn't even get to the login screen.

---

### Post by MasterNetra on 2008-10-16
I got bored quickly of WoW anyway. I had it working at one point on my Dell Latitude D530 but had trouble with Frame Rates too. Regardless after playing it for a week on XP i got bored with it. When it comes to games I'm high maintance. :P XD

---

### Post by emkay_de on 2008-11-02
I got my wow running quite good for an intel 945 use wine 1.1.5 selfcompiled version and the registry tweaks. Got indoor perf. 20-30  fps outdoor 8-12 fps. start wow withe -opengl option.

---

### Post by ZarathustraDK on 2008-11-03
I'm about to try this out on my eee 901 :D

---

### Post by emkay_de on 2008-11-04
Got an eee 900A with Kubuntu 8.04, that should work i m trying to optimize my fps output (change driver, modify x-org.conf) so WoW ll be smooth to play. If you have Questions just ask i hope i can help you with that.

I order to get an functional (k)ubuntu you'll need the eeepckernel, and Ubuntu_ACPI_scripts-EeePC_901_1000.

---

### Post by dukin on 2009-06-19
with the commands that are showing I am still geting 1fps in game I am yousing a acer sp 3610 with a intel 915gm

---

### Post by alex.rayu on 2009-06-19
Get used, man! New releases break more than they fix.

---

