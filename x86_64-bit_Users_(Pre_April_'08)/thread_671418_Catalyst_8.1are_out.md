---
title: "Catalyst 8.1are out"
date: 2008-01-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by aypnia on 2008-01-18
Just checked ati-amd new driver is out

---

### Post by aypnia on 2008-01-18
Resolved Issues

The following section provide a brief description of resolved issues with the latest version of the ATI Catalyst™ Linux software suite. These include:

    * Corruption will no longer be noticed in the lower right corner of the display or on the mouse pointer after the system is running for a long period of time
    * Connecting a display device that supports 1680x1050 to a system running Linux will no longer result in a maximum display resolution of 1280x1024 only being available
    * Custom mode lines in xorg.conf will no longer be ignored by the fglrx driver
    * Suspending to RAM or DISK on kernel version 2.6.23 or later no longer fails 

Known Issues

The following section provides a brief description of known issues associated with the latest version of ATI Catalyst™ Linux software suite. These issues include:

    * On workstation hardware 3D applications will be corrupted if the screen width is not an integer multiple of 64 pixels, for example with a 1680x1050 wide screen display. Further details can be found in topic number 737-31720
    * There is no support for video playback on the second head in dual head mode. Further details can be found in topic number 737-26985
    * Desktop corruption may be noticed when dragging the overlay/video when using dual-display mode. Further details can be found in topic number 737-29578
    * A black screen may be observed on some hardware when switching to the console or leaving the X window system when a Vesa framebuffer console driver is used. Further details can be found in topic number 737-30687
    * Display flicker may be noticed when the gnome screen-saver starts
    * Diagonal tearing may be noticed when playing a video file using a video player that utilizes the XVideo extension
    * Video playback may look blocky when playing a video file using a video player that utilizes the XVideo extension
    * Video Playback may display wrong colors and additional shadow images when cropping or expanding a video file using a video player that utilizes the XVideo extension
    * Building RPM packages for Mandriva may fail

---

### Post by crjackson on 2008-01-19
I can't wait to hear how everyone feels about this one.  I'm sure it'll be a few more releases before I'm going to upgrade all my ATI systems, but I crave for the switch when it's good.

---

### Post by hangfire on 2008-01-19
I tried them on GG/64. They won't allow my ATi 9550 to drive my 1680x1050 in digital mode, only in analog. And that only after considerable hacking of xorg.conf . However my SyncMaster 204BW has always had fuzzy analog, so that's a non-starter.

I tried 8.1 because the last xorg.conf update introduced some serious flashing problems with my setup, and then the last Ubuntu ATi proprietary driver update broke video altogether. Yup, boot to Black Screen of Death (Yes I know about Ctrl-Alt-F1/F2/F3). What's more, with 1/2 dozen install/uninstalls of ATI drivers, something deleted my original (precious) xorg.conf . I know, I should have had a backup...

After spending two weeks on this... I'm rather humiliated, as I liked telling people I'm running 64 bit Linux on last-generation H/W and it works great, can watch videos, flash animation (though that came a little late too), etc., etc., now I'm back to 2D and flash-only for video. Ha!

I have a plan for a way out of this mess. I'm looking for a good, cheap last-gen nVIDIA card.

I expected some problems with running 64-bit, and I was very pleasantly surprised to get things running with an ATi card a couple of months ago on my first trial install of GG/64. I am not surprised at all that the happiness all came to an end due to the ATi card. I had planned to replace it just to run Linux anyway, thought I'd just give it a shot to see how badly ATi's drivers still suck- I wasn't disappointed. It just took an extra month for ATi to show its true colors.

HF

---

### Post by Kilz on 2008-01-20
> **hangfire said:**
> I tried them on GG/64. They won't allow my ATi 9550 to drive my 1680x1050 in digital mode, only in analog. And that only after considerable hacking of xorg.conf . However my SyncMaster 204BW has always had fuzzy analog, so that's a non-starter.

I tried 8.1 because the last xorg.conf update introduced some serious flashing problems with my setup, and then the last Ubuntu ATi proprietary driver update broke video altogether. Yup, boot to Black Screen of Death (Yes I know about Ctrl-Alt-F1/F2/F3). What's more, with 1/2 dozen install/uninstalls of ATI drivers, something deleted my original (precious) xorg.conf . I know, I should have had a backup...

After spending two weeks on this... I'm rather humiliated, as I liked telling people I'm running 64 bit Linux on last-generation H/W and it works great, can watch videos, flash animation (though that came a little late too), etc., etc., now I'm back to 2D and flash-only for video. Ha!

I have a plan for a way out of this mess. I'm looking for a good, cheap last-gen nVIDIA card.

I expected some problems with running 64-bit, and I** was very pleasantly surprised to get things running with an ATi card a couple of months ago on my first trial install of GG/64**. I am not surprised at all that the happiness all came to an end due to the ATi card. I had planned to replace it just to run Linux anyway, thought I'd just give it a shot to see how badly ATi's drivers still suck- I wasn't disappointed. It just took an extra month for ATi to show its true colors.

HF

Why not install the 8.40.4 drivers from the old code base that worked instead of buying more hardware?

---

### Post by hangfire on 2008-01-20
8.40.4? My Synaptic lists 8.37-6 as the latest/greatest available from Ubuntu. Are you suggesting getting a Debian or straight-from-AMD release?

Why buy new hardware? To punish AMD/ATi. Seven months ago they gave a big interview to Phoronix on their Linux development lifecycle; things were supposed to get better and better consistantly, incrementally, continuously.

Instead they are still chasing occasional features and leaving a trail of dead video card models and monitors behind, breaking as more than they add. Why break the 9500/9550? (I'm not the only one). Why leave behind all 1680x1050 users? That's the sweet spot in monitor buying right now. Does this make ANY sense?

nVIDIA's Linux releases, while more occasional, actually WORK. This is not just my opinion. Ask my Purchasing dept how many laptops to back to Dell every time they substitute ATi for nVIDIA. Every single one of them, because the programmers and engineers just can't get them to work. As soon as someone declares victory, something else breaks.

I, in my hubris, thought I could buck the trend and run an ATi at home and fix it and keep it running by sheer will power. I'll admit it, I'm beat. Me and my money are going to nVIDIA.

-HF

---

### Post by Kilz on 2008-01-21
> **hangfire said:**
> 8.40.4? My Synaptic lists 8.37-6 as the latest/greatest available from Ubuntu. Are you suggesting getting a Debian or straight-from-AMD release?

Why buy new hardware? To punish AMD/ATi. Seven months ago they gave a big interview to Phoronix on their Linux development lifecycle; things were supposed to get better and better consistantly, incrementally, continuously.

Instead they are still chasing occasional features and leaving a trail of dead video card models and monitors behind, breaking as more than they add. Why break the 9500/9550? (I'm not the only one). Why leave behind all 1680x1050 users? That's the sweet spot in monitor buying right now. Does this make ANY sense?

nVIDIA's Linux releases, while more occasional, actually WORK. This is not just my opinion. Ask my Purchasing dept how many laptops to back to Dell every time they substitute ATi for nVIDIA. Every single one of them, because the programmers and engineers just can't get them to work. As soon as someone declares victory, something else breaks.

I, in my hubris, thought I could buck the trend and run an ATi at home and fix it and keep it running by sheer will power. I'll admit it, I'm beat. Me and my money are going to nVIDIA.

-HF

Phoronix did something stupid. They hyped the first release of a whole new code base. In linux software is released so the community can help find bugs. Thats what happened. It was buggy and they were found. In other words those that install new software are guinea pigs.
Buy what you want, but a lot of people run ATI cards without problems. We just dont buy into hype, or have a " I must have this new software just because its new" frame of mind. Look even Ubuntu (8.37-6) hasnt started using the code base because they know its beta quality right now.
Each release has been getting better. But its always a good idea to keep stable drivers unless something isnt working, or at least wait till real users have tested them and reported back.
The 8.40.4 was the last of the old code base, I went back to them and they work great. Im waiting for at least a few more months before I will install the completely new drivers, that or wait till someone says they are ready on the forum.

[You can get the 8.40.4 drivers here.]("http://ati.amd.com/support/drivers/linux64/previous/linux64-r-8-40-4.html") then use [this howto to install them.]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually")

---

### Post by hangfire on 2008-01-21
Thank you for the links, I'll give them a try. I've tried everything else.

I don't have a latest-greatest mindset. The latest Ubuntu release broke my ATi, now I have no 3D or video. Getting the latest from ATi direct didn't fix it, either. I install Ubuntu patches because I expect them to fix bugs and patch security, not because I want to try the latest-greatest.

My main point is that ATi has not moved forward much, has broken more, and has not made good on their promise to create an open-source driver better than xorg's and almost as good as their proprietary.

-HF

---

### Post by hangfire on 2008-01-21
I installed according to the directions.

No digital. No video.

grep EE /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): === [swlDalHelperAddCustomizeMode] === CWDDEDI_DisplayGetSetModeTimingOverride failed: 7
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.
(EE) AIGLX: Screen 0 is not DRI capable
$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

Restricted drivers are enabled.

$ sudo dkms remove -m fglrx -v 8.4331 --all

Error! There are no instances of module: fglrx
8.4331 located in the DKMS tree.

(after reboot and a couple of Ctrl-Alt-Bksp's.

?????

-HF

---

### Post by Kilz on 2008-01-21
You might want to go through those instructions again because the ati drivers are not installed. Make sure to edit all commands to reflect the change in version numbers.

---

### Post by hangfire on 2008-01-21
The ATi drivers were installed. Swapping out my xorg.conf for an older one fixed it without any further action (then a Ctrl-Alt-Bksp, anyway).

The major difference was a large level of detail about my monitor was in the broken xorg.conf and not present in the simple one.

Most (not all, alas) of the driver reinstalls I've been doing made a backup of the xorg.conf. After installation and config, I always tried the backlog of xorg.conf's to see if any previous one worked. (I've been Ctrl-Alt-Deleting a LOT). Sometimes one would work a little better than another, but none to my full satisfaction since the xorg/fglrx ubuntu updates last month.

So, my current problem after 8.40 was xorg.conf, but that doesn't explain the other problems I've been having.

Anyway, it's fixed and fixed-in-place now. Thanks for the advice and encouragement, it gave me the motivation to keep going and find a solution.

-HF

---

### Post by Kilz on 2008-01-22
> **hangfire said:**
> The ATi drivers were installed. Swapping out my xorg.conf for an older one fixed it without any further action (then a Ctrl-Alt-Bksp, anyway).

The major difference was a large level of detail about my monitor was in the broken xorg.conf and not present in the simple one.

Most (not all, alas) of the driver reinstalls I've been doing made a backup of the xorg.conf. After installation and config, I always tried the backlog of xorg.conf's to see if any previous one worked. (I've been Ctrl-Alt-Deleting a LOT). Sometimes one would work a little better than another, but none to my full satisfaction since the xorg/fglrx ubuntu updates last month.

So, my current problem after 8.40 was xorg.conf, [B]but that doesn't explain the other problems I've been having.
[/B]
Anyway, it's fixed and fixed-in-place now. Thanks for the advice and encouragement, it gave me the motivation to keep going and find a solution.

-HF

The problems are because ATI in its infinite wisdom decided to start fresh with a complete driver rewrite after 8.40.4. They then did exactly what every other linux software developer does, release barely usable code so the community can find the bugs.
Thats why people who must have the newest software and updates suffer all the bugs. The 8.40 drivers had been in development for years, they worked. Until the bugs are worked out dont fall for the hype and keep the ones you have. If it isnt broke, dont fix it.

---

### Post by r!ots on 2008-01-22
I wanted to update to the new 8.01 drivers but I'm not even able to uninstall my 7.12 drivers which I installed using this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide").

So I wanted to follow the same guide for the 8.01 drivers and first of all tried to uninstall xorg-driver-fglrx via Synaptic.
Unfortunately I got the following error message:

> E: xorg-driver-fglrx: subprocess post-removal script returned error exit status 2

So I did
```
 sudo apt-get purge xorg-driver-fglrx
```

and got this error message:
> (Reading database ... 115781 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: rename involves overwriting `/etc/xdg/compiz/compiz-manager' with
  different file `/etc/xdg/compiz/compiz-manager.ubuntu', not allowed
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas why this is happening?

---

### Post by Melcar on 2008-01-22
> **r!ots said:**
> I wanted to update to the new 8.01 drivers but I'm not even able to uninstall my 7.12 drivers which I installed using this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide").

So I wanted to follow the same guide for the 8.01 drivers and first of all tried to uninstall xorg-driver-fglrx via Synaptic.
Unfortunately I got the following error message:



So I did
```
 sudo apt-get purge xorg-driver-fglrx
```

and got this error message:


Any ideas why this is happening?

Used to get the same thing.  Basically, when you generated and installed the packages, some files for Compiz got overwritten.  I ended up purging and re-installing Compiz at the end.  If you install the driver with the .run script this does not happen.

For me, the driver works "perfectly".  Most of the issues from previous releases are still there, except for the screen resolution bug and the annoying corruption around the mouse pointer.  Running a HD2900XT.

---

### Post by aypnia on 2008-01-23
My opinion  is that this it's probably the best proprietary driver and a major improvement from the previous version. I got though for 1st time a couple of lockups which I believe they are connected with the recent xorg updates.
I shouldn't also forget to mention that I observed for 1st time simultaneous functionality of compiz and other 3d apps (like google earth for example) although with a flickering.
A step towards the right direction good job  from ATI

---

### Post by kellemes on 2008-01-23
> **aypnia said:**
> A step towards the right direction good job  from ATI

Nice it works out for you :-)

For me it really sucks, the last three versions of this stupid driver don't work for so I'm forced to use 8.42.3 (works barely)
I spend too much time on this peace of crap.

Next investment will be a not-ati-card. It's a pity since in general they're much better and better priced as there NVidia counterparts.

---

### Post by r!ots on 2008-01-23
> Used to get the same thing. Basically, when you generated and installed the packages, some files for Compiz got overwritten. I ended up purging and re-installing Compiz at the end. If you install the driver with the .run script this does not happen.

Well I can't install or uninstall anything at the moment, since this stupid error message I get from trying to uninstall the xorg-driver-fglrx package is blocking all other actions in synaptic or apt-get. It is marked as autoremovable and is therefore always processed when I take any other action.
Help, plz..

---

### Post by angels on 2008-01-24
I installed 8.01 as well, but I have some problems with it. As I have previously installed Catalyst 7.12, I was thinking that maybe I have to uninstall it. Can someone suggest me how to do that?
Anyway, I'm thinking to uninstall 8.01, too ... since it really bothers me that my computer freezes everytime I try to logout. Any ideas? 

Thanks for your help.

---

### Post by immesys on 2008-01-24
I was having some grief installing the 8.1 drivers so I completely reinstalled gutsy and followed this guide to the letter (2nd option): 
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

After I log in though, I get a white screen, and nothing else. The X.org.0 log says only the following in terms of errors:

```

(EE) fglrx(0): Failed to initialize CMMQS driver.
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb7f39000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

But I've had no DRI before and it didn't give me a white screen of death. Has anybody else managed to solve this problem?

ATI X800XT AGP
AMD 3400+
Ubuntu Gutsy (Updates to Jan 23rd)

---

### Post by jaozze on 2008-02-09
i Have the same problem, but is with 3D. 
i have 1 monitor syncmaster 920nw 1440x900 and with free driver can't get the widescreen resolution, but with the fglrx can get the resolution but the 3d acel. doesn't work.

here is mi Xorg.0.log.

(EE) fglrx(0): Failed to initialize CMMQS driver.
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb770f000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xe8000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1472,8191)
.
.
.
II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"

i supouse ati driver doesn't work because i havent found any solution

if anyone knows how i can resolve it, post it please

Thankyou.:guitar:

---

### Post by Kilz on 2008-02-09
> **jaozze said:**
> i Have the same problem, but is with 3D. 
i have 1 monitor syncmaster 920nw 1440x900 and with free driver can't get the widescreen resolution, but with the fglrx can get the resolution but the 3d acel. doesn't work.

here is mi Xorg.0.log.

(EE) fglrx(0): Failed to initialize CMMQS driver.
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb770f000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xe8000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1472,8191)
.
.
.
II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"

i supouse ati driver doesn't work because i havent found any solution

if anyone knows how i can resolve it, post it please

Thankyou.:guitar:

what does fglrxinfo give?

---

### Post by jaozze on 2008-02-09
sorry, i forgot to say i have an ATI X850XT AGP card  in a P4

---

### Post by jaozze on 2008-02-09
> **Kilz said:**
> what does fglrxinfo give?

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3)

say that, but i think is because after the error the log gives me 2 warnings saying this:

```
(EE) fglrx(0): Failed to initialize CMMQS driver.
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb770f000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xe8000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1472,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1472,900) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1472 x 7291
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(**) fglrx(0): Video overlay enabled on CRTC1
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

(WW) fglrx(0): Option "VendorName" is not used //this is what i think changes with the error
(WW) fglrx(0): Option "ModelName" is not used

(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
```

---

### Post by Kilz on 2008-02-09
> **jaozze said:**
> display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3)


The reason you are not getting 3d acceeration is because you dont have the ATI drivers working.  fglrxinf should say ATI not Mesa. [This howto is the best for getting the ATI drivers working.]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually")

---

### Post by jaozze on 2008-02-11
Nothing... i've tried to install the driver 3 times or more in a clean installation of Ubuntu and can't get  3D accel. I dont know what's happening... Now when i write glxinfo gives me core dumped error...

I supouse is the first error in the "cat /var/log/Xorg.0.log | grep EE"

(EE) fglrx(0): Failed to initialize CMMQS driver. <-----This one...
(EE) AIGLX: Screen 0 is not DRI capable

Anyone knows what means that?

i'm really sad.... (CAUSE I WANT MY DESKTOP LIKE MY FRIENDS!!!) jejej Joking...

really i would like to know what's happening with my card...](*,)](*,)

---

### Post by Yellow Pasque on 2008-02-11
If anyone has a recent ATI card and isn't concerned with 3D accel, then I highly recommend the open-source radeonhd driver (link is in my sig). It's what I use nowadays.

If 3d accel is a must, then I second Kilz's suggestion of using 8.40.4. No, that version does not support AIGLX/Compiz, but I'd rather see users have their systems working properly than having busted systems with working eye candy.

---

### Post by Páraquedas_cascais on 2008-02-13
Hi, newbie ubuntu user, tried to install my ASUS EAH3870, but my screen turn black, a nice black screen could see nothing lollll... well few days after i install ENVY, now i have a nice white screen, very pure white screen... can some guru, patient guru help me? Thanks... 

:(

---

### Post by Kilz on 2008-02-13
> **Páraquedas_cascais said:**
> Hi, newbie ubuntu user, tried to install my ASUS EAH3870, but my screen turn black, a nice black screen could see nothing lollll... well few days after i install ENVY, now i have a nice white screen, very pure white screen... can some guru, patient guru help me? Thanks... 

:(

You might want to read posts 19- 24 in this thread.

---

### Post by Yellow Pasque on 2008-02-13
Catalyst 8.02 is out today, but doesn't include many fixes (still has AGP issues). I pity you poor souls using it. Oh well, there's always next month, right..?
EDIT: [http://www.phoronix.com/scan.php?page=article&item=999&num=1](http://www.phoronix.com/scan.php?page=article&item=999&num=1)

---

