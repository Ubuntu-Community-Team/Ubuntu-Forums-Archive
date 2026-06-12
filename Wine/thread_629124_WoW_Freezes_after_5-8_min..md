---
title: "WoW Freezes after 5-8 min."
date: 2007-12-02
forum: Wine
---

### Post by Dark Hornet on 2007-12-02
I have searched the forums, and I can't seem to find anyone with my specific issue....so here it is...I can run the game just fine, everything looks great, and it is very smooth.  After about 5-8 min of playing (no matter what I am doing), the game freezes, and I am forced to quit.  Here are some details regarding my setup

1.  nVidia 6800 GT
2.  Ubuntu 7.10--32 bit version
3.  Using the restricted driver, and running the game with OpenGL.

Please take a look at what terminal spit out from the start of the game, until I had to kill it.

-----------------------------------------------------------------------------------------------
terry@terry-desktop:~/World of Warcraft$ wine WoW.exe
fixme:advapi:SetSecurityInfo stub
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
fixme:reg:GetNativeSystemInfo (0x374029c4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x7bbfe4a4) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x34d1a4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34d200,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Killed
-----------------------------------------------------------------------------------------------

Please help, as this is the last issue that I need to resolve before I can be 100% Windows free.

And thanks in advance for any help you can provide.

---

### Post by cogadh on 2007-12-02
Unfortunately, all of those errors are just "fixme" messages, which are mostly just developer notes about unimplemented or incomplete functions in Wine. They generally mean nothing to an end user and I don't see anything in there that I haven't seen a dozen other times with a dozen other games that run fine despite the error messages.

I am curious about the directory you appear to be running the game from. It looks like you installed the game to a location outside of the .wine directory. Is there a particular reason you did this? The reason I ask is because Wine can sometimes have problems resolving drive paths properly and it is usually best to have a game installed in the .wine directory, so that all of the paths are contained to the "fake Windows" directory. I'm not sure it could have anything to do with your problem, though.

---

### Post by Dark Hornet on 2007-12-02
Yeah, I did have the folder installed outside of the WINE directory...I have changed this.  However, I am still having the same issue--I can start the game fine, even log in, and play...infact, I am getting around 45-55 fps most places.  After 4 or so min, the game freezes on me, and then goes "black and white" indicating that it isn't responding, and I have to force quit it.  I have even let it sit for a while just to make sure that the processor, gfx, etc didn't need to "catch up".

---

### Post by cogadh on 2007-12-02
Are you running Compiz (enhanced 3D desktop effects) at the same time as the game?

---

### Post by Dark Hornet on 2007-12-02
Yes, I am...i will disable it and try it real quick...

***EDIT***  I just disabled the visual effects, etc. and it still does the same thing.  I don't think Compiz, or AWN has anything to do with it, as (at least in my mind) I think if they where an issue, they would prevent the game from starting, or something along those lines.

---

### Post by cogadh on 2007-12-02
Wine and Compiz generally don't like each other. Most games will still run if Compiz is enabled, but the performance hit is enormous. That can present itself as a general slow down or lock up that gets worse as the game progresses. 

I think it might be time to look at how the game and Wine are configured. Did you follow the configuration instructions in the WoW Ubuntu how to:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Dark Hornet on 2007-12-02
yes, I followed the instructions on setting up WINE, including adding the regedit hack, and adding the OpenGL, etc settings to the config.wtf file.

---

### Post by hikaricore on 2007-12-02
Just a thought, and just to be sure, try launching the game with the -nosound flag.

> 
wine WoW.exe -opengl -nosound

This is just to see if the problem you're having has anything to do with an underlying sound issue.  ^_^
If it sill happens, we can exclude that as a possibility.

Also do you know what version of the Nvidia driver you are using?

> glxinfo | grep "OpenGL version"

If the driver in the restricted driver manager is slightly outdate (not sure if it is or not) you may want to try a newer one or even the beta driver.

****You'll also want to be keeping compiz/beryl disabled while testing things just to be sure it isn't somehow affecting the game still****

---

### Post by Dark Hornet on 2007-12-02
According to this, I am using the newest version of the driver (not including whatever beta drivers are out)

glxinfo | grep "OpenGL version"
OpenGL version string: 2.1.1 NVIDIA 100.14.19

and the no sound didn't work either...I am still having the same issue.

---

### Post by Sammi on 2007-12-02
Does this only happen with WoW?

Games crashing by them self after a few minutes gameplay can be caused by a faulty Graphics card.

Anyway I have a Nvidia 6800 myself and I'm using the 100.14.23 driver without complications in any game atm. I used the [Envy]("http://albertomilone.com/nvidia_scripts1.html") script to install it, but I would not recommend it to you if you are scared of being stuck at the black screen of death (also known as the command prompt), which you will inevitably face at so point if you start fiddling with graphics card drivers that are not in the official Ubuntu repositories. But on a lighter side, uninstalling and resinstalling the driver using Envy seems to work every time I get in to trouble :rolleyes:

---

### Post by Dark Hornet on 2007-12-02
Yes, this only happens with WoW...everything else works perfectly fine...including other games

---

### Post by hikaricore on 2007-12-02
You may also want to run the "nvidia-settings" interface while running the game, and switch over to the themal info tab.  I'm starting to wonder if you GPU is overheating.  It should not be going above 90C max, and even that's too high.

---

### Post by Dark Hornet on 2007-12-02
You know...I thought the same thing, but no dice....GPU temp never goes over 55 C.

---

### Post by hikaricore on 2007-12-15
bump (just wanna help friend)

---

### Post by gspat on 2007-12-26
this seems to work for me...

nvidia cards seem to choke on the 24 bit textures, try the 16 bit ones

also try to play in a maximized window.

---

### Post by Dark Hornet on 2007-12-26
Will do..thanks for the suggestion.

---

