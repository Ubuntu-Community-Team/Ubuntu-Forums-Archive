---
title: "Jazz Jackrabbit 2 - Black Screen"
date: 2008-08-20
forum: Wine
---

### Post by kasio on 2008-08-20
I have just downloaded Jazz Jackrabbit 2, and when I try it in Wine 1.1.2, the Epic Games logo comes up and then then there is a black screen, and it stops.

I have tried it in fullscreen, emulated desktop (800x600), turning off Compiz, using PlayOnLinux, changing Windows version in wine config.

Can anyone help me?

---

### Post by kasio on 2008-08-20
Anyone?

---

### Post by tjotser on 2008-08-21
I also just downloaded it and it works perfectly here. I checked the wineappDB and also no problems reported there either.

Do you have videocard drivers installed? can you post the output of the terminal when you run WINE  jazz2.exe ?

---

### Post by kasio on 2008-08-21
I have nivida-glx drivers installed, and they are working fine...

Here is terminal output:
```

fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:system:SystemParametersInfoW Unimplemented action: 79 (SPI_GETLOWPOWERTIMEOUT)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f434,0x00000000), stub!
fixme:winsock:is_sockaddr_bound don't know how to tell if IPX socket is bound, assuming it is!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x16e090)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x16e090)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x16e090)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x16e090)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x16e090)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x16e090)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x16e090)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x16e090)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x16e090)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x16e090)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x16e090)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x16e090)->(1,(nil)): Stub
# Repeats until Epic Logo animation finishes #

```

---

### Post by kasio on 2008-08-22
*bump*

---

### Post by kasio on 2008-08-23
I need help. Maybe reinstall wine?

---

### Post by nanderv on 2010-03-01
Try pressing 'Esc'.. That used to skip the video.. So that should make it work..

---

### Post by ThePinkWitch on 2010-03-02
> **kasio said:**
> I have just downloaded Jazz Jackrabbit 2, and when I try it in Wine 1.1.2, the Epic Games logo comes up and then then there is a black screen, and it stops.

I have tried it in fullscreen, emulated desktop (800x600), turning off Compiz, using PlayOnLinux, changing Windows version in wine config.

Can anyone help me?

Hello..I have that game running perfectly no probs at all. maybe try uninstalling it and reinstalling. I think I set mine to run as win 98. I downloaded it thru PlayOnLinux and it worked right away. Hope you get it running ok..It's fun to play :)

---

### Post by Rytron on 2010-06-02
Jazz Jackrabbit 2 runs perfectly here. However it messes up my top panel icons when I exit the game. Does anyone else have this problem and know how to solve it?

---

### Post by asdfoo on 2010-06-02
> **Rytron said:**
> Jazz Jackrabbit 2 runs perfectly here. However it messes up my top panel icons when I exit the game. Does anyone else have this problem and know how to solve it?

Sounds like Wine exposing a bug in something else, your video driver, window manager or xorg.

---

