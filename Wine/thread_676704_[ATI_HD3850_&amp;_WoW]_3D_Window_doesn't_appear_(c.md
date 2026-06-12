---
title: "[ATI HD3850 &amp; WoW] 3D Window doesn't appear (cat. 8.1)"
date: 2008-01-24
forum: Wine
---

### Post by Raum on 2008-01-24
Hello,

Ok, I'll try to explain in english my problem because I did'nt have any clue in french forum...

I've just bought a new graphic card... my last GeForce 7600GT crashed... I'vee thought : "well, I'm sure I can run WoW under Linux as well as old GeForce !" but it was not so simple...

I've installed Ubuntu 7.10/Gutsy, downloaded the latest [Catalyst ATI drivers 8.1](http://ati.amd.com/support/drivers/linux/linux-radeon.html), and following this guide (in french) :
[le guide de cchtml.com](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide).

A "by hand" install but... Compiz is perfectly running ! So I was very suprised, no lag, full 3D, etc... extra. 
**_fglrxinfo**_
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3850
OpenGL version string: 2.1.7276 Release

And then, I've tried to run WoW. So I've got the latest Wine 0.9.53 but WoW didnt run ! I've desactived Compiz without any result. 

In fact, it's strange... A flashing black box appears then disappears and the "WoW" application appears in the taskbar below. My mouse disappears when I move it across the 3D area. So I think the window is here, I can manipulate her, resize her, etc, but the 3D things don't appear.

What do you think about ?

What can I do ? reinstall something ?

--------------------------------------------------
> Section "ServerLayout"

        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

(... sections clavier / souris ...)

Section "Monitor"
        Identifier   "MW221"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies Inc ATI Default Card"
        Driver      "vesa"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies Inc ATI Default Card"
        Monitor    "MW221"
        DefaultDepth     24
        SubSection "Display"
                Modes    "1680x1680" "1680x1050" "1440x1440" "1400x1050" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Today I've added the section :

> 

Section "Module"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "vbe"
EndSection

And turn on this option :  "OpenGLOverlay" à "on"

without any result....

Strange isn't it ? (I'm french and I don't know where to look... these symptoms are ... strange)

Thanks.

Raum

---

### Post by Raum on 2008-01-25
Well... I've tried something with config.wtf

I've replaced config.wtf by this one :
> 
SET gxApi "opengl"
SET ffxDeath "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"


Then my resolution screen changed and the movie started but with a flicking effect with my desktop in background (I wish I'm clear enough ? I'm french so... ehm...  Imagine 1s movie, 1s desktop, 1s movie, 1s desktop, ....)

After this sequence, uglies 3D effects... well not really 3D because it's just lines or missed 3D calculation with a black background... and login and password box... 

Ok, it's better but... it's not really playable. It hit escape, the config.wtf is completed, in particular with "movies 0".

I rerun WoW but now... no movie intro and... no 3D window ! just like the first symptom... WoW Windom is iconized on taskbar, my screen resolution has changed but nothing else....

Any other idea ??

---

### Post by Resonance378 on 2008-01-25
Yep.

Start here: [http://ubuntuforums.org/showthread.php?t=515573](http://ubuntuforums.org/showthread.php?t=515573)  as a double check.

And then go here: [http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378) just to see that your issue is not unique...

And lastly you may find a solution to your issue here: [http://www.wowwiki.com/Linux/Wine/Troubleshooting](http://www.wowwiki.com/Linux/Wine/Troubleshooting)

I recommend bookmarking all 3 as they've been priceless finds for me while I work with my own WoW issues :D

Good luck!

---

### Post by Raum on 2008-01-29
Thanks... I've ran WoW !!!

Sum up : WoW in 1600x1050 with last Catalyst 8.1 at 30FPS with my ATI HD3850... (except Shattrath where my fps drop at 18 ~ 20FPS).

It was not so hard to configure Ubuntu... ^__^

[[img]http://graagb.free.fr/WoW-HD3850-mini.jpg[/img]](http://graagb.free.fr/WoW-HD3850.jpg)

In fact, we need to differentiate three 3D configuration parts : Compiz, WoW and OpenGL. 

1/ I've reinstalled my distribution : Ubuntu 7.10/Gutsy
2/ I've reinstalled the last [Catalyst ATI Drivers 8.1](http://ati.amd.com/support/drivers/linux/linux-radeon.html) with a simple "sh ati-.....run" in a root console... and a standard install, not expert.

A this stade of installation, Compis is not functionnal but OpenGL Drivers are installed so WoW should be running (but didnt because of config.wtf !)

So.... I've edited Config.WTF !

I made some attempts, I've tested parameters one by one, some guides said "use ffxGlow", others said "use M2UseShaders" but the result was bad... black background, or brown... when I've tried to use both parameters ! eh eh ! 

Here is my Config.wtf :

_Config.WTF_
```
SET gxApi "opengl"
SET M2UseShaders "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxWindow "1"
```

Et là WoW fonctionne !

But Compiz didnt run... so... we need more configuration but now in distrubition config files.... I dont remember URL but the main line was :

```
sudo aitconfig --overlay-type=Xv
```

And edit the file  "/usr/bin/compiz" to modify the following parameters :

```
# Driver whitelist
# WHITELIST = "nvidia intel ati radeon i810"
WHITELIST = "fglrx nvidia intel ati radeon i810"
```
```
# blackilist based on the pci ids
# BLACKLIST_PCIIDS = "$T"
BLACKLIST_PCIIDS = ""
```

And restard the X Server.

Compiz should be running.

I've modify my Xorg.conf to replace the "mode" configuration parameter from ATI config by Ubuntu initial config because my XServer starts à 1024x768 in place of 1600x1050 at boot time... and I've added "viewport 0 0" just below.

To activate Compiz, ehm.. I don't know the english interface... ehm... appearance menu... not the compiz one. Don't activate Compiz when you want to play WoW because you may experiment a flashing desktop with 3D Window.

At last, I've corrupted icons... I'll test today in my config.wtf

```

Set UIFaster "2"

```

and... finally I've one bug.... the minimap bug... and blank minimap when I'm in interior (building or something like this)...

I'll have a look to you links later because now... I'm at work ^________^

Thanks and see you

Raum

---

### Post by Spydr4590 on 2008-01-29
You can't fix the mini map issue on Ati cards. It's a known issue. This works fine on Nvidia though.

---

### Post by Raum on 2008-02-08
Ehm... I'm thinking about OpenGL layer in ATI Catalyst Drivers :@

I'm at work actually so I can't test but I remember first time I've tested some WoW configuration, I've ran WoW in DirectX 3D and it ran without any problems (except at 5 FPS... :lolflag:).

So.... if I put the original windows config.wtf file, WoW can run in DirectX mode without 3D problems.... but I can't remember if the minimap bug was present.

Is there anyone who can test WoW in DirectX ?

And if I want to run WoW at 20 -> 30 FPS, I need to reconfigure my config.wtf to run WoW in OpenGL and tweak some variables but the minimap bug appears...

Could it be related to [http://ubuntuforums.org/showthread.php?t=689276](http://ubuntuforums.org/showthread.php?t=689276)

---

