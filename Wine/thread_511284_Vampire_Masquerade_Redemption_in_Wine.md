---
title: "Vampire Masquerade Redemption in Wine"
date: 2007-07-27
forum: Wine
---

### Post by nemo.r on 2007-07-27
I'm trying to play Vampire Masquerade Redemption in Wine, according to the Wine site it should run fine, I was able to install it without any problems, and I also downloaded the 1.1 patch and that installed fine. 

The problems start when I try to play; at first it wouldn't recognize my CD and kept asking for CD 2. I then followed a few instructions I found on the Wine page, (windows 98 mode, direct x mouse control enabled, native window manager deacitvated, OSS audio drivers emulate drivers, pixel and vertex shaders off)

Now what happens is I insert the CD, comes up as 'Vampire_Play' on the desktop, I open it, select autorun, open with Wine, it runs, I get the picture of a statue and a red door, with Play, Help, More and Quit, overlaid on the screen. The Help More and Quit options work fine, but when I select play the green demoshield/install shield screen appears for a second then dissappears. When i select setup.exe from within the CD files the same thing happens, but the demo screen remains until I press exit. FinallyI tried opening it from within .wine, program files etc, I open the file vampire.exe with wine, and the same thing happens as with the autorun, (I press play and the green screen appears then dissappears). I've also tried it with Wine in Windows 2000 mode and 95 mode, same thing happens.

I'm sure I'm missing something very simple, but I really want to get past the blasted door!!

Thanks in advance!

---

### Post by cogadh on 2007-07-27
First off, the game will only run if you get a cracked EXE, the copy protection on the game is not supported by Wine. Secondly, somewhere around Wine 0.9.37 or 38 there was a serious regression that caused the game to stop functioning and the problem still exists with the current Wine, 0.9.41. AFAIK, the only way you can actually run the game now is by downgrading to Wine 0.9.36 or 35. The current AppDB listing that says the game works is based on a test run with 0.9.35, so I would start with that.

I used to play this one all the time and I actually had to boot my Windows partition the other day just to play it again... very sad :(

---

### Post by nemo.r on 2007-07-28
OK, I've installed wine version 0.9.35, and I reinstalled Vampire, then I downloaded the patch and a no cd crack. I had to make the permissions for vampire.exe in the c drive read and write, not read only, then I ran the crack, it said the exe was cracked, so I inserted cd 2, but I'm till getting the same problem. I tried two other cracks, one seemed to work, the other didn't do anything, I clicked on it, open with wine, and it didn't seem to start. 

Either way, with every crack, with the crack in the vampire directory or out, it still can't get past the play button.

Is it a problem with my copy of the game? I tried it in a windows computer in case it was the actual cds, but there it couldn't even reach the installation part, it just says something like preparing to install, then freezes at 99%

---

### Post by cogadh on 2007-07-28
The 99% install error is known problem with installing the game in Windows, it might not be an indication of the condition of your disks. 

If you already applied the crack, then you don't need the CD to run the game anymore (that's the whole point of the crack). Try doing this to launch the game:
```
cd $HOME/.wine/drive_c/Program\ Files/Vampire\ The\ Masquerade\ -\ Redemption/
wine Vampire.exe
```

---

### Post by nemo.r on 2007-07-29
OK, I typed the command in and this is what I got:


```
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd5f508)->(0x8004e,00000013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_LINEPATTERN (0000000a) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_MONOENABLE (0000000b) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_ROP2 (0000000c) value : 0000000d !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_PLANEMASK (0000000d) value : ffffffff !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_LASTPIXEL (00000010) value : 00000001 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_ZVISIBLE (0000001e) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_EDGEANTIALIAS (00000028) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_RANGEFOGENABLE (00000030) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_EXTENTS (0000008a) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_VERTEXBLEND (00000097) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_EXTENTS (0000008a) value : 00000000 !
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
wine: Unhandled page fault on read access to 0x5420657a at address 0x21114dd3 (thread 000f), starting debugger...
WineDbg starting on pid 0x11
Unhandled exception: page fault on read access to 0x5420657a in 32-bit code (0x21114dd3).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:21114dd3 ESP:7fb9f968 EBP:7fb9fd80 EFLAGS:00010202(   - 00      - -RI1)
 EAX:00000000 EBX:7d8f4a80 ECX:5420657a EDX:4d206568
 ESI:7b996a48 EDI:7d8f4de0
Stack dump:
0x7fb9f968:  7d8f4d24 21103ff6 7b996a48 7d8f4d24
0x7fb9f978:  7ecc6ed5 7b996a48 0000ac44 00000000
0x7fb9f988:  7eca87e9 7d8f4d24 0000ac44 00000010
0x7fb9f998:  00000002 00000000 7d8f4a80 7eea9080
0x7fb9f9a8:  7eea61f0 7eea3f10 00000280 000001e0
0x7fb9f9b8:  00000406 00000000 00000000 00000bb5
0200: sel=1007 base=7fe4a000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x21114dd3 in mss32 (+0x14dd3) (0x21114dd3)
fixme:dbghelp:sffip_cb NIY on 'C:\vampire\code\Game\Release\Vampire.pdb'
  2 0x0042d926 in vampire (+0x2d926) (0x0042d926)
  3 0x00000005 (0x00000005)
0x21114dd3: cmpl        $1,0x0(%ecx)
Modules:
Module  Address                 Debug info      Name (87 modules)
PE      0x00400000-00733000     Export          vampire
PE      0x10000000-10062000     Deferred        javai
PE      0x21100000-2115c000     Export          mss32
PE      0x22100000-22111000     Deferred        mssa3d.m3d
PE      0x22200000-22212000     Deferred        mssa3d2.m3d
PE      0x22400000-22411000     Deferred        mssds3dh.m3d
PE      0x22500000-22511000     Deferred        msseax.m3d
PE      0x22600000-22612000     Deferred        mssfast.m3d
PE      0x22c00000-22c14000     Deferred        msseax2.m3d
PE      0x26f00000-26f26000     Deferred        mp3dec.asi
PE      0x65f00000-65fc2000     Deferred        ole32
PE      0x70bd0000-70c35000     Deferred        shlwapi
PE      0x78000000-78044000     Deferred        msvcrt
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7cab8000-7cb30000     Deferred        ddraw<elf>
  \-PE  0x7cad0000-7cb30000     \               ddraw
PE      0x7cb30000-7cdf5000     Deferred        rldirect
ELF     0x7da0b000-7da20000     Deferred        midimap<elf>
  \-PE  0x7da10000-7da20000     \               midimap
ELF     0x7db35000-7db57000     Deferred        msacm32<elf>
  \-PE  0x7db40000-7db57000     \               msacm32
ELF     0x7db57000-7db6e000     Deferred        msacm<elf>
  \-PE  0x7db60000-7db6e000     \               msacm
ELF     0x7db6e000-7dbb0000     Deferred        wineoss<elf>
  \-PE  0x7db80000-7dbb0000     \               wineoss
ELF     0x7dc96000-7dcc6000     Deferred        uxtheme<elf>
  \-PE  0x7dca0000-7dcc6000     \               uxtheme
ELF     0x7dd0a000-7dd0f000     Deferred        libxfixes.so.3
ELF     0x7dd0f000-7dd17000     Deferred        libxrender.so.1
ELF     0x7dd26000-7dd41000     Deferred        imm32<elf>
  \-PE  0x7dd30000-7dd41000     \               imm32
ELF     0x7dd41000-7dd43000     Deferred        libnvidia-tls.so.1
ELF     0x7dd43000-7e5c9000     Deferred        libglcore.so.1
ELF     0x7e5c9000-7e655000     Deferred        libgl.so.1
ELF     0x7e655000-7e65a000     Deferred        libxdmcp.so.6
ELF     0x7e65a000-7e65d000     Deferred        libxau.so.6
ELF     0x7e65d000-7e74e000     Deferred        libx11.so.6
ELF     0x7e74e000-7e75c000     Deferred        libxext.so.6
ELF     0x7e75c000-7e761000     Deferred        libxxf86vm.so.1
ELF     0x7e761000-7e766000     Deferred        libxxf86dga.so.1
ELF     0x7e766000-7e77e000     Deferred        libice.so.6
ELF     0x7e77e000-7e787000     Deferred        libsm.so.6
ELF     0x7e78b000-7e794000     Deferred        libxcursor.so.1
ELF     0x7e796000-7e813000     Deferred        winex11<elf>
  \-PE  0x7e7b0000-7e813000     \               winex11
ELF     0x7e876000-7e896000     Deferred        libexpat.so.1
ELF     0x7e896000-7e8c1000     Deferred        libfontconfig.so.1
ELF     0x7e8c1000-7e8d5000     Deferred        libz.so.1
ELF     0x7e8d5000-7e940000     Deferred        libfreetype.so.6
ELF     0x7eb61000-7eba0000     Deferred        dinput<elf>
  \-PE  0x7eb70000-7eba0000     \               dinput
PE      0x7eba0000-7ec92000     Deferred        wondll
PE      0x7eca0000-7ecf2000     Deferred        binkw32
ELF     0x7ecf6000-7ed77000     Deferred        winmm<elf>
  \-PE  0x7ed00000-7ed77000     \               winmm
ELF     0x7ed77000-7ee26000     Deferred        comctl32<elf>
  \-PE  0x7ed80000-7ee26000     \               comctl32
ELF     0x7ee26000-7ef3f000     Deferred        user32<elf>
  \-PE  0x7ee40000-7ef3f000     \               user32
ELF     0x7ef3f000-7ef4b000     Deferred        libgcc_s.so.1
ELF     0x7f035000-7f935000     Deferred        gdi32<elf>
  \-PE  0x7f080000-7f935000     \               gdi32
ELF     0x7f935000-7f9f4000     Deferred        shell32<elf>
  \-PE  0x7f950000-7f9f4000     \               shell32
ELF     0x7f9f4000-7fa30000     Deferred        advapi32<elf>
  \-PE  0x7fa00000-7fa30000     \               advapi32
ELF     0x7fa30000-7fa4e000     Deferred        iphlpapi<elf>
  \-PE  0x7fa40000-7fa4e000     \               iphlpapi
ELF     0x7fa4e000-7fa77000     Deferred        ws2_32<elf>
  \-PE  0x7fa60000-7fa77000     \               ws2_32
ELF     0x7fa77000-7fa90000     Deferred        wsock32<elf>
  \-PE  0x7fa80000-7fa90000     \               wsock32
ELF     0x7fbf4000-7fcf0000     Deferred        kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fe06000-7fe11000     Deferred        libnss_files.so.2
ELF     0x7fe11000-7fe1b000     Deferred        libnss_nis.so.2
ELF     0x7fe1b000-7fe32000     Deferred        libnsl.so.1
ELF     0x7fe32000-7fe3b000     Deferred        libnss_compat.so.2
ELF     0x7fe4e000-7fe75000     Deferred        libm.so.6
ELF     0x7fe75000-7ff6c000     Deferred        libwine_unicode.so.1
ELF     0x7ff6c000-7ffe0000     Deferred        ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7daf000-b7db3000     Deferred        libdl.so.2
ELF     0xb7db3000-b7ef4000     Deferred        libc.so.6
ELF     0xb7ef5000-b7f0c000     Deferred        libpthread.so.0
ELF     0xb7f0c000-b7f26000     Deferred        libwine.so.1
ELF     0xb7f37000-b7f52000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000011 (D) C:\Program Files\Vampire The Masquerade - Redemption\Vampire.exe
        0000000e    0
        0000000d    0
        0000000f    0 <==
0000000a 
        0000000c    0
WineDbg terminated on pid 0x11

```


I tried to turn on the audio hardware emulation because it was the only thing I recognised, but from wine config, when I pressed the audio tab I got this:

```
Creating link /home/asiyla/.kde/socket-asiyla-laptop.
can't create mcop directory

```

---

### Post by cogadh on 2007-07-30
It sounds like you have Wine configured to use the aRts sound system. I don't know much about that, since Wine's support for it is quite out of date and AFAIK, no longer maintained. You would probably be better off switching to either OSS or the preferred ALSA driver. Of course, both of those requires you to have either the ALSA or OSS sound systems installed. I don't know enough about KDE to say how that might affect your system (die-hard Gnome user myself), if it would affect it at all.

---

### Post by nemo.r on 2007-07-30
YAY! it works. :D

I fiddled about with my audio settings, then from synaptic I installed oss-compat. Under winecfg I set the vampire.exe settings to OSS with emulation turned on, when it was set to ALSA the audio was choppy, now it is smooth.

A final note, the game screen is a quarter the size of my screen, the vampire page on the wine site has a screenshot that looks similar, so I'm guessing that's normal? It didn't change no matter what I set in winecfg and if I change it in game options the screen goes white.

Thank you so much for your help

---

### Post by cogadh on 2007-07-30
If you turn off the "Emulate virtual desktop" and "Allow the window manager to control the application" in winecfg, you should get the game at fullscreen and in any resolutions that your system supports (provided those resolutions are already part of your xorg.conf).

---

### Post by nemo.r on 2007-07-30
OK I spoke too soon... 

It plays all the intro movies fine, but the room at the beginning, seems to be in shadow, then it's like someone turns the lights on, is this supposed to happen, or should it be clearly lit the whole time? Then when the movies stop and you enter the 'playing' mode, the screen goes black.

The heads up display is fine, but the rest of the screen is all black, The cursor is a white square with what looks like little brown bricks in it. :-?

This is what it says in the terminal, (it is longer but I think it repeats itself)

```
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd53968)->(0x10022,00000013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_LINEPATTERN (0000000a) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_MONOENABLE (0000000b) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_ROP2 (0000000c) value : 0000000d !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_PLANEMASK (0000000d) value : ffffffff !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_LASTPIXEL (00000010) value : 00000001 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_ZVISIBLE (0000001e) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_EDGEANTIALIAS (00000028) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_RANGEFOGENABLE (00000030) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_EXTENTS (0000008a) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_VERTEXBLEND (00000097) value : 00000000 !
err:ddraw:set_render_state Unhandled dwRenderStateType D3DRENDERSTATE_EXTENTS (0000008a) value : 00000000 !
```

I disabled desktop double buffering in winecfg, but it would only work in 24 bit, with the same problems. in all the other settings I get this: 

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  1 (X_CreateWindow)
  Serial number of failed request:  23
  Current serial number in output stream:  30

```

---

### Post by nemo.r on 2007-08-05
Well, it fixed itself, am now using wine version 0.9.36 and all glitches have gone, not really sure why, but I'm not complaining!

---

### Post by karth on 2007-12-05
I had no luck with Wine 0.9.50, the intro movies (Activision logo and short movie "it's a world of darkness...") play fine, but the main menu is completely black.

Ubuntu 7.10
OSS Driver + emulation ON
Vertex and pixels shaders OFF
Win 98 compatibility mode
Wine desktop ON

Has anyone had any experience with V:tM-R vs. 0.9.50 ? Appdb says Gold with 0.9.44, so I was wondering...

---

### Post by cogadh on 2007-12-05
Sorry dude, I have the same issues as you. Of course I didn't get "gold" performance out of 0.9.44 either. The game ran, but shadows were all screwed up and textures were missing all over the place. As I said long ago, this game ran its best on 0.9.35 and .36, but it hasn't been the same since then.

---

### Post by karth on 2007-12-05
Oh, well, that's bad news... I remember reading that making 2 versions of wine to live on the same computer is rather tricky, or simply impossible.

Thanks, anyway

---

### Post by cogadh on 2007-12-05
It's not impossible, it just requires you to compile each version manually and install them in different locations, like /usr/bin/<wine version>/. Then when you run each app, you need to specifiy which Wine binary to use.

---

### Post by wingnux on 2008-01-16
That's pretty bad =/ Everything works fine here except for the game itself! When I click "New Game" it shows the loading screen and then it crashes...

EDIT: Oh great! Upgraded from .52 to .53 and now the main menu won't show up, I can only hear the music =/

---

### Post by hachel on 2008-11-17
hello,
I have some problems with the game.
It installed fine after I set wine to win98 and left everything else unchanged and it started and I was able to play. At one point in the game when you come back from the silver mines there is a cutscene after which it turns night. The movie showing the sunset appears (distored, as mentioned in the [wine appdb](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2383)) and after that the game just goes back to desktop.
There were video-cutscenes before and it didn't crash with them.
I changed some of the wine-graphic-configuration, enabling and disabling all the options, after which now I have the game running in a window and with working videos, the game still crashes.
This is the terminal-output from the beginning of the game (so the first couple of lines are not part of the crash):
```
 wine Vampire.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x32f264,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:ddraw:PixelFormat_WineD3DtoDD Can't translate this Pixelformat 62
err:ddraw:PixelFormat_WineD3DtoDD Can't translate this Pixelformat 63
err:ddraw:PixelFormat_WineD3DtoDD Can't translate this Pixelformat 64
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(640,480)
err:d3d:IWineD3DDeviceImpl_SetupFullscreenWindow (0x143280): Want to change the window parameters of HWND 0x1008e, but another style is stored for restoration afterwards
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
^[err:d3d:IWineD3DDeviceImpl_SetupFullscreenWindow (0x143280): Want to change the window parameters of HWND 0x1008e, but another style is stored for restoration afterwards
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:IWineD3DDeviceImpl_SetupFullscreenWindow (0x143280): Want to change the window parameters of HWND 0x1008e, but another style is stored for restoration afterwards
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:IWineD3DDeviceImpl_SetupFullscreenWindow (0x143280): Want to change the window parameters of HWND 0x1008e, but another style is stored for restoration afterwards
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
Warning: JIT compiler "symcjit" not found. Will use interpreter.
```
This is the crash:```

err:d3d:IWineD3DDeviceImpl_SetupFullscreenWindow (0x143280): Want to change the window parameters of HWND 0x1008e, but another style is stored for restoration afterwards
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:IWineD3DDeviceImpl_SetupFullscreenWindow (0x143280): Want to change the window parameters of HWND 0x1008e, but another style is stored for restoration afterwards
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d_surface:IWineD3DSurfaceImpl_LockRect >>>>>>>>>>>>>>>>> GL_OUT_OF_MEMORY (0x505) from glMapBufferARB @ surface.c / 1160
wine: Unhandled page fault on write access to 0x00000000 at address 0x140fd76 (thread 0023), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x0140fd76).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0140fd76 ESP:0032d588 EBP:03fa0028 EFLAGS:00010212(   - 00      - RIA1)
 EAX:00000100 EBX:00000080 ECX:00000040 EDX:00000100
 ESI:03fa0028 EDI:00000000
Stack dump:
0x0032d588:  00000030 016b9628 0032fc08 04520368
0x0032d598:  03fa0028 00000000 00000100 0000093e
0x0032d5a8:  00000080 00000080 00000027 03f529e8
0x0032d5b8:  00000080 016b9628 02d9f770 00000002
0x0032d5c8:  00401000 00000000 00000000 00000000
0x0032d5d8:  0000007c 0012100f 00000080 00000080
Backtrace:
=>1 0x0140fd76 in rldirect (+0xfd76) (0x03fa0028)
  2 0x00000000 (0x00000000)
0x0140fd76: repe movsl	(%esi),%es:(%edi)
Modules:
Module	Address			Debug info	Name (107 modules)
PE	  330000-  382000	Deferred        binkw32
PE	  400000-  733000	Deferred        vampire
PE	  740000-  832000	Deferred        wondll
PE	 1400000- 16c5000	Export          rldirect
PE	10000000-10062000	Deferred        javai
PE	21100000-2115c000	Deferred        mss32
PE	22100000-22111000	Deferred        mssa3d.m3d
PE	22200000-22212000	Deferred        mssa3d2.m3d
PE	22400000-22411000	Deferred        mssds3dh.m3d
PE	22500000-22511000	Deferred        msseax.m3d
PE	22600000-22612000	Deferred        mssfast.m3d
PE	22c00000-22c14000	Deferred        msseax2.m3d
PE	26f00000-26f26000	Deferred        mp3dec.asi
ELF	7aa8e000-7b800000	Deferred        libglcore.so.1
ELF	7b800000-7b93f000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93f000	\               kernel32
ELF	7bc00000-7bcab000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcab000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d173000-7d1bf000	Deferred        dsound<elf>
  \-PE	7d180000-7d1bf000	\               dsound
ELF	7d58e000-7d59d000	Deferred        libgcc_s.so.1
ELF	7d612000-7d6b5000	Deferred        libgl.so.1
ELF	7d6b5000-7d74a000	Deferred        opengl32<elf>
  \-PE	7d6d0000-7d74a000	\               opengl32
ELF	7df78000-7e09b000	Deferred        wined3d<elf>
  \-PE	7df90000-7e09b000	\               wined3d
ELF	7e09b000-7e0f5000	Deferred        ddraw<elf>
  \-PE	7e0a0000-7e0f5000	\               ddraw
ELF	7e0f5000-7e10a000	Deferred        midimap<elf>
  \-PE	7e100000-7e10a000	\               midimap
ELF	7e10a000-7e133000	Deferred        msacm32<elf>
  \-PE	7e110000-7e133000	\               msacm32
ELF	7e133000-7e14c000	Deferred        msacm32<elf>
  \-PE	7e140000-7e14c000	\               msacm32
ELF	7e14c000-7e19c000	Deferred        libpulse.so.0
ELF	7e1ab000-7e1b4000	Deferred        librt.so.1
ELF	7e1b4000-7e27c000	Deferred        libasound.so.2
ELF	7e282000-7e284000	Deferred        libnvidia-tls.so.1
ELF	7e284000-7e28b000	Deferred        libasound_module_pcm_pulse.so
ELF	7e28b000-7e2c2000	Deferred        winealsa<elf>
  \-PE	7e290000-7e2c2000	\               winealsa
ELF	7e30e000-7e341000	Deferred        uxtheme<elf>
  \-PE	7e310000-7e341000	\               uxtheme
ELF	7e341000-7e34a000	Deferred        libxcursor.so.1
ELF	7e34a000-7e34f000	Deferred        libxfixes.so.3
ELF	7e34f000-7e353000	Deferred        libxcomposite.so.1
ELF	7e353000-7e35a000	Deferred        libxrandr.so.2
ELF	7e35a000-7e364000	Deferred        libxrender.so.1
ELF	7e364000-7e36a000	Deferred        libxxf86vm.so.1
ELF	7e36a000-7e36d000	Deferred        libxinerama.so.1
ELF	7e36d000-7e38e000	Deferred        imm32<elf>
  \-PE	7e370000-7e38e000	\               imm32
ELF	7e38e000-7e393000	Deferred        libxdmcp.so.6
ELF	7e393000-7e3ac000	Deferred        libxcb.so.1
ELF	7e3ac000-7e3af000	Deferred        libxcb-xlib.so.0
ELF	7e3af000-7e49e000	Deferred        libx11.so.6
ELF	7e49e000-7e4ad000	Deferred        libxext.so.6
ELF	7e4ad000-7e4c5000	Deferred        libice.so.6
ELF	7e4c5000-7e4ce000	Deferred        libsm.so.6
ELF	7e4d7000-7e4db000	Deferred        libcap.so.1
ELF	7e4dd000-7e579000	Deferred        winex11<elf>
  \-PE	7e4f0000-7e579000	\               winex11
ELF	7e5c5000-7e5ec000	Deferred        libexpat.so.1
ELF	7e5ec000-7e619000	Deferred        libfontconfig.so.1
ELF	7e628000-7e63e000	Deferred        libz.so.1
ELF	7e63e000-7e6b4000	Deferred        libfreetype.so.6
ELF	7e6b4000-7e6ed000	Deferred        dinput<elf>
  \-PE	7e6c0000-7e6ed000	\               dinput
ELF	7e6ed000-7e75a000	Deferred        msvcrt<elf>
  \-PE	7e700000-7e75a000	\               msvcrt
ELF	7e75a000-7e7c1000	Deferred        rpcrt4<elf>
  \-PE	7e770000-7e7c1000	\               rpcrt4
ELF	7e7c1000-7e8d4000	Deferred        ole32<elf>
  \-PE	7e7e0000-7e8d4000	\               ole32
ELF	7e8d4000-7e968000	Deferred        winmm<elf>
  \-PE	7e8e0000-7e968000	\               winmm
ELF	7e968000-7ea2f000	Deferred        comctl32<elf>
  \-PE	7e970000-7ea2f000	\               comctl32
ELF	7ea2f000-7eacf000	Deferred        gdi32<elf>
  \-PE	7ea40000-7eacf000	\               gdi32
ELF	7eacf000-7ec1d000	Deferred        user32<elf>
  \-PE	7eaf0000-7ec1d000	\               user32
ELF	7ec1d000-7ec7a000	Deferred        shlwapi<elf>
  \-PE	7ec30000-7ec7a000	\               shlwapi
ELF	7ec7a000-7eda6000	Deferred        shell32<elf>
  \-PE	7ec90000-7eda6000	\               shell32
ELF	7eda6000-7edfb000	Deferred        advapi32<elf>
  \-PE	7edb0000-7edfb000	\               advapi32
ELF	7edfb000-7ee0f000	Deferred        libresolv.so.2
ELF	7ee10000-7ee13000	Deferred        libxau.so.6
ELF	7ee1e000-7ee3e000	Deferred        iphlpapi<elf>
  \-PE	7ee20000-7ee3e000	\               iphlpapi
ELF	7ee3e000-7ee6b000	Deferred        ws2_32<elf>
  \-PE	7ee50000-7ee6b000	\               ws2_32
ELF	7ee6b000-7ee86000	Deferred        wsock32<elf>
  \-PE	7ee70000-7ee86000	\               wsock32
ELF	7efa6000-7efb2000	Deferred        libnss_files.so.2
ELF	7efb2000-7efcb000	Deferred        libnsl.so.1
ELF	7efcb000-7eff1000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7cc0000-b7cc9000	Deferred        libnss_compat.so.2
ELF	b7cca000-b7cce000	Deferred        libdl.so.2
ELF	b7cce000-b7e2c000	Deferred        libc.so.6
ELF	b7e2d000-b7e46000	Deferred        libpthread.so.0
ELF	b7e55000-b7f8c000	Deferred        libwine.so.1
ELF	b7f8e000-b7fab000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000017    0
00000022 (D) C:\Program Files\Vampire The Masquerade - Redemption\Vampire.exe
	00000032    0
	0000002c   -2
	00000029   15
	00000028   15
	00000026   15
	00000024    0
	00000023    0 <==
Backtrace:
=>1 0x0140fd76 in rldirect (+0xfd76) (0x03fa0028)
  2 0x00000000 (0x00000000)
fixme:d3d:IWineD3DDeviceImpl_Release (0x143280) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x19b2a0 with type 6,WINED3DRTYPE_VERTEXBUFFER

```
My wine-version is 1.1.8
Wine is set to win98 (wouldn't run otherwise, yet install)
When I hit the audio-tab it prompts that there is no audio driver specified in the registry and some driver has been picked for me (ALSA is checked).
Under graphics i checked
```
Allow the window manager to decorate the windows
Allow the window manager to control the windows
Emulate a virtual deskopt (800x600)
Vertext shader = hardware
Allow Pixel shader.
```
As mentioned before, I switched everything off and I didn't change anything regarding the crash.

Any help?

---

### Post by karth on 2008-11-17
Sorry, I am crashing at this exact point (as the Archbishop sends me defending the streets at night).
I see the cutscene, and then the game crashes to the desktop.

---

### Post by hachel on 2008-11-26
hmm i tried around a bit with the wine-settings (window-mode etc), set everything to lowest details and resolution at the vampire settings and then it worked

---

