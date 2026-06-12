---
title: "Why my games fail now?"
date: 2008-08-24
forum: Wine
---

### Post by heillos on 2008-08-24
Hi, 
 
 today my Kubuntu was updated and now there is wine 1.1.3~winehq0~ubuntu~8.04 and my games don't work Sad 
 


   $ env WINEPREFIX="/home/heillos/.wine" wine "C:\Sierra\Zeus - Pan Olimpu\Zeus.exe" 
 fixme:ntoskrnl:KeInitializeSpinLock 0x4577a4 
 fixme:win:EnumDisplayDevicesW ((null),0,0x32f774,0x00000000), stub! 
 fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16 
 fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16 
 fixme:d3d_surface:IWineD3DBaseSurfaceImpl_Blt Can't handle WINEDDBLT_ASYNC flag right now. 
 err:ddraw:IDirectDrawSurfaceImpl_IsLost  (0x142cc8) Implementation was changed from 2 to 0 
 err:ddraw:IDirectDrawSurfaceImpl_QueryInterface No interface 
 err:d3d:IWineD3DDeviceImpl_CreateSurface Unknown requested surface implementation 0! 
 wine: Unhandled page fault on read access to 0x00000000 at address 0x7e1409bc (thread 0009), starting debugger... 
 Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7e1409bc).
   
 
 Why? In prevoius version all was OK.

---

### Post by insane_alien on 2008-08-24
this happens in development versions a lot. by fixing one bug they have created a new one. 

i suggest you go back to the version that worked for you.

---

### Post by heillos on 2008-08-24
Thanx, that works... I hope, there is not permanent bug :(

---

### Post by Morokiane on 2008-08-25
1.1.3 broke every game I like playing.  WoW broke, Icewind Dale 1 and 2 broke, Ventrilo broke...very buggy release...had to go back in 1.1.2

---

