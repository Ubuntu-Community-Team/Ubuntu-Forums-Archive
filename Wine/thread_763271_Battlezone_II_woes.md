---
title: "Battlezone II woes"
date: 2008-04-22
forum: Wine
---

### Post by petzworld999 on 2008-04-22
Battlezone II: Combat Commander installed fine, and it patched fine to 1.3. However, when I start the program, a black screen comes up and the following error message appears:

Can't start hardware accelerated Direct3D 8. 

Then, it gives a URL for the latest DirectX. I have searched the AppDB and it works pretty well, just not for me. Terminal output is as follows:

```


critta@CRITTAC:/media/My Book/Games/Battlezone II/The Game$ wine bzone.exe 
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on ATI IXP Modem, disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x229e73c,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3413
err:ddraw:IDirectDrawImpl_QueryInterface (0x344ef28) The App is requesting a D3D device, but a non-OpenGL surface type was choosen. Prepare for trouble!
err:ddraw:IDirectDrawImpl_QueryInterface  (0x344ef28) You may want to contact wine-devel for help
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?


```

Any ideas on why this is happening and how to fix?

---

### Post by mikedep333 on 2008-04-22
```
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
```

It looks like it is trying to go from 32bit color to 16bit color but is failing. Maybe this is a bug specific to your graphics vendor.
You can probably try going into the wine configuration (winecfg) and choose emulate a virtual desktop (under the graphics section.) That works for me when there you can't change your X resolution to accommodate a wine game.

---

### Post by petzworld999 on 2008-04-22
Well now it starts, but once I get past the intro movie (which runs very slowly) I see a screen that is mostly black and does not respond. That is another problem. 

```
fixme:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(640,480)
fixme:d3d:state_subpixel Render state WINED3DRS_SUBPIXEL not implemented yet
fixme:d3d:state_mipmaplodbias Render state WINED3DRS_MIPMAPLODBIAS not implemented yet

```

---

### Post by petzworld999 on 2008-04-24
I reinstalled, and it runs smoother, but I can still only see part of the screen. I have attached a screenshot.

---

