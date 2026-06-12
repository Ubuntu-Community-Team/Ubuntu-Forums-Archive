---
title: "Age of Empires II"
date: 2007-12-28
forum: Wine
---

### Post by Amanda8404 on 2007-12-28
Hi. I am trying to get Age of Empires II (The Conqueror's Expansion)  to work, and it says this in the terminal:


```
fixme:system:SystemParametersInfoW Unimplemented action: 110 (SPI_GETSHOWIMEUI)
fixme:win:EnumDisplayDevicesW ((null),0,0x33da10,0x00000000), stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x129628)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x129628)->(0x10024,00000013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:system:SystemParametersInfoW Unimplemented action: 111 (SPI_SETSHOWIMEUI)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x129628)->((nil),00000008)

```

The error message that shows up when it tries to start the game is "Could Not Initialize Graphics System. Make sure that your video  card and driver are compatible with Direct Draw". 

Wine HQ says that others have gotten the game to work but this is the first time I am using Wine for anything and I couldn't figure out from their threads how they did it. I am using the newest version of Wine. Is there some setting I should change in Wine, or can you think of something else that might make it work? :confused:

---

### Post by tech9 on 2007-12-28
> **Amanda8404 said:**
> Hi. I am trying to get Age of Empires II (The Conqueror's Expansion)  to work, and it says this in the terminal:


```
fixme:system:SystemParametersInfoW Unimplemented action: 110 (SPI_GETSHOWIMEUI)
fixme:win:EnumDisplayDevicesW ((null),0,0x33da10,0x00000000), stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x129628)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x129628)->(0x10024,00000013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:system:SystemParametersInfoW Unimplemented action: 111 (SPI_SETSHOWIMEUI)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x129628)->((nil),00000008)

```The error message that shows up when it tries to start the game is "Could Not Initialize Graphics System. Make sure that your video  card and driver are compatible with Direct Draw". 

Wine HQ says that others have gotten the game to work but this is the first time I am using Wine for anything and I couldn't figure out from their threads how they did it. I am using the newest version of Wine. Is there some setting I should change in Wine, or can you think of something else that might make it work? :confused:

what kind of video card do you have?

---

### Post by Amanda8404 on 2007-12-29
My video card is: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller.

---

### Post by s1300045 on 2007-12-29
I have the same problem also. My video card is 82852/855GM Integrated Graphics Device. I guess there is some function that has to be enable? But I have already tried everything because I am running compiz. Any suggestion?

---

### Post by tmske on 2007-12-31
did anyone find a solution for this. I have Intel Corporation Mobile GM965/GL960 drivers

---

### Post by NeoFax on 2008-01-03
Try copying the d3dx***.dll files to the same directory as the game is installed(normally ~/.wine/drive_c/Program Files/Microsoft Games/XXX).  Then in winecfg add the application and override the d3dx8 dll to native/builtin.  This may work.  I am running AOEII on a NVIDIA system with no problems other than multiplayer is slow.

---

### Post by tmske on 2008-01-04
Tried it but doesn't work.

I think directx is correctly installed in wine and the dll files all are set correctly.

I think this is a problem with the intel cards but don't know how to fix it.

---

### Post by tjb891 on 2008-01-11
i have a geforce 4 MX 4000 and have the same problem

---

### Post by Tristan_F on 2008-01-12
I think I had also this problem. I managed to play by slightly modifying the wine configuration.

Use winecfg and tell to emulate a desktop in the display part.

Hoep this help

Tristan

---

### Post by Tails9 on 2008-05-07
Try this: ```
wine empires2.exe -- -opengl
```

or start from the cd even if you use a crack.

Good luck.

---

### Post by ptero on 2008-06-29
that's very strange. i've got the same problem now with wine 1.10 and nvidia 7600g. however, everything went fine as i played it with an older version of wine about 3-5 months ago. can't remember though, if it was in ubuntu or in gentoo.

---

### Post by uksuperdude on 2008-06-29
Same problem with wine 1.1.0 and nvidia 8400 GS. I'm sure it worked (although a different PC, but running Hardy) yesterday...

---

### Post by ptero on 2008-06-30
that's very strange. i've got the same problem now with wine 1.10 and nvidia 7600g. however, everything went fine as i played it with an older version of wine about 3-5 months ago. can't remember though, if it was in ubuntu or in gentoo.

EDIT: oops, very sorry for the double post, i thought, the first one didn't go through (i had serious problems with internet yesterday). if you're an admin, please delete this one ;)

---

### Post by ptero on 2008-07-07
huhuh, now something really strange has happened. by doing apt-get update i noticed, that i still had the medibuntu repositiry set up to gutsy (i made a dist-upgrade from fluxbuntu 7.10rc). well, lots of multimedia packages got upgraded. and i thought "why not try to start aoe2 again?". and it worked! however, i got no sound. i closed the game and figured that sound didn't work at all. so i rebooted and had sound working again. however, aoe2 told me about that directdraw error again... so it probably has something to do with sound in ubuntu. however, just disabling the sound in wine didn't help.
here's the list of packages which got updated, maybe somebody could have an idea what could be responsible and how to fix it:
  ffmpeg libavcodec-dev libavcodec1d libavformat-dev libavformat1d
  libavutil-dev libavutil1d libpostproc-dev libpostproc1d libswscale1d
  w32codecs

---

