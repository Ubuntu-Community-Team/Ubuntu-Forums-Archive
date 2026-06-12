---
title: "Worms 2 on wine, (problem changing colour depth)"
date: 2006-11-01
forum: Wine
---

### Post by musther on 2006-11-01
I'm trying to run Worms 2 under Wine, according to the info in the database at WineHQ it works quite well.

I've installed it, which went perfectly, and I can run the main application (frontend.exe), this gives me game options and the like, the problem is when I start the actual game.  The screen goes blank and then changes the resolution (as it should), then I get the message:

'Abnormal Program Termination'.

The terminal output is more useful:

```
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1685b0) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x167cf8)->(0x10024,00000011)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:d3d_surface:IWineGDISurfaceImpl_Blt Can't handle DDBLT_WAIT flag right now.
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x167cf8)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:winmm:MMDRV_Exit Closing while ll-driver open
```

This seems to suggest to me that the issue is when it tries to change the bits per pixel from 32 to 8, (i.e. down to 256 colour).  

Oddly enough I've just realised that my xorg.conf specifies a default of 24, not 32.  

I tried changing the default in xorg.conf to 8 so that when I ran worms it wouldn't have to change it, but X wouldn't start at all after that.

Any suggestions?

---

### Post by o3rat on 2007-11-07
I have the same problem too. I cant resize the window, it just defaults to 640x480

---

### Post by TheOtherShoe on 2007-12-23
I had the same problem changing the color depth when running Alpha Centauri. It should work if you run winecfg, and under the Graphics tab check the box that says "Emulate a virtual desktop". Then for the desktop size enter values matching the resolution of the game. You will have to run the game inside a window, but at least you will be able to run the game.

Note that a warning is in order: if you set a virtual desktop size smaller than about 800x600, the next time you run winecfg it won't fit in the virtual desktop. So it will be difficult to change your settings again.

---

### Post by omega_user on 2007-12-23
I wanna start playing worms2 again. That was one of the great games for me a while ago. However, I can't find my original disk anywhere, and all torrents for it are dead or dying

---

