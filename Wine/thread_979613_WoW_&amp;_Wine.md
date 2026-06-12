---
title: "WoW &amp; Wine"
date: 2008-11-12
forum: Wine
---

### Post by Death_To_The_World on 2008-11-12
Hi,
 I installed WoW with wine. When I run the game though it is very very lagy and slow. I have an ati x700 card and havent installed anything but what came on the newest ubuntu. I am also using a samsung tv as a monitor. Can anyone please help me?

---

### Post by Espryon on 2008-11-12
Try some of these  tweaks i found on the ubuntu forum 

 


December 4th, 2006    #1  
Sammi 
100% Pure Ubuntu

 
 
 

Join Date: Mar 2006
Location: Faroe Islands
Posts: 896 
Thanks: 6
Thanked 11 Times in 10 Posts 
  Howto: WOW with Wine (help.ubuntu.com/community/WorldofWarcraft) 

--------------------------------------------------------------------------------

HOWTO: WoW with Wine

This howto is for installing and playing World of Warcraft using Wine under Ubuntu.


The howto found in this post is just a short'n'simple version, intended to demonstrate the minimum amount of steps required to make WoW run. The complete howto, which will likely be more of a help to you, is found in the Ubuntu community documentation wiki:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)



Short'n'simple HOWTO 
(only 9 steps to enter the next world  )

1. Open a terminal(also called a konsole, CLI, and command prompt) and choose one of these two commands to run, based on your version of Ubuntu:

For Ubuntu Hardy Heron (8.04)
Code:
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.listFor Ubuntu Gutsy Gibbon (7.10)
Code:
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list2. Now do these commands in a terminal:

Code:
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wine3. Copy all of the files from all of the CD's to a directory on your hard drive (overwrite when prompted).

4. Open a terminal and do these commands inside to start the installation:

Code:
cd /<path-to-directory>/
wine Installer.exeReplace <path-to-directory/> with the right path to the directory where you copied all the files.

5. Wait and click next when possible. 

6. Do this command in a terminal, and just press ok to close the configuration utility that opens:

Code:
winecfg7. Now run this command in a terminal:

Code:
gedit ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/wtf/Config.wtfAdd these lines to the text file:

Code:
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"8. Save the file and exit.

9. You should be able to play WoW using the shortcut on your desktop, or by running this command:

Code:
 wine "C:\Program Files\World of Warcraft\WoW.exe"

Almost mandatory performance enhancing tweak
This is a simple registry edit for Wine that will dramatically increase the framerate in game for both ATi and nVidia users.

Open a terminal window, type regedit and press enter. This will start the Wine equivalent of the windows registry editor. If you are familiar with using the registry editor under windows then this is pretty much the same.

Notice: the guide below is case sensitive!

1. Find this key HKEY_CURRENT_USER\Software\Wine\
2. Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder
3. Right-click on the wine folder and select [NEW][KEY]
4. Replace the text New Key #1 with OpenGL
5. Right-click in the right hand pane and select [NEW] then [String Value]
6. Replace New Value #1 with DisabledExtensions
7. Then double click anywhere on the line, a dialog box will open.
8. In the value field type GL_ARB_vertex_buffer_object



Getting Help
If this short guide doesn't work right away for you, then please look over the complete howto first:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

If, after following every step in the complete howto, you are still having troubles running the game, I would like to invite you to look over this comprehensive troubleshooting article, for common issues, that arise from following this guide:
[https://help.ubuntu.com/community/Wo...roubleshooting](https://help.ubuntu.com/community/Wo...roubleshooting)

Also, in case the troubleshooting section doesn't solve your issue, you are welcome to post questions in this tread, but in order for other people to be able to effectively help you, you need to be very descriptive about your issue, and post some useful info about your system specs etc. Please write up some details about your 
CPU 
RAM 
Graphics card make and model 
Graphics card driver version number 
Wine version number 
Here is a more detailed article dealing with the issue of asking support questions the most effective way:
[http://ubuntucat.wordpress.com/2007/...-linux-forums/](http://ubuntucat.wordpress.com/2007/...-linux-forums/)

And please be polite to people. We are all just jolly amateurs, like yourself. 


Help Others
As the complete howto is a community help file, YOU are free to edit and improve it in any way YOU feel - and please do so, so that others may benefit from what you figured out 

--------------------------------------------------------------------------------
Last edited by Sammi; April 30th, 2008 at 08:32 PM.. Reason: some more tiny improvements + hardy heron wine repository

---

### Post by Faith912 on 2008-11-12
First go to the folder of wow, then in interface folder then on WTF folder,
next open Config.wtf and erase all contenets and put this ^^

SET locale "enUS"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "50"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET pixelShaders "1"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET realmList "Darkpeninsula.net"
SET patchlist "us.version.worldofwarcraft.com"
SET SmallCull "0.010000"
SET DistCull "500.000000"
SET farclip "777"
SET specular "1"
SET particleDensity "0.25"
SET groundEffectDensity "64"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET readScanning "-1"
SET readContest "-1"
SET expansionMovie "0"
SET readTerminationWithoutNotice "-1"
SET gxVSync "0"
SET gxCursor "0"
SET windowResizeLock "1"
SET textureFilteringMode "5"
SET DesktopGamma "1"
SET Gamma "1.000000"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET shadowLevel "0"
SET groundEffectDist "140"
SET weatherDensity "3"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET gameTip "21"
SET uiScale "1"
SET autoSelfCast "1"
SET shadowLOD "0"
SET questFadingDisable "1"
SET alwaysShowActionBars "1"
SET realmName "DarkPeninsula Reborn"
SET lastCharacterIndex "1"
SET checkAddonVersion "0"
SET enableCombatText "1"
SET combatTextFloatMode "3"
SET fctDodgeParryMiss "1"
SET fctLowManaHealth "1"
SET rwrw "data7999"
SET minimapZoom "0"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0"
SET Sound_AmbienceVolume "0.60000002384186"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"

Next be SURE YOU HAVE INSTALLED ATI DRIVER FOR YOUR VIDEO CARD!!!!

---

### Post by Death_To_The_World on 2008-11-12
Thank you guys! Im gonna try these steps in a moment. Where would I find the x700 x64 ATI driver? I had trouble trying to figure out which driver to get when I had xp.

---

### Post by Death_To_The_World on 2008-11-12
Espryon, I used Cedega to install WoW because I couldnt get the hang of it.

Faith912, I did what you said but now when I use wine and click wow.exe the screen just blinks a bunch of times then stops. I tried clicking wow again after that and it made my system freeze. I guess I should change the wtf file back to normal. How would I do that? What else should I try?

Also the .wtf file was in a folder named WTF it was not inside the Interface folder. The Interface folder was empty.

I followed this guide
[http://wiki.kaspersandberg.com/doku.php?id=howtos:wine:worldofwarcraft](http://wiki.kaspersandberg.com/doku.php?id=howtos:wine:worldofwarcraft)

still lag though. That or when I go to wine and hit browse and select wow.exe the screen just flickers a few times then nothing happens.

---

### Post by Death_To_The_World on 2008-11-12
Goosebumps.

---

### Post by OMJD on 2008-11-13
> **Death_To_The_World said:**
> Thank you guys! Im gonna try these steps in a moment. Where would I find the x700 x64 ATI driver? I had trouble trying to figure out which driver to get when I had xp.

I suggest using Envy. It's an application intended for use with Ubuntu, and it will automatically find, and install the most suitable driver for your graphics card. (Compatible with both Nvidia and ATI cards) You can install it via Synaptic, or you can download it directly from their website:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Hope that helps :)

- Rich

---

### Post by hotballz87 on 2008-11-13
there isint a envy verdion written for 8.10 yet according to the website, the restricted drivers worked for BC, i dunno about wrath though, i havent gotten that far

---

### Post by OMJD on 2008-11-13
> **hotballz87 said:**
> there isint a envy verdion written for 8.10 yet according to the website, the restricted drivers worked for BC, i dunno about wrath though, i havent gotten that far

It seemed to work fine for me on 8.10. I was having problems with the latest Nvidia drivers, so I'm using one of the older ones from Envy, and now it appears to be ok.

---

### Post by hotballz87 on 2008-11-13
cool i will have to keep that in mind once i finish installing this headache....

---

### Post by Death_To_The_World on 2008-11-14
Apparently my ati driver was not enabled. I enabled it and now when i start wow it crashes immediately and gives me an error and sends a report to Blizzard. Should I type out what the error says?

Also, maybe I am dumb, but I installed Envy and now it is nowhere to be found on my computer O.o 
Where is it?

---

### Post by OMJD on 2008-11-15
> **Death_To_The_World said:**
> Also, maybe I am dumb, but I installed Envy and now it is nowhere to be found on my computer O.o 
Where is it?

You probably installed the command line version.

> **Faith912 said:**
> First go to the folder of wow, then in interface folder then on WTF folder,
next open Config.wtf and erase all contenets and put this ^^

SET locale "enUS"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "50"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET pixelShaders "1"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET realmList "Darkpeninsula.net"
SET patchlist "us.version.worldofwarcraft.com"
SET SmallCull "0.010000"
SET DistCull "500.000000"
SET farclip "777"
SET specular "1"
SET particleDensity "0.25"
SET groundEffectDensity "64"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET readScanning "-1"
SET readContest "-1"
SET expansionMovie "0"
SET readTerminationWithoutNotice "-1"
SET gxVSync "0"
SET gxCursor "0"
SET windowResizeLock "1"
SET textureFilteringMode "5"
SET DesktopGamma "1"
SET Gamma "1.000000"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET shadowLevel "0"
SET groundEffectDist "140"
SET weatherDensity "3"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET gameTip "21"
SET uiScale "1"
SET autoSelfCast "1"
SET shadowLOD "0"
SET questFadingDisable "1"
SET alwaysShowActionBars "1"
SET realmName "DarkPeninsula Reborn"
SET lastCharacterIndex "1"
SET checkAddonVersion "0"
SET enableCombatText "1"
SET combatTextFloatMode "3"
SET fctDodgeParryMiss "1"
SET fctLowManaHealth "1"
SET rwrw "data7999"
SET minimapZoom "0"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0"
SET Sound_AmbienceVolume "0.60000002384186"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"

Next be SURE YOU HAVE INSTALLED ATI DRIVER FOR YOUR VIDEO CARD!!!!


Cheers, but unfortunately it didn't solve the problem for me. I'm still getting lower FPS than what I used to get when I last played WoW. (3 months ago) I used to get 70FPS+, now I get between 15-20FPS. :S

---

