---
title: "[SOLVED] World of Warcraft - Ati Offical Drivers (Working)"
date: 2007-12-31
forum: Wine
---

### Post by Spydr4590 on 2007-12-31
Okay this is a simple how to get World of Warcraft working for ATI Cards. I've only tested this on ATI x1900 series Card, so if you have any other ATI card and this guide works for you then please post a response.

This was done from a fresh install using the Ubuntu 7.10 32-bit and 64-bit Operating Systems. After the system was installed, I made sure to download all the updates. You can do this by going to the System Menu-->Then to the Administration Menu-->and Click on Update Manager. Click check and after the update manager refreshes choose install. You will be asked to reboot. Go ahead and reboot.

After you have restarted goto [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) Choose Ubuntu on the right and then your Ubuntu Build number and follow Step 2 Manual install the driver. This will install the ATI Driver Correctly. Follow these instructions exactly to the letter!

**Note: Unfortunately at the time of this writing Ati/AMD 7.12 (8.443.1) Drivers don't work correctly with certain video and opengl. You will need to disable compiz fusion after you install the ATI Driver. Goto system menu--> preferences-->Appearance. Then click on visual effects tab, and choose none. You must restart or else after you install wine and wow you will not be able to see the graphics displayed correctly.**

Goto [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) and follow the instructions to download the latest version of WINE and install. 

Install the Wine Gecko IE engine by going to Applications Menu-->then click on terminal and type in this code```
wine iexplore http://www.winehq.org
``` Usually for whatever reason this will fail to download right the first try. Go ahead and exit out of the terminal if this freezes and restart the terminal again. Then type the following command again till you see wine homepage loaded correctly.

Configure wine by going to the Applications Menu--> Wine Menu--> then click on Configure wine. Click on the applications tab and choose Windows Xp. Now goto the audio tabe and make sure only oss driver is check marked. Lastly click on the drives tab and choose auto detect. Now save these settings and exit.

Create two folders on your desktop. Make one WoW and the other WoW-Crusade(for the expansion). Copy all files from your wow discs to the wow directory. Then copy all your crusade files to the crusade folder.

[B]Note: Make sure you leave no wow cds in your cd rom drive!
[/B]

Goto your wow folder and right click installer.exe and choose "open with other application" Scroll all the way to the bottem and choose wine. Just click install and wait a few seconds, the garbbled license agreement will allow you to click agree. Wow will install. Do the same thing for the expansion.

Download [http://files.filefront.com/World+of+WarCraft+230+English+Full+Patch/;9031070;/fileinfo.html](http://files.filefront.com/World+of+WarCraft+230+English+Full+Patch/;9031070;/fileinfo.html) and install.

**Note: Do not run World of Warcraft yet!**

Download Config.wtf.zip, Right click it and choose extract here. The default opengl of this file is at 1280x1024. If you need a smaller screen size edit this file with a text editor and change gxresolution to the size you prefer. Goto the Applications Menu--> Wine Menu--> and click on browse c:\ drive. Then navigate from drive c, to program files, to world of warcraft, to WTF folder. Copy the config.wtf to this directory and make sure to delete any other wtf files you see there.

**Note: You have to do this or text will become unreadable, and this does increase your FPS [http://www.wowwiki.com/Linux/Wine#Registry_Tweak_for_FPS_Boost](http://www.wowwiki.com/Linux/Wine#Registry_Tweak_for_FPS_Boost)**

Run wow once and log onto any of your characters. DO NOT configure any in game OPTIONS yet. Choose exit. Now download applytoforehead.zip extract this file and place this in your world of warcraft-->interface-->addons folder. Now restart the game, and you will be able to change in game options without crashing.

A Final note about addons, you can't just install all of them to you interface-->addons folder. Like auctioneer you can't extract the one folder and put it in the directory. This will not work. You will need to open up the auctioneer folder and take out all those folders and place it in your interface directory. That's all! Enjoy World of Warcraft with your ATi Graphics cards :) I hope this helps many ati users out there!

---

### Post by jseiser on 2007-12-31
a friend gave me his laptop, with Xpress 200M and wants ubuntu installed and WOW working, so im going to try this tonight.  ive only installed on nvidia and via cars, so i hope im not getting in over my head :)

---

### Post by sudomaster on 2008-01-05
This was by far the best tutorial on setting up WoW that I've found.  I have an older laptop with an ATI Mobility X700 card and the game actually shouldn't really work on it, but with this tutorial it (sort of) does...

The only problems I'm having is that I get these strange spikes appearing on the screen and can't read any of the text on the buttons or in dialogs when talking to a vender.  Any ideas?

---

### Post by sudomaster on 2008-01-05
Fixed my icons/dialog issues by using FPS edit above!

---

### Post by sampotter on 2008-01-31
I just signed up here for the singular purpose of downloading Config.wtf file, hoping it would solve my problem with getting WoW to run.  It worked like a charm, so I thought I would extend my purpose to saying thanks.  So, thanks! :)

---

### Post by Catholicnerd on 2008-02-01
Well, WoW is working for me, but not like a charm.  I'm getting 4fps with my Radeon X1200.  *sigh*

---

### Post by Balmung on 2008-02-01
^_^ This helped alot thanks. My card is a ATI Radeon™ Xpress 1100.

---

### Post by eriktheblu on 2008-02-20
This is about the 4th guide I've used to get WoW to work under Ubuntu, and it finally worked. Thanks for posting this!

My card is the Xpress 200 integrated.

I dual boot with 7.10 and XP media center (Ubuntu is appropriately in the formatted Windows recovery partition). WoW does run significantly slower under Ubuntu and Xubuntu than it does in Windows, but it is still quite playable (with minimal graphics settings, I easily had 40+ fps)

Thanks again.

---

### Post by gus1986 on 2008-02-22
I just wanted to say thank you. I followed this guide and now I can play WoW perfectly.

---

### Post by alfirin on 2008-02-27
Excellent guide! It works fine with my Ati radeon X700. 
The only problem is that I can't play in 1280x1024. The screen turns black and says "out of range 40kHz/85Hz" I changed it to 1024x768 and it works fine.Does anyone know how to fix my resolution? :confused:

---

### Post by jasc on 2008-03-02
This fixed the black screen I originally had, but I still have the problem of the screen going white (with the exception of my character, the mobs, and a few details on the edges) whenever I enter a building or a cave. Any idea how to fix this? Outside of houses, buildings, structures, or caves, the graphics are fine, it's just inside those that the graphics go almost totally white.

---

### Post by sanitario on 2008-04-19
I'm using a Thinkpad T60 with a X1300, this worked excellent, with the exception of the minimap not working indoors. Thanks for the great guide!

Oh, right, I'm using Gutsy, and I went with the included ATI drivers and wine, no need to download external packages.

---

### Post by mpoy70 on 2008-05-07
Thank you very much! I was in desperation but with your files is working on my Toshiba A200 notebook with ATI Mobility Radeon 2600.

---

### Post by Myoshi on 2008-05-07
Anyone else experincing the compass map to be entirely white and know how to fix?

edit: nvm its only inside inn's and buildings it does this.

---

### Post by Siddx4 on 2008-05-19
First of all.  Like many have previously said.  This guide is absolutely awesome.  Google is full of guides that are rubbish...well, mostly just irrelevant for these specs.

For the most part, wow "works".  The problems I still have being the minimap thing others have, and graphical "tearing" or glitches across the whole screen, affecting menu text as well.  It works completely for about 5 seconds.  Visual effects on my desktop are off, which added the 5 seconds, but that's it.

Can someone point out what I'm missing perhaps?  Any help would be great.

*curses nvidia*

Using 8.04 HH and Wine 1.0-rc1

Xorg.conf
> 
Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"Capabilities"	"0x00000800"
	Option		"UseFastTLS"	"off"
	Option		"KernelModuleParm"	"locked-userpages=0"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "Module"
	Load		"glx"
EndSection


Config.wtf
> SET ffxGlow "0"
SET locale "enUS"
SET hwDetect "0"
SET UIFaster "2"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x1024"
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
SET gameTip "73"
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
SET coresDetected "2"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET Sound_OutputDriverName "System Default"
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
SET realmName "The Venture Co"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"

---

### Post by sanitario on 2008-05-21
> **Siddx4 said:**
> First of all.  Like many have previously said.  This guide is absolutely awesome.  Google is full of guides that are rubbish...well, mostly just irrelevant for these specs.

For the most part, wow "works".  The problems I still have being the minimap thing others have, and graphical "tearing" or glitches across the whole screen, affecting menu text as well.  It works completely for about 5 seconds.  Visual effects on my desktop are off, which added the 5 seconds, but that's it.

Can someone point out what I'm missing perhaps?  Any help would be great.



Did you do the Registry Tweak at [http://www.wowwiki.com/Linux/Wine#Registry_Tweak_for_FPS_Boost](http://www.wowwiki.com/Linux/Wine#Registry_Tweak_for_FPS_Boost) ? Cause I forgot that first and had tons of tearing and glitches all over. After the tweak it all worked brilliantly, except the tearing. 

Good luck!

---

### Post by Siddx4 on 2008-05-21
I did at one point but took it off when backtracking little things that worked vs didn't work.

BUT, I recently got wow to work great, at least until  I walked indoors, then the same thing.  But I seem to remember others posting about that specifically, so I should be able to fix that as well.  Thanks for the reply, and I'll do the registry tweak now also! :D

Thanks, and I'll check in with more problems later no doubt, but hopefully not WoW problems. :guitar:

**update**
Registry tweak fixed the indoor tearing.  Only things left are configuring extra mouse buttons, and other little things.

This thread rocks.  Thanks again to all.

---

### Post by eggplant37 on 2008-07-30
> **Siddx4 said:**
> I did at one point but took it off when backtracking little things that worked vs didn't work.

BUT, I recently got wow to work great, at least until  I walked indoors, then the same thing.  But I seem to remember others posting about that specifically, so I should be able to fix that as well.  Thanks for the reply, and I'll do the registry tweak now also! :D

Thanks, and I'll check in with more problems later no doubt, but hopefully not WoW problems. :guitar:

**update**
Registry tweak fixed the indoor tearing.  Only things left are configuring extra mouse buttons, and other little things.

This thread rocks.  Thanks again to all.


I must say I agree with the fact that this thread is awesome. However, I'm at the same point. I've gotten WoW running very well, though sluggish, only 7-8 fps in IF AH on Zangarmarsh realm, using both the official driver and the one that apt-gets on my Dell Inspiron 1501 with ATI Radeon Xpress 1500 IGP. The minimap is a whiteout in interior buildings and cities, and doing the phase effect for the stolen mana modules is completely impossible because the overlay for the phase effect completely whites out the screen. 

I wonder what tweaking, if any, to the fglrx module settings in xorg.conf might fix this?

---

### Post by Spydr4590 on 2008-07-30
This link might help you also [http://www.wowwiki.com/Linux/Wine/Troubleshooting](http://www.wowwiki.com/Linux/Wine/Troubleshooting) Talks about some xorg options.

---

### Post by eggplant37 on 2008-07-31
> **Spydr4590 said:**
> This link might help you also [http://www.wowwiki.com/Linux/Wine/Troubleshooting](http://www.wowwiki.com/Linux/Wine/Troubleshooting) Talks about some xorg options.

Saw it, tried it all, with the exception of looking at the kernel tuning. That may get done over the weekend, but I've a server here at home I wanted to get upgraded, so it's on backburner for now. Wish me luck. 

As always, other suggestions are welcome.

---

### Post by viperdak on 2008-08-06
awesome job on the guide.  WoW was the only thing holding me back from a total switch to Ubuntu.  Now as soon as i can get Ventrilo to work i'll be set.  Ubuntu rules and so do helpful people like all you guys in the forums!!  woot!

Thanks

---

### Post by mambro on 2008-08-28
Good job! It works for me with an ATI X300

---

### Post by darcklaw on 2008-10-29
Works perfect with x1650 pro

---

### Post by Mrmisanthrope_ on 2008-11-21
nevermind.... its late and Im a linux newb. wine-doors v1.00 does not WineHQ make.

Thanks for the excellent tutorial!

---

### Post by Noctivagant on 2009-01-04
Thanks for this.

This may keep me from going back to Windows at home forever.

---

### Post by crzyazn on 2009-01-05
are u guys having issues runnin wow in window mode? when i go in-game and enable window mode, w/o wine, it sometimes will just flicker alot but sometimes it only flickers when i click the mouse. does anyone have a fix for this cause id love to go from wow to talkin to pplz on pidgin or switching songs. PlEASE HELP ME!!!

---

### Post by sirdrakey on 2009-01-06
don't know if this will help anyone but i have a Asus M3A78-CM only the board no cards and it has a 770 ati on board well the conf.wtf on the download didn't work well for me the talk channels and name plates were flicking and ripping across the screen so i used my old one and it works just a little glitch looks like a flicker in the left bottom corner. here it is

> SET locale "enUS"
SET portal "us"
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
SET mouseSpeed "0.5"
SET Gamma "1.000000"
SET lastCharacterIndex "4"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET Sound_OutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "397"
SET particleDensity "1.000000"
SET groundEffectDensity "32"
SET realmName "Archimonde"
SET gameTip "2"
SET VoiceActivationSensitivity "0.39999997615814"
SET textureFilteringMode "2"
SET spellEffectLevel "5"
SET groundEffectDist "90"
SET environmentDetail "0.75"
SET ffxDeath "0"
SET gxDepthBits "24"

if this helps good luck and how do you get the add-ons back?:popcorn:

---

### Post by Tourne on 2009-03-25
Hey, great guide I have sort of success from it. Running ATI X1200 before the tutorial WoW would make my computer crash, now it loads up, with sound! but not a clear picture (or even semi distinguishable) help? pidgin? :D Will post step by step how to fix if I ever manage to :X

---

### Post by False Dmitry II on 2009-09-26
Needed to get WoW working for a friend on a X1950 Pro, and following the WoWwiki along with using this conf.wtf did it just fine. I'm running Hardy, since I knew that it's drivers wouldn't be in Jaunty.

---

### Post by Shadower1348 on 2010-12-13
ive done almost all steps and so far this is as far as any guide has worked for me, i read a lot of comments and can tell its prob. going to work! THANK YOU this is the first guide that has worked for me!

---

### Post by AdamGM on 2011-02-04
I have an ati radeon 4350 and an intel i5 quadcore. 
When I run wow, my video options are stuck on low... could I use your config.wtf and addon to fix this with everything already installed?

---

