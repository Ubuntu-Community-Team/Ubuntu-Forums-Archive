---
title: "[SOLVED] ATI has released Catalyst 7.12 Drivers"
date: 2007-12-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-12-20
ATI has released the last round of Catalyst drivers for 2007 - Anyone test drove them yet?
 
[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)
 
[SIZE="4"]**New Features **[/SIZE]
This release of the ATI Catalyst™ Linux driver introduces support for the following new operating systems: 
 
Red Flag DT 6.0 Support 
OpenSUSE 10.3 support 

[SIZE="4"]**Resolved Issues **[/SIZE]
The following section provide a brief description of resolved issues with the latest version of the ATI Catalyst™ Linux software suite. These include: 
 
     * A memory leak is no longer noticed when running OpenGL applications 
     * Running X -configure no longer results in a segmentation fault in the fglrx driver 
     * fglrxinfo no longer reports OpenGL Render string: as Mesa GLX Indirect on systems containing an ATI
        Rialto AGP series of product 

[SIZE="4"]**Known Issues **[/SIZE]
The following section provides a brief description of known issues associated with the latest version of ATI Catalyst™ Linux software suite. These issues include: 
 
     * There is no support for video playback on the second head in dual head mode. Further details can be
        found in topic number 737-26985 
     * Desktop corruption may be noticed when dragging the overlay/video when using dual-display mode. 
        Further details can be found in topic number 737-29578 
     * A black screen may be observed on some hardware when switching to the console or leaving the X 
        window system when a Vesa framebuffer console driver is used. Further details can be found in topic 
        number 737-30687 
     * Corruption may be noticed in the lower right corner of the display after the system is running for a long 
       period of time 
     * Display flicker may be noticed when the gnome screen-saver starts 
     * Diagonal tearing may be noticed when playing a video file using a video player that utilizes the XVideo 
        extension 
     * Video playback may look blocky when playing a video file using a video player that utilizes the XVideo 
        extension 
     * Video Playback may display wrong colors and additional shadow images when cropping or expanding a 
        video file using a video player that utilizes the XVideo extension 
     * Connecting a display device that supports 1680x1050 to a system running Linux may result in a 
        maximum display resolution of 1280x1024 only being available 
     * Custom mode lines in xorg.conf may be ignored by the fglrx driver 
     * Building RPM packages for Mandriva may fail

---

### Post by olskar on 2007-12-20
The list of known issues is getting longer... I'&#314;l wait..

---

### Post by melenor on 2007-12-20
I was wondering is there any way to easily upgrade to this new driver, or do i have to do what i did for 7.11 again?

Also anyone know if this resolves the issues with scrolling and the video playback while compiz-fusion is on? on mine whenever i play a movie it flickers and the movie itself not the program stays on top of all the other apps and scrolling is slow and lags alot.

---

### Post by hangfire on 2007-12-20
> **crjackson said:**
> ATI has released the last round of Catalyst drivers for 2007 - Anyone test drove them yet?
...

     * Connecting a display device that supports 1680x1050 to a system running Linux may result in a maximum display resolution of 1280x1024 only being available 
  

Not me! No 1680x1050? That's a deal-killer.

Another hairball release from ATi.

When will the promised GOOD STUFF start coming? I guess AMD is too busy writing off $billions from their ATi acquisition to invest in Linux software engineers.

---

### Post by Melcar on 2007-12-21
That resolution issue is driving everyone nuts.  Basically, almost no one is getting any WS resolutions out of these drivers.

---

### Post by Technophobia on 2007-12-21
Why is everything on the internet so fat? I guess if I put my head in a vice I'll be fine. 1680x1050 you will be missed.

---

### Post by adarkenigma on 2007-12-21
> Also anyone know if this resolves the issues with scrolling and the video playback while compiz-fusion is on? on mine whenever i play a movie it flickers and the movie itself not the program stays on top of all the other apps and scrolling is slow and lags alot.
does anyone has answer to this? 
does aiglx work better with this driver then default 7.1.0-8.37.6 version driver?

---

### Post by Kilz on 2007-12-21
> **hangfire said:**
> Not me! No 1680x1050? That's a deal-killer.

Another hairball release from ATi.

When will the promised GOOD STUFF start coming? I guess AMD is too busy writing off $billions from their ATi acquisition to invest in Linux software engineers.

I think an understanding on how linux software is released is a good idea. 
Linux software is released as soon as it has any functionality so that the community (users) can help find the issues (bugs) that need to be fixed. This is no different. The driver based on new code was only released 4 releases ago. Bugs are being found and fixed. If you require stability, dont install the newest  or latest of anything. The 8.40.4 drivers from the old code base work.

---

### Post by ravenon on 2007-12-21
Ah yes, installing and using software that is clearly under development, fun isn't it.
I have an MSI 64 bit laptop running Gutsy with all updates; has an X700 graphics card, 1280x800 resolution. I installed the 7.12 driver via:
sudo apt-get install dkms
sudo bash ati-driver-installer-8.443.1-x86.x86_64.run --buildpkg Ubuntu/gutsy
Then installed the three debs, rebooted and all worked--dkms did its job. The nice thing is that suspend/hibernate and resume now WORK. So evidently, the SLUB vs SLAB problem has been worked over by AMD/ATI.

However, compiz does not work anymore. The output of compiz --replace is:
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5653 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 378: /usr/local/bin/compiz: not found

At this point, metacity kicks in. I don't know the meaning of the /usr/bin/compiz: 378 line.

None the less, it is more important to me that suspend work on my laptop.
Fix for compiz was found in the Desktop effects subforum: edit /usr/bin/compiz
change lines 30 and 31 to:
COMPIZ_BIN_PATH="/usr/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/lib/compiz/"

and then a few lines down, change to:
COMPIZ_NAME="compiz.real" # Final name for compiz (compiz.real)

I am not sure when the compiz file was changed or by what.

---

### Post by aypnoia on 2007-12-21
If I understood well it says that it MAY be problem with 1680x1050 not that is out of the question. I 'm currently having 7.11 on my x1950 pro with 1680x1050 so I don't see why it shouldn't work on 7.12 especially since I have some corruption problems on mouse pointer from time to time and some other little bugs with the current driver. Lets see:)

---

### Post by aypnoia on 2007-12-21
1680x1050 is working with 7.12 I can confirm (At least on my rig). Just on logon screen you get 1280x1024 but that's how it was for me and with 7.11.
Compiz seems to function smoothly too.

---

### Post by Casual Fan on 2007-12-21
> **ravenon said:**
> The nice thing is that suspend/hibernate and resume now WORK. So evidently, the SLUB vs SLAB problem has been worked over by AMD/ATI.

Sweet. Anybody else have this experience too? I'm using the open-source driver still just so I can suspend.

---

### Post by homerhomer on 2007-12-21
I'm currently running a compaq presario v2000 series lappy  (AMD)

The installer works great!
I installed dkms first and the then ran ATI's installer with the following switch --buildpkg ubuntu/7.10
and then installed the packages that were created.

Thats when the good ended. 

what didn't work
my resolution was stuck at 1024x768. This resolution looks stretched and is unbearable on my laptop.   After going through some forums and googling, I was unable to find a fix.  How is this not a show stopper? 

just for kicks, I booted up Open Arena to see how it ran. with the new drivers the frames jumped from mid-20s to mid-50s. This was really nice, but in typical ATI fashion it was hindered by the brightness controls being broken. 

I wish they would not release drivers that are so broken. Theses drivers should be considered BETA at best.

The uninstaller was broken too.  The uninstall script wanted to replace the compiz config that it changed and it failed. so I had to manually remove ATI's file and then the uninstaller worked

Is there a QA team at ATI/AMD?

---

### Post by Kilz on 2007-12-21
> **homerhomer said:**
> 
I wish they would not release drivers that are so broken. Theses drivers should be considered BETA at best.

The uninstaller was broken too.  The uninstall script wanted to replace the compiz config that it changed and it failed. so I had to manually remove ATI's file and then the uninstaller worked

Is there a QA team at ATI/AMD?

[Read post #8]("http://ubuntuforums.org/showpost.php?p=3991130&postcount=8")

---

### Post by bestguy on 2007-12-21
Iam very happy with 7.12 because the Standby Function is working like a charme. 

Compiz is working but the Video Performance is slow down since 7.11. Also what i noticed is that with VLC the OpenGL output dont work anymore. Thats very sad because this was the only mode which one has a goog quality in Fullscreen Playback. 

Also i tried my Luck with the 1680x1050 Resolution. No Chance. But after i do a 

aticonfig --initiate -f 

and Restart ..then i have 1600x1200 and thats not so bad even the Fonts are not so sharp as in Widescreenmode. Maybe one of the profs ..found a workaround for this. 

best regards and merry Xmas to all

---

### Post by bestguy on 2007-12-21
> **aypnoia said:**
> 1680x1050 is working with 7.12 I can confirm (At least on my rig). Just on logon screen you get 1280x1024 but that's how it was for me and with 7.11.
Compiz seems to function smoothly too.

can you post the 

Screen / Device / Monitor  Section from your xorg.conf ? 

and what Monitor you have ? 

I tried in the meantime all combinations but with no luck. Every Modeline, even the produced from Aticonfig --resolution=0,.... is been ignored by the driver. 

regards

---

### Post by aya_pro on 2007-12-21
> **homerhomer said:**
> 
what didn't work
my resolution was stuck at 1024x768. This resolution looks stretched and is unbearable on my laptop.   After going through some forums and googling, I was unable to find a fix.  How is this not a show stopper? 


I installed 7.12 via envy and had resolution on my 16:9 laptop dropped from the normal 1440x900 I had with 7.11 and the previous drivers to 1152x864. I haven't found a solution to get it back, so returned to 7.11. Does anybody else have this problem?

---

### Post by aypnoia on 2007-12-21
This is really weird I was just checking my xorg and I realized that there is no 1680x1050@60Hz mentioned anywhere.On Ati control center though the maximum analysis is stated correctly 1680x1050:confused:
Here is what you asked  

Section "Device"
	Identifier	"Ati x1950 pro"
	Boardname	"ati"
	Busid		"PCI:5:0:0"
	Driver		"fglrx"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"L226W"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
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
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Ati x1950 pro"
	Monitor		"L226W"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1600x1200@60"	"1792x1344@60"	"1600x1200@65"	"1400x1050@75"	"1400x1050@60"	"1280x960@75"	"1280x1024@60"	"1280x960@60"	"1280x1024@75"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection


My monitor is a LG222wtq-sf
Here is and ati control center screenshot:

---

### Post by bestguy on 2007-12-22
thx apnoia for your answer. 

In my Ati Panel, the Monitor is properly logged as :

AL2016W with max. 1680 x 1200 @ 85Hz

but on the Resolution Selector are only normal 4:3 modes available. So iam stuck at 1600x1200. 

In the original Gnome Resolution tool theres more options, with choosing Monitor but even with the right setting X wont start until i remove this Modelines from xorg.config. 

It seems that all wide screen resolutions causing trouble with the 7.12 Ati. Very strange. They fix one and open on the other side another bug. 

regards

---

### Post by MrKirby on 2007-12-22
Just for reference:

I have an ATI Radeon x1600 Pro AGP 512 (non-mobility) that I was only previously able to get desktop effects to work with XGL until this update.  Using XGL with the previous version STILL had the slow scrolling problem for me, so if you have an x1600 series i would suggest switching, because I actually saw a very slight improvement in the scrolling problem.

I also now have direct rendering, which also didn't seem possible (or easy to accomplish) with this card and desktop effects previously.

Compiz works great, seems just a bit slower, but definitely acceptable as far as all the flashy stuff.

Downside: Problems playing videos.  All flickery and stuff playing with VLC, movieplayer etc. in a window, but the flickering does not happen in fullscreen.  This does not affect flash videos ( l like stumble video), although it does affect their performance in browser windows, so keeping your stumble videos to a small size and just using enhanced desktop zoom to put 'em fullscreen seems to make the framerates watchable.

Overall, I'm *happier* with the new drivers and AIGLX on my radeon X1600 and am looking forward to more improvements.

Now that I think of it, though, I haven't tried XGL with the new drivers, but I think I'm just gonna keep it here for now, as it's useable and will make it easier to upgrade the drivers again later.

[Another thread that shows my config for those who are interested]("http://ubuntuforums.org/showthread.php?p=3991041#post3991041")

---

### Post by MrKirby on 2007-12-22
Also, my screen resolutions seem to be working fine.

---

### Post by aypnia on 2007-12-22
> **bestguy said:**
> thx apnoia for your answer. 

In my Ati Panel, the Monitor is properly logged as :

AL2016W with max. 1680 x 1200 @ 85Hz

but on the Resolution Selector are only normal 4:3 modes available. So iam stuck at 1600x1200. 

In the original Gnome Resolution tool theres more options, with choosing Monitor but even with the right setting X wont start until i remove this Modelines from xorg.config. 

It seems that all wide screen resolutions causing trouble with the 7.12 Ati. Very strange. They fix one and open on the other side another bug. 

regards

Just remembered  to tell you that when I changed my monitor few days ago from my old CRT to my current wide LCD I also could not  use wide screen resolutions. What seems to have solved the problem was
sudo dpkg-reconfigure xserver-xorg
and manually setting it up. I even tried first (before manual setup) to install monitor from CD driver I got with it, which didn't work also (misreported refreshes and max resolutions) .
Generaly my impression so far with proprietary drivers is that doing anything about drivers through the system>administration>screen and graphics gui is making a mess so try to stick with command line and avoid screen and graphics altogether

---

### Post by bestguy on 2007-12-22
i tried with reconfigure but without result. The Modelines are just been ignored. So i stuck with 1600x1200 an wait for the next Driver Release. 

Altogether the 7.12 are not so bad. The scrolling in Firefox works great. Compiz works. Standby works. 

So lets see what the next release brings. In the meantime i try to install some sharper fonts.

regards

---

### Post by Yellow Pasque on 2007-12-22
Wow, no 1680x1050? Blasphemy!

For those who don't care about 3D games/effects, I would recommend the radeonhd open-source driver.
[http://www.phoronix.com/scan.php?page=article&item=843&num=1](http://www.phoronix.com/scan.php?page=article&item=843&num=1)

---

### Post by lockpicker on 2007-12-23
hey, i've tried to install the driver on gutsy but without success..

i've removed previous fglrx (installed by repository) and rebooted, then installed dkms, build and installed the packages, executed aticonfig and rebooted.

but now fglrx isn't enabled, it uses mesa.
in the xorg log i've noticed some errors... can someone help me? :)

```


X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux crash 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 23 10:53:18 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 1019,1870 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24d2 card 1019,1870 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1019,1870 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 1019,1870 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1019,1870 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1019,1870 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1019,1870 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1019,1870 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,71cd card 174b,0850 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,71ed card 174b,0851 rev 00 class 03,80,00 hdr 00
(II) PCI: 02:01:0: chip 1102,0002 card 1102,8040 rev 05 class 04,01,00 hdr 80
(II) PCI: 02:01:1: chip 1102,7002 card 1102,0020 rev 05 class 09,80,00 hdr 80
(II) PCI: 02:02:0: chip 1106,3044 card 1106,3044 rev 46 class 0c,00,10 hdr 00
(II) PCI: 02:05:0: chip 14f1,8800 card 17de,08a1 rev 05 class 04,00,00 hdr 80
(II) PCI: 02:05:2: chip 14f1,8802 card 17de,08a1 rev 05 class 04,80,00 hdr 80
(II) PCI: 02:0b:0: chip 10b7,9200 card 1019,3920 rev 78 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf2000000 - 0xf5ffffff (0x4000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x70000000 - 0x700fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x71cd) rev 0, Mem @ 0xe0000000/28, 0xf1000000/16, I/O @ 0xa000/8
(--) PCI: (1:0:1) ATI Technologies Inc unknown chipset (0x71ed) rev 0, Mem @ 0xf1010000/16
(--) PCI: (2:5:0) unknown vendor (0x14f1) unknown chipset (0x8800) rev 5, Mem @ 0xf2000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xdfffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf5000000 - 0xf500007f (0x80) MX[B]
	[1] -1	0	0xf3000000 - 0xf3ffffff (0x1000000) MX[B]
	[2] -1	0	0xf5001000 - 0xf50017ff (0x800) MX[B]
	[3] -1	0	0x70100000 - 0x701003ff (0x400) MX[B]
	[4] -1	0	0xf6000000 - 0xf60003ff (0x400) MX[B]
	[5] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[6] -1	0	0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xf1000000 - 0xf100ffff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[10] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[11] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[12] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[13] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[14] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[20] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[21] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[22] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[23] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xf1010000 - 0xf101ffff (0x10000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf5000000 - 0xf500007f (0x80) MX[B]
	[1] -1	0	0xf3000000 - 0xf3ffffff (0x1000000) MX[B]
	[2] -1	0	0xf5001000 - 0xf50017ff (0x800) MX[B]
	[3] -1	0	0x70100000 - 0x701003ff (0x400) MX[B]
	[4] -1	0	0xf6000000 - 0xf60003ff (0x400) MX[B]
	[5] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[6] -1	0	0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xf1000000 - 0xf100ffff (0x10000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[9] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[10] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[11] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[12] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[13] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[14] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[20] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[21] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[22] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[23] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xf1010000 - 0xf101ffff (0x10000) MX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf5000000 - 0xf500007f (0x80) MX[B]
	[5] -1	0	0xf3000000 - 0xf3ffffff (0x1000000) MX[B]
	[6] -1	0	0xf5001000 - 0xf50017ff (0x800) MX[B]
	[7] -1	0	0x70100000 - 0x701003ff (0x400) MX[B]
	[8] -1	0	0xf6000000 - 0xf60003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xf1000000 - 0xf100ffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf1010000 - 0xf101ffff (0x10000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[18] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[20] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[21] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[27] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[28] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[29] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[30] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.44.3
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.44.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.443.1                  
(II) ATI Proprietary Linux Driver Build Date: Dec 19 2007 21:29:14
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x71CD) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf5000000 - 0xf500007f (0x80) MX[B]
	[5] -1	0	0xf3000000 - 0xf3ffffff (0x1000000) MX[B]
	[6] -1	0	0xf5001000 - 0xf50017ff (0x800) MX[B]
	[7] -1	0	0x70100000 - 0x701003ff (0x400) MX[B]
	[8] -1	0	0xf6000000 - 0xf60003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xf1000000 - 0xf100ffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf1010000 - 0xf101ffff (0x10000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[17] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[18] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[20] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[21] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[27] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[28] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[29] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[30] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x8209578
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf5000000 - 0xf500007f (0x80) MX[B]
	[5] -1	0	0xf3000000 - 0xf3ffffff (0x1000000) MX[B]
	[6] -1	0	0xf5001000 - 0xf50017ff (0x800) MX[B]
	[7] -1	0	0x70100000 - 0x701003ff (0x400) MX[B]
	[8] -1	0	0xf6000000 - 0xf60003ff (0x400) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xf1000000 - 0xf100ffff (0x10000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[13] -1	0	0xf1010000 - 0xf101ffff (0x10000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[20] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[21] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[22] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[23] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[24] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[30] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[31] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[32] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[33] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "Radeon X1600 Series" (Chipset = 0x71cd)
(--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0x0850)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xf1000000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV530
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
(WW) fglrx(0): Failed to open DRM connection
(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: PHL  Model: 824  Serial#: 17703
(II) fglrx(0): Year: 2005  Week: 12
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate  Composite  SyncOnGreen
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): Default color space is primary color space
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.639 redY: 0.342   greenX: 0.297 greenY: 0.615
(II) fglrx(0): blueX: 0.146 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@67Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 75  vid: 20273
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) fglrx(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) fglrx(0): Serial No:  VN  017703
(II) fglrx(0): Monitor name: Philips 190S5
(II) fglrx(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 82 kHz, PixClock max 140 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff00410c240827450000
(II) fglrx(0): 	0c0f01030e261e78eea2a5a3574c9d25
(II) fglrx(0): 	115054bfef80314f454f614f714f8180
(II) fglrx(0): 	010101010101302a009851002a403070
(II) fglrx(0): 	1300782d1100001e000000ff0020564e
(II) fglrx(0): 	20203031373730330a20000000fc0050
(II) fglrx(0): 	68696c697073203139305335000000fd
(II) fglrx(0): 	00384c1e520e000a202020202020001a
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 500/405MHz @ 0Hz [enable load balancing]
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 30 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x1024 (pitch 0)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(--) fglrx(0): Display dimensions: (380, 300) mm
(--) fglrx(0): DPI set to (85, 86)
(--) fglrx(0): Virtual size is 1280x1024 (pitch 1280)
(**) fglrx(0): *Mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   74.48  1280 1336 1472 1664  720 721 724 746 +hsync
(**) fglrx(0): *Mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.76  1152 1224 1344 1536  864 865 868 900 +hsync
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0): *Mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"   78.43  1024 1080 1192 1360  768 769 772 801 +hsync
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"   45.50  800 840 920 1040  600 601 604 625 +hsync
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   26.71  720 736 808 896  480 481 484 497 +hsync
(**) fglrx(0): *Mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 +hsync +vsync
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"   28.07  640 696 736 832  400 413 415 449
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"   19.68  512 528 576 632  384 384 385 416
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   24.75  400 408 448 528  300 601 602 625 doublescan
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   15.75  320 328 360 416  240 481 482 501 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   13.10  320 352 368 416  200 406 407 417 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) fglrx(0): HPV inactive
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.44.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf1000000 - 0xf100ffff (0x10000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xf5000000 - 0xf500007f (0x80) MX[B]
	[7] -1	0	0xf3000000 - 0xf3ffffff (0x1000000) MX[B]
	[8] -1	0	0xf5001000 - 0xf50017ff (0x800) MX[B]
	[9] -1	0	0x70100000 - 0x701003ff (0x400) MX[B]
	[10] -1	0	0xf6000000 - 0xf60003ff (0x400) MX[B]
	[11] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[12] -1	0	0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
	[13] -1	0	0xf1000000 - 0xf100ffff (0x10000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xf1010000 - 0xf101ffff (0x10000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[19] 0	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000bc00 - 0x0000bc7f (0x80) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[24] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b01f (0x20) IX[B]
	[26] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[27] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[33] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[34] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[35] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[36] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x10000000
(==) fglrx(0): Write-combining range (0xe0000000,0x10000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 7167
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "it"
(**) Generic Keyboard: XkbLayout: "it"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded


```

i've searched on google for the errors but i've found no working solution.
thx

---

### Post by Applegeek on 2007-12-23
I thought my Radeon HD 2600XT was working, once all the Compiz stuff was up and running.  But playing videos (windowed) still blows...anyone have a fix for this?  I notice that after a whole the screen savers start to flicker and crash as well.

Or do we just have to wait??  The kids love to play with all the Compiz stuff, so at least that's working.

I think I'll just revert back to the NVidia card for the time being...What a shame.  I was so hoping that the ATI cards would works a little better, they seem to render video a little cleaner - but at this point it looks like the NVidia drivers are still much more functional.

---

### Post by rockorequin on 2007-12-23
@lockpicker: I got the same errors as you getting fglrx (for Catalyst 7.11, but it is probably the same as 7.12) to load, and the solution was:

1. Try:

modprobe -vf fglrx

If the output is something like this: "install /sbin/lrm-video fglrx"

then modify "/etc/modprobe.d/lrm-video" and comment out the line with fglrx, ie:

#install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS

2. Try 

dmesg | grep fglrx

If you see a message like this:

fglrx: ... firegl_stub_register failed

try removing the Radeon tool and rebooting. I did both 'sudo rmmod radeon' and removed radeontool using Synaptic. 

Then after rebooting X, fglrx loaded up ok and fglrxinfo and amdcce both showed it was using ATI instead of Mesa as the OpenGL provider.

---

### Post by Multi-Booter on 2007-12-25
> **hangfire said:**
> Not me! No 1680x1050? That's a deal-killer.

Another hairball release from ATi.

When will the promised GOOD STUFF start coming? I guess AMD is too busy writing off $billions from their ATi acquisition to invest in Linux software engineers.

> **Melcar said:**
> That resolution issue is driving everyone nuts.  Basically, almost no one is getting any WS resolutions out of these drivers.

> **aypnoia said:**
> If I understood well it says that it MAY be problem with 1680x1050 not that is out of the question. I 'm currently having 7.11 on my x1950 pro with 1680x1050 so I don't see why it shouldn't work on 7.12 especially since I have some corruption problems on mouse pointer from time to time and some other little bugs with the current driver. Lets see:)

OK guys, I did not get past reading page one... BUT HERE ARE MY PERSONAL EXPERIENCES...

I am running the 64 bit Ubuntu 7.10 on the hardware listed below...
ATI X1300 Pro & a Dell widescreen monitor with 1680x1050 native resolution.

This driver has no problem at all with providing me a clean display of 1680x1050.
The previous versions also provided me with the same resolution no problem, but it was not very clean before.

I still find room to complain though.... because who in the world wants 1680x1050 resolution?
I mean as far as I am concerned, you can have it...... OR IS THERE SOMETHING I AM MISSING?????

Things are so small at that resolution... especially text... and I also haven't found the best font style to use either.
So it is not ideal for someone like me who reads a lot of text.

I personally much prefer a resolution such as 1280x800.
The windows version of the ATI Catalyst provides me both resolutions and I use the 1280x800.
Under the linux version, this resolution is not even an option.


**What can I do to make 1680x1050 resolution more liveable... such as larger fonts in everything?**

---

### Post by lockpicker on 2007-12-25
> **rockorequin said:**
> @lockpicker: I got the same errors as you getting fglrx (for Catalyst 7.11, but it is probably the same as 7.12) to load, and the solution was:

1. Try:

modprobe -vf fglrx

If the output is something like this: "install /sbin/lrm-video fglrx"

then modify "/etc/modprobe.d/lrm-video" and comment out the line with fglrx, ie:

#install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS
.

This have worked for me, thx alot :)
Now i have to fix a problem with my dvb, with opensource drivers it works but with fglrx the X server crash... in feisty was ok, but in gutsy i've this problem, i hope i'll fix it :)

Happy Xmas!

---

### Post by kayvortex on 2007-12-25
To confirm what aya_pro asked, I also gave the 7.12 a go in the hope that it would get my 1440x900 resolution, but alas no.

Also, to everyone experiencing flickering video playback try using the x11 video output: for mplayer (for example) this would be:

```
mplayer -vo x11
```

If this works, you can edit the file "/etc/mplayer/mplayer.conf" and change the line "vo=xv" to "vo=x11".

For vlc, go to Settings -> Preferences. Then, check "Advanced Preferences" at the bottom, and drop down the "Video" option and click on "Output Modes" (i.e. don't drop into that section, just select it). Finally, change "Video output module" to "X11 video output".

---

### Post by jack handy on 2007-12-25
other than the lower resolution, everything else seems to be working perfectly for me!  great that i can finally play WoW without worrying about it crashing every 5 minutes, and that i dont need to find different video players to get videos to play correctly. 

looking forward to the resolution bug being fixed in the next driver release! :guitar:

---

### Post by GuiPoM on 2007-12-26
Hi there !

There is no more Composite on my X server since catalyst 7.12. I own a FireGL V3100. Previous 7.42 or 7.43 (7.11) had to be hacked to pass hardware detection, but were fully functionnal, including Composite enabled.

I have installed 8.44 (so 7.12) last week, but I have got a new error I never met befor (less /var/log/Xorg.0.log | grep "Comp"):

```

(**) Extension "Composite" is enabled
(II) Loading extension XVideo-MotionCompensation
(II) fglrx(0): RENDER and Composite disabled when OpenGL Overlay enabled
```

Note that my xorg.conf is correct:

```

Section "Device"
	Identifier	"ATI Technologies Inc RV370 5B64 [FireGL V3100 (PCIE)]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	#Option		"VideoOverlay"	  	"on"
	#Option		"OpenGLOverlay"	  	"off"
	#Option		"MergedFB"	  	"on"
	Option 		"TexturedXrender" 	"on"
	Option 		"Textured2D"		"on"
EndSection
```
I tried all options removed, and all to off, nothing more that this no composite error message :'(

Any idea about what is going wrong with these 8.44 and FireGL ? any known issue ?

---

### Post by betrion on 2007-12-26
still hasnt fixed that weird textures issue with vertex shaders for me(very bright textures)....
[http://img341.imageshack.us/img341/5253/silkroadsu0.jpg](http://img341.imageshack.us/img341/5253/silkroadsu0.jpg)
this is what happens when i turn on vertex shaders in wine, and native linux games have this issue too..8.40.4 is much more compatible but slower than this version.

---

### Post by Kilz on 2007-12-26
> **betrion said:**
> still hasnt fixed that weird textures issue with vertex shaders for me(very bright textures)....
[http://img341.imageshack.us/img341/5253/silkroadsu0.jpg](http://img341.imageshack.us/img341/5253/silkroadsu0.jpg)
this is what happens when i turn on vertex shaders in wine, and native linux games have this issue too..8.40.4 is much more compatible but slower than this version.

Have you filed bug reports with ATI?

---

### Post by moron on 2007-12-26
Just in case anyone else is having the widescreen issue where you are actually getting 1280x1040 instead, at least in my case (x1200 embedded) I was able to get back the correct resolution by starting up amdcccle and then:

changing resolution to something lower than 1680x1050 (hit apply)
changing resolution back to 1680x1050

So far it looks like this may be necessary at each start up of X (arrgh).

Here's my xorg.conf:

---------------

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "int10"
        Load  "vbe"
        Load  "dbe"
        Load  "v4l"
        Load  "glx"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "ca"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        ModeLine     "1680x1050" 146.2 1680 1784 1960 2240 1050 1053 1059 1089
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1680x1050"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "XVideo" "enable"
EndSection
---------------

Xv still doesn't work of course but at least the resolution isn't all messed up.

Cheers

---

### Post by cbrigstocke on 2007-12-26
I'm having a problem with video playback when compiz is on.  It very rarely works in a window and sometimes it doesn't work fullscreen either.  If I swith the overlay to opengl it works, but the video quality is pretty bad with sheering.  Anyone have any ideas or know where I should look?  I have a radeon 9800pro at 1024x768 dvi output.

Thanks

I found out that reducing the eye candy (cube reflection) just a little bit fixes the problem.

---

### Post by bkraptor on 2007-12-27
> **Multi-Booter said:**
> OK guys, I did not get past reading page one... BUT HERE ARE MY PERSONAL EXPERIENCES...

I am running the 64 bit Ubuntu 7.10 on the hardware listed below...
ATI X1300 Pro & a Dell widescreen monitor with 1680x1050 native resolution.

This driver has no problem at all with providing me a clean display of 1680x1050.
The previous versions also provided me with the same resolution no problem, but it was not very clean before.

I still find room to complain though.... because who in the world wants 1680x1050 resolution?
I mean as far as I am concerned, you can have it...... OR IS THERE SOMETHING I AM MISSING?????

Things are so small at that resolution... especially text... and I also haven't found the best font style to use either.
So it is not ideal for someone like me who reads a lot of text.

I personally much prefer a resolution such as 1280x800.
The windows version of the ATI Catalyst provides me both resolutions and I use the 1280x800.
Under the linux version, this resolution is not even an option.


**What can I do to make 1680x1050 resolution more liveable... such as larger fonts in everything?**

You could set the DPI value to the real DPI of your display. To do that, go to:
System -> Preferences -> Appearance -> Fonts -> click on Details

The resolution setting is your DPI setting. It comes with 96 by default, but you should always fill in your real DPI.

To calculate your DPI, use this formula:

DPI = Y_resolution / square_root( diagonal * diagonal / aspect_ratio_constant )

Y_resolution is the smaller number from your resolution in pixels (for 1680x1050, Y_resolution would be 1050). diagonal is your screen diagonal in inches.

aspect_ratio_constant depends on your display's aspect ratio:
For 16:10 use 3.56
For 16:9 use 4.16
For 5:4 use 2.56
For 4:3 use 2.78

Examples of DPI for different resolutions and diagonals for 16:10 displays:
15.4" with 1680x1050: 128 DPI
15.4" with 1440x900: 110 DPI
15.4" with 1280x800: 98 DPI
14.1" with 1440x900: 120 DPI
14.1" with 1280x800: 107 DPI
17" with 1680x1050: 116 DPI
17" with 1440x900: 100 DPI

---

### Post by iramhernandez on 2007-12-27
I was unable to get 7.12 to work with a Radeon 1650 AGP 512 MB.  I used envy to load the drivers.  When I started X after an install and reboot, my computer was completely blank.  X would not start and I was unable to reboot the computer except by restarting the PC physically.  when I went back to 7.11 the computer worked fine again.

I was exited because this driver promised speed improvements on AGP based systems but  I'll have to wait until a later version surfaces.

---

### Post by Ber P on 2007-12-27
I've noticed that when I run glxgears I get around 3900 fps (Radeon 9600). But if I start up OO word processor it increases to around 5200 fps? Anyone know why? And can I be sure to have maximum perfomance when running games(under wine)?
Also - is the driver correct installed if ```
apt-cache show xorg-driver-fglrx | grep Version
``` returns ```
Version: 8.443.1-1
Version: 7.1.0-8.37.6+2.6.22.4-14.10
Version: 7.1.0-8.37.6+2.6.22.4-14.9

```
Anyone knows what the second and third line are refering to?

---

### Post by moron on 2007-12-27
Ditto here, I am currently running at 1680x1050 using 7.12 (model x1200) though I have had to occasionally reset the resolution using the "amdcccle" configuration tool.  It also required a custom modeline for my monitor.

Cheers

---

### Post by cbrigstocke on 2007-12-28
> **Ber P said:**
> Also - is the driver correct installed 

Have you tried fglrxinfo? That will tell you about the drivers you are running at that instant. I'm not sure about the output regarding your fglrx drivers, but it appears that you have more than one version installed.

---

### Post by Ber P on 2007-12-28
fglrxinfo gives me:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.1.7170 Release

```
which I think is ok. 
If I have old drivers installed as well, does anyone knows how to get rid of them?

I think I still has a problem with memoryleak eventhough ATI claim's to have fixed it with 8.443. I think so because running games under wine, works for 5-10 min.'s, and then my system hard locks.

Can anyone else confirm the increased perfomance issue when running OO as described above?

---

### Post by evetrins on 2007-12-28
moron,

What's Your "custom modeline"?
I tried to do the same, but standard modeline for "1620x1050@60" does not work for my lcd LG206W conected with DVI. Display says, mode is not supported, it show crazy 171 Hz (?!)

---

### Post by Yellow Pasque on 2007-12-28
> **evetrins said:**
> moron,

What's Your "custom modeline"?
I tried to do the same, but standard modeline for "1620x1050@60" does not work for my lcd LG206W conected with DVI. Display says, mode is not supported, it show crazy 171 Hz (?!)
Maybe you should try 1680x1050 if that's not a typo in your post :P

---

### Post by CypherHackz on 2007-12-28
wait, i check on their website, the latest version support 

Operating Systems Distributions Supported
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_712_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_712_linux.html)

# Red Hat Enterprise Linux suite
# Novell/SuSE product suite 

so it does not support ubuntu right? i have radeon hd2600xt. last time i upgraded the driver has make the display become unreadable. there are many square (like pixels) on the screen. and also, ubuntu use lower resolution which is 800x600.

so i need to reinstall ubuntu. and now i am afraid to upgrade the driver. but i can't use the ubuntu desktop animation because ubuntu can't detect my graphic card.

-cypher.

---

### Post by evetrins on 2007-12-28
> **Temüjin said:**
> Maybe you should try 1680x1050 if that's not a typo in your post :P

It is in post :(

---

### Post by aypnia on 2007-12-28
Ok since my last post I cleaned up my xorg cause I realized I had 1680x1050 and 1280x1024 but nothing else smaller.
It looks like my monitor was managing the  1680x1050 by mistake :) since the xorg was keeping my old CRT's modelines. Nevertheless I done under these conditions in commandline _ xvitune -show_ and I got the functioning 1680x1050 modeline for my LG L226WTQ   which I added in my new clean xorg.
So for the ones having the same monitor it goes like this:

Section "Monitor"
	Identifier	"L226W"
	modeline	"1680x1050"   119.00   1680 1728 1760 1840   1050 1053 1059 1080 +vsync		
EndSection

The only side effect so far is that ati control center is reporting a 59hz refresh while screen menu itself shows 60hz as it should.
I hope this helps somebody:)

---

### Post by CypherHackz on 2007-12-28
nevermind. i have found the easiest and the safest way to update. im using [envy]("http://albertomilone.com/nvidia_scripts1.html"). really nice tool.

-cypher.

---

### Post by hotgly on 2008-01-01
I ‘ve got three problems with the ati-driver-8.44 and been unsatisfied and have to turn to the restricted driver of Ubuntu sources.
1.Resolution: my screen is 1280x768 with ati radeon9700,I've done everything,such as modeline, mode, vertisync horiscan,things like that, and at last to find that it's just locked to 1024x768 and never give me an option for 1280x768 to fill the two black margins.
2.Suspend/Resume: the screen just goes to black after Suspend and will never be lighted before powering off and reboot.
3.Occasional 100%CPU when compiz is active: Occasional is not bothering, but scroll is always not very smooth and it'll be an eyesuffer after several minutue.
any suggestions?

---

### Post by Kilz on 2008-01-01
> **hotgly said:**
> I ‘ve got three problems with the ati-driver-8.44 and been unsatisfied and have to turn to the restricted driver of Ubuntu sources.
1.Resolution: my screen is 1280x768 with ati radeon9700,I've done everything,such as modeline, mode, vertisync horiscan,things like that, and at last to find that it's just locked to 1024x768 and never give me an option for 1280x768 to fill the two black margins.
2.Suspend/Resume: the screen just goes to black after Suspend and will never be lighted before powering off and reboot.
3.Occasional 100%CPU when compiz is active: Occasional is not bothering, but scroll is always not very smooth and it'll be an eyesuffer after several minutue.
any suggestions?

Did you report your issues to ATI?

---

### Post by Mizzou_Engineer on 2008-01-01
Your advice eventually works, but I ran into a few problems from a brand-spanking-new 7.10 install:

1. Executing the command at first gave the error "./packages/Ubuntu/ati-packager.sh: 176: dpkg-architecture: not found."

That problem was solved by installing the package **dpkg-dev** since it provides the dpkg-architecture command. 

2. Now the command identifies the architecture as amd64 but throws off another error: "make: dh_testdir: Command not found."

dh_testdir is in the package **debhelper** and after I installed debhelper, the driver .debs were generated by the ATi driver install script. 

So an updated list of instructions would read like so:

1. sudo apt-get install dkms dpkg-dev debhelper 
2. sudo bash ati-driver-installer-8.443.1-x86.x86_64.run --buildpkg Ubuntu/gutsy
3. sudo dpkg -i ./fglrx-amdcccle_8.443.1-1.amd64.deb
4. sudo dpkg -i ./fglrx-kernel-source_8.443.1-1.amd64.deb
5. sudo dpkg -i ./xorg-driver-fglrx_8.443.1-1.amd64.deb
6. sudo dpkg -i ./xorg-driver-fglrx-dev_8.443.1-1.amd64.deb

---

### Post by hotgly on 2008-01-02
yes.and the widescreen issue is known issue and the other two also happens ,i'm waiting for the next month

---

### Post by Formaldehyde on 2008-01-02
> **hotgly said:**
> yes.and the widescreen issue is known issue and the other two also happens ,i'm waiting for the next month

I'm always waiting for "next month"

---

### Post by crjackson on 2008-01-02
I got tired of waiting and got an nVidia 7900 GTO for my main system.

I still have several ATI systems waiting though :(

---

### Post by silviur on 2008-01-03
The latest ATI drivers made Hibernate work on my computer. It didn't work before in Gutsy (Radeon 9550). I suspect xserver-xorg is the culprit (desktop effects won't work without xserver-xorg installed, regardless of the driver version or type (regular or restricted)), but that's another problem. I updated to the Ati driver version from 20 december, and Hibernate works like a charm.

---

### Post by Giannis68 on 2008-01-03
solved for me LG L226WTQ and Radeon 9700 Pro
[http://ubuntuforums.org/showpost.php?p=3592089&postcount=3](http://ubuntuforums.org/showpost.php?p=3592089&postcount=3)


Section "Device"
    Identifier    "ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]"
    Boardname    "ati"
    Busid        "PCI:1:0:0"
    Driver        "fglrx"
    Screen    0
EndSection

Section "Monitor"
    Identifier    "L226W"
    Option        "DPMS"
    Option        "DDC"    "false" 
    Vendorname    "LG"
    Modelname    "LG L226WTQ(Digital)"
    Horizsync    28.0-83.0
    Vertrefresh    56.0-75.0
# 1680x1050 @ 59.00 Hz (GTF) hsync: 64.07 kHz; pclk: 144.55 MHz
  modeline "1680x1050@59"  144.55  1680 1784 1968 2256  1050 1051 1054 1086 
#  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
#  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
#  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
#
    Displaysize    444    277#1680x1050    96dpi
    # calc: (x|y)pixels * 25.4 / dpi
    #    DisplaySize    426    266    # 1680x1050 100dpi
    #    DisplaySize    355    222    # 1680x1050 120dpi
    #    DisplaySize    444    277    # 1680x1050 96dpi
    #    DisplaySize    338    254    # 1280x960 96dpi
    #    DisplaySize    338    270    # 1280x1024 96dpi
    #    DisplaySize    370    277    # 1400x1050 96dpi
    #    DisplaySize    423    370    # 1600x1400 96dpi
    #    DisplaySize    270       203    # 1024x768 96dpi
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]"
    Monitor        "L226W"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1920    1200
        Modes        "1680x1050@59"    "1440x1440"    "1280x1024"    "1280x960"    "1152x864"    "1024x768"    "800x600"    "720x400"    "640x480"
    EndSubSection
EndSection

---

### Post by Adahn on 2008-01-03
anyone running these successfully with a 3850/3870?

---

### Post by Yellow Pasque on 2008-01-03
> **Adahn said:**
> anyone running these successfully with a 3850/3870?
No, because they're unsupported at this time. See the link in my sig for the open-source radeonhd driver. That should at least give you full 2D.

---

### Post by Adahn on 2008-01-03
> **Temüjin said:**
> No, because they're unsupported at this time. See the link in my sig for the open-source radeonhd driver. That should at least give you full 2D.

thanks.  
I'm using those now, but was thinking perhaps the new 7.12's fixed this.

---

### Post by zubat on 2008-01-03
> **melenor said:**
> I was wondering is there any way to easily upgrade to this new driver, or do i have to do what i did for 7.11 again?

Also anyone know if this resolves the issues with scrolling and the video playback while compiz-fusion is on? on mine whenever i play a movie it flickers and the movie itself not the program stays on top of all the other apps and scrolling is slow and lags alot.

Sorry if this has been answered but I just used envy to upgrade I recomend envy for updating ati drivers, Also when I tried video playback with these new drivers it was choppy at first, but then i resloved this by  changing ```
Option "VideoOverlay" "on"
``` to ```
Option "VideoOverlay" "off"
``` in xorg.conf

---

### Post by BogusJoe on 2008-01-03
> **Adahn said:**
> anyone running these successfully with a 3850/3870?

Hey Adahn, the ATI HD3870 worked on Hardy Heron 64 bit version if you would like to try.  See post here: [http://ubuntuforums.org/showthread.php?t=655107](http://ubuntuforums.org/showthread.php?t=655107)

This does not work on Gutsy 7.10 64bit.  Tried and failed.

---

### Post by richard.tufty on 2008-01-03
> **Mizzou_Engineer said:**
> Your advice eventually works, but I ran into a few problems from a brand-spanking-new 7.10 install:

1. Executing the command at first gave the error "./packages/Ubuntu/ati-packager.sh: 176: dpkg-architecture: not found."

That problem was solved by installing the package **dpkg-dev** since it provides the dpkg-architecture command. 

2. Now the command identifies the architecture as amd64 but throws off another error: "make: dh_testdir: Command not found."

dh_testdir is in the package **debhelper** and after I installed debhelper, the driver .debs were generated by the ATi driver install script. 

So an updated list of instructions would read like so:

1. sudo apt-get install dkms dpkg-dev debhelper 
2. sudo bash ati-driver-installer-8.443.1-x86.x86_64.run --buildpkg Ubuntu/gutsy
3. sudo dpkg -i ./fglrx-amdcccle_8.443.1-1.amd64.deb
4. sudo dpkg -i ./fglrx-kernel-source_8.443.1-1.amd64.deb
5. sudo dpkg -i ./xorg-driver-fglrx_8.443.1-1.amd64.deb
6. sudo dpkg -i ./xorg-driver-fglrx-dev_8.443.1-1.amd64.deb

Mizzou_Engineer, thanks so much for that bit of info! I have been trying for 6 hours to get the ATI drivers installed on a fresh Gutsy install (my first Linux install for about 5 years) and I was ready to throw the whole thing out of the window and go back to M$. 

I was having all sorts of problems with the MESA driver taking over, and now it's all good!

Thanks once again,

Richard

---

### Post by esteckis on 2008-01-04
ATI has released a new driver dated 12/20.

There is also another post to install the ATI driver,
Envy site [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

1/3/08 The NEW Envy program installed the new ATI dated 12/20/07 driver and special effects and compiz both work. The only thing with the new ATI driver for me is the screen slightly flickers when the screen saver is running. Out of 12 times of trying to get the ATI installed, special effects to take and Compiz working, this NEW ENVY version worked for me.

ATI 1250 series onboard video using UBUNTU Gutsy 64 bit version

---

### Post by Torqumada286 on 2008-01-04
> **Temüjin said:**
> No, because they're unsupported at this time. See the link in my sig for the open-source radeonhd driver. That should at least give you full 2D.

I wish I had known that before putting one in my system.  Guess I'll keep my Windows parition for my games.  :(

Torqumada

---

### Post by revoltism on 2008-01-06
> **aypnia said:**
> Ok since my last post I cleaned up my xorg cause I realized I had 1680x1050 and 1280x1024 but nothing else smaller.
It looks like my monitor was managing the  1680x1050 by mistake :) since the xorg was keeping my old CRT's modelines. Nevertheless I done under these conditions in commandline _ xvitune -show_ and I got the functioning 1680x1050 modeline for my LG L226WTQ   which I added in my new clean xorg.
So for the ones having the same monitor it goes like this:

Section "Monitor"
    Identifier    "L226W"
    modeline    "1680x1050"   119.00   1680 1728 1760 1840   1050 1053 1059 1080 +vsync        
EndSection

The only side effect so far is that ati control center is reporting a 59hz refresh while screen menu itself shows 60hz as it should.
I hope this helps somebody:)

You are my hero. I love you it worked by simply changing to your modeline and i am using a LG L225WT monitor. I have also compiz-fusion running perfect and installed ati driver with Envy. Have x1950 pro ati card.

---

