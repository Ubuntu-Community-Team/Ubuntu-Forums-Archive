---
title: "WoW freezes after accepting EULA"
date: 2008-08-19
forum: Wine
---

### Post by anthony.phipps on 2008-08-19
So I've searched and searched for days and still haven't found a problem. I turn to you, oh grand community of ubuntu.

So i can open WoW and accept both the little EULA things, right after i click accept on the 2nd one the game freezes my entire pc. 

[LIST]
[*]No CTRL+ALT F1 or Backspace...when it freezes me up
[*]I am running the latest Wine.
[*]I have applied every single troubleshooting technique on this page
[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)
[*]Im running hardy heron on a Lenovo Thinkpad R61
[/LIST]

please ask for more info if you need it...

one last thing, rock on!
:guitar:

---

### Post by Eviljim on 2008-08-19
Does your machine have the Intel GMA X3100 graphics card inside??

If so try here

[http://forums.wow-europe.com/thread.html;jsessionid=BBC5143D974336AD2A5BC1A5DCB86584.app09_02?topicId=3615101564&sid=1]("http://forums.wow-europe.com/thread.html;jsessionid=BBC5143D974336AD2A5BC1A5DCB86584.app09_02?topicId=3615101564&sid=1")

[http://www.intel.com/support/graphics/sb/CS-025607.htm]("http://www.intel.com/support/graphics/sb/CS-025607.htm")

If there are problems with windows drivers, you might want to find some earlier Ubuntu ones?

Regards

---

### Post by anthony.phipps on 2008-08-19
> tony@tony-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
tony@tony-laptop:~$ 


no but im gonna try the SET uiFaster "0" and see what else is offered..thanks for the reference.

EDIT: apparently i DO have the X3100 based on [http://www.intellinuxgraphics.org/documentation.html](http://www.intellinuxgraphics.org/documentation.html)
> The Mobile Intel® GM965 Express Chipset is the whole piece of silicon, including PCI Express, memory, and CPU interfaces along with the graphics accelerator. The Mobile Intel® Graphics Media Accelerator X3100 is just that part of the GM965 which is used for graphics.

---

### Post by anthony.phipps on 2008-08-19
my problem doesnt really coincide with theirs...they have intermittent crashes whereas i can recreate the exact moment over and over...right after the Terms of Use agreement disappears the computer freezes...no crash or black screen, just freeze...

*scratches head*

EDIT: btw SET uiFaster "0" didn't work =P

---

### Post by anthony.phipps on 2008-08-19
just to make sure, i installed the latest driver...not sure how to roll it back

> tony@tony-laptop:~$ sudo apt-get install xserver-xorg-video-intel
[sudo] password for tony: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
The following packages were automatically installed and are no longer required:
  x11proto-kb-dev mesa-common-dev libxdmcp-dev xtrans-dev x11proto-core-dev
  libglu1-mesa-dev dkms x11proto-input-dev libpthread-stubs0-dev libxau-dev
  libpthread-stubs0 libgl1-mesa-dev libx11-dev libxcb-xlib0-dev libxcb1-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
tony@tony-laptop:~$ 

---

### Post by justin99 on 2008-08-19
I might remember having a similar problem, when my removable disk was mounted so that my user only had read-only access to the Wow directory. Unmounting and remounting as my user (instead of root owner) fixed it for me.. check permissions in that folder, can you make a new file there to prove that you have write permisssions? I think Wow.exe tries to write out to disk that you have accepted the EULA, and then barfs. Just a thought.
You can use the the command
chown -R user:user /path/to/wow
to change the owner to those files if this is the case.

---

### Post by Eviljim on 2008-08-20
> **justin99 said:**
> I might remember having a similar problem, when my removable disk was mounted so that my user only had read-only access to the Wow directory. Unmounting and remounting as my user (instead of root owner) fixed it for me.. check permissions in that folder, can you make a new file there to prove that you have write permisssions? I think Wow.exe tries to write out to disk that you have accepted the EULA, and then barfs. Just a thought.
You can use the the command
chown -R user:user /path/to/wow
to change the owner to those files if this is the case.

Ah, yes, very true. WoW will need to write to the config.wtf file located in your /wow/wtf folder for sure.

Maybe thats the issue?

---

### Post by anthony.phipps on 2008-08-20
that was actually a pretty good idea but it didn't work for me...same results >.<

here's the command i ran
> tony@tony-laptop:~$ chown -R tony "/home/tony/.wine/drive_c/Program Files/World of Warcraft"

---

### Post by anthony.phipps on 2008-08-20
so i read around and looked at some other people's config.wtf files they posted...
then i added two lines to my config.wtf file:
```
SET readEULA "1"
SET readTOS "1"
```
and it worked!

now i can log in but i have a corrupt data file so i still gotta recopy the game :lolflag:

thanks for your suggestions!

---

### Post by anthony.phipps on 2008-08-20
```
ERROR #131 (0x85100083) File Corrupt

Program:	C:\Program Files\World of Warcraft\WoW.exe

File:	character\tauren\male\taurenmale.m2
```

the latest and greatest error. I get this when i select my tauren male character at the character select screen...even after i recopied from a known working WoW installation. i guess ill ask a friend to copy his wow folder for me off his mac!

---

### Post by anthony.phipps on 2008-08-20
for anyone following i found i need to redownload wow.exe. i renamed it to 1wow.exe and ran the repair.exe found in the /world of warcraft/ folder. 

Now i have to download patch 2.3.0 just to update that one file...too bad the repair.exe doesnt download the latest one lol...anyway ill write back in 713mb from now, or after work tomorrow!

---

### Post by bumpycat on 2008-09-27
A followup to your thread - I'm also running Ubuntu (8.04) on a Thinkpad R61e. I've gone through various problems and can now start WOW and get all the way to character selection. However, as soon as I choose a character and enter the game world, the game freezes (sometimes with terrain graphic glitches). I don't suppose you encountered anything like this? Could you post the contents of your Config.wtf?

Thanks in advance!

My Config.wtf:

SET locale "enGB"
SET realmList "eu.logon.worldofwarcraft.com"
SET patchlist "eu.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxAPI "opengl"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET M2UseShaders "0"
SET videoOptionsVersion "1"
SET textureFilteringMode "0"
SET pixelShaders "1"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET readTerminationWithoutNotice "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET Sound_EnableHardware "1"
SET SmallCull "0.080000"
SET DistCull "350.000000"
SET farclip "400.000000"
SET specular "1"
SET particleDensity "1.000000"
SET realmName "Turalyon"
SET ffxDeath "0"
SET ffxGlow "0"
SET gameTip "3"
SET uiFaster "0"

---

### Post by Eviljim on 2008-09-29
> **bumpycat said:**
> A followup to your thread - I'm also running Ubuntu (8.04) on a Thinkpad R61e. I've gone through various problems and can now start WOW and get all the way to character selection. However, as soon as I choose a character and enter the game world, the game freezes (sometimes with terrain graphic glitches). I don't suppose you encountered anything like this? Could you post the contents of your Config.wtf?

Thanks in advance!

My Config.wtf:

SET locale "enGB"
SET realmList "eu.logon.worldofwarcraft.com"
SET patchlist "eu.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxAPI "opengl"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET M2UseShaders "0"
SET videoOptionsVersion "1"
SET textureFilteringMode "0"
SET pixelShaders "1"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET readTerminationWithoutNotice "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET Sound_EnableHardware "1"
SET SmallCull "0.080000"
SET DistCull "350.000000"
SET farclip "400.000000"
SET specular "1"
SET particleDensity "1.000000"
SET realmName "Turalyon"
SET ffxDeath "0"
SET ffxGlow "0"
SET gameTip "3"
SET uiFaster "0"

Im assuming you are using an Intel g/card. You may need to change the SET gxAPI "OpenGL" to SET gxAPI "d3d"?

Or, would you be using the Cartographer mod by any chance?

If so disable it and try again.

---

### Post by bumpycat on 2008-09-29
> **Eviljim said:**
> Im assuming you are using an Intel g/card. You may need to change the SET gxAPI "OpenGL" to SET gxAPI "d3d"?

Or, would you be using the Cartographer mod by any chance?

If so disable it and try again.

Magic! Switching to d3d did the trick. I should have searched for my laptop model first - there's another thread that recommends the same.

Thank you!

---

