---
title: "half life 2 crashes on start up"
date: 2008-07-15
forum: Wine
---

### Post by terry f on 2008-07-15
Hi

I hope some one can help me get half life 2 to run. When I start up the game it crashes. I can see the blared screen where the menu should load but it crashes before that happens. I have read that there is a bug with the sound setting in wine and have already taken care of that. Does any one know of what may be causing it to crash.

---

### Post by scragar on 2008-07-15
run the application from the terminal(use edit menu to find the command),and be sure to remove anything that say's:
```
WINEDEBUG=-all
```
since this would hide the debug.

post the lines around the time it crashes.

---

### Post by terry f on 2008-07-15
I got this as and output

```
terry@terry-desktop:~/.wine/drive_c/Program Files/Steam$ WINEDEBUG=-all wine steam.exe -applaunch 220 -novid -dxlevel 90 -width 1024 -height 768
CellID: Fetching server list from CSDS. . .
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
CellID: CSDS returned 157 servers.
CellID: Connecting to 208.111.140.3:27031. . .
CellID: Connect to 208.111.140.3:27031 took 126 MS
CellID: Nothing beat our old best time of 34 MS
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
wine: Call from 0xf2f5e01 to unimplemented function vstdlib_s.dll.Q_CopyAndFixSlashes, aborting


```

---

### Post by greyfox1 on 2008-07-15
I don't know what the fix for this would be, but I'd say it's definitely a sound issue given the references to ALSA in the 2nd to last line of terminal output.  Is there a reason why you are using ALSA and not PulseAudio?

---

### Post by terry f on 2008-07-15
I don't know why I don't use PulseAudio other then it is not an option in the config menu.  Can you tell me how to set it up?

---

### Post by greyfox1 on 2008-07-22
Actually, forget what I said.  I didn't realize that PulseAudio isn't an option under WINE.  So, consider this a *bump*-- anyone make anything from his terminal output?

---

### Post by evets25 on 2008-07-22
I had a similar problem with HL2 under wine that was related to sound and caused a crash when you start up HL2. What it was was that a part of steam was stealing control of the sound card and wouldn't let go, and so when HL2 started, it wanted control of the sound card, but steam wouldn't play nice... anywho, my solution was a weird hack. I would start up another program that used sound (like a movie in totem), then opened steam while the sound card was in use, to prevent steam from getting access to the sound card. Then I closed totem, to release the sound card, and opened HL2. Voila. no crash, HL2 is happy and can access the sound card. 

This probably has a couple dozen other solutions and is a a huge problem that I don't fully understand, but try this, and do some digging on HL2 and steam-related sound-issues, on the wine appdb page, and on the cedega forums.

---

### Post by veillifter on 2008-07-22
(WARNING, I AM A UBUNTU N00B)

I too am having crashes upon start up of Half-Life 2.  I have no clue what the problem could be and have only just installed Ubuntu recently.  I have made sure to install the proper (restricted) graphics car drivers (ATI Mobility Radeon x1600), and have also fooled around wither certain "sound-issues" solutions.  

The valvE movie opens up (with sound), however the keyboard/mouse do not seem to work, as the game doesn't cut to the main menu.  I have to wait until soon, the "Loading" is seen in the bottom right-hand corner, and the blurry background of City 17 can be seen.  Just as I think it's going to load the menus, the game reverts back to Steam, no Half-Life 2 in sight.

I (finally) figured out how to open HL2 via the terminal, and this is what I got:
> veillifter@veillifter-laptop:~$ wine ~/.wine/drive_c/Program\ FIles/Steam/SteamApps/exodusd/half-life\ 2/hl2.exe -applaunch 440
fixme:win:EnumDisplayDevicesW ((null),0,0x32e13c,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3594
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1416d0) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1416d0) Event query: Unimplemented, but pretending to be supported
fixme:d3d_surface:IWineD3DSurfaceImpl_PreLoad >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glGenTextures @ surface.c / 513
fixme:d3d_surface:IWineD3DSurfaceImpl_PreLoad >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ surface.c / 517
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexImage2D @ surface.c / 340
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCopyTexSubImage2D @ surface.c / 936
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1416d0) : stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1416d0) Event query: Unimplemented, but pretending to be supported
err:alsa:ALSA_copyFormat calculated 50 bytes, capping to 40 bytes
fixme:wave:wodOpen unimplemented format: WAVE_FORMAT_ADPCM
wine: Call from 0xea220e1 to unimplemented function vstdlib_s.dll.Q_CopyAndFixSlashes, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
fixme:d3d_surface:IWineD3DSurfaceImpl_PreLoad >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glGenTextures @ surface.c / 513
fixme:d3d_surface:IWineD3DSurfaceImpl_PreLoad >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glBindTexture @ surface.c / 517
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glTexImage2D @ surface.c / 340
fixme:d3d_surface:read_from_framebuffer_texture >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCopyTexSubImage2D @ surface.c / 936
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1416d0) : stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1416d0) Event query: Unimplemented, but pretending to be supported
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e2c8 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xe466010) : pBox=0x32e31c stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1416d0) : stub
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:avifile:AVIFileExit (): stub!



I figured to post in this thread as my problem is (sorta) the same.
I hope the community can provide insight/help us both out, thank you.

~Dave

---

### Post by Baarhisveiki on 2008-07-27
well....last time i visited the wine website their where talking bout having fixed the bug of Half life 2....so i guess its an wine problem since a previous update. It should be oke with the latest Wine 1.1.1 ? Check it out. I dont have hl2 so i cant.

---

### Post by terry f on 2008-07-28
I got half life 2 to start up now and it runs after I updated my drivers. But, it is slow, very slow, and every thing is turned as low as possible.

---

### Post by aoanla on 2008-07-28
Run Half Life 2 with the -dxlevel 81 
option set.

DirectX 9 in Wine is slow for Source-engine games at present (and has been since reasonable DirectX 9 support was added to Wine), so you need to tell HL2 to be a DX8.1 game instead.

---

