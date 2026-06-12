---
title: "Fish Tycoon in Wine -- help please"
date: 2007-04-30
forum: Wine
---

### Post by Nikusan on 2007-04-30
Hi all,

Trying to play Fish Tycoon in wine here. The AppDB claims it's platinum, but I'm gettin the following error:

```
GapiDraw
"Failed initializing DirectDraw. only 16-bit and 32-bit displays are supported in windowed mode."
```

Console output:

```
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x170438) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x16fc28)->(0x1002e,00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x16fc28)->(0x1002e,00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x16fc28)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
```

I've tried both 0.9.33 (feisty) and 0.9.36 (winehq), same results.

If 3d drivers come into the equation I've got a Radeon Mobility X1600 with fglrx. fglrxinfo says my vendor string is ATI and glxinfo says direct rendering: yes, so I assume it's not an fglrx problem.

Any ideas? How would I make it run in full screen?

---

### Post by fain on 2007-11-18
I have this problem with a game called shadow of legend. I fixed it by changing the default color depth to 16 bit in /etc/X11/xorg.conf. The game ran fine after that. But i don't want to run my desktop in 16 bit all the time just for 1 game :( There needs to be a better fix for this

[http://bugs.winehq.org/show_bug.cgi?id=2680]("http://bugs.winehq.org/show_bug.cgi?id=2680")

---

