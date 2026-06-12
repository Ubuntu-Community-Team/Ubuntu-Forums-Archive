---
title: "Ubuntu (+ wine) + Oblivion = !#@?!"
date: 2007-09-10
forum: Wine
---

### Post by fi1th on 2007-09-10
Hi all.

I'm a relatively new Ubuntu Feisty Fawn user, I have just created my own average PC. I have a 3.0GHz P4 processor, 1GB RAM, 80GB Parallel ATA, and (my pride) a 512MB x1650 PRO ATI Radeon card. I have the graphic drivers for ATI on linux, the 8.40 I believe.

However, this is not my problem. I am having issues with the recently released Elder Scrolls IV: Oblivion. I have all the files for the game, that is to say that I have not installed the game from the disc but have copied the files over my network. 

Running "~/Oblivionlauncher.exe" works sweet, it comes up with the passive music etc. Yet when I attempt to run "~/Oblivion.exe" in wine through the terminal it brings up the launcher quickly (little 200px squared) and then vanishes, changing my screens resolution from 1024x768 to 640x480. The terminal also leaves me with a rather long list that I find hard to decipher, I am wondering if anyone can help me with this. This is what I am left with (as well as a munted looking screen res.):

filth@filth-desktop:~$ wine '/home/filth/Oblivion origonal/Oblivion.exe'
err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetCurrentReadDCARB) - not found
fixme:win:EnumDisplayDevicesW ((null),0,0x33f034,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
err:d3d:getColorBits Unsupported format: WINED3DFMT_A4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_A4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_A4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_X4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_X4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_X4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_X4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_X4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_X4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_A4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_A4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_X4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_X4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_X4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_X4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_X4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_X4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_A4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_A4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_X4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_X4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_X4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_X4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_X4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_X4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_A4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_A4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_X4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_X4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_X4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_X4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_X4R4G4B4
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_X4R4G4B4
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x149f30) : stub, simulating 64MB for now, returning 64MB left
wine: Unhandled page fault on read access to 0x00000004 at address 0x58dcfc (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x0058dcfc).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0058dcfc ESP:0033e64c EBP:00000000 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:52d41e7a EDX:ffffffff
 ESI:00000000 EDI:00a69470
Stack dump:
0x0033e64c:  00000000 00000000 52e7f822 1f001c7c
0x0033e65c:  1b000f28 00000000 00000000 0033e998
0x0033e66c:  7bc4ca36 0033ea14 7bc9f4c0 15000a14
0x0033e67c:  00a69470 00000000 00000000 00000000
0x0033e68c:  00000000 00000000 00000000 00000000
0x0033e69c:  00000000 00000000 00000208 0033ea14
Backtrace:
=>1 0x0058dcfc in oblivion (+0x18dcfc) (0x00000000)
0x0058dcfc: movl        0x4(%ebp),%ecx
Modules:
Module  Address                 Debug info      Name (92 modules)
PE        400000-  baf000       Export          oblivion
PE        bb0000-  dff000       Deferred        d3dx9_27
PE      18000000-18068000       Deferred        binkw32
ELF     6ae4b000-6af20000       Deferred        wined3d<elf>
  \-PE  6ae60000-6af20000       \               wined3d
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bcc2000-7bcf1000       Deferred        d3d9<elf>
  \-PE  7bcd0000-7bcf1000       \               d3d9
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf7f000-7bf94000       Deferred        midimap<elf>
  \-PE  7bf90000-7bf94000       \               midimap
ELF     7bf94000-7bfce000       Deferred        wineoss<elf>
  \-PE  7bfa0000-7bfce000       \               wineoss
ELF     7bfce000-7c000000       Deferred        uxtheme<elf>
  \-PE  7bfe0000-7c000000       \               uxtheme
ELF     7c2c9000-7c2ef000       Deferred        msacm32<elf>
  \-PE  7c2d0000-7c2ef000       \               msacm32
ELF     7c35d000-7c375000       Deferred        msacm32<elf>
  \-PE  7c360000-7c375000       \               msacm32
ELF     7c375000-7c37a000       Deferred        libxfixes.so.3
ELF     7c37a000-7c383000       Deferred        libxcursor.so.1
ELF     7c383000-7c3a0000       Deferred        imm32<elf>
  \-PE  7c390000-7c3a0000       \               imm32
ELF     7c3a0000-7c3a8000       Deferred        libxrender.so.1
ELF     7cfce000-7cfd4000       Deferred        libxrandr.so.2
ELF     7d82f000-7d838000       Deferred        librt.so.1
ELF     7d8f2000-7e25f000       Deferred        fglrx_dri.so
ELF     7e25f000-7e2ff000       Deferred        libgl.so.1
ELF     7e2ff000-7e304000       Deferred        libxdmcp.so.6
ELF     7e304000-7e307000       Deferred        libxau.so.6
ELF     7e307000-7e3f8000       Deferred        libx11.so.6
ELF     7e3f8000-7e406000       Deferred        libxext.so.6
ELF     7e406000-7e40b000       Deferred        libxxf86vm.so.1
ELF     7e40b000-7e423000       Deferred        libice.so.6
ELF     7e423000-7e42c000       Deferred        libsm.so.6
ELF     7e437000-7e4c1000       Deferred        winex11<elf>
  \-PE  7e450000-7e4c1000       \               winex11
ELF     7e53a000-7e55a000       Deferred        libexpat.so.1
ELF     7e55a000-7e585000       Deferred        libfontconfig.so.1
ELF     7e585000-7e599000       Deferred        libz.so.1
ELF     7e599000-7e604000       Deferred        libfreetype.so.6
ELF     7e604000-7e66b000       Deferred        msvcrt<elf>
  \-PE  7e620000-7e66b000       \               msvcrt
ELF     7e66b000-7e698000       Deferred        ws2_32<elf>
  \-PE  7e670000-7e698000       \               ws2_32
ELF     7e698000-7e6b2000       Deferred        wsock32<elf>
  \-PE  7e6a0000-7e6b2000       \               wsock32
ELF     7e6b2000-7e6c6000       Deferred        lz32<elf>
  \-PE  7e6c0000-7e6c6000       \               lz32
ELF     7e6c6000-7e6e0000       Deferred        version<elf>
  \-PE  7e6d0000-7e6e0000       \               version
ELF     7e6e0000-7e739000       Deferred        shlwapi<elf>
  \-PE  7e6f0000-7e739000       \               shlwapi
ELF     7e739000-7e83c000       Deferred        shell32<elf>
  \-PE  7e750000-7e83c000       \               shell32
ELF     7e83c000-7e885000       Deferred        dsound<elf>
  \-PE  7e840000-7e885000       \               dsound
ELF     7e885000-7e913000       Deferred        winmm<elf>
  \-PE  7e890000-7e913000       \               winmm
ELF     7e913000-7e926000       Deferred        libresolv.so.2
ELF     7e926000-7e944000       Deferred        iphlpapi<elf>
  \-PE  7e930000-7e944000       \               iphlpapi
ELF     7e944000-7e99d000       Deferred        rpcrt4<elf>
  \-PE  7e950000-7e99d000       \               rpcrt4
ELF     7e99d000-7ea3c000       Deferred        ole32<elf>
  \-PE  7e9b0000-7ea3c000       \               ole32
ELF     7ea3c000-7ea72000       Deferred        dinput<elf>
  \-PE  7ea50000-7ea72000       \               dinput
ELF     7ea72000-7ea8b000       Deferred        dinput8<elf>
  \-PE  7ea80000-7ea8b000       \               dinput8
ELF     7ea8b000-7ead3000       Deferred        advapi32<elf>
  \-PE  7eaa0000-7ead3000       \               advapi32
ELF     7ead3000-7eadf000       Deferred        libgcc_s.so.1
ELF     7ebd4000-7ec94000       Deferred        gdi32<elf>
  \-PE  7ebf0000-7ec94000       \               gdi32
ELF     7ec94000-7edd2000       Deferred        user32<elf>
  \-PE  7ecb0000-7edd2000       \               user32
ELF     7edd2000-7ee90000       Deferred        comctl32<elf>
  \-PE  7ede0000-7ee90000       \               comctl32
ELF     7efa2000-7efad000       Deferred        libnss_files.so.2
ELF     7efad000-7efb7000       Deferred        libnss_nis.so.2
ELF     7efb7000-7efce000       Deferred        libnsl.so.1
ELF     7efce000-7eff5000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7cb5000-b7cb9000       Deferred        libdl.so.2
ELF     b7cb9000-b7dfa000       Deferred        libc.so.6
ELF     b7dfb000-b7e12000       Deferred        libpthread.so.0
ELF     b7e1d000-b7f31000       Deferred        libwine.so.1
ELF     b7f33000-b7f4e000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) Z:\home\filth\Oblivion origonal\Oblivion.exe
        00000010   15
        0000000f   15
        0000000d    0
        00000009    0 <==
filth@filth-desktop:~$ 


Please help if you can and thank you for you time :-)

---

### Post by cisforcojo on 2007-09-10
I've never done it but I know it's possible. This guy Mongoose is really knowledgeable about this. Check out the Oblivion and Wine thread here:
[http://ubuntuforums.org/showthread.php?t=349764&highlight=oblivion](http://ubuntuforums.org/showthread.php?t=349764&highlight=oblivion)

---

### Post by ronin69hof on 2007-09-10
works 100%

[http://www.uesp.net/wiki/Oblivion:Linux](http://www.uesp.net/wiki/Oblivion:Linux)

cheers

---

