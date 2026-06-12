---
title: "[SOLVED] Thief 2 won't even start (rc4)"
date: 2008-06-11
forum: Wine
---

### Post by OpposingForce on 2008-06-11
Ubuntu 8.04, Wine 1.0 rc4, latest nvidia drivers

I just installed thief 2, the install got to 100% but then wouldn't close when it was finished.  I don't think that has much to do with anything because it happened with diablo 2 also and it works.  Anyway, thief 2 does not even start.  I click the icon, and it just goes to a black screen, flickers real fast, then goes back to the desktop.  Any help is appreciated

edit- Windowed mode does not work either.  I also just tried compatibility mode and it does the same thing for all the versions of windows compatibility, except in windows 95 mode it just goes black and says "video mode not supported" on my monitor.

---

### Post by cogadh on 2008-06-12
Supposedly, the game won't work on multi-core or hyper threading systems (Windows or Wine) unless you set the processor affinity to a single core. If you have a multi-core or hyperthreading processor in your system, you can get around that issue by installing the schedtool package and running the game like this:
```
schedtool -a 0x2 -e wine thief2.exe
```

---

### Post by OpposingForce on 2008-06-12
Actually I use a single core processor.  It's an AMD 64 3700+ .. but I didn't install 64 bit ubuntu because I've heard it's a pain to get some things working.  I'm running 32 bit and single core.

---

### Post by cogadh on 2008-06-12
Run the game from the terminal and post the output.

---

### Post by OpposingForce on 2008-06-12
```
cory@cory-desktop:~$ wine /home/cory/.wine/drive_c/Program\ Files/Thief2/thief2.exe
err:mixer:MIX_Open ioctl(/dev/mixer, SOUND_MIXER_DEVMASK) failed (Invalid argument)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f660,0x00000000), stub!
wine: Unhandled page fault on read access to 0x00000000 at address 0x428049 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00428049).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00428049 ESP:0033fcf0 EBP:80000003 EFLAGS:00010256(   - 00      RIZAP1)
 EAX:00000000 EBX:80000003 ECX:ffffffff EDX:00000000
 ESI:00b1bb50 EDI:00000000
Stack dump:
0x0033fcf0:  00000006 0033fd80 00080000 00b24a5c
0x0033fd00:  80000003 004212dd 00b1bb50 80000003
0x0033fd10:  00000000 00000015 004211e7 0033fd80
0x0033fd20:  005b5ae5 00b19d2c 00080000 0033fd80
0x0033fd30:  005b7d10 00b132fc 00080000 0033fd80
0x0033fd40:  00000000 00b1acc4 00000000 0062a5ac
Backtrace:
=>1 0x00428049 in thief2 (+0x28049) (0x80000003)
0x00428049: movb	0x0(%eax),%cl
Modules:
Module	Address			Debug info	Name (76 modules)
PE	  400000-  7db000	Export          thief2
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d2fc000-7d330000	Deferred        dplayx<elf>
  \-PE	7d300000-7d330000	\               dplayx
ELF	7d347000-7d352000	Deferred        libgcc_s.so.1
ELF	7d35f000-7d396000	Deferred        dinput<elf>
  \-PE	7d370000-7d396000	\               dinput
ELF	7d93f000-7e454000	Deferred        libglcore.so.1
ELF	7e454000-7e4f8000	Deferred        libgl.so.1
ELF	7e505000-7e608000	Deferred        wined3d<elf>
  \-PE	7e520000-7e608000	\               wined3d
ELF	7e630000-7e687000	Deferred        ddraw<elf>
  \-PE	7e640000-7e687000	\               ddraw
ELF	7e687000-7e6d1000	Deferred        dsound<elf>
  \-PE	7e690000-7e6d1000	\               dsound
ELF	7e6d1000-7e6e5000	Deferred        midimap<elf>
  \-PE	7e6e0000-7e6e5000	\               midimap
ELF	7e6e5000-7e70b000	Deferred        msacm32<elf>
  \-PE	7e6f0000-7e70b000	\               msacm32
ELF	7e70b000-7e722000	Deferred        msacm32<elf>
  \-PE	7e710000-7e722000	\               msacm32
ELF	7e722000-7e75d000	Deferred        wineoss<elf>
  \-PE	7e730000-7e75d000	\               wineoss
ELF	7e75d000-7e766000	Deferred        libxcursor.so.1
ELF	7e766000-7e76b000	Deferred        libxfixes.so.3
ELF	7e76b000-7e76e000	Deferred        libxcomposite.so.1
ELF	7e76e000-7e774000	Deferred        libxrandr.so.2
ELF	7e774000-7e77c000	Deferred        libxrender.so.1
ELF	7e77c000-7e77f000	Deferred        libxinerama.so.1
ELF	7e77f000-7e79f000	Deferred        imm32<elf>
  \-PE	7e790000-7e79f000	\               imm32
ELF	7e79f000-7e7a4000	Deferred        libxdmcp.so.6
ELF	7e7a4000-7e7bc000	Deferred        libxcb.so.1
ELF	7e7bc000-7e7bf000	Deferred        libxau.so.6
ELF	7e7bf000-7e8a6000	Deferred        libx11.so.6
ELF	7e8a6000-7e8b4000	Deferred        libxext.so.6
ELF	7e8b4000-7e8b9000	Deferred        libxxf86vm.so.1
ELF	7e8b9000-7e8d1000	Deferred        libice.so.6
ELF	7e8d1000-7e8d9000	Deferred        libsm.so.6
ELF	7e8e2000-7e8e4000	Deferred        libnvidia-tls.so.1
ELF	7e8e6000-7e97d000	Deferred        winex11<elf>
  \-PE	7e8f0000-7e97d000	\               winex11
ELF	7e99b000-7e9bc000	Deferred        libexpat.so.1
ELF	7e9bc000-7e9e6000	Deferred        libfontconfig.so.1
ELF	7e9e6000-7e9fb000	Deferred        libz.so.1
ELF	7e9fb000-7ea6b000	Deferred        libfreetype.so.6
ELF	7ea6b000-7ea6d000	Deferred        libxcb-xlib.so.0
ELF	7ea78000-7ea8b000	Deferred        libresolv.so.2
ELF	7ea98000-7eab6000	Deferred        iphlpapi<elf>
  \-PE	7eaa0000-7eab6000	\               iphlpapi
ELF	7eab6000-7eb17000	Deferred        rpcrt4<elf>
  \-PE	7eac0000-7eb17000	\               rpcrt4
ELF	7eb17000-7ebbb000	Deferred        ole32<elf>
  \-PE	7eb30000-7ebbb000	\               ole32
ELF	7ebbb000-7ec4d000	Deferred        winmm<elf>
  \-PE	7ebd0000-7ec4d000	\               winmm
ELF	7ec4d000-7ec9f000	Deferred        advapi32<elf>
  \-PE	7ec60000-7ec9f000	\               advapi32
ELF	7ec9f000-7ed3a000	Deferred        gdi32<elf>
  \-PE	7ecb0000-7ed3a000	\               gdi32
ELF	7ed3a000-7ee81000	Deferred        user32<elf>
  \-PE	7ed50000-7ee81000	\               user32
ELF	7efa1000-7efac000	Deferred        libnss_files.so.2
ELF	7efac000-7efb6000	Deferred        libnss_nis.so.2
ELF	7efb6000-7efce000	Deferred        libnsl.so.1
ELF	7efce000-7eff3000	Deferred        libm.so.6
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7c86000-b7c8a000	Deferred        libdl.so.2
ELF	b7c8a000-b7dd9000	Deferred        libc.so.6
ELF	b7dda000-b7df2000	Deferred        libpthread.so.0
ELF	b7dff000-b7f35000	Deferred        libwine.so.1
ELF	b7f37000-b7f53000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Thief2\thief2.exe
	0000001d   15
	0000001c   15
	00000019    0
	00000009    0 <==
0000000c 
	00000016    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000017 
	00000018    0
Backtrace:
=>1 0x00428049 in thief2 (+0x28049) (0x80000003)
fixme:winmm:MMDRV_Exit Closing while ll-driver open
cory@cory-desktop:~$ 

```

---

### Post by cogadh on 2008-06-12
Instead of running the game with the full path, change directories to the game's install directory, then "wine" the executable:
```
cd ~/.wine/drive_c/Program\ Files/Thief2
wine thief2.exe
```
Windows programs prefer to be run from within the directory where they are installed, otherwise they have trouble finding all the necessary support files. Using that method may make some of that error go away, but there is one particular portion that error doesn't look good at all:
```
err:mixer:MIX_Open ioctl(/dev/mixer, SOUND_MIXER_DEVMASK) failed (Invalid argument)
```
It is usually normal to get some sound errors when running Wine, but that one is a little different. It looks like you have a sound card that is capable of hardware mixing, but the mixer device is failing when Wine tries to use it. Do you have a unique or custom sound configuration, either system-wide or in Wine?

---

### Post by OpposingForce on 2008-06-12
> **cogadh said:**
> Instead of running the game with the full path, change directories to the game's install directory, then "wine" the executable:
```
cd ~/.wine/drive_c/Program\ Files/Thief2
wine thief2.exe
```
Windows programs prefer to be run from within the directory where they are installed, otherwise they have trouble finding all the necessary support files. Using that method may make some of that error go away, but there is one particular portion that error doesn't look good at all:
```
err:mixer:MIX_Open ioctl(/dev/mixer, SOUND_MIXER_DEVMASK) failed (Invalid argument)
```
It is usually normal to get some sound errors when running Wine, but that one is a little different. It looks like you have a sound card that is capable of hardware mixing, but the mixer device is failing when Wine tries to use it. Do you have a unique or custom sound configuration, either system-wide or in Wine?

Ok I tried that first part, about CDing to the thief directory and running the command, and it just came up with a grey screen that kept flickering between grey and black colors and I had to reset X to make it stop.  

The second part yes, I'm using OSS4 and followed this guy's guide:

[http://ubuntuforums.org/showthread.php?t=780961&highlight=oss4](http://ubuntuforums.org/showthread.php?t=780961&highlight=oss4)

I'm using a creative xfi card and OSS4 is the only choice I have for getting the card to work in linux.  I don't have a problem with any other game in WINE with OSS, diablo 2, half life, hl2, etc, all work fine with it.

---

### Post by cogadh on 2008-06-12
When you run those other games from the terminal do you get the same mixer error? If so, then it is probably just a red herring and we can ignore it. If not, then Thief 2 must be doing something different than those other games with sound that Wine or OSS4 doesn't like.

---

### Post by OpposingForce on 2008-06-12
Just ran diablo II using the same cd procedure you told me to use for thief2.  This was the output

```
cory@cory-desktop:~/.wine/drive_c/Program Files/Diablo II$ wine Diablo\ II.exe
err:mixer:MIX_Open ioctl(/dev/mixer, SOUND_MIXER_DEVMASK) failed (Invalid argument)
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg2: Permission denied
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
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
fixme:advapi:SetSecurityInfo stub
cory@cory-desktop:~/.wine/drive_c/Program Files/Diablo II$ fixme:win:EnumDisplayDevicesW ((null),0,0x807724,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:ddraw:IDirectDrawSurfaceImpl_Flip Can't find a flip target
err:ddraw:IDirectDrawSurfaceImpl_Flip Can't find a flip target
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
cory@cory-desktop:~/.wine/drive_c/Program Files/Diablo II$ 

```

The game started and played fine and I heard sound, just like normal.

---

### Post by OpposingForce on 2008-06-12
Update: Thief 1 works.  I just installed it and it plays.  It runs on basically the same engine as Thief 2 which is odd why T2 doesn't work.  Here is the console output of the install process and first run of the game.

```
cory@cory-desktop:/media/cdrom0$ wine setup.exe -lgntforce
err:mixer:MIX_Open ioctl(/dev/mixer, SOUND_MIXER_DEVMASK) failed (Invalid argument)
err:mixer:MIX_Open ioctl(/dev/mixer, SOUND_MIXER_DEVMASK) failed (Invalid argument)
err:mmio:MMIO_ParseExtA No . in szFileName: "G:\\SETUP\\"
err:mmio:MMIO_ParseExtA No . in szFileName: "G:\\SETUP\\"
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:menubuilder:WaitForParentProcess Unable to wait for parent process, error 0
err:menubuilder:WaitForParentProcess Unable to wait for parent process, error 0
err:menubuilder:WaitForParentProcess Unable to wait for parent process, error 0
err:menubuilder:WaitForParentProcess Unable to wait for parent process, error 0
err:menubuilder:WaitForParentProcess Unable to wait for parent process, error 0
err:menubuilder:WaitForParentProcess Unable to wait for parent process, error 0
err:menubuilder:InvokeShellLinker failed wait for semaphore
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:InvokeShellLinker failed wait for semaphore
err:menubuilder:InvokeShellLinker failed wait for semaphore
err:menubuilder:InvokeShellLinker failed wait for semaphore
err:menubuilder:InvokeShellLinker failed wait for semaphore
err:menubuilder:InvokeShellLinker failed wait for semaphore
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
err:mixer:MIX_Open ioctl(/dev/mixer, SOUND_MIXER_DEVMASK) failed (Invalid argument)
err:mixer:MIX_Open ioctl(/dev/mixer, SOUND_MIXER_DEVMASK) failed (Invalid argument)
err:mixer:MIX_Open ioctl(/dev/mixer, SOUND_MIXER_DEVMASK) failed (Invalid argument)
err:mixer:MIX_Open ioctl(/dev/mixer, SOUND_MIXER_DEVMASK) failed (Invalid argument)
fixme:ole:CoCreateInstance no instance created for interface {a3d8cec0-7e5a-11cf-bbc5-00805f6cef20} of class {bd323430-ce94-11ce-82dd-0800095a5b55}, hres is 0x80004002
fixme:ole:CoCreateInstance no instance created for interface {a3d8cec0-7e5a-11cf-bbc5-00805f6cef20} of class {bd323431-ce94-11ce-82dd-0800095a5b55}, hres is 0x80004002
fixme:ole:CoCreateInstance no instance created for interface {a3d8cec0-7e5a-11cf-bbc5-00805f6cef20} of class {87ca6f02-49e4-11cf-a3fe-00aa003735be}, hres is 0x80004002
fixme:ole:CoCreateInstance no instance created for interface {a3d8cec0-7e5a-11cf-bbc5-00805f6cef20} of class {bd323432-ce94-11ce-82dd-0800095a5b55}, hres is 0x80004002
fixme:ole:CoCreateInstance no instance created for interface {a3d8cec0-7e5a-11cf-bbc5-00805f6cef20} of class {bd323433-ce94-11ce-82dd-0800095a5b55}, hres is 0x80004002
fixme:ole:CoCreateInstance no instance created for interface {a3d8cec0-7e5a-11cf-bbc5-00805f6cef20} of class {87ca6f04-49e4-11cf-a3fe-00aa003735be}, hres is 0x80004002
cory@cory-desktop:/media/cdrom0$ err:mixer:MIX_Open ioctl(/dev/mixer, SOUND_MIXER_DEVMASK) failed (Invalid argument)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f868,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:quartz:FilterGraphInner_QueryInterface unknown interface {56a868a3-0ad4-11ce-b03a-0020af0ba770}
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:VideoRendererInner_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
err:quartz:Parser_Destroy pinref should be null, is 1, destroying anyway
fixme:quartz:FilterGraphInner_QueryInterface unknown interface {56a868a3-0ad4-11ce-b03a-0020af0ba770}
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:VideoRendererInner_QueryInterface No interface for {56a868b3-0ad4-11ce-b03a-0020af0ba770}!
err:quartz:Parser_Destroy pinref should be null, is 1, destroying anyway
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1559f8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1559f8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1559f8) : stub
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1559f8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1559f8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1559f8) : stub
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1559f8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1559f8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1559f8) : stub
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1559f8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1559f8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1559f8) : stub
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1559f8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1559f8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1559f8) : stub
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1559f8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1559f8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x1559f8) : stub
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface

```



**Edit**: Also just found this

[http://www.ttlg.com/forums/showthread.php?referrerid=35319&t=103711](http://www.ttlg.com/forums/showthread.php?referrerid=35319&t=103711)

Someone else with (seemly) the same problem using wine.  Someone on the forum there mentioned it being a codec not registering/starting properly.  I'll try reinstalling the game later maybe

edit - reinstalling worked.  the game runs pretty well

---

