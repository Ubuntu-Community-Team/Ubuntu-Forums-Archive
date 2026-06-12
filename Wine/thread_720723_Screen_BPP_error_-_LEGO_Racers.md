---
title: "Screen BPP error - LEGO Racers"
date: 2008-03-10
forum: Wine
---

### Post by chezzo on 2008-03-10
I'm trying to run Lego Racers with wine. It's installed fine but when I try to run it this is what happens...

wine "C:\Program Files\LEGO Racers\LEGORacers.exe" -novideo
fixme:win:EnumDisplayDevicesW ((null),0,0x34f2a4,0x00000000), stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x12db48)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x12db48)->(0x10024,00000811)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
wine: Unhandled page fault on write access to 0x00221000 at address 0xb7cf67e7 (thread 0009), starting debugger...
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7bc40aad

I tried following the advice in [http://ubuntuforums.org/showthread.php?t=649283](http://ubuntuforums.org/showthread.php?t=649283) but it didn't help.

---

### Post by chezzo on 2008-03-11
Sorry, should also have mentioned that the screen flickers a bit and the resolution gets set to 640x480 so I have to manually switch it back.

---

### Post by chezzo on 2008-03-11
Hmm, the plot thickens... I managed to get a bit further by using native dinput and quartz files, so when I try to load it now I get a black screen and then an error saying 
> Fatal Error
I/O error occurred
file GImages.idb
File not found

When I click "OK" the program terminates.

The terminal now reads
> fixme:win:GetRawInputDeviceList (pRawInputDeviceList=(nil), puiNumDevices=0x34fb80, cbSize=8) stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f2a4,0x00000000), stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x12e158)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x12e158)->(0x2005c,00000811)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x12e158)->(0x2005c,00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x12e158)->((nil),00000008)

I have tried searching both my PC and Google for "GImages.idb", both to no avail

---

### Post by chezzo on 2008-03-11
Now updated to the newest version of wine to see if it would help. It hasn't. I get the same error message and the terminal now reads
> fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
fixme:win:GetRawInputDeviceList (pRawInputDeviceList=(nil), puiNumDevices=0x34fb80, cbSize=8) stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f2d4,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16

---

### Post by chezzo on 2008-03-12
bump

i tried copying over from an install in windows, but still got the same problem

---

### Post by chezzo on 2008-03-13
bump...

someone must be able to help me! i've tried everything I can think of but still getting the same problem

---

### Post by chezzo on 2008-03-15
bump

---

### Post by chezzo on 2008-03-19
bump

---

### Post by happyhamster on 2008-03-19
Which wine version are you using? I ask because the wine database lists wine 0.9.53 as gold. (It's possible that more recent wine versions work worse.)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9757&iTestingId=20005](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9757&iTestingId=20005)

---

### Post by chezzo on 2008-03-20
> **happyhamster said:**
> Which wine version are you using? I ask because the wine database lists wine 0.9.53 as gold. (It's possible that more recent wine versions work worse.)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9757&iTestingId=20005](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9757&iTestingId=20005)

I was using whatever version is the latest in the Ubuntu update manager, then I installed the newest version (0.9.57) to see if it would help (it didn't). Do you reckon it's worth downgrading to 0.9.53 then?

---

### Post by dualscreenman on 2008-03-21
I seriously can't see how the person who submitted the gold got it to work by only substituing a native .dll.

I *can* get the Lego Racers demo to the main menu by using native devenum, dinput, and quartz dlls, but input of any sort doesn't work. I'm suspecting that these fixmes are to blame:

fixme:win:GetRawInputDeviceList (pRawInputDeviceList=(nil), puiNumDevices=0x33fda8, cbSize=8) stub!
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x7229f3bc, uiNumDevices=1, cbSize=12) stub!
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x7229f3a4, uiNumDevices=1, cbSize=12) stub!
fixme:d3d:state_subpixel Render state WINED3DRS_SUBPIXEL not implemented yet

Looks like Wine just plain doesn't support Lego Racers. :( It's a shame, because the 3D does all kinds of crazy crap in windows. 3D renders perfectly on the computer controlled races the game'll do if you leave it at the main menu for long enough.

---

### Post by dogeatery on 2008-07-05
I'm having hte same problem with Rome: Total War.  It's so disheartening, I thought I was close to having it work.  I know other people have gotten R:TW working in Ubuntu/Linux with wine but I can't get it past the copyrights page.  It just disappears and leaves me with the below terminal output.  I have tried switching some of the dlls as per this thread but this causes it to stop recognizing DirectX (I installed a later version of DirectX than the one that comes with R:TW)

Hope someone can help, terminal output is below:


```
dogeatery@dogeatery-laptop ~ $ wine /media/cdrom0/Launch.exe 
dogeatery@dogeatery-laptop ~ $ fixme:win:EnumDisplayDevicesW ((null),0,0x33de0c,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x137da0) : stub
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadTexture (0x13e838) Operation not supported for scratch textures
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d_surface:fb_copy_to_texture_direct >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glCopyTexSubImage2D @ surface.c / 2744
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x137da0) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x137da0) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x137da0) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x137da0) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x137da0) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x137da0) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x137da0) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x137da0) : stub
wine: Unhandled page fault on read access to 0x00000003 at address 0xda976e (thread 0029), starting debugger...
Unhandled exception: page fault on read access to 0x00000003 in 32-bit code (0x00da976e).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00da976e ESP:0033320c EBP:062abec8 EFLAGS:00010287(   - 00      RISP1C)
 EAX:00000001 EBX:00000003 ECX:00333250 EDX:00000003
 ESI:00333228 EDI:00333250
Stack dump:
0x0033320c:  00333224 00000003 00000001 00b0b9ab
0x0033321c:  00333224 00333228 00333580 00000001
0x0033322c:  01025aa1 00000003 00333580 00000001
0x0033323c:  00333580 00000001 062a66e8 00b0b928
0x0033324c:  fffffffd 00000000 00000000 04444480
0x0033325c:  00da87e2 00000003 00333580 04444478
Backtrace:
=>1 0x00da976e in rometw (+0x9a976e) (0x062abec8)
  2 0x00333580 (0x02944dec)
  3 0x00b03044 in rometw (+0x703044) (0x00b03480)
  4 0xf98b20ec (0x83535657)
  5 0x00000000 (0x00000000)
0x00da976e: movzbl    0x0(%edx),%ebx
Modules:
Module    Address            Debug info    Name (101 modules)
PE      340000-  358000    Deferred        mssds3d.m3d
PE      360000-  37b000    Deferred        mssdsp.flt
PE      400000- 29e49be    Export          rometw
PE    21100000-21160000    Deferred        mss32
PE    22300000-2232b000    Deferred        msseax.m3d
PE    22400000-22415000    Deferred        msssoft.m3d
PE    26f00000-26f29000    Deferred        mssmp3.asi
ELF    7b800000-7b930000    Deferred        kernel32<elf>
  \-PE    7b820000-7b930000    \               kernel32
ELF    7bc00000-7bca4000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bca4000    \               ntdll
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
ELF    7d76d000-7d7b7000    Deferred        dsound<elf>
  \-PE    7d770000-7d7b7000    \               dsound
ELF    7dfa8000-7e1e9000    Deferred        r200_dri.so
ELF    7e1e9000-7e24b000    Deferred        libgl.so.1
ELF    7e24b000-7e27e000    Deferred        uxtheme<elf>
  \-PE    7e250000-7e27e000    \               uxtheme
ELF    7e2a6000-7e2ba000    Deferred        midimap<elf>
  \-PE    7e2b0000-7e2ba000    \               midimap
ELF    7e2ba000-7e2e0000    Deferred        msacm32<elf>
  \-PE    7e2c0000-7e2e0000    \               msacm32
ELF    7e2e0000-7e2f7000    Deferred        msacm32<elf>
  \-PE    7e2f0000-7e2f7000    \               msacm32
ELF    7e2f7000-7e3ba000    Deferred        libasound.so.2
ELF    7e3cc000-7e402000    Deferred        winealsa<elf>
  \-PE    7e3e0000-7e402000    \               winealsa
ELF    7e402000-7e40b000    Deferred        libxcursor.so.1
ELF    7e40b000-7e410000    Deferred        libxfixes.so.3
ELF    7e410000-7e413000    Deferred        libxcomposite.so.1
ELF    7e413000-7e419000    Deferred        libxrandr.so.2
ELF    7e419000-7e421000    Deferred        libxrender.so.1
ELF    7e421000-7e424000    Deferred        libxinerama.so.1
ELF    7e424000-7e444000    Deferred        imm32<elf>
  \-PE    7e430000-7e444000    \               imm32
ELF    7e444000-7e449000    Deferred        libxdmcp.so.6
ELF    7e449000-7e461000    Deferred        libxcb.so.1
ELF    7e461000-7e548000    Deferred        libx11.so.6
ELF    7e548000-7e556000    Deferred        libxext.so.6
ELF    7e556000-7e55b000    Deferred        libxxf86vm.so.1
ELF    7e55b000-7e573000    Deferred        libice.so.6
ELF    7e573000-7e57b000    Deferred        libsm.so.6
ELF    7e57e000-7e588000    Deferred        libdrm.so.2
ELF    7e588000-7e58b000    Deferred        libxdamage.so.1
ELF    7e58d000-7e624000    Deferred        winex11<elf>
  \-PE    7e5a0000-7e624000    \               winex11
ELF    7e62a000-7e64b000    Deferred        libexpat.so.1
ELF    7e64b000-7e675000    Deferred        libfontconfig.so.1
ELF    7e676000-7e678000    Deferred        libxcb-xlib.so.0
ELF    7e687000-7e69c000    Deferred        libz.so.1
ELF    7e69c000-7e70c000    Deferred        libfreetype.so.6
ELF    7e70c000-7e738000    Deferred        ws2_32<elf>
  \-PE    7e710000-7e738000    \               ws2_32
ELF    7e738000-7e752000    Deferred        wsock32<elf>
  \-PE    7e740000-7e752000    \               wsock32
ELF    7e752000-7e811000    Deferred        comctl32<elf>
  \-PE    7e760000-7e811000    \               comctl32
ELF    7e811000-7e825000    Deferred        lz32<elf>
  \-PE    7e820000-7e825000    \               lz32
ELF    7e825000-7e83e000    Deferred        version<elf>
  \-PE    7e830000-7e83e000    \               version
ELF    7e83e000-7e866000    Deferred        msvfw32<elf>
  \-PE    7e840000-7e866000    \               msvfw32
ELF    7e866000-7e89d000    Deferred        dinput<elf>
  \-PE    7e870000-7e89d000    \               dinput
ELF    7e89d000-7e8b5000    Deferred        dinput8<elf>
  \-PE    7e8a0000-7e8b5000    \               dinput8
ELF    7e8b5000-7e8e0000    Deferred        d3d8<elf>
  \-PE    7e8c0000-7e8e0000    \               d3d8
ELF    7e8e0000-7e9e3000    Deferred        wined3d<elf>
  \-PE    7e8f0000-7e9e3000    \               wined3d
ELF    7e9e3000-7ea13000    Deferred        d3d9<elf>
  \-PE    7e9f0000-7ea13000    \               d3d9
ELF    7ea13000-7eaa5000    Deferred        winmm<elf>
  \-PE    7ea20000-7eaa5000    \               winmm
ELF    7eaa5000-7eab8000    Deferred        libresolv.so.2
ELF    7eab8000-7ead6000    Deferred        iphlpapi<elf>
  \-PE    7eac0000-7ead6000    \               iphlpapi
ELF    7ead6000-7eb38000    Deferred        rpcrt4<elf>
  \-PE    7eae0000-7eb38000    \               rpcrt4
ELF    7eb38000-7ebd6000    Deferred        gdi32<elf>
  \-PE    7eb50000-7ebd6000    \               gdi32
ELF    7ebd6000-7ed1d000    Deferred        user32<elf>
  \-PE    7ebf0000-7ed1d000    \               user32
ELF    7ed1d000-7ed6f000    Deferred        advapi32<elf>
  \-PE    7ed30000-7ed6f000    \               advapi32
ELF    7ed6f000-7ee13000    Deferred        ole32<elf>
  \-PE    7ed80000-7ee13000    \               ole32
ELF    7ee13000-7ee6b000    Deferred        ddraw<elf>
  \-PE    7ee20000-7ee6b000    \               ddraw
ELF    7ee6b000-7ee76000    Deferred        libnss_files.so.2
ELF    7ee76000-7ee8e000    Deferred        libnsl.so.1
ELF    7ee8e000-7ee97000    Deferred        libnss_compat.so.2
ELF    7ee98000-7ee9b000    Deferred        libxau.so.6
ELF    7efc9000-7efee000    Deferred        libm.so.6
ELF    7eff6000-7f000000    Deferred        libnss_nis.so.2
ELF    b7cd6000-b7cda000    Deferred        libdl.so.2
ELF    b7cda000-b7e29000    Deferred        libc.so.6
ELF    b7e2a000-b7e42000    Deferred        libpthread.so.0
ELF    b7e54000-b7f8a000    Deferred        libwine.so.1
ELF    b7f8c000-b7fa8000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
    0000001a    0
    00000019    0
    00000013    0
    00000012    0
    0000000e    0
    0000000d    0
0000000f 
    00000015    0
    00000014    0
    00000011    0
    00000010    0
00000016 
    0000001b    0
    00000018    0
    00000017    0
0000001e 
    0000001f    0
00000028 (D) C:\Program Files\Activision\Rome - Total War\RomeTW.exe
    0000002c   15
    0000002b   15
    0000002a    0
    00000029    0 <==
Backtrace:
=>1 0x00da976e in rometw (+0x9a976e) (0x062abec8)
  2 0x00333580 (0x02944dec)
  3 0x00b03044 in rometw (+0x703044) (0x00b03480)
  4 0xf98b20ec (0x83535657)
  5 0x00000000 (0x00000000)

```

---

### Post by dogeatery on 2008-07-05
So I have been going through the terminal output and decided that the errors really start with:

```
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
```

Now I'm confused as to how to make my color depth go to 16 bits ... I have done all sorts of searching and the "best" solution I can find is to run a second X session in 16-bit resolution.  I have tried messing with this a little bit, but I am afraid I'll f*** up my computer.

I should mention that I'm running wine v1.1 and I have tried it in all versions of Windows in winecfg.  I can provide a complete list of dll overrides, if necessary (it will be a lot of typing).

---

### Post by nanderv on 2009-12-25
Lego racers DOES run if you use the nintendo 64 version, and run that version trough Project64. Project64 is an nintendo 64 emulator.. Windows only, but runs perfectly in wine.

---

