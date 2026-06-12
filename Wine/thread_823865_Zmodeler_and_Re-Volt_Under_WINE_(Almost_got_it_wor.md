---
title: "Zmodeler and Re-Volt Under WINE (Almost got it working, but need some help)"
date: 2008-06-09
forum: Wine
---

### Post by Gaming4JC on 2008-06-09
Hello All,
I am running WINE 1.0 RC4 on Ubuntu hardy. So far so good, but when I run Zmodeler I get this in the terminal just before it crashes:
> 
wine "C:\Program Files\Zmodeler\Zmodeler.exe"
fixme:win:EnumDisplayDevicesW ((null),0,0x33e3e4,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
luke@luke-desktop:~$ wine "C:\Program Files\Zmodeler\Zmodeler.exe"
fixme:win:EnumDisplayDevicesW ((null),0,0x33e3e4,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface


It loads but does nothing and I have to terminate it.

This next one is more tricky. I can load Re-Volt just fine if I load it via clicking on it from the virtual drive. But if I access it from the WINE Start Menu or from the terminal I get this:
> 
wine "C:\Program Files\Acclaim Entertainment\Re-Volt\revolt.exe"
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Brooktree Bt878, disabling mixer


Anyone know how to fix this? :(

---

### Post by Gaming4JC on 2008-06-11
Hmm.. I looked around. My logs say it has something to do with OpenGL. Doesn't WINE come with OpenGL preinstalled or is there a place to download it (like the Gecko engine)?:KS

---

### Post by cogadh on 2008-06-11
OpenGL support is a function of your video card's drivers, however, that has nothing to do with your problem. The "fixme" messages you are getting are just developer notes about unimplemented or incomplete functions in Wine. Unless you want to take the time to code those incomplete functions for the Wine devs, there is nothing you, as a user, can do to fix them. 

The ALSA messages you got are also non-issues. They just indicate that you have a sound card that is not capable of hardware mixing. Everyone with a sound card like that gets those messages, but sound still works and it doesn't prevent applications from running. As for getting Re-Volt to run, have you already tried the suggestions on the game's AppDB page:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3151](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3151)

---

### Post by OmikronZeta on 2009-04-24
ReVolt works fine for me with WINE. A little slower to load, than in windows, and the text and power-up display are a little weird.

---

