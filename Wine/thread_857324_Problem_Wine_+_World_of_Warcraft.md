---
title: "Problem: Wine + World of Warcraft"
date: 2008-07-12
forum: Wine
---

### Post by MasterNetra on 2008-07-12
I followed the guide by the letter pretty much ( [http://ubuntuforums.org/showthread.php?t=579378&page=1](http://ubuntuforums.org/showthread.php?t=579378&page=1) ), but when i get to the login screen the login screen's background is gone. I login in. The Character List background is gone. I go in game. Characters. mobs and such don't load. Avatar pic don't load along with a number of other things just blackness where most things should be (save for on terrain stuff which mostly just isn't there) i remove the openGL from the config and everything appears but I only run at 1 fps. My General specs are in my signature.

xorg.conf:

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
EndSection

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Synaptics Touchpad"
EndSection


WoW config:

SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET hwDetect "0"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET SmallCull "0.010000"
SET DistCull "350.000000"
SET frillDensity "8"
SET farclip "417"
SET particleDensity "1.000000"
SET movie "0"
SET expansionMovie "0"
SET readTerminationWithoutNotice "-1"
SET coresDetected "2"
SET videoOptionsVersion "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET patchlist "us.version.worldofwarcraft.com"
SET spellEffectLevel "0"
SET gameTip "7"
SET gxWindow "1"
SET gxMaximize "1"
SET gxTripleBuffer "1"
SET gxVSync "0"
SET windowResizeLock "1"
SET textureFilteringMode "0"
SET DesktopGamma "1"
SET Gamma "1.000000"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET baseMip "1"
SET groundEffectDist "70"
SET weatherDensity "0"
SET ffxGlow "0"
SET ffxDeath "0"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET uiScale "1"
SET shadowLOD "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"

(I purposely left realm, and server entries out of this post, they would have no baring anyway.)

---

### Post by mriedel on 2008-07-12
Did you remember to run WoW in opengl mode?

Easiest way to do it is to append "-opengl" as in

```
wine [...]/WoW.exe -opengl
```

---

### Post by MasterNetra on 2008-07-12
I generally use the Shortcuts provided how would i mod the shortcut? I mean its to the launcher not wow.exe itself?

---

### Post by MasterNetra on 2008-07-12
My Launcher shortcut is: ***env WINEPREFIX="/home/master/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe"***

I tried modding it to: ***env WINEPREFIX="/home/master/.wine" wine "C:\Program Files\World of Warcraft\Wow.exe" -opengl*** But nothing happens and putting the -opengl inside the " " causes it not to launch at all.

---

### Post by mriedel on 2008-07-12
For a desktop or panel launcher, right click it, select properties, go to the Launcher tab and append -opengl to the field labeled Command so that it reads

```
[...]/WoW.exe -opengl
```

---

### Post by MasterNetra on 2008-07-12
> **mriedel said:**
> For a desktop or panel launcher, right click it, select properties, go to the Launcher tab and append -opengl to the field labeled Command so that it reads

```
[...]/WoW.exe -opengl
```

Like i said doing that with -opengl inside the double quotes with Wow.exe (the .exe file doesn't have the last w caped) results in it not launching at all. outside the double quotes nothing changes.

***env WINEPREFIX="/home/master/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe"*** The orginal command.

***env WINEPREFIX="/home/master/.wine" wine "C:\Program Files\World of Warcraft\Wow.exe -opengl"*** Doesn't launch at all.

***env WINEPREFIX="/home/master/.wine" wine "C:\Program Files\World of Warcraft\Wow.exe" -opengl*** Launches but no change.

---

### Post by mriedel on 2008-07-12
I'm sorry, while I was posting my reply, your second post read "sorry for double posting" or sth ;)

This should mean that your problem lies elsewhere. If you wanna be sure, cd to your WoW directory in a terminal and run

```
wine WoW.exe -opengl
```

on that console. If the problem persists, try a forum search. If I recall correctly, a similar issue has been discussed in another WoW-related thread on these forums.

---

### Post by MasterNetra on 2008-07-12
> **mriedel said:**
> I'm sorry, while I was posting my reply, your second post read "sorry for double posting" or sth ;)

This should mean that your problem lies elsewhere. If you wanna be sure, cd to your WoW directory in a terminal and run

```
wine WoW.exe -opengl
```

on that console. If the problem persists, try a forum search. If I recall correctly, a similar issue has been discussed in another WoW-related thread on these forums.
How do i handle spaces in terminal?

Oop nvm i just used * for them.

---

### Post by mriedel on 2008-07-12
If you want to cd to, say, a dir called Program Files, you'd type

```
cd Program\ Files
```

backslash-space is a so-called escape sequence. The backslash escapes the space, so that it's used as a space, not a separator between arguments (as in rm file1 file2).

---

### Post by MasterNetra on 2008-07-12
Oh well mute point. No dice this is result:

[B][I]fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x32eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ec94,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f57c,0x00000000), stub!
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  598
  Current serial number in output stream:  598[/I][/B]

I think its determined not to run >.<

---

### Post by mriedel on 2008-07-12
Check this: [http://bugs.winehq.org/show_bug.cgi?id=6637](http://bugs.winehq.org/show_bug.cgi?id=6637)

Try upgrading and, if that doesn't work, downgrading your video drivers.

---

### Post by MasterNetra on 2008-07-12
I think its my visual manager or whatever you call it. It the failure was on Metacity which i had changed it to earlier because i was told that compiz wasn't friendly with OpenGL programs at least not for wine stuff. I changed it back to COmpiz, it loaded but the problems i had stated about stuff not being there occured. What other managers are there so i can try them?

Also that bug report is for Nvidia which i don't have.

---

### Post by mriedel on 2008-07-12
Compiz should be fine. WoW used to run just fine in it for me. Some people experience improved performance when they turn off desktop effects in System -> Preferences -> Appearance -> Visual Effects (Tab).

I'd say try the video driver update/downgrade and if that doesn't change things for you, we'll have a look at your window manager :)

Edit: Since you don't have an nvidia card, it seems a little less probable, that the driver update will help you. Still it's mostly a good thing to be at the most recent versions when having trouble with games, so you won't be wasting time trying that.

---

### Post by Akingboy on 2008-07-12
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
Taken from there
> Config.wtf

WoW uses DirectX by default, but for most people it will not perform well in this mode. If this is the case for you, then you should change it to run in OpenGL mode instead. To do this you need to find the file wtf/Config.wtf in your main WoW directory. By default it is found in /home/<username>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/, where <username> is you computer login name. Note that since .wine begins with a period, you will not be able to see it, but you may still access it in a terminal. In the Nautilus file manager, you can press Ctrl + h to see hidden files. If config.wtf does not exist, run the game and log into a character. The game should then create the file. Open it using a text editor, and add the following line to it:

SET gxApi "opengl"

If you experience poor performance, graphical glitches, or the game does not run at all, then add the following options as well:

SET ffxDeath "0"
SET ffxGlow "0"

[SIZE="4"]If you experience a problem with missing character and object models, and/or the login windows background is black, add:

SET M2UseShaders "0"[/SIZE]

Note that disabling ffxGlow may also enable antialiasing for some users.

If you experience stuttering, bad sound or no sound what so ever, then add the following options as well:

SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"

---

### Post by MasterNetra on 2008-07-12
lol yea found that out sometime after my last post. Now if i can only improve my fps. its about 15-16 in rural areas about 1-4 in captial citys. I turned down the details as far as they go but not really much change. It wasa little more then twice as fast in windows (15fps at least for crowded areas most of the time occasionally lower but meh.) 30fps - 60fps in most other areas and all this with graphics and stuff on high...*sighs* **Hunts around for solution to low fps**

---

### Post by MasterNetra on 2008-07-12
**Deleted accidental double post***

---

### Post by Akingboy on 2008-07-12
Turn to lowest your terrain distance. It has HUGE impact on fps.
But if you have all lowest like you sayd something about it then are you using openGl mode?

> WoW uses DirectX by default, but for most people it will not perform well in this mode. If this is the case for you, then you should change it to run in OpenGL mode instead. To do this you need to find the file wtf/Config.wtf in your main WoW directory. By default it is found in /home/<username>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/, where <username> is you computer login name. Note that since .wine begins with a period, you will not be able to see it, but you may still access it in a terminal. In the Nautilus file manager, you can press Ctrl + h to see hidden files. If config.wtf does not exist, run the game and log into a character. The game should then create the file. Open it using a text editor, and add the following line to it:

SET gxApi "opengl"



Also found this:
> Registry configuration

This is a simple registry edit for Wine that will dramatically increase the framerate in game. It is gathered from this thread on Ubuntuforums.org: [http://www.ubuntuforums.org/showthread.php?t=303509](http://www.ubuntuforums.org/showthread.php?t=303509)

Open a terminal window, type regedit and press enter. This will start the Wine equivalent of the windows registry editor. If you are familiar with using the registry editor under windows then this is pretty much the same.

   1. Find this key HKEY_CURRENT_USER\Software\Wine\
   2. Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder
   3. Right-click on the wine folder and select [NEW] then [KEY]
   4. Replace the text New Key #1 with OpenGL
   5. Right-click in the right hand pane and select [NEW] then [String Value]
   6. Replace New Value #1 with DisabledExtensions (Notice it's case sensitive!)
   7. Then double click anywhere on the line, a dialog box will open.
   8. In the value field type GL_ARB_vertex_buffer_object 

Note: If you are unable to rename the newly created key "New Key #1" to "OpenGL" then expand the left hand pane of the regedit window using the vertical divider bar. You should now be able to change it. A known bug in Wine is causing this unwanted behavior.

Hope these help.

---

### Post by avam323 on 2008-07-12
What kind of video card are you using? If it's not a discrete card, that's probably your issue. I run WoW on a 256M NVidia card and keep my desktop cube enabled at all times (and run it in a window, for the most part). Everything works great (fps 70 in low-traffic areas, 30-45 in high-traffic). When I was using my onboard video card I had that same problem. $25 to a guy at work who had an extra card fixed it. Just don't forget to install the proprietary drivers for it.

---

### Post by MasterNetra on 2008-07-12
> **avam323 said:**
> What kind of video card are you using? If it's not a discrete card, that's probably your issue. I run WoW on a 256M NVidia card and keep my desktop cube enabled at all times (and run it in a window, for the most part). Everything works great (fps 70 in low-traffic areas, 30-45 in high-traffic). When I was using my onboard video card I had that same problem. $25 to a guy at work who had an extra card fixed it. Just don't forget to install the proprietary drivers for it.

Well for one I'm on a labtop. Second my stuff is in my signature :p

---

### Post by mriedel on 2008-07-13
Your onboard graphics device uses shared memory. It has no own video ram but uses up parts of your main memory. WoW is both RAM- and VRAM-intense so this could indeed be your problem.

Other than that, try the registry tweak posted above. It is said to significantly improve WoW performance on wine.

---

### Post by webbed on 2008-07-13
As long as you have the entry

SET gxApi "OpenGL"

In your config.wtf file you will not need to call the --opengl flag when running World of Warcraft.

What video drivers are you using? The default drivers that come with Ubuntu do not support advanced OpenGL rendering. Just like the advanced desktop effects for Ubuntu the correct gfx drivers must be installed first.

If you are using an NVIDA or ATI video card there is a tool available to automaticlly download and install the correct drivers:

[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by avam323 on 2008-07-18
> **MasterNetra said:**
> Well for one I'm on a labtop. Second my stuff is in my signature :p

This being the case, currently WoW takes up over 600M of ram when running all the other things i mentioned as well. I couldn't get it to render the toons properly w/o a discrete card (even with all the tweaks). You may have to dual-boot to resolve this issue (not a perfect answer, but probably the only one that will work). I've got a notebook that won't run it for the same reason, I found out recently. My notebook is a 1.8G dual core amd w/ 2G ram and *gags* vi$ta. It can barely run WoW w/ a fps of more than 15-20 in low-traffic areas. High traffic, it can get down to 5-10.

---

### Post by tanyaacatherine on 2008-10-31
World of Warcraft is Blizzard’s subscription-based massively multiplayer online role playing game set in the world of Azeroth, scene of past Warcraft strategy games. The game lets players go online to interact with each other and computer-controlled characters and monsters as they explore the world.
----------------
Tanyaa
[WoW Gold]("http://www.wow-gold-price-list.com")

---

### Post by Greyed on 2008-10-31
I'd highly suspect your video card.  Since it isn't one of the big two I doubt that WoW would run.  IE, the important question that needs to be answered now is "Has anyone with an on-board Intel video card gotten WoW to run?"

---

### Post by Hairy_Palms on 2008-11-01
the registry fix actually makes FPS worse for a lot of people since the 3.0 patch, if youve got it applied id suggest trying with it removed.

---

### Post by jamessnell on 2009-03-03
Any progress on this? I have this problem with Wine 1.1.6, on Ubuntu 8.10 using an Intel X3100 GPU. :(

---

