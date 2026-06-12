---
title: "Trying to get WC3 to work with wine."
date: 2008-07-14
forum: Wine
---

### Post by Lakjin on 2008-07-14
Okay so I installed both Warcraft III and the expansion onto ubuntu, into the wine c drive thing and tried running with wine. but it just...freezes thats all.

after doing a lot of research i see that maybe i have to run it with "opengl"?

i keep seeing this:
wine Warcraft3.exe -opengl

over and over but i have no idea where to put it...i tried in terminal but thats doing nothing

It finally hit me to run it as sudo but i ran into another problem
lakjin@lakjin-laptop:~$ sudo wine war3.exe --opengl
[sudo] password for lakjin:
wine: /home/lakjin/.wine is not owned by you

then i read up on how i should never run wine as sudo =X
so then i did sudo rm -rf ~/.wine && winecfg

and here i am. so what do i do now? How can i get this to work? Should i reinstall wc3 onto ubuntu (it got deleted somehow during this process)? Or is it possible to run wc3 from my /host/program files folder since i already have it installed on vista? thx!

Thx!

---

### Post by Lakjin on 2008-07-15
heres my log incase anyone is wondering:
lakjin@lakjin-laptop:~$ wine "/home/lakjin/.wine/drive_c/Program Files/Warcraft III/war3.exe" --opengl
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:cursor:SetSystemCursor (0x111e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f03),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f02),stub!
err:ole:CoCreateInstance apartment not initialised
libGL error: drmMap of framebuffer failed (Cannot allocate memory)
libGL error: reverting to (slow) indirect rendering
fixme:win:EnumDisplayDevicesW ((null),0,0x33eca4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f07c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec90,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x32 @75! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x32 @70! (XRandR)
fixme:quartz:AVISplitter_InitializeStreams stream 1: frames found: 2172570, frames meant to be found: 2173350
fixme:win:EnumDisplayDevicesW ((null),0,0x33df34,0x00000000), stub!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
err:ntdll:RtlpWaitForCriticalSection section 0x159bcc "videorenderer.c: VideoRendererImpl.csFilter" wait timed out in thread 0021, blocked by 0013, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x159bcc "videorenderer.c: VideoRendererImpl.csFilter" wait timed out in thread 0021, blocked by 0013, retrying (60 sec)
Terminated

Update: I read somewhere that the ingame movies dont work, so i deleted the movies folder. wc3 loads up, but 1) its REALLY REALY slow and 2) it keeps flashing back and worth from wc3 to the desktop...

---

### Post by kdorf on 2008-07-15
Yes, you need to reinstall. The ~/.wine directory is where all of your installed applications go by default. Running wine with sudo is insecure and messes up your .wine directory permissions.

You need to run Warcraft with
```
wine "C:\Program Files\Warcraft III\war3.exe" -opengl
```

Just like that in terminal.

---

### Post by Lakjin on 2008-07-15
wine "/home/lakjin/.wine/drive_c/Program Files/Warcraft III/war3.exe" --opengl

isnt that the same thing? i already tried that.

---

