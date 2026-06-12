---
title: "Need help getting a game working."
date: 2008-08-08
forum: Wine
---

### Post by Nuvious on 2008-08-08
I'm trying to get Star Wars Tie Fighter (the 95 version, not the dos version) working.  So far it loads, takes keyboard input, works with the mouse and all.  However, when I start a mission, it does not respond to joystick input and keyboard input freezes the application (wine still runs fine).  Here's the debug file with "warn+dll" implemented.

> err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Logitech USB Headset, disabling mixer
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32f754,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:int:DOSVM_Int1aHandler int1a: unknown/not implemented parameters:
int1a: AX b102, BX 0007, CX 0061, DX 1033, SI 0000, DI 1033, DS 007b, ES 007b
fixme:mcicda:MCICDA_GetError Unknown mode 1
fixme:d3d:state_monoenable Render state WINED3DRS_MONOENABLE not implemented yet
fixme:d3d:state_subpixel Render state WINED3DRS_SUBPIXEL not implemented yet
fixme:d3d:state_subpixelx Render state WINED3DRS_SUBPIXELX not implemented yet
fixme:d3d:state_monoenable Render state WINED3DRS_MONOENABLE not implemented yet (hundreds of these)


Two questions, first how do I set up the game on the command line to run in Windows 95 compatibility mode?  Finally, how do I make sure that it only uses the Wine dlls and not the Windows dlls (I'm trying to keep this fix portable for linux so one day I can make a linux distro of vintage games that runs off of a DVD).

Thanks in advance for serious replies!

---

### Post by raj7095 on 2009-11-07
Sorry, I am not good when it comes to using windows emulators. Why don't you go to winehq.com

---

### Post by beastrace91 on 2009-11-07
> **raj7095 said:**
> Sorry, I am not good when it comes to using windows emulators. Why don't you go to winehq.com

Did you really just make a post to say you are not sure how to help? Thats border line spam IMO.

@OP - To run an application with a certain Wine version (say Windows 95 as you want to) open your winecfg (Applications->Wine->WineCFG or **winecfg** in terminal) and select "add application" on the main page and find the .exe you wish to run using a different Windows version then once you add it click over and select a different Windows version to run it with from the drop down. And now when ever the selected .exe is run with Wine (from terminal or otherwise) it is run with the different Windows version.

EDIT: Also just saw the first post is over a year dead... Don't thread resurrect :/

Regards,
~Jeff

---

### Post by overdrank on 2009-11-07
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---

