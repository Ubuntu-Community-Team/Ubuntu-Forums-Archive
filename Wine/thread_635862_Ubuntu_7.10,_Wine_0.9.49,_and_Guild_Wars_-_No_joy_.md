---
title: "Ubuntu 7.10, Wine 0.9.49, and Guild Wars - No joy :("
date: 2007-12-09
forum: Wine
---

### Post by Barrucadu on 2007-12-09
I just can't seem to get Guild Wars working in Wine! I've included everything that could be useful:

**_Exact Problem_**
I can load guild wars, log in, and select a character. After selecting a character, when loading the area, the game closes.

**_Version Information_**
**Ubuntu Version:** 7.10
**WINE Version:** 0.9.49

**_WineCFG_**
**Windows Version:** Windows 98

_Graphics_
**Allow DirectX apps to stop the mouse leaving their window:** Y
**Allow the window manager to control the windows:** Y
**Emulate a virtual desktop:** N
**Vertex shader support:** None
**Allow pixel shader (if supported by hardware):** N
**Screen resoulution:** 96dpi

_Sound_
**Hardware Acceleration:** Full
**Default Sample Rate:** 44100
**Default Bits Per Sample:** 16
**Driver Emulation:** Y

_Drives_
**C:** ../drive_c
**D:** /media/cdrom0
**E:** /media/MIKES HD
**F:** /media/MOVIES
**Z:** /

**_Terminal Output_**
There is loads of output, so i'll just include the last 15 lines or so...
```

fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b9598) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b9598) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b9598) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b9598) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b9598) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1b9598) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1b9598) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1b9598) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1b9598) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1b9598) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1b9598) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1b9598) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1b9598) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1b9598) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1b9598) : stub

```

---

### Post by cogadh on 2007-12-09
There is a Wine subforum here now, you should post your Wine questions there. It might also be worth it to search those forums for help, Guild Wars questions are posted a lot and this one may already have an answer there:
[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

I must say, you are the first person to actually post a useful amount of information when asking a question about Wine. Thank you so much for that, your efforts will make helping you so much easier.

A few questions/suggestions:[LIST=1]
[*]Why are you using Windows 98 mode?
[*]There is a newer version of Wine (0.9.50) that corrects many problems specific to Guild Wars, you may want to update to it
[*]Unfortunately, you included the least useful 15 lines of terminal output. The "fixme" messages are just developer notes about unimplemented or incomplete functions in Wine. They mean nothing to a normal user and there is usually nothing you can do to make them go away. What could really help are any "err" messages.
[*]Some hardware information would also be helpful, such as video card make/model and driver version being used.
[/LIST]

---

### Post by chronusdark on 2007-12-09
i would like to say i just installed GW with the latest wine and it went perfectly i never touched the settings

---

### Post by Barrucadu on 2007-12-09
> **cogadh said:**
> There is a Wine subforum here now, you should post your Wine questions there. It might also be worth it to search those forums for help, Guild Wars questions are posted a lot and this one may already have an answer there:
[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)
Oops, didnt notice that. Though I did find some of the guides there in google, and none of them helped.

> **cogadh said:**
> Why are you using Windows 98 mode?
The last guide I looked at said to use it, and I just haven't changed it again.

> **cogadh said:**
> There is a newer version of Wine (0.9.50) that corrects many problems specific to Guild Wars, you may want to update to it
That's the first version of Wine I tried, and I had the exact same problem.

> **cogadh said:**
> What could really help are any "err" messages.
I just logged the output, and there are no err messages, just a few hundred fixme's.

> **cogadh said:**
> Some hardware information would also be helpful, such as video card make/model and driver version being used.
Is there a handy command I can type in the terminal to get that?

---

### Post by cogadh on 2007-12-09
First, you should update back to 0.9.50, the fixes included in it are definitely worth it. Second, set Wine to either Win 2000 or XP, both will usually work better than 98 for modern games. 

To get the hardware info, run this:
```
glxinfo | grep server
```
and to confirm that you actually have 3D acceleration enabled, run this:
```
glxinfo | grep direct
```
If it comes back with the result "direct rendering: No" then 3D games won't work until that is fixed.

If it comes back with a "direct rendering: Yes", then according the the information on the Wine AppDB page for the game, you need to run it like this in order to get it to run smoothly:
```
cd ~/.wine/drive_c/Program\ Files/GUILD\ WARS/
wine Gw.exe -image -dsound - >/dev/null 2>&1
```
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194)

---

### Post by Barrucadu on 2007-12-09
> **cogadh said:**
> First, you should update back to 0.9.50, the fixes included in it are definitely worth it. Second, set Wine to either Win 2000 or XP, both will usually work better than 98 for modern games. 
Done and done.

> **cogadh said:**
> To get the hardware info, run this:
```
glxinfo | grep server
```
```
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
```

> **cogadh said:**
> and to confirm that you actually have 3D acceleration enabled, run this:
```
glxinfo | grep direct
```
```
direct rendering: Yes
```

> **cogadh said:**
> If it comes back with a "direct rendering: Yes", then according the the information on the Wine AppDB page for the game, you need to run it like this in order to get it to run smoothly:
```
cd ~/.wine/drive_c/Program\ Files/GUILD\ WARS/
wine Gw.exe -image -dsound - >/dev/null 2>&1
```
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194)
Now it displays the loading screen, and dies with no output. However, if I remove the -image flag, I get to the same point as before.

---

### Post by cogadh on 2007-12-09
You are running on an SGI machine? I'm not sure that can even do gaming (properly, that is). AFAIK, this game will only work if you have an Nvidia or ATI based graphics card.

---

### Post by Barrucadu on 2007-12-09
Well, all my games ran perfectly on Windows, so the graphics card can't be the problem.

---

### Post by cogadh on 2007-12-09
I'm talking in Linux, not Windows. Even though you are trying to run the game in Wine, its not the same as running it in Windows. The driver differences alone could cause many problems. Just ask anyone who tries to run a game in Linux that runs fine in Windows with an ATI card. The ATI driver, while getting much better, is not the easiest thing to work with in Linux and often leads to much Linux gaming difficulty.

Honestly, I don't know nearly enough about SGI graphics in Linux to even make a guess as to whether or not that might be the source of the problem. At most, I could say I have a strong suspicion that it might have something to do with it.

---

### Post by Barrucadu on 2007-12-09
I'll investigate dual-booting. Though it's a bit annoying having to have Windows installed just to play games.

---

