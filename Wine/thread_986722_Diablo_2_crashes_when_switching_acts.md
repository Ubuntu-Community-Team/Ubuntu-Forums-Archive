---
title: "Diablo 2 crashes when switching acts"
date: 2008-11-18
forum: Wine
---

### Post by tee2 on 2008-11-18
Diablo 2 1.12 and latest wine. (1.1.8) Whenever I use a waypoint or meshief, etc. the game will crash with an illegal exception, access violation error. After some googling and searching of this forum I can't find any answers. Has anyone had this problem or know of how to fix it?

---

### Post by cogadh on 2008-11-19
We need more info. Run the game from the terminal and post the output here.

---

### Post by tee2 on 2008-11-19
```
tee@tee-desktop:~/.wine/drive_c/Program Files/Diablo II$ wine game.exe
err:mixer:MIX_Open ioctl(/dev/mixer, SOUND_MIXER_DEVMASK) failed (No such device or address)
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f338,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:d3d:IWineD3DDeviceImpl_CreateSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:d3d:IWineD3DDeviceImpl_CreateSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
err:d3d:IWineD3DDeviceImpl_SetupFullscreenWindow (0x13dc48): Want to change the window parameters of HWND 0x20028, but another style is stored for restoration afterwards
err:d3d:IWineD3DDeviceImpl_SetupFullscreenWindow (0x13dc48): Want to change the window parameters of HWND 0x20028, but another style is stored for restoration afterwards
err:ddraw:IDirectDrawSurfaceImpl_Flip Can't find a flip target
err:ddraw:IDirectDrawSurfaceImpl_Flip Can't find a flip target
err:ddraw:IDirectDrawSurfaceImpl_Flip Can't find a flip target
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:d3d:IWineD3DDeviceImpl_CreateSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
err:d3d:IWineD3DDeviceImpl_SetupFullscreenWindow (0x13dc48): Want to change the window parameters of HWND 0x20028, but another style is stored for restoration afterwards
fixme:d3d:IWineD3DDeviceImpl_CreateSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
err:d3d:IWineD3DDeviceImpl_SetupFullscreenWindow (0x13dc48): Want to change the window parameters of HWND 0x20028, but another style is stored for restoration afterwards
fixme:d3d:IWineD3DDeviceImpl_CreateSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
err:d3d:IWineD3DDeviceImpl_SetupFullscreenWindow (0x13dc48): Want to change the window parameters of HWND 0x20028, but another style is stored for restoration afterwards
fixme:d3d:IWineD3DDeviceImpl_CreateSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
err:d3d:IWineD3DDeviceImpl_SetupFullscreenWindow (0x13dc48): Want to change the window parameters of HWND 0x20028, but another style is stored for restoration afterwards
wine: Unhandled page fault on read access to 0x025d7c2c at address 0x6ff5cfe1 (thread 0021), starting debugger...
Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
0000001b 
	0000001c    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'
tee@tee-desktop:~/.wine/drive_c/Program Files/Diablo II$ 

```


That's the output. Any clues?

---

### Post by Gary13579 on 2008-11-19
Is Game.exe the official game, or is it D2Loader? D2Loader is buggy with switching acts and crashing (not to mention Warden is back on, and they are banning for D2Loader).

---

### Post by tee2 on 2008-11-19
> **Gary13579 said:**
> Is Game.exe the official game, or is it D2Loader? D2Loader is buggy with switching acts and crashing (not to mention Warden is back on, and they are banning for D2Loader).

It's the official game. No third party mods here.

---

### Post by tee2 on 2008-11-20
bump

:confused:

---

### Post by tee2 on 2008-11-21
bump again

---

### Post by tee2 on 2008-11-24
bump yet again

---

### Post by Shhnap on 2009-01-03
I think it is a regression in wine. Try and go back to 1.0 and see what happens. Soon the wine developers will fix the issue. I had this problem on another computer and that fixed it. :)

---

