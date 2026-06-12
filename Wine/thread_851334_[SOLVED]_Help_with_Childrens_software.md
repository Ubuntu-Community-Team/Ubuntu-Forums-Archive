---
title: "[SOLVED] Help with Childrens software"
date: 2008-07-06
forum: Wine
---

### Post by ARhere on 2008-07-06
I am trying to get this software to work for our children's program on our churches computers.  They all run Ubuntu 8.04 with WINE 1.1.0.  The software is [www.lifelinekids.com](www.lifelinekids.com) and uses Flash for the interface and Quicktime for the movies.  I installed the program in WINE and also installed Quicktime 6.5.1 under WINE as well.

The programs starts and works great except when it tries to play a Quicktime movie within the program.  You hear the sound but the screen where the movie is played is blank.  I have tested Quicktime by itself in WINE and it works fine.  I have also tried ```
sudo chmod -vR 777 <path of Quicktime and Program>
``` but that did nothing.

I noticed when the movie started to play I see the following scroll in the terminal...
```
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\QTFont.for",L"C:\\windows\\QTFont.qfn",(null)): stub
fixme:mountmgr:harddisk_ioctl unsupported ioctl 70c00
fixme:mountmgr:harddisk_ioctl unsupported ioctl 70c00
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x3ef09c8)->(0x32d46c, (nil)): Stub!

```
Any of you Linux geeks with a bleeding heart to help make this work.  If I cannot, then I know the children's director will think the "computers are broke" and will want to spend $$$ for MS preloaded computers.

-AR

---

### Post by ARhere on 2008-07-06
I ran the program using the winedbg command.  This is the output.
```
Wine-dbg>step
Single stepping until exit from function, 
which has no line number information.
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x33e504,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\QTFont.for",L"C:\\windows\\QTFont.qfn",(null)): stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\QTFont.for",L"C:\\windows\\QTFont.qfn",(null)): stub
fixme:mountmgr:harddisk_ioctl unsupported ioctl 70c00
fixme:mountmgr:harddisk_ioctl unsupported ioctl 70c00
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d30c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d46c, (nil)): Stub!
fixme:ddraw:IDirectDrawImpl_GetFourCCCodes (0x7420178)->(0x33d46c, (nil)): Stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmp22BA1.FOT",L"C:\\windows\\temp\\AAXab17.tmp",(null)): stub
fixme:font:CreateScalableFontResourceW (0,L"C:\\windows\\system32\\tmpE8BA1.FOT",L"C:\\windows\\temp\\AAXab83.tmp",(null)): stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
Invalid address (0x7b877567) for breakpoint 0, disabling it
Process of pid=0016 has terminated
Wine-dbg>

```

Any ideas?
-AR

---

### Post by ARhere on 2008-07-06
[SIZE="6"]PING![/SIZE]

Any ideas?  I was wondering if it would have something to do with permissions.  The main flash based program (*in WINE*) is trying to access Quicktime (*also in WINE*).  Is there something special I have to do to let a program in WINE call another program?

-AR

---

### Post by ARhere on 2008-07-08
In case anyone is curious an easier solution presented itself.  The software vendor released a new version based on flash instead of Quicktime.

It was nice becasue I told the company owner that he should port it to MAC and Linux as it is *relatively* easy to do so with flash.

-AR

---

