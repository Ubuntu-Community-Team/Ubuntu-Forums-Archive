---
title: "Can't Run Modern Warfare 3 on Wine"
date: 2012-02-22
forum: Wine
---

### Post by CyberMushroom on 2012-02-22
I have wine-1.3.15 installed in my Ubuntu 11.04 and I tried installing Modern Warfare 3. It installed successfully but when I try to play it it comes up with a program error box that says:

```
The program iw5sp.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience
```when I click the button that says close, the error disappears but the taskbar button for Modern Warfare 3 is still there and when I check the terminal from where i executed the command I can see that the program is still running. I have to press the CTRL+C to terminate the process.

here is the Terminal output when I try to run the game:

```

$ wine iw5sp.exe 
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x171168,0x1710b0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x171168,0x1710b0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1492c8,0x149250): stub
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.
wine: Unhandled page fault on read access to 0x0000003c at address 0x43bc94 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x0000003c in 32-bit code (0x0043bc94).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0043bc94 ESP:0032fc6c EBP:0032fcf4 EFLAGS:00210297(  R- --  I S -A-P-C)
 EAX:00000000 EBX:00000001 ECX:00110064 EDX:00000000
 ESI:0032fc98 EDI:fffffffe
Stack dump:
0x0032fc6c:  0065e694 00000000 fffffffe 0032fcf4
0x0032fc7c:  00000100 00000001 00000001 0032fcf4
0x0032fc8c:  0065e9b5 0065e9e9 00000001 024c40e0
0x0032fc9c:  00000000 00000000 00000008 020e9460
0x0032fcac:  020e9420 fffffffe 0032fcf4 00411961
0x0032fcbc:  024c40d8 00000000 00659c6f 0065eb1e
Backtrace:
=>0 0x0043bc94 in iw5sp (+0x3bc94) (0x0032fcf4)
  1 0x00470f12 in iw5sp (+0x70f11) (0x0032fe90)
  2 0x7b85856c call_process_entry+0xb() in kernel32 (0x0032fea8)
  3 0x7b85920f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  4 0x7bc72f18 call_thread_func+0xb() in ntdll (0x0032fef8)
  5 0x7bc759c0 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  6 0x7bc4a9da call_dll_entry_point+0x629() in ntdll (0x0032ffe8)
0x0043bc94: cmpl    $0,0x3c(%eax)
Modules:
Module    Address            Debug info    Name (116 modules)
PE      330000-  336000    Deferred        steam_api
PE      400000- 2759000    Export          iw5sp
PE    168a0000-168bd000    Deferred        mileseq.flt
PE    169d0000-169e1000    Deferred        msseax.flt
PE    18000000-18033000    Deferred        binkw32
PE    21100000-21197000    Deferred        mss32
PE    22300000-22306000    Deferred        mssds3d.flt
PE    24100000-24112000    Deferred        mssdsp.flt
PE    26400000-2642a000    Deferred        mssvoice.asi
PE    26f00000-26f20000    Deferred        mssmp3.asi
ELF    7b800000-7b990000    Dwarf           kernel32<elf>
  \-PE    7b810000-7b990000    \               kernel32
ELF    7bc00000-7bcbb000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcbb000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7df6f000-7dfa3000    Deferred        uxtheme<elf>
  \-PE    7df80000-7dfa3000    \               uxtheme
ELF    7dfb9000-7dfbf000    Deferred        libxfixes.so.3
ELF    7dfbf000-7dfc9000    Deferred        libxcursor.so.1
ELF    7dfc9000-7dfd1000    Deferred        libxrandr.so.2
ELF    7dfd1000-7dfdb000    Deferred        libxrender.so.1
ELF    7dfdb000-7dfe1000    Deferred        libxxf86vm.so.1
ELF    7dfe1000-7e007000    Deferred        libm.so.6
ELF    7e007000-7e028000    Deferred        imm32<elf>
  \-PE    7e010000-7e028000    \               imm32
ELF    7e0c3000-7e0c7000    Deferred        libxcomposite.so.1
ELF    7e0c7000-7e0cb000    Deferred        libxinerama.so.1
ELF    7e0cb000-7e0d1000    Deferred        libxdmcp.so.6
ELF    7e0d1000-7e0d5000    Deferred        libxau.so.6
ELF    7e0d5000-7e0ee000    Deferred        libxcb.so.1
ELF    7e0ee000-7e0f3000    Deferred        libuuid.so.1
ELF    7e0f3000-7e20e000    Deferred        libx11.so.6
ELF    7e20e000-7e21d000    Deferred        libxext.so.6
ELF    7e21d000-7e235000    Deferred        libice.so.6
ELF    7e235000-7e23d000    Deferred        libsm.so.6
ELF    7e25e000-7e307000    Deferred        winex11<elf>
  \-PE    7e270000-7e307000    \               winex11
ELF    7e341000-7e36b000    Deferred        libexpat.so.1
ELF    7e36b000-7e39a000    Deferred        libfontconfig.so.1
ELF    7e39a000-7e3af000    Deferred        libz.so.1
ELF    7e3af000-7e435000    Deferred        libfreetype.so.6
ELF    7e435000-7e46c000    Deferred        libncurses.so.5
ELF    7e48d000-7e500000    Deferred        rpcrt4<elf>
  \-PE    7e4a0000-7e500000    \               rpcrt4
ELF    7e500000-7e604000    Deferred        ole32<elf>
  \-PE    7e520000-7e604000    \               ole32
ELF    7e604000-7e6f8000    Deferred        comctl32<elf>
  \-PE    7e610000-7e6f8000    \               comctl32
ELF    7e6f8000-7e75c000    Deferred        shlwapi<elf>
  \-PE    7e710000-7e75c000    \               shlwapi
ELF    7e75c000-7e959000    Deferred        shell32<elf>
  \-PE    7e770000-7e959000    \               shell32
ELF    7e959000-7e989000    Deferred        ws2_32<elf>
  \-PE    7e960000-7e989000    \               ws2_32
ELF    7e989000-7e99f000    Deferred        powrprof<elf>
  \-PE    7e990000-7e99f000    \               powrprof
ELF    7e99f000-7ead0000    Deferred        wined3d<elf>
  \-PE    7e9b0000-7ead0000    \               wined3d
ELF    7ead0000-7eb04000    Deferred        d3d9<elf>
  \-PE    7eae0000-7eb04000    \               d3d9
ELF    7eb04000-7eb60000    Deferred        advapi32<elf>
  \-PE    7eb10000-7eb60000    \               advapi32
ELF    7eb60000-7ebee000    Deferred        gdi32<elf>
  \-PE    7eb70000-7ebee000    \               gdi32
ELF    7ebee000-7ed23000    Deferred        user32<elf>
  \-PE    7ec00000-7ed23000    \               user32
ELF    7ed23000-7edbc000    Deferred        winmm<elf>
  \-PE    7ed30000-7edbc000    \               winmm
ELF    7efbc000-7efc8000    Deferred        libnss_files.so.2
ELF    7efc8000-7efdf000    Deferred        libnsl.so.1
ELF    7efe7000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f69db000-f69f1000    Deferred        midimap<elf>
  \-PE    f69e0000-f69f1000    \               midimap
ELF    f69f1000-f6a1a000    Deferred        msacm32<elf>
  \-PE    f6a00000-f6a1a000    \               msacm32
ELF    f6a1a000-f6a21000    Deferred        libogg.so.0
ELF    f6a21000-f6a48000    Deferred        libvorbis.so.0
ELF    f6a48000-f6bc0000    Deferred        libvorbisenc.so.2
ELF    f6bc0000-f6c0c000    Deferred        libflac.so.8
ELF    f6c0c000-f6c72000    Deferred        libsndfile.so.1
ELF    f6c72000-f6c7b000    Deferred        libwrap.so.0
ELF    f6c7b000-f6cb8000    Deferred        libdbus-1.so.3
ELF    f6cb8000-f6d01000    Deferred        libpulsecommon-0.9.22.so
ELF    f6d01000-f6d42000    Deferred        libpulse.so.0
ELF    f6d42000-f6e0e000    Deferred        libasound.so.2
ELF    f6e10000-f6e29000    Deferred        msacm32<elf>
  \-PE    f6e20000-f6e29000    \               msacm32
ELF    f6e29000-f6e2f000    Deferred        libasound_module_pcm_pulse.so
ELF    f6e2f000-f6e65000    Deferred        winealsa<elf>
  \-PE    f6e40000-f6e65000    \               winealsa
ELF    f6e65000-f6ead000    Deferred        dsound<elf>
  \-PE    f6e70000-f6ead000    \               dsound
ELF    f6ead000-f6f9d000    Deferred        libglsl.so
ELF    f6f9d000-f7190000    Deferred        libdricore.so
ELF    f7190000-f7199000    Deferred        librt.so.1
ELF    f7199000-f71b5000    Deferred        libgcc_s.so.1
ELF    f72a0000-f72f6000    Deferred        libgl.so.1
ELF    f72fa000-f72ff000    Deferred        libxcb-atom.so.1
ELF    f72ff000-f7305000    Deferred        libxtst.so.6
ELF    f7305000-f7308000    Deferred        libx11-xcb.so.1
ELF    f730b000-f7317000    Deferred        swrast_dri.so
ELF    f7317000-f73c2000    Deferred        crypt32<elf>
  \-PE    f7320000-f73c2000    \               crypt32
ELF    f73c2000-f7400000    Deferred        rsaenh<elf>
  \-PE    f73d0000-f7400000    \               rsaenh
ELF    f7401000-f740c000    Deferred        libnss_nis.so.2
ELF    f740e000-f7412000    Deferred        libdl.so.2
ELF    f7412000-f756f000    Deferred        libc.so.6
ELF    f756f000-f7588000    Deferred        libpthread.so.0
ELF    f7591000-f759b000    Deferred        libdrm.so.2
ELF    f759b000-f759f000    Deferred        libxdamage.so.1
ELF    f75a1000-f75a9000    Deferred        libnss_compat.so.2
ELF    f75a9000-f76ea000    Dwarf           libwine.so.1
ELF    f76ec000-f770a000    Deferred        ld-linux.so.2
ELF    f770a000-f770b000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Activision\Call of Duty- Modern Warfare 3\iw5sp.exe
    00000028    0
    00000027    2
    00000026   15
    00000025   15
    00000021   -1
    00000020    0
    0000001f    0
    00000009    0 <==
0000000e services.exe
    0000001b    0
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000017    0
    00000016    0
    00000013    0
    00000012    0
00000018 plugplay.exe
    0000001c    0
    0000001a    0
    00000019    0
0000001d explorer.exe
    0000001e    0
Backtrace:
=>0 0x0043bc94 in iw5sp (+0x3bc94) (0x0032fcf4)
  1 0x00470f12 in iw5sp (+0x70f11) (0x0032fe90)
  2 0x7b85856c call_process_entry+0xb() in kernel32 (0x0032fea8)
  3 0x7b85920f ExitProcess+0xc9e() in kernel32 (0x0032fee8)
  4 0x7bc72f18 call_thread_func+0xb() in ntdll (0x0032fef8)
  5 0x7bc759c0 call_thread_entry_point+0x6f() in ntdll (0x0032ffc8)
  6 0x7bc4a9da call_dll_entry_point+0x629() in ntdll (0x0032ffe8)

```Here are my specifications:
```

Processor: AMD Athlon II X2 250 3.0GHz
Memory: 2x2GB (4GB) 1333 DDR3
Graphics Card: NVIDIA GeForce 9500GT 1GB 128Bit
 '-> NVIDIA Driver Version: 295.20

```Any suggestions on how to fix this issue? If you have encountered this issue before and have fixed this please share your resolution with me in this thread.

---

### Post by aura7 on 2012-02-22
Try CrossOver Games
 
[http://www.codeweavers.com/products/cxgames/](http://www.codeweavers.com/products/cxgames/)
 
It supports call of duty MW3 you can click Install a Game and Write Call of Duty Modern Warfare 3 and check.
 
The problem is ... it is paid ...... still you can try this free for 30 days.

---

### Post by CyberMushroom on 2012-02-22
thank you for that but I'm looking for a fix using wine like possible configurations and the likes. any other suggestions to fix this issue using wine? please share your thoughts on this and fixes that you might know of. thanks

---

### Post by HolgerB on 2012-02-23
Hint: Wines AppDB always give a good idea wether a game work under WINE by any means and shows possible work arounds:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=24738](http://appdb.winehq.org/objectManager.php?sClass=version&iId=24738)

From the rating at the site I would say win 1.3.32 and 1.3.33 provide the best base for running MW3.

---

### Post by Dlambert on 2012-02-24
PlayOnLinux is a great (Free) frontend to WINE as well.

---

### Post by CyberMushroom on 2012-02-27
thank you for your suggestions. but does anybody know any specific configurations in wine alone? like which winetricks dll should i add, what override must i use and what not?

---

