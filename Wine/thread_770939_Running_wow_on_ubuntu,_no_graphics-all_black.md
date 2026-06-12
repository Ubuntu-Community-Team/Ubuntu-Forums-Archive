---
title: "Running wow on ubuntu, no graphics-all black"
date: 2008-04-27
forum: Wine
---

### Post by situz on 2008-04-27
I'm totally new to linux, but I've read alot of guides and such on how to get WoW to work on linux Ubuntu. 
for example:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

and I've done everything this guide specify, aswell as the troubleshoot:
[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

I'm running on Ubuntu 8.04 on this computer:
motherboard: Asus M2N32-SLI Deluxe
graphics card: Sapphire Radeon x1900XT
cpu: AMD Athlon 64 X2 4600+

here's a screenshot of how wow looks like when i run it:
[IMG]http://img115.imageshack.us/img115/245/screenshotvo5.png[/IMG]

when i try running wow with d3d i get a wow error upon startup. 
if i run wow without these following lines in the config.wtf, the whole screens turns black, but the music is going, which means the game is running:
> SET ffxDeath "0"
SET ffxGlow "0"

what can be wrong? :(

Thanks in advance for any help!

---

### Post by rickggreen on 2008-04-27
You did not say which version of wine you are running,I run 60. I have a different graphics card and am running at 1660 / 1050 and had a similiar problem. Fixed by setting dpi to 125 in the wine config under the graphics tab.

---

### Post by Woody1987 on 2008-04-27
are you running the game in opengl or direct3d? You should be running in opengl, to do so open a terminal and go to the folder

```
cd /home/USERNAME/.wine/drive_c/Program\ Files/World\ of\ Warcraft/
```

then run

```
wine Wow.exe -opengl
```

---

### Post by situz on 2008-04-28
thanks for the replies!

to answer rickggreen first:
I got version 59 of wine, I tried to upgrade it to 60 by firstly uninstalling it with the "add/remove" tool under "applications", then following the instructions on this page:
[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

after doing so, I checked the "about" tab on winecfg, and it said version 0.9.59 still. weird, did I do it wrong? 

anyway, I tried to set the Dpi to 125 on the "graphics" tab, like you said. it didn't fix the problem:(

too woody1987: I'm running wow with opengl, by using this setting in the config.wtf file:
> SET gxApi "opengl"

if I set it to "d3d" instead, I get a wow error, obviously.

thanks again, in advance for any help =)

EDIT: Suddenly the update manager prompted me to update wine, so Its updated to version 60 now, and the dpi is set to 125, and I still have the same problem :\ 

there must be something wrong with the graphics driver, I haven't installed any driver except what Ubuntu have prompted me to.

EDIT 2: I installed this program: [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)
then it installed the correct graphics driver, so that should work correctly now. 
after a reboot i checked wow again, and i STILL have the same problem! :(
*getting frustrated*

---

### Post by situz on 2008-04-28
YES I finally found a solution to this problem!
I found a guy on this page who had the same problem:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11329)

the fix is simply just to add this line in the config.wtf file:
> SET M2UseShaders "0"

thanks anyway for the help! =)

---

### Post by The Squig on 2008-04-28
exactly the same problem here. Im on a x1950 pro card. Not sure which version of wine tho. 

If I start the game without the opengl switch I dont get the blackness but then I dont get no login in window neither.

edit:

SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0" 

yep these settings fixed it. well, performance was pretty much cut by half compared to Windows but that was expected (still playable tho and if i reduce graphix itll run smooth I think. I had given up hope on getting this to work with my ati card :D

---

### Post by situz on 2008-04-28
try to add/change these settings in your config.wtf file:
> SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET UIFaster "2"
SET M2UseShaders "0"

You should run it in Opengl.
I've also posted all the steps I've gone through earlier in this topic, so I suggest you try those, and if you still have the problem, I honestly don't know what can be wrong:P 

anyway I figured I'd post a screen shot of how wow runs now =) this is my alt btw:
[IMG]http://img405.imageshack.us/img405/4712/screenshot1ae9.png[/IMG]

I get a pretty nice frame rate actually, all graphics settings are set to max, and resolution is 1280x1024.
the fps on this screen is approximately how low it goes down when I'm in IF. 
seems the conversion to Linux was really worth it! I LOVE LINUX <3

---

### Post by situz on 2008-04-28
> **The Squig said:**
> exactly the same problem here. Im on a x1950 pro card. Not sure which version of wine tho. 

If I start the game without the opengl switch I dont get the blackness but then I dont get no login in window neither.

edit:

SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0" 

yep these settings fixed it. well, performance was pretty much cut by half compared to Windows but that was expected (still playable tho and if i reduce graphix itll run smooth I think. I had given up hope on getting this to work with my ati card :D

Regarding your bad performance I have a few question, which might help you:

- have you used EnvyNG to get the correct drivers for your graphics card?:
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

- have you done the "registry boost" for better fps?:
[https://help.ubuntu.com/community/WorldofWarcraft#head-4b2ddfc20b64caffa3c5fbfad67a0480440ccad2](https://help.ubuntu.com/community/WorldofWarcraft#head-4b2ddfc20b64caffa3c5fbfad67a0480440ccad2)

- have you installed the dll files mentioned here?:
[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting#head-7a7b1babed59c98107504cc424f08fe7d7aeac7b](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting#head-7a7b1babed59c98107504cc424f08fe7d7aeac7b)

---

### Post by thisismalhotra on 2008-04-28
WHoa guys thanks for the fix, I came here to post the same issues  LOL

I did clean install of hardy over the weekend and I had the same issue as the OP. I will check if the fix works tonight. I have already moved to ubuntu on my desktop and the only reason I still had XP on my laptop was WoW.

Btw I have Gateway MT3705 with ATI xpress 200M(You'll be surprised wow works on that too .. LOL)

---

### Post by situz on 2008-04-28
hehe
let me know how it works out for ya =)

---

### Post by The Squig on 2008-04-28
Ok ive done the registry tweak now and im running the game in its own xserver session. Huge boost. still not quite as fast as win xp but not so far from that. 

Also checkd my wine version and its 0.9.60

---

### Post by thisismalhotra on 2008-04-29
> **situz said:**
> hehe
let me know how it works out for ya =)

Unfortunately I have done everything on this thread and on the troubleshooting page.

My graphic will stutter and is very bad. PLS HELPSee Screenshot)

Here is my config.wtf

```
SET ffxGlow "0"
SET locale "enUS"
SET hwDetect "0"
SET UIFaster "2"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x800"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET SmallCull "0.010000"
SET DistCull "500.000000"
SET farclip "777"
SET movie "0"
SET expansionMovie "0"
SET Gamma "1.000000"
SET readTOS "1"
SET readEULA "1"
SET realmList "us.logon.worldofwarcraft.com"
SET gameTip "83"
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
SET Sound_VoiceChatInputDriverIndex "1"
SET Sound_VoiceChatOutputDriverIndex "1"
SET Sound_OutputDriverIndex "1"
SET realmName "Zul'jin"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET gxWindow "1"
SET checkAddonVersion "0"
SET lastCharacterIndex "1"
SET mapShadows "0"
SET gxApi "OpenGL"
```

Here is my xorg.conf

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
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Option 		"Capabilities" "0x00000800"
 	Option 		"UseFastTLS" "2"
 	Option 		"KernelModuleParm" "locked-userpages=0"
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

---

### Post by situz on 2008-04-29
hmm, looks like there is some error with the way wine is handling the game text. I found a guy with the same problem as you:
[http://img216.imageshack.us/img216/6558/wowerrorju6.jpg](http://img216.imageshack.us/img216/6558/wowerrorju6.jpg)

and it is said that the bug happens when you move from an indoor place, to an outdoor place, can you comfirm this?

anyway a guy said a workaround is to log out and in each time the text screws up. 

but it might have something todo with the dll files:
riched20.dll and riched32.dll , are you sure you installed these dll files, and wrote over the old ones?

---

### Post by thisismalhotra on 2008-04-29
> **situz said:**
> hmm, looks like there is some error with the way wine is handling the game text. I found a guy with the same problem as you:
[http://img216.imageshack.us/img216/6558/wowerrorju6.jpg](http://img216.imageshack.us/img216/6558/wowerrorju6.jpg)

and it is said that the bug happens when you move from an indoor place, to an outdoor place, can you comfirm this?

anyway a guy said a workaround is to log out and in each time the text screws up. 

but it might have something todo with the dll files:
riched20.dll and riched32.dll , are you sure you installed these dll files, and wrote over the old ones?

Yes I confirm that cause sometime when I log in the game it is fine but as soon as I move into the in or something .. it craps up on me. If I have to log out each and everytime that is just nor working out as lot of dungeons, raid etc etc are indoors.

I did copy the riched20 & 32 from winxp to wine in ubuntu.. any clues...

EDIT: Hey Situz, if you dont mind can you post/upload your config.wtf & xorg.conf and I will try using that tonight and see if that works.(I assume you are on the latest patch)

I have nvidia 8800GT on my desktop and WoW runs flawlessly on that (even better than XP/vista)without all these chages but IDK why ATi just sucks at it..... :(

---

### Post by situz on 2008-04-29
> **thisismalhotra said:**
> Yes I confirm that cause sometime when I log in the game it is fine but as soon as I move into the in or something .. it craps up on me. If I have to log out each and everytime that is just nor working out as lot of dungeons, raid etc etc are indoors.

I did copy the riched20 & 32 from winxp to wine in ubuntu.. any clues...

EDIT: Hey Situz, if you dont mind can you post/upload your config.wtf & xorg.conf and I will try using that tonight and see if that works.(I assume you are on the latest patch)

I have nvidia 8800GT on my desktop and WoW runs flawlessly on that (even better than XP/vista)without all these chages but IDK why ATi just sucks at it..... :(

I understand that it's really gonna suck to have to log in and out each time that happens, but you could try /console reloadui instead of logging out/in.

you said you copied the dll files from your winxp installation to wine in ubuntu? you have to download the dll, because I assume they have some differences. anyway the correct dll files can be found here:
[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting#head-7a7b1babed59c98107504cc424f08fe7d7aeac7b](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting#head-7a7b1babed59c98107504cc424f08fe7d7aeac7b)

to be honest I don't think the problem lies in the config.wtf file and the xorg.conf file, but I uploaded the files in a zip now. 

Gool luck mate :guitar:

---

### Post by The Squig on 2008-04-29
> **situz said:**
> hmm, looks like there is some error with the way wine is handling the game text. I found a guy with the same problem as you:
[http://img216.imageshack.us/img216/6558/wowerrorju6.jpg](http://img216.imageshack.us/img216/6558/wowerrorju6.jpg)

and it is said that the bug happens when you move from an indoor place, to an outdoor place, can you comfirm this?

anyway a guy said a workaround is to log out and in each time the text screws up. 

but it might have something todo with the dll files:
riched20.dll and riched32.dll , are you sure you installed these dll files, and wrote over the old ones?

I had graphic bugs like in that image until I ran the game in its own xerver session.

example (gnome: stop gdm):
```
sudo /etc/init.d/gdm stop
```

then to start the game from the console:
```
sudo startx `which wine` wow.exe
```

also gave me a big speed boost.

---

### Post by willc0de4food on 2008-04-30
> **The Squig said:**
> I had graphic bugs like in that image until I ran the game in its own xerver session.

example (gnome: stop gdm):
```
sudo /etc/init.d/gdm stop
```

then to start the game from the console:
```
sudo startx `which wine` wow.exe
```

also gave me a big speed boost.

the game wont run for me via this method. after executing the startx command it starts to open a session and then closes immediately and goes back to the cli.

---

### Post by thisismalhotra on 2008-04-30
> **willc0de4food said:**
> the game wont run for me via this method. after executing the startx command it starts to open a session and then closes immediately and goes back to the cli.

Me neither guys I am still stuck with those graphics ... can anybody think of anything else.

---

### Post by thisismalhotra on 2008-04-30
> **situz said:**
> I understand that it's really gonna suck to have to log in and out each time that happens, but you could try /console reloadui instead of logging out/in.

you said you copied the dll files from your winxp installation to wine in ubuntu? you have to download the dll, because I assume they have some differences. anyway the correct dll files can be found here:
[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting#head-7a7b1babed59c98107504cc424f08fe7d7aeac7b](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting#head-7a7b1babed59c98107504cc424f08fe7d7aeac7b)

to be honest I don't think the problem lies in the config.wtf file and the xorg.conf file, but I uploaded the files in a zip now. 

Gool luck mate :guitar:

Thanks Man,

I did download the dll's and it still is the same ... any clues.. I did everything I could find online ... but still the same issues. Even if I am outdoor most of the time ... it will stutter after few mins of playing ...

---

### Post by thisismalhotra on 2008-05-02
/bump

HELP PLEASEEEEEEEEEEEEEEEEEEEE :(

---

### Post by situz on 2008-05-02
tbh mate I can't think of anything that can fix your problem. sorry

---

### Post by Tsume on 2008-05-04
Until someone figures this out, I find the best option to be

/console gxrestart

Reloads the graphics engine and the text is back, WITHOUT relogging.

And here I thought the problem was my crappy Intel 910 GMA :)

---

### Post by Dreamlocked on 2008-05-09
I got the no text-graphical corruption as well.

I posted this on [phoronix]("http://www.phoronix.com/forums/showthread.php?t=9581") as well.

Can anyone post there to confirm that this line appears in Xorg.0.log once you encounter the graphical bug?
```

Warning: LookupDrawable()/SecurityLookupDrawable() are deprecated.  Please convert your driver/module to use dixLookupDrawable().

```

---

### Post by Braytok on 2008-05-30
I used to have the same problem with indoor game crash.

Found this addon on wowinterface.com

[http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html](http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html)

Solved my problem.

I'm running Ubuntu 8.04 on a Sempron 2600 with an ATI Radeon 9600.

---

### Post by taavi on 2008-08-31
Thank you very much situz!

*SET M2UseShaders "0" *

worked for me. Although FPS is not the best it's playable. I hope it works in instas and battlegrounds -- although if it doesn't, then I must have dual boot for windows still.

PS! Strange is that minimap is white, not showing map...

EDIT: Well, minimap works strangely, sometimes it shows map, sometimes it's transparent and shows whatever is underneath it, sometimes it's white.

---

### Post by IdentityPrime on 2008-10-23
Hi, I had this problem yesterday then I got it to work..

now the only problem I have is about after 10 seconds of walking around my graphics go crazy.. I get screen tears and glitches and it looks like someone is breaking my monitor..

Any idea how to fix this?

---

### Post by duncan_nz on 2008-11-08
I'm having the same issues, on ubuntu 8.10 with ati drivers from ubuntu repos.

Every time I go inside in the game, it goes all crazy on the bottom left hand side!

---

### Post by situz on 2008-11-12
> **duncan_nz said:**
> I'm having the same issues, on ubuntu 8.10 with ati drivers from ubuntu repos.

Every time I go inside in the game, it goes all crazy on the bottom left hand side!

i have the same problem now, searching the web for fixes, but no luck yet..
please post here if you find a fix!

---

