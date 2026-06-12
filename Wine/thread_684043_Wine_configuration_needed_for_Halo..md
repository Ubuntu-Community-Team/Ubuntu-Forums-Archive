---
title: "Wine configuration needed for Halo."
date: 2008-01-31
forum: Wine
---

### Post by indianballer24 on 2008-01-31
I have been searching for 2 hours now and I have not been able to find how to run Halo 1 or Halo trial on Wine 0.9.54. Many people claim they have got it to work but nobody ever gives a complete description. Does anyone know how to set this up. Thank you so much for your help.

---

### Post by Dark Aspect on 2008-01-31
> **indianballer24 said:**
> I have been searching for 2 hours now and I have not been able to find how to run Halo 1 or Halo trial on Wine 0.9.54. Many people claim they have got it to work but nobody ever gives a complete description. Does anyone know how to set this up. Thank you so much for your help.

Halo 1 broke after wine version 0.9.42.If you have crossover you can play the game though that other wise the only fix I know is to downgrade Wine.

---

### Post by Ferrat on 2008-01-31
> **Dark Aspect said:**
> Halo 1 broke after wine version 0.9.42.If you have crossover you can play the game though that other wise the only fix I know is to downgrade Wine.

As he said, others have gotten it to work with 0.9.54, maintainers at winehq rate it as gold with minor problems like not the best sound and mouse acts up sometimes like it does in wine with alot of apps

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720)

[QUOTE= WineHQ]
Installation

It is recommended that you modify your winecfg for ALSA and Windows XP/2K.

1) Download mfc42.dll from: [http://www.dll-files.com/dllindex/download.php?mfc42download0UKiRIdLjP](http://www.dll-files.com/dllindex/download.php?mfc42download0UKiRIdLjP)

2) Unzip mfc42.dll and place it into Wine's system32 folder.

3) Mount your Halo CD and run setup.exe.

4) Go through Setup as normal.

5) Go to Halo's folder on your HardDisk, and run haloupdate.exe and wait for it to update.

6) Download the version 1.07 no-cd patch here: [http://www.gameburnworld.com/dl/dl.php?file=HaloCombatEvolvedv1.07NoCDFixedexeEng.rar](http://www.gameburnworld.com/dl/dl.php?file=HaloCombatEvolvedv1.07NoCDFixedexeEng.rar)

^^^ Kudos to GameBurnWorld for the patch. =]

7) Extract and place it in your Halo folder (replace the older one).

8) Run halo.exe as is or with the arguments below, depending on your preference and system, then enjoy!


 
Command Line Arguments

If you feel adventurous, you can try these other arguments, as they may affect your gameplay to the better or the worse.
-?

Displays a list of all arguments.

-nosound
Disables all sound.

-novideo
Disables video playback.

-nojoystick 
Disables joystick/gamepads.

-nogamma
Disables adjustment of gamma.

-useff
Forces the game to run as a fixed function card.

-use11
Forces the game to run as a shader 1.1 card.

-use20
Forces the game to run as a shader 2.0 card.

-safemode
Disables as much as possible from the game.

-window
Runs the game in a window.

-width640
Forces the game to run at 640x480.

-vidmode w,h,r 
Forces the game to run at width, height, refresh rate.

-adapter x
Forces the game to run fullscreen on a multimon adaptor.

-port x
Server port address used when hosting games.

-cport x
Client port address used when joining games.

-ip x.x.x.x
Server IP address used when you have multiple IP addresses.

-screenshot
Enables the "Print Screen" key to generate screenshots

-timedemo
Runs four movies and writes out timedemo.txt.

-console
Enables the debugging console.

(Source: [http://www.gamespot.com/pc/action/halo/download.html?sid=6076971](http://www.gamespot.com/pc/action/halo/download.html?sid=6076971))
[/QUOTE]

---

### Post by indianballer24 on 2008-01-31
I did those exact steps but it did not work. How am I supposed to configure Wine. (Virtual desktop or not, if yes what size) What arguments should I use? (I only care about gameplay, I dont care about sound or cutscenes)

---

### Post by devguy on 2008-01-31
I'd also like some help with this.  I've tried those exact steps.  I've noticed that turning off all sound devices (oss/alsa) in winecfg allows me to get to the movies before the game starts.  However, once the movies finish, I get a blank virtual desktop with a little tab in bottom left corner that says Halo and is all garbled.  Then a prompt appears asking about an error and gives me options of "debug" or "exit" and both just quit wine.

I've also tried installing a swap space of 1024 mb (I have 1280mb RAM) and that didn't help.

Machine: Pentium M 1.7GHZ
1280mb DDR PC2700
ATI Mobility 9000 with default driver
Gutsy Gibbon
Wine 0.9.54

---

### Post by Ferrat on 2008-02-01
> **indianballer24 said:**
> I did those exact steps but it did not work. How am I supposed to configure Wine. (Virtual desktop or not, if yes what size) What arguments should I use? (I only care about gameplay, I dont care about sound or cutscenes)

Can you install it? 
if not, what does output say 

Can you start it? 
if not, what happens exactly, what does output say?

Comp specs?

Have you removed any previous installation of wine?

---

### Post by Ferrat on 2008-02-01
> **devguy said:**
> I'd also like some help with this.  I've tried those exact steps.  I've noticed that turning off all sound devices (oss/alsa) in winecfg allows me to get to the movies before the game starts.  However, once the movies finish, I get a blank virtual desktop with a little tab in bottom left corner that says Halo and is all garbled.  Then a prompt appears asking about an error and gives me options of "debug" or "exit" and both just quit wine.

I've also tried installing a swap space of 1024 mb (I have 1280mb RAM) and that didn't help.

Machine: Pentium M 1.7GHZ
1280mb DDR PC2700
ATI Mobility 9000 with default driver
Gutsy Gibbon
Wine 0.9.54


The little cube in the corner often indicate that there is a problem setting the right resolution, try standard 800x600 vir. desk and see what that does?

---

### Post by indianballer24 on 2008-02-01
The game installed fine but it wont start. How do I get the output?

Computer specifications:

1GB of RAM DDR II SDRAM - 533 MHz

Intel Core 2 Duo T5500 / 1.66 GHz

Graphics Processor / Vendor- Intel GMA 950

Video Memory-  Dynamic Video Memory Technology 3.0

Max Allocated RAM Size- 128 MB

Gutsy Gibbon 7.10


I did a clean install of wine just before I installed halo.

---

### Post by devguy on 2008-02-01
> **Ferrat said:**
> The little cube in the corner often indicate that there is a problem setting the right resolution, try standard 800x600 vir. desk and see what that does?

Yeah, I have it set to run a virtual desktop at 800,600.  I've tried 640,480, and 1024,768 all to no avail.

I even tried using Cedega, but all that  happens is that it won't start because it can't find the CD, even though it was in the DVD rom drive.  If I try a no cd crack, Cedega started opening up about 5 new windows a second, quickly making me have to ctrl+alt+backspace.  It wouldn't let me patch the game to the newest version, either.

---

### Post by Ferrat on 2008-02-02
> **indianballer24 said:**
> The game installed fine but it wont start. How do I get the output?

Computer specifications:

1GB of RAM DDR II SDRAM - 533 MHz

Intel Core 2 Duo T5500 / 1.66 GHz

Graphics Processor / Vendor- Intel GMA 950

Video Memory-  Dynamic Video Memory Technology 3.0

Max Allocated RAM Size- 128 MB

Gutsy Gibbon 7.10


I did a clean install of wine just before I installed halo.

with output I mean what comes out when you launch it in a terminal 

if you're unsure of the commands best is to just select pref. on the shortcut and copy paste whatever command that uses :)

Don't have Halo myself but will see if I can't get a cd to try out and see if I can make it work :)

---

### Post by indianballer24 on 2008-02-04
Here is the output when I put it into terminal. When I try to launch it this way an error message comes up  telling me that the config.txt file is missing. But when I launch it using the shortcut I don't get this error.

indianballer24@indianballer24-laptop:~$ env WINEPREFIX="/home/indianballer24/.wine" wine "C:\Program Files\Microsoft Games\Halo\halo.exe"
fixme:win:EnumDisplayDevicesW ((null),0,0x34d510,0x00000000), stub!
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x134db0, L"dwDirectXVersionMajor", 0x34d948)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x134db0, L"dwDirectXVersionMinor", 0x34d948)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x134db0, L"szDirectXVersionLetter", 0x34d948)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x134db0, L"szDirectXVersionEnglish", 0x34d948)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x134db0, L"szDirectXVersionLongEnglish", 0x34d948)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x134db0, L"bDebug", 0x34d948)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x135030, L"DxDiag_SystemInfo", 0x134db0)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x135030, L"DxDiag_SystemDevices", 0x136488)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x135030, L"DxDiag_LogicalDisks", 0x1364f8)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136560,L"ddraw.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szPath", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szName", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bExists", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szVersion", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szAttributes", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szLanguageEnglish", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeHigh", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeLow", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bBeta", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bDebug", 0x34cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136560,L"dplayx.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szPath", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szName", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bExists", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szVersion", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szAttributes", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szLanguageEnglish", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeHigh", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeLow", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bBeta", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bDebug", 0x34cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136560,L"dpnet.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szPath", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szName", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bExists", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szVersion", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szAttributes", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szLanguageEnglish", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeHigh", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeLow", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bBeta", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bDebug", 0x34cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136560,L"dinput.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szPath", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szName", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bExists", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szVersion", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szAttributes", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szLanguageEnglish", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeHigh", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeLow", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bBeta", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bDebug", 0x34cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136560,L"dinput8.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szPath", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szName", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bExists", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szVersion", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szAttributes", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szLanguageEnglish", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeHigh", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeLow", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bBeta", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bDebug", 0x34cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136560,L"dsound.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szPath", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szName", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bExists", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szVersion", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szAttributes", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szLanguageEnglish", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeHigh", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeLow", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bBeta", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bDebug", 0x34cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136560,L"dswave.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szPath", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szName", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bExists", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szVersion", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szAttributes", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szLanguageEnglish", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeHigh", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeLow", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bBeta", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bDebug", 0x34cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136560,L"d3d8.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szPath", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szName", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bExists", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szVersion", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szAttributes", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szLanguageEnglish", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeHigh", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeLow", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bBeta", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bDebug", 0x34cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136560,L"d3d9.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szPath", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szName", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bExists", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szVersion", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szAttributes", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szLanguageEnglish", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeHigh", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeLow", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bBeta", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bDebug", 0x34cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136560,L"dmband.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szPath", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szName", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bExists", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szVersion", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szAttributes", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szLanguageEnglish", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeHigh", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeLow", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bBeta", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bDebug", 0x34cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136560,L"dmcompos.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szPath", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szName", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bExists", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szVersion", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szAttributes", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szLanguageEnglish", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeHigh", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeLow", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bBeta", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bDebug", 0x34cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136560,L"dmime.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szPath", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szName", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bExists", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szVersion", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szAttributes", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szLanguageEnglish", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeHigh", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeLow", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bBeta", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bDebug", 0x34cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136560,L"dmloader.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szPath", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szName", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bExists", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szVersion", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szAttributes", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szLanguageEnglish", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeHigh", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeLow", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bBeta", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bDebug", 0x34cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136560,L"dmscript.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szPath", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szName", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bExists", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szVersion", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szAttributes", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szLanguageEnglish", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeHigh", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeLow", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bBeta", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bDebug", 0x34cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136560,L"dmstyle.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szPath", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szName", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bExists", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szVersion", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szAttributes", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szLanguageEnglish", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeHigh", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeLow", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bBeta", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bDebug", 0x34cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136560,L"dmsynth.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szPath", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szName", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bExists", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szVersion", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szAttributes", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szLanguageEnglish", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeHigh", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeLow", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bBeta", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bDebug", 0x34cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136560,L"dmusic.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szPath", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szName", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bExists", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szVersion", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szAttributes", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szLanguageEnglish", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeHigh", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeLow", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bBeta", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bDebug", 0x34cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136560,L"devenum.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szPath", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szName", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bExists", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szVersion", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szAttributes", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szLanguageEnglish", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeHigh", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeLow", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bBeta", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bDebug", 0x34cd88)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x136560,L"quartz.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szPath", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szName", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bExists", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szVersion", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szAttributes", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"szLanguageEnglish", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeHigh", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"dwFileTimeLow", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bBeta", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x136560, L"bDebug", 0x34cd88)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x135030, L"DxDiag_DirectXFiles", 0x136560)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x13aed0, L"0", 0x13aef0)
fixme:win:EnumDisplayDevicesW ((null),0,0x34d1e8,0x00000000), stub!
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aef0, L"szDeviceName", 0x34cf58)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aef0, L"szDescription", 0x34cf48)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aef0, L"szDisplayMemoryLocalized", 0x34cf38)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aef0, L"szDisplayMemoryEnglish", 0x34cf28)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aef0, L"dwWidth", 0x34cf18)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aef0, L"dwHeight", 0x34cf08)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aef0, L"dwBpp", 0x34cef8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aef0, L"szVendorId", 0x34cee8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aef0, L"szDeviceId", 0x34ced8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aef0, L"szKeyDeviceKey", 0x34cec8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13aef0, L"szKeyDeviceID", 0x34ceb8)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x135030, L"DxDiag_DisplayDevices", 0x13aed0)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x13b668, L"DxDiag_SoundDevices", 0x13b688)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x13b668, L"DxDiag_SoundCaptureDevices", 0x13b6d8)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x135030, L"DxDiag_DirectSound", 0x13b668)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x135030, L"DxDiag_DirectMusic", 0x13b798)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x135030, L"DxDiag_DirectInput", 0x13b800)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x135030, L"DxDiag_DirectPlay", 0x13b868)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x13bbf8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13bbf8, 1, 0x13bc10)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szCatName", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidCat", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidFilter", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwMerit", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwInputs", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwOutputs", 0x34ce88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13bbf8, 1, 0x13bc28)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szCatName", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidCat", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidFilter", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwMerit", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwInputs", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwOutputs", 0x34ce88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13bbf8, 1, 0x13c0a0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szCatName", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidCat", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidFilter", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwMerit", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwInputs", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwOutputs", 0x34ce88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13bbf8, 1, 0x13c490)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szCatName", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidCat", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidFilter", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwMerit", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwInputs", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwOutputs", 0x34ce88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13bbf8, 1, 0x13ca78)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szCatName", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidCat", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidFilter", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwMerit", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwInputs", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwOutputs", 0x34ce88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13bbf8, 1, 0x13cea0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szCatName", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidCat", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidFilter", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwMerit", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwInputs", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwOutputs", 0x34ce88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13bbf8, 1, 0x13d2f8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szCatName", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidCat", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidFilter", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwMerit", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwInputs", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwOutputs", 0x34ce88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x13b9b8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x13b9b8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x13b9c0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13b9c0, 1, 0x13b9d8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szCatName", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidCat", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dsnoop:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidFilter", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwMerit", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwInputs", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwOutputs", 0x34ce88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x13b988)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13b988, 1, 0x13b9a0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szCatName", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidCat", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Midi Through"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidFilter", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwMerit", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwInputs", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwOutputs", 0x34ce88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x13b9b8)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x13b9b8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13b9b8, 1, 0x13e458)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szCatName", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidCat", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"DirectSound: dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidFilter", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwMerit", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwInputs", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwOutputs", 0x34ce88)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x13b9b8, 1, 0x13e470)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szCatName", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidCat", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34cea8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szClsidFilter", 0x34cea8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"szName", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwMerit", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwInputs", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x13b8d0, L"dwOutputs", 0x34ce88)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x135030, L"DxDiag_DirectShowFilters", 0x13b8d0)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x135030, L"DxDiag_DirectSound.DxDiag_SoundDevices", 0x34d9cc)
indianballer24@indianballer24-laptop:~$

---

### Post by indianballer24 on 2008-02-05
Any ideas Ferrat?

---

### Post by devguy on 2008-02-12
Hmm, I just tried Halo again using the new version of Wine (0.9.55) and still no good.  It is odd that I can view the intro movies, but as soon as they finish, the whole application minimizes to the bottom left of the Wine Desktop and Halo throws an error in it with both options (debug/close) causing Wine to quit.

Halo in safemode doesn't help either (neither does -use11 flag).  Any ideas?

---

### Post by indianballer24 on 2008-02-14
> **devguy said:**
> Hmm, I just tried Halo again using the new version of Wine (0.9.55) and still no good.  It is odd that I can view the intro movies, but as soon as they finish, the whole application minimizes to the bottom left of the Wine Desktop and Halo throws an error in it with both options (debug/close) causing Wine to quit.

Halo in safemode doesn't help either (neither does -use11 flag).  Any ideas?
Have you tried "-nosound" and "-novideo"?

---

### Post by devguy on 2008-02-15
> **indianballer24 said:**
> Have you tried "-nosound" and "-novideo"?

Yeah, still no good.

---

### Post by indianballer24 on 2008-02-16
Maybe you should try these. Make sure your running it in a virtual desktop. Tell me if it works.

-novideo
-nosound
-vidmode w,h,r
      (set width, height, and refresh rate the same as your virtual desktop)

and then if all that doesnt work add safemode
-safemode


make sure you put them all in the shortcut at the same time.

---

### Post by devguy on 2008-02-17
> **indianballer24 said:**
> Maybe you should try these. Make sure your running it in a virtual desktop. Tell me if it works.

-novideo
-nosound
-vidmode w,h,r
      (set width, height, and refresh rate the same as your virtual desktop)

and then if all that doesnt work add safemode
-safemode


make sure you put them all in the shortcut at the same time.

I've tried every combination of every switch I can find, and none seem to work (including the ones you posted).  :confused:

---

### Post by indianballer24 on 2008-02-21
What are the specifications for your system?

---

### Post by devguy on 2008-02-22
> **indianballer24 said:**
> What are the specifications for your system?

Pentium M Dothan 1.7ghz
1x1024 PC2700 + 1x256 PC2700
ATI Radeon 9000 Mobility 32mb
80GB ATA/6 5400RPM Hitachi
Dell 1024x768 laptop display
Ubuntu 7,10 x86 Gutsy
1024mb Swap partition

---

### Post by indianballer24 on 2008-02-23
> **devguy said:**
> Pentium M Dothan 1.7ghz
1x1024 PC2700 + 1x256 PC2700
ATI Radeon 9000 Mobility 32mb
80GB ATA/6 5400RPM Hitachi
Dell 1024x768 laptop display
Ubuntu 7,10 x86 Gutsy
1024mb Swap partition
Your processer's probably not good enough to run halo on wine. It wouldn't hurt to upgrade your RAM to 2GB either. PC2700 is really outdated. You should probably just buy a better computer.

---

