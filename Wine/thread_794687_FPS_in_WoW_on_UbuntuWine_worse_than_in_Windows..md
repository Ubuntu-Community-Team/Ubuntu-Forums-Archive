---
title: "FPS in WoW on Ubuntu/Wine worse than in Windows."
date: 2008-05-14
forum: Wine
---

### Post by Syroco on 2008-05-14
So I've done everything correct to install WoW, I followed this HowTo:
[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

I did the registry edit and edited the config file.

I get ~15FPS outside, max settings.
In Windows I would get 40 fps (This was even low for Windows, the patch really affected my FPS)

I used Envy to get my graphic card drivers.

What can I do?? I really like Ubuntu, I don't want to give it up..

Oh, and my GFX card is: Nvidia GeForce 8400 GS 512mb

---

### Post by shae on 2008-05-14
Are you running it with desktop effects on or off?

---

### Post by Syroco on 2008-05-14
Are you talking about the Extra Effects?

---

### Post by dtrot55 on 2008-05-14
You could try running WoW in a earlier version of Wine....try out playonlinux.com...great tool to manage "MULTIPLE" installations of WINE in which you can force a game to run in whatever version you want...i had FPS issues in CSS and forcing verison 46 made the game playable...so i would give that a shot.

---

### Post by shae on 2008-05-14
Yes, I am talking about the extra effects.  Try setting visual effects to none.

---

### Post by Syroco on 2008-05-14
> **dtrot55 said:**
> You could try running WoW in a earlier version of Wine....try out playonlinux.com...great tool to manage "MULTIPLE" installations of WINE in which you can force a game to run in whatever version you want...i had FPS issues in CSS and forcing verison 46 made the game playable...so i would give that a shot.

Okay, I installed that.  But I can't find it :(
Know where it's usually at?


Also, I went into my Nvidia control panel, and it has am openGL optimizer, helped in-game a bit. :)

Still looking to get more of a boost in my fps though. 

Also, does anyone know how to reduce the cursor lag from the result of using openGL?

---

### Post by Syroco on 2008-05-15
Anyone? :X

---

### Post by AngryBash on 2008-05-15
I remember a setting to launch WoW in Opengl mode on Windows. I was just thinking, if you launched WoW in Linux with Opengl mode activated, wouldnt that speed the game up a little? That way it could make direct Opengl calls, instead of going via DirectX. 

I dont remember how to activate the Opengl mode, i think it was a command line option.

---

### Post by Resonance378 on 2008-05-15
A search would return

wine WoW.exe -opengl

along with information to put

SET gxAPI "OpenGL" in your WoW  Config.wtf file...

Turn Desktop Effects OFF

I'm on an ATI 9600XT - a card quite a bit older than yours with 1G of RAM for my 3.0Ghz CPU... I get 105fps indoors and 30fps outdoors if you can use that as a 'benchmark'

---

### Post by Syroco on 2008-05-15
I do run my WoW in openGL.

I still get very bad FPS for my system. (3.6ghzp4, 2gig of ddr2, 8400 GS 512mb)
I would get a stable 60fps outdoors, and sometimes to 80, with around 40 indoors, this is when I ran WoW in Windows.

Where would I find my installation of PlayOnLinux?  I installed it but I can't find it anywhere.

Also, my question was how do I reduce the cursor lag in WoW?(a common side-effect of playing WoW in openGL)

---

### Post by caeroe on 2008-05-15
> **Syroco said:**
> So I've done everything correct to install WoW, I followed this HowTo:
[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

I did the registry edit and edited the config file.

I get ~15FPS outside, max settings.
In Windows I would get 40 fps (This was even low for Windows, the patch really affected my FPS)


Something changed amongst Ubuntu Hardy, Wine, or maybe a very recent WoW patch.  I doubt the last candidate, I'm pretty sure I was using the same patch version when I upgraded, then later got WoW 2.4.2.

I had excellent performance back on Gutsy with an older version of Wine, whatever came before 1.0rc1.  

Now FPS struggles to go over 35 in graphic intense areas.  In XP it's 70-100.  Performance in Gutsy was nearly identical, maybe 60-90.  I've done everything, regedit, lowered settings, removed desktop effects, etc.  

It's out of my hands, and I'm back on XP for now... and probably for good.  My Linux experiments always end like this; gaming is never there.

---

### Post by Faud on 2008-05-15
You shouldnt get any cursor lag because of opengl. I dont get any and my system is a lot less then yours. That could be an option in wine.
What res are you running WoW at.

---

### Post by Faud on 2008-05-15
> **caeroe said:**
> Something changed amongst Ubuntu Hardy, Wine, or maybe a very recent WoW patch.  I doubt the last candidate, I'm pretty sure I was using the same patch version when I upgraded, then later got WoW 2.4.2.

I had excellent performance back on Gutsy with an older version of Wine, whatever came before 1.0rc1.  

Now FPS struggles to go over 35 in graphic intense areas.  In XP it's 70-100.  Performance in Gutsy was nearly identical, maybe 60-90.  I've done everything, regedit, lowered settings, removed desktop effects, etc.  

It's out of my hands, and I'm back on XP for now... and probably for good.  My Linux experiments always end like this; gaming is never there.
I would probaly say that you are right, ,but remember that WoW was built for windows, should it just be an amazing possibility that it works at all in linux ? Im gonna go out on a limb and say that if all that you want your computer for is to play wow, then go back to XP. If you want to learn, spend time playing with different interfaces, music player, learn how to even build your own OS then linux is for you AND get free user support for it all, then linux is for you.
I look at being able to play WoW on my Ubuntu as a nice bonus..nothing more. Plus I play on a virtual desktop with wow armory running so when im pvping it takes me 10 seconds to armory the guy/gal Im against $$$

---

### Post by pissedoffdude on 2008-05-15
Looks like your graphics card isn't supported by the latest *stable* nvidia drive which envy provides.  Try installing the latest beta one from [http://www.nvidia.com/object/linux_display_ia32_173.08.html]("http://www.nvidia.com/object/linux_display_ia32_173.08.html")

---

### Post by travelor on 2008-05-18
I'm also experiencing huge FPS problems. I even went out and bought a new nvidia card to attempt to solve the issue. I can get 15-20fps in a building, but turn around and face outside and it drops instantly to 5fps, and stays there until I turn back around. I was trying to setup this system as a second box, and have seen wow play nice on linux, but it refuses this time. I've run it in d3d, opengl, and straight. same thing everytime. I've turned off desktop effects, made every tweak I can find, tried the tweak #2 but it fails due to not owning .wine folder and like I said bought a new card.

I grabbed envy today and it grabbed drivers for the new card (Geforce 6200 256 - running drivers 169.12) and it runs just as crappy as an old pos geforce2mx card.

Config file

SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "71"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET doodadAnim "0"
SET lodDist "100.000000"
SET SmallCull "0.010000"
SET DistCull "500.000000"
SET frillDensity "12"
SET farclip "477"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET expansionMovie "0"
SET realmList "us.logon.worldofwarcraft.com"
SET readTerminationWithoutNotice "-1"
SET coresDetected "1"
SET videoOptionsVersion "1"
SET showToolsUI "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
SET Sound_OutputDriverName "System Default"
SET patchlist "us.version.worldofwarcraft.com"
SET spellEffectLevel "6"
SET realmName "Rexxar"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET gameTip "34"
SET profanityFilter "0"
SET cameraDistanceMaxFactor "1.7999999523163"
SET xpBarText "1"
SET playerStatusText "1"
SET targetStatusText "1"
SET displayFreeBagSlots "1"
SET guildMemberNotify "1"
SET showTargetOfTarget "1"
SET questFadingDisable "1"
SET hidePartyInRaid "1"
SET ShowTargetCastbar "1"
SET groundEffectDensity "48"
SET accountName "accountname"
SET gxCursor "0"
SET DesktopGamma "1"
SET Gamma "1.000000"
SET groundEffectDist "130"
SET uiScale "1"
SET shadowLOD "0"
SET gxWindow "1"
SET lastCharacterIndex "6"
SET textureFilteringMode "3"
SET shadowLevel "0"
SET ffxDeath "0"
SET ffxGlow "0"

Xorg file

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Depth	24
		Modes		"1280x720@60"	"1280x800@75"	"1280x768@60"	"1280x768@75"	"800x600@60"	"1280x800@60"	"800x600@75"	"1440x900@75"	"800x600@72"	"1440x900@60"	"1600x1024@60"	"1680x1050@60"	"1920x1200@60"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce 6800 (generic)"
	Busid		"PCI:5:9:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Device"
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 6800 (generic)"
	Busid		"PCI:5:9:0"
	Driver		"nvidia"
	Screen	1
	Vendorname	"NVIDIA"
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
	Option		"Emulate3Buttons"	"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Proview"
	Modelname	"Proview 713/716"
	Horizsync	30.0-80.0
	Vertrefresh	60.0-75.0
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

---

### Post by igster on 2008-05-19
travelor,

I notice you don't have SET gxApi "opengl" as part of your Config.wtf.  That will set it to render in OpenGL which works way better for most people.  I assume you've seen the [Ubuntu wiki article]("https://help.ubuntu.com/community/WorldofWarcraft") but in case you haven't it's very helpful.  The article at WoWWiki is also very good - [http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

I recommend trying the latest version of wine (Wine 1.0-rc1). I've seen a huge performance boost.

I also have seen better performance from the latest beta version of [Nvidia's binary driver]("http://www.nvidia.com/object/linux_display_ia32_173.08.html") (ver 173.08).  Getting it installed isn't too painful but can be frustrating.  Also, I am using an 8800 GT which I know benefits from several fixes in this version that may not apply to your card.

The only other thing I can think of is turning some settings down under the in-game video options.  The ones that seem to affect my framerate the most are terrain distance, texture filtering, weather intensity and clutter density/radius (which I have all the way down for both...who needs clutter anyway?)

Hope this helps!

---

### Post by wererabbit on 2008-05-19
Hi Travelor,

I realize that this probably isn't what you want to hear, but it's meant kindly and in your best interest. 

While the geforce 4100 series was a nice step up from the geforce2mx series, the geforce 6200 is really a slightly upgraded 4100 card, two iterations later.  It's a decent performer in D3D/OpenGL but you would be hard-pressed to find it in most performance gaming systems on the market, even when it was current.

Without other system specs to go on, it sounds to me like you are being limited by the ability of the card to process the amount of data needed to run WoW well. Usually this is typified by the ability to go inside an instance or building and get decent fps, but when outdoors, your fps plummets.   

That said, there are some very (extremely) affordable upgrades on the market for your video card, even on the AGP bus if you're still on an older system.  You need to aim for the 7600/8600/9600 series of budget cards or for the more expensive 6800/7800/8800/9800 series in order to get reasonable to superior OpenGL performance.  Just so you have a perspective on the proportions I'm talking about, in comparison with your 6100, the 6800gt card would run about 3x-5x faster. The 7600gs performs similarly, and the 7800gs/gt cards would be 5x-15x faster in real-world performance than your current card depending on your application.  

I'm not saying your card is bad, I'm saying that it has gone past its prime and isn't suiting your current needs.  :) If you just bought the card, return it and devote your cash to at least a 6800gt or better, you'll be much happier with your system and with WoW performance.

---

### Post by rickggreen on 2008-05-19
I quess I am lucky then, I dual boot (XP, Ubuntu 8.04 64), my install is on the XP partition, so I can run in either system. I am getting better FPS in Ubuntu, usually by 5-15 fps. Lag is always better in linux, around 40 to 50 % less. I am running Wine 1.0 rc. I have also had the same experience running in 8.04  on a 32 bit partition. I have used none of the treaks, just quessing, but are your addons up to date. I had some problems when 2.4.2 came out until I updated them.

---

### Post by dtrot55 on 2008-05-19
> **Syroco said:**
> Okay, I installed that.  But I can't find it :(
Know where it's usually at?


Also, I went into my Nvidia control panel, and it has am openGL optimizer, helped in-game a bit. :)

Still looking to get more of a boost in my fps though. 

Also, does anyone know how to reduce the cursor lag from the result of using openGL?


It will be in your applications menu>game>playonlinux if i remember correctly.

I too am having issues...CSS runs like crap in versions 46 all the way to 1.0.  So far 46 gives me the best performance out of all of them but its not great.  In 46 i get around 30-50FPS..all other versions its 9-20fps.  I am running a 8600GT and I manually installed the Nvidia drivers with no problems.  Also Guildwars doesnt even open in any version of WINE for me so im pretty annoyed with wine at this point.  So I am just going to use Ubuntu as a basic surfing , chatting, music, video machine...its not worth putting forth the effort to try and game on it.

---

### Post by travelor on 2008-05-20
I'll respond to both messages here.

> "travelor,

I notice you don't have SET gxApi "opengl" as part of your Config.wtf. That will set it to render in OpenGL which works way better for most people. I assume you've seen the Ubuntu wiki article but in case you haven't it's very helpful. The article at WoWWiki is also very good - [http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

I recommend trying the latest version of wine (Wine 1.0-rc1). I've seen a huge performance boost.

I also have seen better performance from the latest beta version of Nvidia's binary driver (ver 173.0. Getting it installed isn't too painful but can be frustrating. Also, I am using an 8800 GT which I know benefits from several fixes in this version that may not apply to your card.

The only other thing I can think of is turning some settings down under the in-game video options. The ones that seem to affect my framerate the most are terrain distance, texture filtering, weather intensity and clutter density/radius (which I have all the way down for both...who needs clutter anyway?)

Hope this helps!"

The file I posted was after I attempted to run without OpenGL, so I pulled it off both the config.wtf, and the -opengl from the icon (wow.exe -opengl) I also turned down, not just the settings you listed, but all settings, and it never changed anything. I'm also running the newest wine (and Hardy, which might have something to do with it not working correctly on my end as vent also stopped working, but meh) I didn't try the beta drivers, but at this point I'm going to say screw it and leave it alone. If anything I might reinstall 7.10 and try again later down the road.
	
> Re: FPS in WoW on Ubuntu/Wine worse than in Windows.
Hi Travelor,

I realize that this probably isn't what you want to hear, but it's meant kindly and in your best interest.

While the geforce 4100 series was a nice step up from the geforce2mx series, the geforce 6200 is really a slightly upgraded 4100 card, two iterations later. It's a decent performer in D3D/OpenGL but you would be hard-pressed to find it in most performance gaming systems on the market, even when it was current.

Without other system specs to go on, it sounds to me like you are being limited by the ability of the card to process the amount of data needed to run WoW well. Usually this is typified by the ability to go inside an instance or building and get decent fps, but when outdoors, your fps plummets.

That said, there are some very (extremely) affordable upgrades on the market for your video card, even on the AGP bus if you're still on an older system. You need to aim for the 7600/8600/9600 series of budget cards or for the more expensive 6800/7800/8800/9800 series in order to get reasonable to superior OpenGL performance. Just so you have a perspective on the proportions I'm talking about, in comparison with your 6100, the 6800gt card would run about 3x-5x faster. The 7600gs performs similarly, and the 7800gs/gt cards would be 5x-15x faster in real-world performance than your current card depending on your application.

I'm not saying your card is bad, I'm saying that it has gone past its prime and isn't suiting your current needs. If you just bought the card, return it and devote your cash to at least a 6800gt or better, you'll be much happier with your system and with WoW performance.

I realise my choice of card wasn't the best, but I was shooting for a budget system so my gf could just play the game with me at some point. The system is older yes, but still very good in terms of speed. Small form Compaq D530 - 2.5ghz cpu, 2g ram. Runs Ubuntu, and compiz for all the eye candy that the ladies like, even played videos while out in cube without issue, just can't play any games which is the sore spot. This is also a test system more then anything, as I'd like to make my game pc ubuntu and complete the changeover from win2k. I'll just take the card back to curcuit city (hate buying online, can't stand the waiting...) and try again later. Thanks for the replies.


__________________

---

### Post by justin whitaker on 2008-05-20
You did the OpenGL, but not the Audio hacks from WoWWiki. Do the sound changes as well. It does help with FPS. Also, decrease your draw distance ingame.

---

### Post by fullburned on 2008-05-27
The same problem. But I have ATI Radeon x3450. With Ubuntu 7.10 It run smoothly even better than with WinXP... but now in Ubuntu 8.04 the situation is just awfull...
None of the suggestions works:(
I even removed compiz but it doesn't help:(

---

### Post by Sammi on 2008-05-27
@ fullburned

You have a ATI card, while the OP has an Nvidia. Maybe you have the same symptoms, but I doubt you have the same issue.

If nothing in the guides troubleshooting section helps then your out of luck. ATI just hasn't delivered reliable Linux drivers, though we're expecting this to change now that AMD bought them and are opening up the specs.

---

### Post by keyboardslave on 2008-09-17
same problem here im using beta drivers and i have compiz working perfectly, just getting 12fps in ccs... 0_o, im using a gtx260.

---

### Post by caeroe on 2008-09-17
I've done all the tweaks, reg edits, and whatnot.  I simply just won't get the same performance.  Apparently there are some lucky ones out there that get the same or even better FPS.

WinXP:  60-75+ fps (capped at 75) in Outland and WotLK Beta
Wine:  20-30 fps

I'm disappointed in the lack of gaming for this platform, Wine has done an admirable job.  
Linux will not attract the home users in droves until they get mass acceptance from the gaming industry.  The gaming industry will not bother with Linux until the market is there first.

Will I forever need to dual boot if I want a full gaming library?

---

