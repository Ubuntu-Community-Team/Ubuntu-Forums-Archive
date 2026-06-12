---
title: "Any progress with The Sims?"
date: 2008-01-26
forum: Wine
---

### Post by anjilslaire on 2008-01-26
Hey everyone,

Has there been any progress getting the original The Sims games (not Sims 2) to run under Wine? All of the results in the Wine App DB look pretty grim. Just checking to see if anyone knows of any progress.
The wife asked me to install the originals on her new Dell 1420 laptop, so I'm just checking in for any pointers while I experiment.

Thanks!

---

### Post by anjilslaire on 2008-01-27
Update:
I've gotten The Sims installed successfully, input my cd key, etc. Everything seems OK installer-wise.
However, When I run it, either at 800x600 or 1024x768, I get the followin output. Note however, when run at 800x600, the scren goes momentarily black, then has something garbled on the splash screen before dumpin back to the desktop.  Konsole output:
```

laire@sheeple:~/.wine/drive_c/Program Files/Maxis/The Sims$ wine Sims.exe
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
fixme:win:EnumDisplayDevicesW ((null),0,0x34ee14,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
fixme:d3d:IWineD3DDeviceImpl_CreateSurface Trying to create a render target that isn't in the default pool
err:ddraw:PixelFormat_DD2WineD3D Unknown Pixelformat!
err:ddraw:IDirectDrawImpl_CreateNewSurface Unsupported / Unknown pixelformat
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 88760091
wine: Unhandled page fault on read access to 0xffffffff at address 0xffffffff (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0xffffffff in 32-bit code (0xffffffff).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:ffffffff ESP:0034f9a4 EBP:0034fa38 EFLAGS:00010206(   - 00      - RIP1)
 EAX:0034facc EBX:0091d7a8 ECX:0034fc3c EDX:0034fa01
 ESI:00000000 EDI:0034fa20
Stack dump:
0x0034f9a4:  0054e52d 0034facc 0091d828 0091d86c
0x0034f9b4:  0091d7a8 0000007c 00001007 00000258
0x0034f9c4:  00000320 00000000 00000000 00000000
0x0034f9d4:  00000000 00000000 00000000 00000000
0x0034f9e4:  00000000 00000000 00000000 00000000
0x0034f9f4:  00000000 00000000 00000000 00000020
Backtrace:
=>1 0xffffffff (0x0034fa38)
  2 0x0054d944 in sims (+0x14d944) (0x0034fad8)
  3 0x004beac1 in sims (+0xbeac1) (0x0034fc48)
  4 0x004b3c12 in sims (+0xb3c12) (0x0034fdf8)
  5 0x00574c38 in sims (+0x174c38) (0x0034fe10)
  6 0x00537610 in sims (+0x137610) (0x005c186c)
  7 0x00574bd7 in sims (+0x174bd7) (0x00574b38)
0xffffffff: -- no code accessible --
Modules:
Module  Address                 Debug info      Name (86 modules)
PE        3b0000-  3d5000       Deferred        ijl10
PE        400000-  6b6000       Export          sims
PE      60000000-600e0000       Deferred        gimex
ELF     7b800000-7b925000       Deferred        kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d1d7000-7d2c7000       Deferred        wined3d<elf>
  \-PE  7d1f0000-7d2c7000       \               wined3d
ELF     7d2c7000-7d31b000       Deferred        ddraw<elf>
  \-PE  7d2d0000-7d31b000       \               ddraw
ELF     7d31b000-7d32f000       Deferred        midimap<elf>
  \-PE  7d320000-7d32f000       \               midimap
ELF     7d32f000-7d355000       Deferred        msacm32<elf>
  \-PE  7d340000-7d355000       \               msacm32
ELF     7d355000-7d390000       Deferred        wineoss<elf>
  \-PE  7d360000-7d390000       \               wineoss
ELF     7d428000-7d48d000       Deferred        msvcrt<elf>
  \-PE  7d440000-7d48d000       \               msvcrt
ELF     7d48d000-7d4b4000       Deferred        msvfw32<elf>
  \-PE  7d490000-7d4b4000       \               msvfw32
ELF     7d664000-7d67b000       Deferred        msacm32<elf>
  \-PE  7d670000-7d67b000       \               msacm32
ELF     7d694000-7d6c6000       Deferred        uxtheme<elf>
  \-PE  7d6a0000-7d6c6000       \               uxtheme
ELF     7d6c6000-7d6cf000       Deferred        libxcursor.so.1
ELF     7d6cf000-7d6d4000       Deferred        libxfixes.so.3
ELF     7d6d4000-7d6d7000       Deferred        libxcomposite.so.1
ELF     7d6d7000-7d6df000       Deferred        libxrender.so.1
ELF     7da92000-7da94000       Deferred        libnvidia-tls.so.1
ELF     7da94000-7e42c000       Deferred        libglcore.so.1
ELF     7e42c000-7e4c2000       Deferred        libgl.so.1
ELF     7e4c2000-7e4c7000       Deferred        libxdmcp.so.6
ELF     7e4c7000-7e4ca000       Deferred        libxau.so.6
ELF     7e4ca000-7e5bb000       Deferred        libx11.so.6
ELF     7e5bb000-7e5c9000       Deferred        libxext.so.6
ELF     7e5c9000-7e5ce000       Deferred        libxxf86vm.so.1
ELF     7e5ce000-7e5e6000       Deferred        libice.so.6
ELF     7e5e6000-7e5ee000       Deferred        libsm.so.6
ELF     7e5f0000-7e5f6000       Deferred        libxrandr.so.2
ELF     7e606000-7e695000       Deferred        winex11<elf>
  \-PE  7e610000-7e695000       \               winex11
ELF     7e702000-7e722000       Deferred        libexpat.so.1
ELF     7e722000-7e74d000       Deferred        libfontconfig.so.1
ELF     7e74d000-7e762000       Deferred        libz.so.1
ELF     7e762000-7e7d2000       Deferred        libfreetype.so.6
ELF     7e7ea000-7e834000       Deferred        dsound<elf>
  \-PE  7e7f0000-7e834000       \               dsound
ELF     7e834000-7e851000       Deferred        imm32<elf>
  \-PE  7e840000-7e851000       \               imm32
ELF     7e851000-7e86a000       Deferred        version<elf>
  \-PE  7e860000-7e86a000       \               version
ELF     7e86a000-7e87d000       Deferred        libresolv.so.2
ELF     7e881000-7e895000       Deferred        lz32<elf>
  \-PE  7e890000-7e895000       \               lz32
ELF     7e895000-7e8b3000       Deferred        iphlpapi<elf>
  \-PE  7e8a0000-7e8b3000       \               iphlpapi
ELF     7e8b3000-7e911000       Deferred        rpcrt4<elf>
  \-PE  7e8c0000-7e911000       \               rpcrt4
ELF     7e911000-7e9b0000       Deferred        ole32<elf>
  \-PE  7e920000-7e9b0000       \               ole32
ELF     7e9b0000-7ea3c000       Deferred        winmm<elf>
  \-PE  7e9c0000-7ea3c000       \               winmm
ELF     7ea3c000-7eafb000       Deferred        comctl32<elf>
  \-PE  7ea40000-7eafb000       \               comctl32
ELF     7eafb000-7eb52000       Deferred        shlwapi<elf>
  \-PE  7eb10000-7eb52000       \               shlwapi
ELF     7eb52000-7ec56000       Deferred        shell32<elf>
  \-PE  7eb60000-7ec56000       \               shell32
ELF     7ec56000-7eca0000       Deferred        advapi32<elf>
  \-PE  7ec60000-7eca0000       \               advapi32
ELF     7eca0000-7ed37000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed37000       \               gdi32
ELF     7ed37000-7ee6e000       Deferred        user32<elf>
  \-PE  7ed50000-7ee6e000       \               user32
ELF     7ef8d000-7ef98000       Deferred        libnss_files.so.2
ELF     7ef98000-7efa2000       Deferred        libnss_nis.so.2
ELF     7efa2000-7efba000       Deferred        libnsl.so.1
ELF     7efba000-7efc3000       Deferred        libnss_compat.so.2
ELF     7efc3000-7efe8000       Deferred        libm.so.6
ELF     b7cb4000-b7cb8000       Deferred        libdl.so.2
ELF     b7cb8000-b7e02000       Deferred        libc.so.6
ELF     b7e02000-b7e1a000       Deferred        libpthread.so.0
ELF     b7e32000-b7f46000       Deferred        libwine.so.1
ELF     b7f48000-b7f64000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Maxis\The Sims\Sims.exe
        00000009    0 <==
0000000a
        0000000b    0
00000010
        00000012    0
        00000011    0
Backtrace:
=>1 0xffffffff (0x0034fa38)
  2 0x0054d944 in sims (+0x14d944) (0x0034fad8)
  3 0x004beac1 in sims (+0xbeac1) (0x0034fc48)
  4 0x004b3c12 in sims (+0xb3c12) (0x0034fdf8)
  5 0x00574c38 in sims (+0x174c38) (0x0034fe10)
  6 0x00537610 in sims (+0x137610) (0x005c186c)
  7 0x00574bd7 in sims (+0x174bd7) (0x00574b38)
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
laire@sheeple:~/.wine/drive_c/Program Files/Maxis/The Sims$               

```
Any thoughts? Running Kubuntu Gutsy, Wine 0.9.54, Nvidia 6600GT with Nvidia drivers, etc

---

### Post by Vadi on 2008-01-27
I think you're better off with the wine wizards now.

---

### Post by anjilslaire on 2008-01-27
> **Vadi said:**
> I think you're better off with the wine wizards now.

If you mean being posted here in the Wine forum, you may be right. It looks like Artificial Intelligence moved my thread here after posting in the games forum.

---

### Post by Vadi on 2008-01-27
No, I meant on the official winehq.org website :/

---

### Post by Faud on 2008-01-27
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1015](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1015)

BUT, I have heard of people actually getting it to work, they did some heavy tweaking though. I would google it. You arent going to get a straight install that I know of.

---

### Post by anjilslaire on 2008-01-28
> **Faud said:**
> [http://appdb.winehq.org/objectManager.php?sClass=version&iId=1015](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1015)

BUT, I have heard of people actually getting it to work, they did some heavy tweaking though. I would google it. You arent going to get a straight install that I know of.
Yes, I've been reading through the wine db, that's how I got as far as I have so far.

---

### Post by piousp on 2008-06-22
I'm stuck there too, but using Kubuntu Hardy with Wine 1.0

:(

---

### Post by h4mx0r on 2008-12-15
Wow I thought the sims 1 was working already greatly with wine. I also thought sims 2 was close to being playable too by now. Strange I must have viewed some other wine review of it elsewhere. Have you checked with the playonlinux people or the winehq irc? Perhaps some wine blogs?

---

### Post by h4mx0r on 2008-12-15
I did some poking and found this exerpt in the sims wiki:

"The Sims and all its expansion packs were ported to the Mac by Aspyr Media, Inc..
The Sims was ported to Linux using Transgaming's WineX technology (now known as Cedega) and was bundled with Mandrake Linux Gaming Edition. However, both WineX and the Cedega engine are unable to run the Windows version of the game. The original port will no longer run on modern Linux distributions and is unable to accept the various add-on packs intended for the Windows version."

Mandrake distro was later named Mandriva and I found this post on their forum [http://mandrivausers.org/index.php?showtopic=35720](http://mandrivausers.org/index.php?showtopic=35720)

So I guess you need to rip out the anti debugger codes to get it to run/run better. Anyway best of luck bet they the same people whom wrote the Spore game's drm.

---

