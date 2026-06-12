---
title: "Wine help Please"
date: 2007-05-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by BOOBOOJS on 2007-05-26
I am having trouble with Stronghold Crusader and Command and Conquer Generals under wine.
I have tried wine 0.27, 0.35, and 0.36 under Feisty
no matter what version Generals returns:
 
```
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x4d841a8) : stub, simulating 64MB for now, returning 64MB left
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - (nil) 0x1754e8 ): semi-stub
fixme:d3d8:ValidatePixelShader (0x1e71fac (nil) 0 (nil)): stub
fixme:d3d8:ValidatePixelShader (0x1a208a8 (nil) 0 (nil)): stub
fixme:d3d8:ValidatePixelShader (0x1e71fac (nil) 0 (nil)): stub
fixme:imm:ImmReleaseContext (0x10026, 0x1754e8): stub
booboo@boobooub01:~$ wine '/home/booboo/Desktop/Wine Drive C/drive_c/Program Files/EA Games/Command and Conquer Generals/generals.exe' 
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x4d841a8) : stub, simulating 64MB for now, returning 64MB left
fixme:imm:ImmGetDefaultIMEWnd (0x2002e - (nil) 0x1754e8 ): semi-stub
fixme:d3d8:ValidatePixelShader (0x1e71fac (nil) 0 (nil)): stub
fixme:d3d8:ValidatePixelShader (0x1a208a8 (nil) 0 (nil)): stub
fixme:d3d8:ValidatePixelShader (0x1e71fac (nil) 0 (nil)): stub
fixme:imm:ImmReleaseContext (0x2002e, 0x1754e8): stub
```

```
Crusader Returns
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x183fe0) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1830d0)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x186e98)->(0x10044,00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x186e98)->(0x10044,00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x186e98)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x186e98)->(0x10044,00000013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d_surface:IWineGDISurfaceImpl_Blt Can't handle DDBLT_WAIT flag right now.
```

Thanks in advance

---

### Post by Cappy on 2007-05-26
Both have How-to's in the Wine AppDB, did you follow them?

Stronghold:
[http://appdb.winehq.org/appview.php?iVersionId=3906](http://appdb.winehq.org/appview.php?iVersionId=3906)

Command & Conquer: Generals:
[http://appdb.winehq.org/appview.php?iVersionId=1717](http://appdb.winehq.org/appview.php?iVersionId=1717)

---

### Post by kiev on 2007-05-27
I install wine from here
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main

---

### Post by BOOBOOJS on 2007-05-27
Yes I have renamed / deleted  the movies in C&C Generals , installed the no cd patch, the options.ini, and the dll

I have installed crusader and the nocd patch, but did not see the point in compiling wine with the mentioned cursor patch.

I have tried both emulating diff win versions turning on and off pixel shading and hardware accell, emulating a virtual desktop (1024x768), switching between alsa and oss, removing my wine dir and starting from scratch.

The only thing that bothers me is that they are both listed as working even under Feisty.
in both cases wine complains about not being able to negotiate small enough sound bits, and I get d3d errors like thenotice about configuring the app to use  double buffering.

Warcraft 3 works great in D3D mode

System specs:
Feisty x86-64
HP Parvillion DV9008NR
AMD Turion 64 X2
1G DDR2
Nvidia Geforce Go 6150 integrated graphics (1440x900)

---

### Post by tbonepower07 on 2007-05-28
I am having the exact same problem for Generals, as is at least one other person on the Wine DB forum, with one exception - my computer is 32 bit.  I thought I'd post here anyways, as this is an appropriate place otherwise.  Any ideas?

---

### Post by BOOBOOJS on 2007-05-29
Fixed Crusader my fault failed to execute from crusader directory, not so lucky with generals though

---

