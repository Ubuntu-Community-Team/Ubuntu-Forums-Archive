---
title: "2-8 FPS in WoW outdoors"
date: 2008-01-21
forum: Wine
---

### Post by aliencam on 2008-01-21
most of the post is just information to document every single possible problem/solution. it is usually unnecessary to read my entire post. usually the "summary" at the top will do.  

[B]

Summary:[/B]

WoW works at only 2-6  FPS, sometimes 8 when I am standing still.  I have tried all the FPS tweaks, and the registry hack.  and  the --opengl flag.  
while writing this post, i started a new undead character, and indoors in the starting area i was getting 35 FPS, but when I walk outside it instantly goes down to 2-6. 

in glxgears i get around 1000 FPS with compiz off, and 500 with compiz on (watching the gears, not minimized) 

[B]
My Computer's Specs[/B]

Lenovo x61 Tablet
Ubuntu Gutsy 7.10
Video Card: Intel Graphics Media Accelerator X3100 (compatible with open gl 1.5) 
Intel Core 2 Duo 1.8 (L 7700)
3 GB DDR2 PC5200



**What I have done (or, what might have caused the problem), or "a history of WOW on my computer":**

installed wine from

```
sudo apt-get install wine
```

(but I did not add the winehq repository, i just added it from whatever is in the normal (enabled everything) ubuntu repos. ) (or i might have installed from add/remove programs/synaptic)

started off installing WOW with WINE and no extra config. it ran at 2 FPS.

i did the registry hack for opengl

added the following to config.wtf:

```
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
```

wow opened, but there were no models at all, the only thing I could see was the environment (no characters/plants/ anything else) wow ran at 2 FPS still

Installed Cedega, installed WOW in Cedega, same framerate. Uninstall WOW in Cedega, uninstall Cedega, back to WINE.

I removed

```

SET gxApi "opengl"
```

from config.wtf

WOW ran at 2 FPS again, just like it did the first time. still unplayable.

googled for awhile, found [http://www.wowwiki.com/Linux/Wine/Troubleshooting](http://www.wowwiki.com/Linux/Wine/Troubleshooting)

added back to config.wtf

```

SET gxApi "opengl"
SET M2UseShaders "0"
```

WOW ran semi-usably, at 8 FPS (usable for 15 minutes until I go crazy)

so I tried running the script to run WOW on it's own x server, it did not work. all I ever got was an empty X window, and I switched back to X-0 with ctrl-alt-f7



notes:
ASLA sound works fine. I can hear sound. I would rather not switch WINE to OSS, or add the

```

SET SoundOutputSystem "1"
SET SoundBufferSize "150"

```
lines to config.wtf. (because those only control sound as far as I know, and my sound works fine)

[B]
Config.WTF file:[/B]


```
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET SmallCull "0.080000"
SET DistCull "350.000000"
SET frillDensity "8"
SET farclip "400.000000"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET realmList "us.logon.worldofwarcraft.com"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET coresDetected "2"
SET videoOptionsVersion "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET patchlist "us.version.worldofwarcraft.com"
SET realmName "Draenor"
SET gameTip "6"
SET ffxDeath "0"
SET ffxGlow "0"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET mouseSpeed "1"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "1"
SET UberTooltips "0"
SET M2UseShaders "0"
SET gxApi "opengl"
SET textureFilteringMode "0"


```


**Terminal Log from when WOW was working at low FPS:**
(it's the same output if i run it with the --opengl flag also) 
```

cameron@camubuntux61tab:~$ '/home/cameron/.wine/drive_c/Program Files/World of Warcraft/Wow.exe' 
ALSA lib ../../src/conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed84,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34ecac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f40c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f580,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f55c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34f124,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:reg:GetNativeSystemInfo (0x374029c4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x7d49c4a4) stub!
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x34d1a4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34d200,0x00000000), stub!
fixme:imm:ImmAssociateContextEx (0x20024, (nil), 16): stub

```

---

### Post by Meow27 on 2008-01-22
as a general reply, this might be a gfx card driver issue but dont take my word for it. i dont really know the asnwer

---

### Post by aliencam on 2008-01-22
i don't know, it could be a  driver issue.  the video card (s)? chosen by default in the screen preferences menu are 

graphics card (VESA Driver (generic))> choose by name>" intel- experimental modesetting driver for I..." (the rest is unreadable) 

and
Graphics Card (VESA Driver (generic))> choose by name>  "vesa- Generic VESA -compliant video cards" 

i don't know if that means I have 2 detected video chips? (im on a laptop with integrated) or if the second is a backup driver. 

but thinkwik says "There is a Graphics driver for the Mobile Intel 965 Express Chipset Family at Intels Support Site. This driver is just a snapshot of the Xorg/XFree86 driver." 

thinkwiki link: [http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_X3100](http://www.thinkwiki.org/wiki/Intel_Graphics_Media_Accelerator_X3100)

IBM link: [http://downloadcenter.intel.com/Filter_Results.aspx?strTypes=all&ProductID=2301&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/Filter_Results.aspx?strTypes=all&ProductID=2301&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)


i'll try changing the top driver to choose by model> intel>965...

---

### Post by aliencam on 2008-01-22
that did not work.  changing my driver to the 965 chipset driver (which is the chipset I have) messed up everything, and I was unable to see anything.  trying to get everything fixed messed up my xorg.conf, and made 8 new ones (xorg.conf1-xorg.conf7)  and i ended up having to reconfigure my whole xorg.conf (i have a tablet pc, and setting up the pen/tablet/extra mouse buttons and the trackpoint is a pain) 

anyway, changing the video driver to what i thought it should be just messed up the display totally.... maybe i should reinstall xorg??? my driver is included in all x.org versions since 2.0 according to intel's site.

---

### Post by mumixam on 2008-01-22
hey, i have almost the same problemm with the same x3100, only my game doesn't start in opengl at all saying - World of Warcraft was unable to start 3d acceleration.

If you read through the forums here you'l soon find out that x3100 users are doomed if they are to play wow in ubuntu unntil intell releases proper drivers for linux distr.

---

### Post by ryansinn on 2008-02-20
I've been playing around with getting WoW to work well ... 

I'm running Hardy 8.04 64-bit ... Wine 0.9.55 is currently broken so I had to test with Codeweavers' Crossover to test... but the performance on my Lenovo ThinkPad X61t model 776898U with an integrated X3100 graphics card is poor.  If I look straight down with the camera view I can get 18fps but that's the best.

I've found a way to lower the graphics settings to just about as low as they can go ... and you can get 4fps, but the graphics quality is just garbage.

When I run World of Warcraft in Windows Vista I get 18fps to 30fps... so there is hope for the card and we know the issue is with the emulation or the video drivers...

Hopefully we can tweak these as a good and get some better performance.

```

SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET SmallCull "0.040000"
SET useWeatherShaders "0"
SET weatherDensity "0"
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET DistCull "350.000000"
SET frillDensity "8"
SET particleDensity "0.400000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET realmList "us.logon.worldofwarcraft.com"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET coresDetected "2"
SET videoOptionsVersion "1"
SET showToolsUI "0"
SET Sound_OutputDriverName "System Default"
SET gameTip "16"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET EnableMicrophone "0"
SET MusicVolume "0.60000002384186"
SET SoundVolume "1"
SET MasterVolume "1"
SET ffx "0"
SET AmbienceVolume "0.60000002384186"
SET uiScale "1"
SET mouseSpeed "1"
SET cameraPitchMoveSpeed "90"
SET cameraYawMoveSpeed "180"
SET cameraPitchSmoothSpeed "45"
SET cameraYawSmoothSpeed "180"
SET cameraSmoothStyle "0"
SET cameraSmoothTrackingStyle "0"
SET cameraDistanceMaxFactor "1"
SET SoundZoneMusicNoDelay "1"
SET statusBarText "1"
SET minimapZoom "0"
SET guildMemberNotify "1"
SET profanityFilter "0"
SET minimapInsideZoom "5"
SET Gamma "1.000000"
SET fullAlpha "1"
SET mapShadows "0"
SET shadowLevel "0"
SET unitDrawDist "200.000000"
SET farclip "177"
SET lod "1"
SET MaxLights "1"
SET baseMip "1"
SET spellEffectLevel "6"
SET groundEffectDist "20"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET rotateMinimap "1"
SET textureFilteringMode "0"
SET cameraView "0"
SET TerrainMip "1"
SET lodDist "50"
SET doodadAnim "0"

```

The UI in WoW is working 100% and everything draws properly.

If you want to up the level of quality change these:
```

SET lod
SET lodDist
SET TerrainMip
SET farclip

```

The big deal being TerrainMip and the "clip" settings

Also the "lodDist" is the distance at which the quality is reduced.

For what I would consider "average" video quality (low resolution though) would be this config

```

SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET SmallCull "0.040000"
SET useWeatherShaders "0"
SET weatherDensity "0"
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET DistCull "350.000000"
SET frillDensity "32"
SET farclip "357"
SET particleDensity "1.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET realmList "us.logon.worldofwarcraft.com"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET coresDetected "2"
SET videoOptionsVersion "1"
SET lastCharacterIndex "2"
SET showToolsUI "0"
SET Sound_OutputDriverName "System Default"
SET patchlist "us.version.worldofwarcraft.com"
SET gameTip "62"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET EnableMicrophone "0"
SET MusicVolume "0.60000002384186"
SET SoundVolume "1"
SET MasterVolume "1"
SET ffx "0"
SET AmbienceVolume "0.60000002384186"
SET uiScale "1"
SET mouseSpeed "1"
SET cameraPitchMoveSpeed "90"
SET cameraYawMoveSpeed "180"
SET cameraPitchSmoothSpeed "45"
SET cameraYawSmoothSpeed "180"
SET cameraSmoothStyle "0"
SET cameraSmoothTrackingStyle "0"
SET cameraDistanceMaxFactor "1"
SET SoundZoneMusicNoDelay "1"
SET statusBarText "1"
SET minimapZoom "0"
SET guildMemberNotify "1"
SET profanityFilter "0"
SET minimapInsideZoom "5"
SET Gamma "1.000000"

```

The graphics look alright with the Config.wtf directly above, but the fps is 2fps unless you're looking down... the second you see the horizon the framerate becomes unbearable.

---

### Post by norsk on 2008-03-05
In the beginning of February it looks like Intel release documentation on how to write drivers for the x3100 GPU:

[http://www.phoronix.com/scan.php?page=article&item=984&num=1](http://www.phoronix.com/scan.php?page=article&item=984&num=1)
[http://intellinuxgraphics.com/index.html](http://intellinuxgraphics.com/index.html)

So aside from that, the Intel lists instructions on how to install latest drivers, has anyone tried this or are these the same drivers that I'd have anyways?

[http://intellinuxgraphics.com/install.html](http://intellinuxgraphics.com/install.html)

---

### Post by aliencam on 2008-03-05
this is the first I've ever heard of new drivers... i'll have to check it out.  maybe today isn't such a good idea though, midterms galore.

---

### Post by Resonance378 on 2008-03-05
in all of this a specific wine version is never mentioned.

at command:  wine --version

what is it?

Shouldn't matter throughout the long run of this issue as it sounds like it is a intel graphics driver issue with their X3100.

And according to information on a bug report I recently filed for WoW in -opengl ... Wine does a 1 for 1 translation of OpenGL

---

### Post by norsk on 2008-03-05
Although I am an extremely novice Linux user, I am almost positive this is an X3100/Intel Driver issue, and not so much a Wine issue.  It's too bad this thread was started in the Wine forums but this is the only post I have found where I can at least communicate with a few other people with identical problems as mine.

And as far as those drivers go, I am, as I said, extremely novice when it comes to Linux and I do not fully understand the directions to install those drivers on my own by following the directions on the link I submitted.  I'd be very grateful for some instructions on how to do so though, I am able to get as far as downloading those 3 packages but I am confused about why there are 3 separate ones and the division of them from 2d/3d etc.

I might give it another go when I have some time, but my last foray into the unknown force me to reformat my Linux partition :guitar:

---

### Post by aliencam on 2008-03-06
I put this in the WINE folder because at the time i didn't realize it was a driver issue.  and it does involve wine to a certain extent. I'll be trying this out after midterms friday.

---

### Post by Resonance378 on 2008-03-06
good luck with it and let us know how it goes

I'd be more than happy to help but I don't have the hardware you do so I can only offer advice on within the context of what I've been doing.

---

### Post by norsk on 2008-03-06
Awesome sounds good, good luck with exams.

---

### Post by aliencam on 2008-03-09
> **norsk said:**
> In the beginning of February it looks like Intel release documentation on how to write drivers for the x3100 GPU:

[http://www.phoronix.com/scan.php?page=article&item=984&num=1](http://www.phoronix.com/scan.php?page=article&item=984&num=1)
[http://intellinuxgraphics.com/index.html](http://intellinuxgraphics.com/index.html)

So aside from that, the Intel lists instructions on how to install latest drivers, has anyone tried this or are these the same drivers that I'd have anyways?

[http://intellinuxgraphics.com/install.html](http://intellinuxgraphics.com/install.html)

hey your URLs are wrong :P  it's intellinuxgraphics.**org** not .com.  that took me forever to figure out lol...

---

### Post by norsk on 2008-03-09
Oh weird those links have changed since I put them up there.  [http://intellinuxgraphics.com/](http://intellinuxgraphics.com/) was a sight before but apparently it has been replaced by [http://www.moblin.org/](http://www.moblin.org/) which is a completely different sight entirely (but looks like it is now a sight dedicated to the deveopment of intel-based products in a linux environment)

---

### Post by norsk on 2008-03-09
On that note [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/) is the old site that I was referring to whereas the moblin.org site I think might be dedicated to a different platform of intel linux devices.

---

### Post by aliencam on 2008-03-09
yeah i figured that out.  i'm in the middle of the process, but i'm having a problem compiling because of this error: 

No package 'xvmc' found
No package 'fontsproto' found


no luck on google, or on the forums so far, so I made a new topic. waiting for a reply to that one.

---

### Post by norsk on 2008-03-09
I really don't  know what I'm doing here, but I'm trying to follow various guides including this one: [http://dri.freedesktop.org/wiki/Building#head-b3fb665c9f24b4a32424b78428c082e830832250](http://dri.freedesktop.org/wiki/Building#head-b3fb665c9f24b4a32424b78428c082e830832250)

I'm as far as this: > $ sudo apt-get install git-core
$ sudo git-clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel
$ sudo git-clone git://anongit.freedesktop.org/git/mesa/drm
$ sudo git-clone git://anongit.freedesktop.org/git/mesa/mesa
$ sudo apt-get install autoconf
$ sudo apt-get install automake


But am now receiving this error when I run drm$: sudo ./autogen.sh --prefix=/opt/xorg > ~/drm$ sudo ./autogen.sh --prefix=/opt/xorg
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.ac: tracing
autoreconf: configure.ac: not using Libtool
autoreconf: running: /usr/bin/autoconf
configure.ac:28: error: possibly undefined macro: AC_DISABLE_STATIC
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:29: error: possibly undefined macro: AC_PROG_LIBTOOL
autoreconf: /usr/bin/autoconf failed with exit status: 1
jensbodal@vostro1400:~/drm$ sudo ./autogen.sh --prefix=/opt/xorg
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.ac: tracing
autoreconf: configure.ac: not using Libtool
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
configure.ac:24: installing `./missing'
configure.ac:24: installing `./install-sh'
libdrm/Makefile.am:21: Libtool library used but `LIBTOOL' is undefined
libdrm/Makefile.am:21:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
libdrm/Makefile.am:21:   to `configure.ac' and run `aclocal' and `autoconf' again.
libdrm/Makefile.am:21:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
libdrm/Makefile.am:21:   its definition is in aclocal's search path.
libdrm/Makefile.am: installing `./depcomp'
tests/Makefile.am:9: Libtool library used but `LIBTOOL' is undefined
tests/Makefile.am:9:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
tests/Makefile.am:9:   to `configure.ac' and run `aclocal' and `autoconf' again.
tests/Makefile.am:9:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
tests/Makefile.am:9:   its definition is in aclocal's search path.
autoreconf: automake failed with exit status: 1


---

### Post by aliencam on 2008-03-09
I got past your errorby not adding the -prefix=/opt/xorg to the autogen.sh, but i'm still stuck on my error :(

---

### Post by norsk on 2008-03-09
Still get errors if I remove that :( > jensbodal@vostro1400:~/drm$ sudo ./autogen.sh 
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.ac: tracing
autoreconf: configure.ac: not using Libtool
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
libdrm/Makefile.am:21: Libtool library used but `LIBTOOL' is undefined
libdrm/Makefile.am:21:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
libdrm/Makefile.am:21:   to `configure.ac' and run `aclocal' and `autoconf' again.
libdrm/Makefile.am:21:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
libdrm/Makefile.am:21:   its definition is in aclocal's search path.
tests/Makefile.am:9: Libtool library used but `LIBTOOL' is undefined
tests/Makefile.am:9:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
tests/Makefile.am:9:   to `configure.ac' and run `aclocal' and `autoconf' again.
tests/Makefile.am:9:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
tests/Makefile.am:9:   its definition is in aclocal's search path.
autoreconf: automake failed with exit status: 1


---

### Post by norsk on 2008-03-09
Ok had to run sudo apt-get install libtool to get past that error, so I guess I'll see where this takes me

---

### Post by norsk on 2008-03-12
Any luck?

---

### Post by aliencam on 2008-03-14
no luck here, i can't get the actual driver installed, i still get 
```

No package 'xvmc' found
No package 'fontsproto' found
```


so i'm right in the middle of everything ,and this really is terrable because now all my accelerated graphics are disabled, so I can't use compiz.  

i got drm and mesa installed fine, but i can't build the xf86-video-intel driver because of the error above.  nobody ever posted a reply to the topic i made.  

ugh these forums are all about timing now.  impossible to ever get a reply because they're so busy... everyone just make sure to reply to anything you know to help make these forums a better place please.

---

### Post by norsk on 2008-03-17
Well I'm going to put this on the backburner for now, school > linux.  Hopefully something will change when version 8 comes out for the distro.

---

### Post by aliencam on 2008-03-19
> **norsk said:**
> Well I'm going to put this on the backburner for now, school > linux.  Hopefully something will change when version 8 comes out for the distro.

yeah probably a good idea lol.  are you able to have compiz working still though? evrything is messed up for me without it (i have a bunch of screenlets running and they don't play well without compiz working...)

---

### Post by donnyblaze1 on 2008-03-19
Hey guys, just wanted to chime in with some good news on the X3100 front.  Check out my post here [http://ubuntuforums.org/showthread.php?t=579378&page=150]("http://ubuntuforums.org/showthread.php?t=579378&page=150").  I've gotten WoW to run with those settings very reasonably on my X3100.  Still not perfect, but it is definitely useable, and I'm sure it will only get better with some decent drivers.

Don't give up on the ol' 965 just yet :)

---

### Post by aliencam on 2008-03-21
wow sounds good, i didn't try it yet, i still have to fix all my problems, i currently can't do ANYTHING graphical because i'm in the middle of the driver update and everything is broken... if anyone knows how to "roll back" (i know it's not that easy) that would be awesome... 


just to clear up any mis-linking or confusion, i believe the post he was referring to is quoted here (in a "code" box so we don't have huge scrolling) 

```
> **donnyblaze1 said:**
> After some more playing, I'm happy to report that WoW is now fully functional and playable on my X3100!  Of course, there is some room for improvement on the performance side...but I just finished running 15 3v3 arena rounds with no problems whatsoever.  Performance is comparable (+/- 10-15% fps) to WoW on same hardware in XP.  (Yes, I know its an apples to oranges comparison, but just to give others an idea.)

I do have a couple questions for the experts here, but first let me post the info others will need to duplicate my results on X3100 hardware.

System specs:

Sony Vaio VGN-NR110E
Pentium Dual Core
1GB RAM
Intel X3100 gfx
Xubuntu Gutsy
wine 0.9.29 (I have tried literally every version of wine from 0.9.47 backwards, .29 is the only version that will launch WoW without Error  132.  0.9.29 also fixed the earlier problem I had with no characters or NPCs, I am still looking into the underlying reasons for this.)
World of Warcraft:  Applytoforehead add-on installed, along with my standard compliment of UI add-ons (mainly PhotekUI X7).

winecfg settings:

Windows Version:  Windows XP
Window settings:  Allow DirectX apps to stop the mouse...UNCHECKED
Allow the window manager to control...UNCHECKED
Virtual desktop...UNCHECKED
D3D Vertex Shader Support:  Hardware
Allow Pixel Shader...UNCHECKED
Audio:  OSS Driver
DirectSound Hardware Acceleration: Emulation
Driver Emulation...UNCHECKED
Well-documented OpenGL registry tweak applied

Config.wtf:

SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x800"
SET gxRefresh "60"
SET gxFixLag "0"
SET gxMultisampleQuality "0.000000"
SET lod "1"
SET SmallCull "0.070000"
SET DistCull "350.000000"
SET shadowLOD "0"
SET frillDensity "48"
SET farclip "177"
SET particleDensity "0.900000"
SET unitDrawDist "300.000000"
SET movie "0"
SET expansionMovie "0"
SET Gamma "1.000000"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "0"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "1"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET realmName "Mug'thol"
SET gameTip "27"
SET AmbienceVolume "0.60000002384186"
SET minimapInsideZoom "0"
SET uiScale "0.81000000238419"
SET useUiScale "1"
SET checkAddonVersion "0"
SET MasterSoundEffects "0"
SET EnableMusic "0"
SET EmoteSounds "0"
SET SoundListenerAtCharacter "0"
SET minimapZoom "0"
SET CombatDamage "0"
SET CombatHealing "0"
SET mouseSpeed "1"
SET profanityFilter "0"
SET cameraYawMoveSpeed "90"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "2"
SET statusBarText "1"
SET UnitNameNPC "1"
SET cameraDistanceMoveSpeed "15"
SET targetNearestDistanceRadius "22"
SET targetNearestDistance "44"
SET UnitNamePlayerPVPTitle "0"
SET cameraView "0"
SET coresDetected "2"
SET readTerminationWithoutNotice "1"
SET Sound_OutputDriverName "System Default"
SET movieSubtitle "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.60000002384186"
SET Sound_AmbienceVolume "0.69999998807907"
SET weatherDensity "3"
SET ChatMusicVolume "0.5"
SET ChatSoundVolume "0.5"
SET ChatAmbienceVolume "0.5"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET EnableVoiceChat "1"
SET PushToTalkButton "'"
SET anisotropic "4"
SET Sound_EnableErrorSpeech "0"
SET Sound_ZoneMusicNoDelay "1"
SET readScanning "-1"
SET readContest "-1"
SET videoOptionsVersion "1"
SET textureFilteringMode "0"
SET groundEffectDensity "64"
SET groundEffectDist "140"
SET processAffinityMask "3"
SET accountName "xxxxxxx"
SET DesktopGamma "1"
SET ffxDeath "0"
SET ffxGlow "0"

Things that still need work:

1) I run wow.exe with no arguments, in assumed D3D mode.  Using the -opengl argument yields terribad graphical results (everything is discolored, artifacts hopping all over the screen, only upper torso of characters show on screen).  I assume this is because of poor OpenGL implementation in either the "intel" driver or the hardware itself, but if anyone has any tips here please chime in.  I'd prefer to run in native OpenGL mode to prevent the D3D overhead. Using -opengl does seem to run faster and more fluidly than D3D, the graphical errors just make it unplayable.

2) Double cursors!  Running WoW in full-screen mode I have 2 cursors...my regular X cursor and the Warcraft "glove" cursor following along behind it ever-so-slightly.  It really doesn't impact play too much, but it is definitely an annoyance.

3) Terminal output.  Not sure if this is an "error" or not, but my while running WoW, my terminal fills up with
[CODE]fixme:d3d:IWineD3DQueryImpl_Issue (0x1190edb8) : Occlusion queries not supported.
fixme:d3d:IWineD3DQueryImpl_GetData (0x1190edb8) : Occlusion queries not supported. Returning 1.
```
Is this anything to worry about?

To summarize:
I'm very pleased to be running this well on X3100.  WoW now definitely runs well enough to ditch Windows (for me at least, I know this is a bit subjective).  With the few issues listed above and general fps improvements to work on, I feel like we don't have too far to go to make WoW as good as it can be on the hardware.  X3100 users please give my config a shot, hopefully we can duplicate some of this success!

[/CODE]

---

