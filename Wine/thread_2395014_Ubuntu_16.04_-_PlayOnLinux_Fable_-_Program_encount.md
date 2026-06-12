---
title: "Ubuntu 16.04 - PlayOnLinux Fable - Program encountered serious problem"
date: 2018-06-25
forum: Wine
---

### Post by sakura1604u on 2018-06-25
Hi all,

I'm new to ubuntu, only been using it a few weeks but I think I am picking it up rather quickly. Until now I have managed to resolve many issues by browsing the web but this problem has me stuck and seems too specific to find an answer pre-exsisting posts.

This is the first game I have tried installing on ubuntu, so here we go....

Laptop:
Toshiba Satellite L300D-11V
Ubuntu 16.04
Wine - I have tried to run Fable using 1.4 and 1.8 (as advised in a install guide I will link bellow). With these two, I run fable from PlayOnLinux, nothing happens for a while and then it crashes.
The PlayOnLinux Debugger gives me:
```
Running wine-1.4 Fable.exe (Working directory : /home/sakura/.PlayOnLinux/wineprefix/Fable/drive_c/Program Files/Microsoft Games/Fable - The Lost Chapters)
err:winedevice:ServiceMain driver L"WineBus" failed to load
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
err:systray:initialize_systray Could not create tray window
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
err:ole:CoCreateInstance apartment not initialised
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
fixme:storage:create_storagefile Storage share mode not implemented.
err:process:__wine_kernel_init boot event wait timed out
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
fixme:atl:AtlAxWinInit semi-stub
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg0: Permission denied
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 1.
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 2.
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d004 (device=4 access=3 func=401 method=0)
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000001 not handled
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
err:d3d_caps:WineD3D_CreateFakeGLContext Failed to create a window.
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:ddraw:ddraw_attach_d3d_device Failed to create window, last error 0.
err:ddraw:ddraw_create_swapchain Failed to create swapchain, hr 0x80004005.
err:ddraw:ddraw7_SetCooperativeLevel Failed to create swapchain, hr 0x80004005.
err:ddraw:ddraw_attach_d3d_device Failed to create window, last error 0.
err:ddraw:ddraw_create_swapchain Failed to create swapchain, hr 0x80004005.
err:ddraw:ddraw7_SetCooperativeLevel Failed to create swapchain, hr 0x80004005.
wine: Unhandled page fault on read access to 0x000019c0 at address 0x19c0 (thread 0009), starting debugger...
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libSM.so.6: cannot open shared object file: No such file or directory
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
Unhandled exception: page fault on read access to 0x000019c0 in 32-bit code (0x000019c0).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:000019c0 ESP:0030c600 EBP:7d68fea8 EFLAGS:00210202(  R- --  I   - - - )
 EAX:ffb05204 EBX:00000000 ECX:ffb05204 EDX:7d68fee8
 ESI:00000002 EDI:ffb05204
Stack dump:
0x0030c600:  f7fbe465 00000002 ffb05204 ffb05210
0x0030c610:  f7fbf970 7de094b4 00000000 f7fd3000
0x0030c620:  00000001 00000009 0030c40e f7fbe3cb
0x0030c630:  00000006 00000014 7e0161a0 ffb05204
0x0030c640:  f7fbe58e ffb05210 00000000 00000000
0x0030c650:  00000000 00000000 00000002 00000000
Backtrace:
=>0 0x000019c0 (0x7d68fea8)
0x000019c0: -- no code accessible --
Modules:
Module    Address            Debug info    Name (78 modules)
PE      340000-  3bb000    Deferred        msvcp71
PE      400000- 1bb1000    Deferred        fable
PE     1bc0000- 1e13000    Deferred        d3dx9_25
PE     2a10000- 2a30000    Deferred        configdetect
PE    10000000-10029000    Deferred        strings
ELF    7b800000-7b8f6000    Deferred        kernel32<elf>
  \-PE    7b810000-7b8f6000    \               kernel32
ELF    7bc00000-7bcc1000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcc1000    \               ntdll
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
PE    7c340000-7c396000    Deferred        msvcr71
ELF    7d688000-7d691000    Deferred        librt.so.1
ELF    7dba8000-7dcbe000    Deferred        libasound.so.2
ELF    7dcbe000-7dd00000    Deferred        dsound<elf>
  \-PE    7dcc0000-7dd00000    \               dsound
ELF    7de09000-7de34000    Deferred        winealsa<elf>
ELF    7de34000-7de8b000    Deferred        riched20<elf>
  \-PE    7de40000-7de8b000    \               riched20
ELF    7dea3000-7dec4000    Deferred        mmdevapi<elf>
  \-PE    7deb0000-7dec4000    \               mmdevapi
ELF    7dec4000-7dee1000    Deferred        libgcc_s.so.1
ELF    7e039000-7e06c000    Deferred        uxtheme<elf>
  \-PE    7e040000-7e06c000    \               uxtheme
ELF    7e082000-7e0ad000    Deferred        libpng12.so.0
ELF    7e0ad000-7e0c1000    Deferred        libz.so.1
ELF    7e0c1000-7e171000    Deferred        libfreetype.so.6
ELF    7e171000-7e18a000    Deferred        libresolv.so.2
ELF    7e1a9000-7e1ca000    Deferred        iphlpapi<elf>
  \-PE    7e1b0000-7e1ca000    \               iphlpapi
ELF    7e1ca000-7e1f9000    Deferred        ws2_32<elf>
  \-PE    7e1d0000-7e1f9000    \               ws2_32
ELF    7e1f9000-7e213000    Deferred        wsock32<elf>
  \-PE    7e200000-7e213000    \               wsock32
ELF    7e213000-7e23a000    Deferred        msacm32<elf>
  \-PE    7e220000-7e23a000    \               msacm32
ELF    7e23a000-7e2e6000    Deferred        winmm<elf>
  \-PE    7e240000-7e2e6000    \               winmm
ELF    7e2e6000-7e3d9000    Deferred        comctl32<elf>
  \-PE    7e2f0000-7e3d9000    \               comctl32
ELF    7e3d9000-7e443000    Deferred        shlwapi<elf>
  \-PE    7e3f0000-7e443000    \               shlwapi
ELF    7e443000-7e652000    Deferred        shell32<elf>
  \-PE    7e450000-7e652000    \               shell32
ELF    7e652000-7e744000    Deferred        oleaut32<elf>
  \-PE    7e670000-7e744000    \               oleaut32
ELF    7e744000-7e765000    Deferred        imm32<elf>
  \-PE    7e750000-7e765000    \               imm32
ELF    7e765000-7e7db000    Deferred        rpcrt4<elf>
  \-PE    7e770000-7e7db000    \               rpcrt4
ELF    7e7db000-7e8e0000    Deferred        ole32<elf>
  \-PE    7e7f0000-7e8e0000    \               ole32
ELF    7e8e0000-7e8fb000    Deferred        dinput8<elf>
  \-PE    7e8f0000-7e8fb000    \               dinput8
ELF    7e8fb000-7e988000    Deferred        msvcrt<elf>
  \-PE    7e910000-7e988000    \               msvcrt
ELF    7e988000-7ea45000    Deferred        gdi32<elf>
  \-PE    7e990000-7ea45000    \               gdi32
ELF    7ea45000-7eb83000    Deferred        user32<elf>
  \-PE    7ea60000-7eb83000    \               user32
ELF    7eb83000-7ecba000    Deferred        wined3d<elf>
  \-PE    7eb90000-7ecba000    \               wined3d
ELF    7ecba000-7ecf1000    Deferred        d3d9<elf>
  \-PE    7ecc0000-7ecf1000    \               d3d9
ELF    7ecf1000-7ed51000    Deferred        advapi32<elf>
  \-PE    7ed00000-7ed51000    \               advapi32
ELF    7ef51000-7ef64000    Deferred        libnss_files.so.2
ELF    7ef64000-7ef71000    Deferred        libnss_nis.so.2
ELF    7ef71000-7ef8c000    Deferred        libnsl.so.1
ELF    7ef8c000-7efe1000    Deferred        libm.so.6
ELF    7efe8000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f7c76000-f7c7b000    Deferred        libdl.so.2
ELF    f7c7b000-f7e31000    Deferred        libc.so.6
ELF    f7e31000-f7e4e000    Deferred        libpthread.so.0
ELF    f7e63000-f7e6d000    Deferred        libnss_compat.so.2
ELF    f7e6d000-f7fae000    Dwarf           libwine.so.1
ELF    f7faf000-f7fd4000    Deferred        ld-linux.so.2
ELF    f7fd7000-f7fd8000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Microsoft Games\Fable - The Lost Chapters\Fable.exe
    00000044    1
    00000009    0 <==
0000000a wineboot.exe
    0000000b    0
0000000e services.exe
    00000025    0
    0000001d    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    00000019    0
    00000014    0
    00000013    0
0000001a plugplay.exe
    0000001f    0
    0000001c    0
    0000001b    0
00000027 rundll32.exe
    00000028    0
00000029 explorer.exe
    0000002a    0
0000002d control.exe
    0000002e    0

```

I have also tried 3.0 and 3.11 which seem to work better, with these I get "wine configuration is being updated" followed by the initial Fable loading screen (Just a picture with "FABLE" in the top left), this then closes and I get the message:
"The program Fable.exe has encountered a serious problem and needs to close."
I get these two outputs:
```
Running wine-3.0 Fable.exe (Working directory : /home/sakura/.PlayOnLinux/wineprefix/Fable/drive_c/Program Files/Microsoft Games/Fable - The Lost Chapters)
0025:err:module:load_builtin_dll failed to load .so lib for builtin L"winebus.sys": libudev.so.0: cannot open shared object file: No such file or directory
0025:err:winedevice:async_create_driver failed to create driver L"WineBus": c0000142
002f:fixme:atl:AtlAxWinInit version 0300 semi-stub
002f:fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
002f:err:aspi:SCSI_OpenDevice Failed to open device /dev/sg0: Permission denied
002f:fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 1.
002f:fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 2.
0017:fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d004 (device=4 access=3 func=401 method=0)
0039:err:ntdll:RtlpWaitForCriticalSection section 0x7bce5960 "loader.c: loader_section" wait timed out in thread 0039, blocked by 0033, retrying (60 sec)
0034:err:ntdll:RtlpWaitForCriticalSection section 0x7bce5960 "loader.c: loader_section" wait timed out in thread 0034, blocked by 0033, retrying (60 sec)
0035:err:ntdll:RtlpWaitForCriticalSection section 0x48ada0 "?" wait timed out in thread 0035, blocked by 0033, retrying (60 sec)
0040:err:ntdll:RtlpWaitForCriticalSection section 0x7bce5960 "loader.c: loader_section" wait timed out in thread 0040, blocked by 0033, retrying (60 sec)
wine: Unhandled page fault on read access to 0x00000008 at address 0x7d942337 (thread 0009), starting debugger...

```
```

Unhandled exception: page fault on read access to 0x00000008 in 32-bit code (0x7d942337).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7d942337 ESP:0030c3c0 EBP:0030c5c8 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:7c93e188 ECX:7c879540 EDX:00000000
 ESI:00000000 EDI:00000000
Stack dump:
0x0030c3c0:  bf800000 bf800000 3f800000 3f800000
0x0030c3d0:  79f61137 7a605000 00000000 7c879540
0x0030c3e0:  ffffffff ffffffff ffffffff ffffffff
0x0030c3f0:  00000000 7a35de03 0030c4a4 0030c40c
0x0030c400:  7a0e6c40 00000000 7a35de15 77617264
0x0030c410:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x7d942337 (0x0030c5c8)
  1 0x79f875ec in r300_dri.so (+0x4da5eb) (0x00000000)
  2 0x79f87b4f in r300_dri.so (+0x4dab4e) (0x00000005)
  3 0x79e9dce9 in r300_dri.so (+0x3f0ce8) (0x00000005)
  4 0x79e96423 in r300_dri.so (+0x3e9422) (0x00000004)
  5 0x79e969f7 in r300_dri.so (+0x3e99f6) (0x7c95f8d8)
  6 0x7a0c6bf9 in r300_dri.so (+0x619bf8) (0x00000001)
  7 0x7a0c8ba2 in r300_dri.so (+0x61bba1) (0x7c863208)
  8 0x79e8474d in r300_dri.so (+0x3d774c) (0x7c863208)
  9 0x79cc411e in r300_dri.so (+0x21711d) (0x7c863208)
  10 0x79c86169 in r300_dri.so (+0x1d9168) (0x0030c9f8)
  11 0x79c8644d in r300_dri.so (+0x1d944c) (0x0030ca78)
  12 0x7ec12c7a in wined3d (+0xc2c79) (0x0030ca78)
  13 0x7ec13370 in wined3d (+0xc336f) (0x0030cf18)
  14 0x7ec1bb1c in wined3d (+0xcbb1b) (0x0030d028)
  15 0x7eba0d0e in wined3d (+0x50d0d) (0x0030d478)
  16 0x7eba4e27 in wined3d (+0x54e26) (0x0030d4a8)
  17 0x7ec25f49 wined3d_create+0x68() in wined3d (0x0030d4e8)
  18 0x7d7bcf13 DirectDrawEnumerateExA+0x82() in ddraw (0x0030dac8)
  19 0x02b05bde in configdetect (+0x5bdd) (0x7d790000)
  20 0x00000003 (0x00905a4d)
0x7d942337: repe movq    0x0(%esi,%eax,1),%mm2
Modules:
Module    Address            Debug info    Name (138 modules)
PE      400000- 1bb1000    Deferred        fable
PE     1bc0000- 1e13000    Deferred        d3dx9_25
PE     2b00000- 2b20000    Export          configdetect
PE    10000000-10029000    Deferred        strings
ELF    760ba000-79aad000    Deferred        libllvm-5.0.so.1
ELF    79aad000-7a800000    Dwarf           r300_dri.so
ELF    7a800000-7a939000    Deferred        opengl32<elf>
  \-PE    7a820000-7a939000    \               opengl32
ELF    7ac00000-7ac87000    Deferred        riched20<elf>
  \-PE    7ac10000-7ac87000    \               riched20
ELF    7b400000-7b7f1000    Deferred        kernel32<elf>
  \-PE    7b420000-7b7f1000    \               kernel32
ELF    7bc00000-7bcf9000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcf9000    \               ntdll
ELF    7c000000-7c003000    Deferred        <wine-loader>
ELF    7cb4e000-7cb95000    Deferred        usp10<elf>
  \-PE    7cb50000-7cb95000    \               usp10
ELF    7cc95000-7ccab000    Deferred        libgpg-error.so.0
ELF    7ccab000-7cd20000    Deferred        libpcre.so.3
ELF    7cd20000-7cdcf000    Deferred        libgcrypt.so.20
ELF    7cdcf000-7cdf5000    Deferred        liblzma.so.5
ELF    7cdf5000-7ce1b000    Deferred        libselinux.so.1
ELF    7ce1b000-7cea9000    Deferred        libsystemd.so.0
ELF    7cea9000-7cf03000    Deferred        libdbus-1.so.3
ELF    7cf03000-7cf8f000    Deferred        libgmp.so.10
ELF    7cf8f000-7cfc4000    Deferred        libhogweed.so.4
ELF    7cfc4000-7d001000    Deferred        libnettle.so.6
ELF    7d001000-7d035000    Deferred        libidn.so.11
ELF    7d035000-7d10b000    Deferred        libkrb5.so.3
ELF    7d10b000-7d263000    Deferred        libgnutls.so.30
ELF    7d2cc000-7d2d5000    Deferred        libffi.so.6
ELF    7d2d5000-7d2da000    Deferred        libkeyutils.so.1
ELF    7d2da000-7d2ef000    Deferred        libtasn1.so.6
ELF    7d2ef000-7d350000    Deferred        libp11-kit.so.0
ELF    7d350000-7d35d000    Deferred        libkrb5support.so.0
ELF    7d35d000-7d38e000    Deferred        libk5crypto.so.3
ELF    7d38e000-7d3a2000    Deferred        libavahi-client.so.3
ELF    7d3a2000-7d3f4000    Deferred        libgssapi_krb5.so.2
ELF    7d3f4000-7d47b000    Deferred        libcups.so.2
ELF    7d4b6000-7d4ed000    Deferred        libtxc_dxtn.so
ELF    7d4ed000-7d509000    Deferred        libbsd.so.0
ELF    7d509000-7d52c000    Deferred        libtinfo.so.5
ELF    7d52c000-7d563000    Deferred        libedit.so.2
ELF    7d563000-7d57f000    Deferred        libelf.so.1
ELF    7d57f000-7d58b000    Deferred        libdrm_amdgpu.so.1
ELF    7d58b000-7d599000    Deferred        libdrm_radeon.so.1
ELF    7d599000-7d5a3000    Deferred        libdrm_nouveau.so.2
ELF    7d5a3000-7d5b3000    Deferred        libsensors.so.4
ELF    7d5b3000-7d5c7000    Deferred        libdrm.so.2
ELF    7d5c7000-7d5e2000    Deferred        libxcb-glx.so.0
ELF    7d5e2000-7d600000    Deferred        libglapi.so.0
ELF    7d701000-7d70f000    Deferred        libavahi-common.so.3
ELF    7d718000-7d788000    Deferred        libgl.so.1
ELF    7d788000-7d800000    Dwarf           ddraw<elf>
  \-PE    7d790000-7d800000    \               ddraw
ELF    7d900000-7d905000    Deferred        libcom_err.so.2
ELF    7d909000-7d90f000    Deferred        libxcb-dri2.so.0
ELF    7d90f000-7d912000    Deferred        libx11-xcb.so.1
ELF    7d912000-7d916000    Deferred        libxdamage.so.1
ELF    7d916000-7d919000    Deferred        libxshmfence.so.1
ELF    7d919000-7d921000    Deferred        libxcb-sync.so.1
ELF    7d921000-7d925000    Deferred        libxcb-present.so.0
ELF    7d925000-7d929000    Deferred        libxcb-dri3.so.0
ELF    7d948000-7d94f000    Deferred        libxfixes.so.3
ELF    7d94f000-7d95b000    Deferred        libxcursor.so.1
ELF    7d95b000-7d96e000    Deferred        libxi.so.6
ELF    7d96e000-7d972000    Deferred        libxcomposite.so.1
ELF    7d972000-7d97f000    Deferred        libxrandr.so.2
ELF    7d97f000-7d98b000    Deferred        libxrender.so.1
ELF    7d98b000-7d992000    Deferred        libxxf86vm.so.1
ELF    7d992000-7d996000    Deferred        libxinerama.so.1
ELF    7d996000-7d99d000    Deferred        libxdmcp.so.6
ELF    7d99d000-7d9a1000    Deferred        libxau.so.6
ELF    7d9a1000-7d9c7000    Deferred        libxcb.so.1
ELF    7d9c7000-7db12000    Deferred        libx11.so.6
ELF    7db12000-7db27000    Deferred        libxext.so.6
ELF    7db27000-7db44000    Deferred        libgcc_s.so.1
ELF    7db46000-7dbd8000    Deferred        winex11<elf>
  \-PE    7db50000-7dbd8000    \               winex11
ELF    7dc39000-7dc63000    Deferred        libexpat.so.1
ELF    7dc63000-7dcac000    Deferred        libfontconfig.so.1
ELF    7dccb000-7dd67000    Deferred        libfreetype.so.6
ELF    7dd67000-7dd80000    Deferred        libresolv.so.2
ELF    7dd86000-7dd9f000    Deferred        libz.so.1
ELF    7dd9f000-7ddc8000    Deferred        iphlpapi<elf>
  \-PE    7ddb0000-7ddc8000    \               iphlpapi
ELF    7ddc8000-7de06000    Deferred        ws2_32<elf>
  \-PE    7ddd0000-7de06000    \               ws2_32
ELF    7de06000-7de20000    Deferred        wsock32<elf>
  \-PE    7de10000-7de20000    \               wsock32
ELF    7de20000-7de4c000    Deferred        msacm32<elf>
  \-PE    7de30000-7de4c000    \               msacm32
ELF    7de4c000-7df06000    Deferred        winmm<elf>
  \-PE    7de50000-7df06000    \               winmm
ELF    7df06000-7df80000    Deferred        shlwapi<elf>
  \-PE    7df10000-7df80000    \               shlwapi
ELF    7df80000-7e1e1000    Deferred        shell32<elf>
  \-PE    7df90000-7e1e1000    \               shell32
ELF    7e1e1000-7e328000    Deferred        oleaut32<elf>
  \-PE    7e200000-7e328000    \               oleaut32
ELF    7e328000-7e3d7000    Deferred        msvcr71<elf>
  \-PE    7e340000-7e3d7000    \               msvcr71
ELF    7e3d7000-7e52c000    Deferred        msvcp71<elf>
  \-PE    7e420000-7e52c000    \               msvcp71
ELF    7e52c000-7e551000    Deferred        imm32<elf>
  \-PE    7e530000-7e551000    \               imm32
ELF    7e551000-7e5d8000    Deferred        rpcrt4<elf>
  \-PE    7e560000-7e5d8000    \               rpcrt4
ELF    7e5d8000-7e742000    Deferred        ole32<elf>
  \-PE    7e5f0000-7e742000    \               ole32
ELF    7e742000-7e75d000    Deferred        dinput8<elf>
  \-PE    7e750000-7e75d000    \               dinput8
ELF    7e75d000-7e814000    Deferred        msvcrt<elf>
  \-PE    7e770000-7e814000    \               msvcrt
ELF    7e814000-7ea02000    Deferred        user32<elf>
  \-PE    7e830000-7ea02000    \               user32
ELF    7ea02000-7eb37000    Deferred        gdi32<elf>
  \-PE    7ea10000-7eb37000    \               gdi32
ELF    7eb37000-7ec8b000    Dwarf           wined3d<elf>
  \-PE    7eb50000-7ec8b000    \               wined3d
ELF    7ec8b000-7ecca000    Deferred        d3d9<elf>
  \-PE    7ec90000-7ecca000    \               d3d9
ELF    7ecca000-7ed47000    Deferred        advapi32<elf>
  \-PE    7ece0000-7ed47000    \               advapi32
ELF    7ef47000-7ef5a000    Deferred        libnss_files.so.2
ELF    7ef5a000-7ef67000    Deferred        libnss_nis.so.2
ELF    7ef67000-7ef82000    Deferred        libnsl.so.1
ELF    7ef82000-7ef8c000    Deferred        libnss_compat.so.2
ELF    7ef8c000-7efe1000    Deferred        libm.so.6
ELF    7efe7000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f7ba8000-f7bad000    Deferred        libdl.so.2
ELF    f7bad000-f7d63000    Deferred        libc.so.6
ELF    f7d63000-f7d80000    Deferred        libpthread.so.0
ELF    f7d96000-f7d9f000    Deferred        librt.so.1
ELF    f7d9f000-f7f56000    Dwarf           libwine.so.1
ELF    f7f57000-f7f7c000    Deferred        ld-linux.so.2
ELF    f7f7f000-f7f80000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Microsoft Games\Fable - The Lost Chapters\Fable.exe
    00000042    1
    00000009    0 <==
0000000e services.exe
    0000001d    0
    00000013    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    0000001c    0
    00000017    0
    00000016    0
    00000012    0
0000001a plugplay.exe
    0000001f    0
    0000001e    0
    0000001b    0
00000028 explorer.exe
    0000002c    0
    0000002b    0
    0000002a    0
    00000029    0
0000002e inse17.tmp
    00000040    0
    00000039    0
    00000035    0
    00000034    0
    0000002f    0
System information:
    Wine build: wine-3.0
    Platform: i386
    Version: Windows 7
    Host system: Linux
    Host version: 4.13.0-45-generic

```

This is how I installed Fable:
[http://www.gamersonlinux.com/forum/threads/fable-the-lost-chapters-guide.167/](http://www.gamersonlinux.com/forum/threads/fable-the-lost-chapters-guide.167/)

The only thing I have done differently was set my GPU memory to 128mb as after using
```
sudo lspci -v -s 01:05.0
```

I got

```
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS690M [Radeon Xpress 1200/1250/1270] (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems RS690M [Radeon Xpress 1200/1250/1270]
    Flags: bus master, fast devsel, latency 64, IRQ 25
    Memory at 80000000 (64-bit, prefetchable) [size=128M]
    Memory at 8c200000 (64-bit, non-prefetchable) [size=64K]
    I/O ports at 5000 [size=256]
    Memory at 8c100000 (32-bit, non-prefetchable) [size=1M]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Kernel driver in use: radeon
    Kernel modules: radeon
```



I have tried to look into this, despite not being able to find errors exactly like mine I thought I would try solutions for the closest I could find. Some things suggested installing proprietary graphic drivers, unfortunately, after a bit of digging around I found out that newer linux versions do not support the AMD drivers for the x1250 range and to install them I would have to roll back to an earlier version of Linux BUT most people with this GPU seem to have been fine with the built in Linux drivers and chose not to roll back.

I am not sure where to go with this now so any help would be GREATLY appreciated.

Thank you in advance and I look forward to joining the Linux community.

---

### Post by Perfect Storm on 2018-06-25
Thread moved to wine forum.

---

### Post by sakura1604u on 2018-06-25
Thank you moving this to the correct place, I did look around a bit before posting and thought it was in the right place but I am new here and still learning.

Edit: Did I just thank an AI?... #-o

---

### Post by Dennis N on 2018-06-25
First thing you can do is fix this:
```
libSM.so.6: cannot open shared object file: No such file or directory
```
Install the package **libsm6**
Then try again to run the program.

---

### Post by sakura1604u on 2018-06-25
Hi and first of all, thank you for taking the time to try and help.

> **Dennis N said:**
> First thing you can do is fix this:
Install the package **libsm6**

I tried to install libsm6 and got the following

```
sudo apt-get install libsm6
[sudo] password for Sakura: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsm6 is already the newest version (2:1.2.2-1).
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

---

### Post by Dennis N on 2018-06-25
> **sakura1604u said:**
> Hi and first of all, thank you for taking the time to try and help.



I tried to install libsm6 and got the following

```
sudo apt-get install libsm6
[sudo] password for Sakura: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsm6 is already the newest version (2:1.2.2-1).
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

Apparently it's a 32-bit game. From your previous display:
```
fault on read access to 0x00000008 in 32-bit code (0x7d948337).
```
Try install of 32-bit version of the package:
```
sudo apt install libsm6:i386
```
Then try again.

---

### Post by sakura1604u on 2018-06-25
I installed that successfully, ran it again and same thing happened:

```

Running wine-3.0 Fable.exe (Working directory : /home/sakura/.PlayOnLinux/wineprefix/Fable/drive_c/Program Files/Microsoft Games/Fable - The Lost Chapters)
0068:fixme:atl:AtlAxWinInit version 0300 semi-stub
0068:fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
0068:err:aspi:SCSI_OpenDevice Failed to open device /dev/sg0: Permission denied
0068:fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 1.
0068:fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 2.
0017:fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d004 (device=4 access=3 func=401 method=0)
wine: Unhandled page fault on read access to 0x00000008 at address 0x7d940337 (thread 0065), starting debugger...
0034:err:ntdll:RtlpWaitForCriticalSection section 0x7bce5960 "loader.c: loader_section" wait timed out in thread 0034, blocked by 0033, retrying (60 sec)
0039:err:ntdll:RtlpWaitForCriticalSection section 0x7bce5960 "loader.c: loader_section" wait timed out in thread 0039, blocked by 0033, retrying (60 sec)
0035:err:ntdll:RtlpWaitForCriticalSection section 0x48ada0 "?" wait timed out in thread 0035, blocked by 0033, retrying (60 sec)
0040:err:ntdll:RtlpWaitForCriticalSection section 0x7bce5960 "loader.c: loader_section" wait timed out in thread 0040, blocked by 0033, retrying (60 sec)

```

```

Unhandled exception: page fault on read access to 0x00000008 in 32-bit code (0x7d940337).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7d940337 ESP:0030c3c0 EBP:0030c5c8 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:7c970c20 ECX:7c94be00 EDX:00000000
 ESI:00000000 EDI:00000000
Stack dump:
0x0030c3c0:  bf800000 bf800000 3f800000 3f800000
0x0030c3d0:  79f61137 7a605000 00000000 7c94be00
0x0030c3e0:  ffffffff ffffffff ffffffff ffffffff
0x0030c3f0:  00000000 7a35de03 0030c4a4 0030c40c
0x0030c400:  7a0e6c40 00000000 7a35de15 77617264
0x0030c410:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x7d940337 (0x0030c5c8)
  1 0x79f875ec in r300_dri.so (+0x4da5eb) (0x00000000)
  2 0x79f87b4f in r300_dri.so (+0x4dab4e) (0x00000005)
  3 0x79e9dce9 in r300_dri.so (+0x3f0ce8) (0x00000005)
  4 0x79e96423 in r300_dri.so (+0x3e9422) (0x00000004)
  5 0x79e969f7 in r300_dri.so (+0x3e99f6) (0x7c94e9d8)
  6 0x7a0c6bf9 in r300_dri.so (+0x619bf8) (0x00000001)
  7 0x7a0c8ba2 in r300_dri.so (+0x61bba1) (0x7c8742e8)
  8 0x79e8474d in r300_dri.so (+0x3d774c) (0x7c8742e8)
  9 0x79cc411e in r300_dri.so (+0x21711d) (0x7c8742e8)
  10 0x79c86169 in r300_dri.so (+0x1d9168) (0x0030c9f8)
  11 0x79c8644d in r300_dri.so (+0x1d944c) (0x0030ca78)
  12 0x7ec12c7a in wined3d (+0xc2c79) (0x0030ca78)
  13 0x7ec13370 in wined3d (+0xc336f) (0x0030cf18)
  14 0x7ec1bb1c in wined3d (+0xcbb1b) (0x0030d028)
  15 0x7eba0d0e in wined3d (+0x50d0d) (0x0030d478)
  16 0x7eba4e27 in wined3d (+0x54e26) (0x0030d4a8)
  17 0x7ec25f49 wined3d_create+0x68() in wined3d (0x0030d4e8)
  18 0x7d86cf13 DirectDrawEnumerateExA+0x82() in ddraw (0x0030dac8)
  19 0x02b15bde in configdetect (+0x5bdd) (0x7d840000)
  20 0x00000003 (0x00905a4d)
0x7d940337: repe movq    0x0(%esi,%eax,1),%mm2
Modules:
Module    Address            Debug info    Name (138 modules)
PE      400000- 1bb1000    Deferred        fable
PE     1bc0000- 1e13000    Deferred        d3dx9_25
PE     2b10000- 2b30000    Export          configdetect
PE    10000000-10029000    Deferred        strings
ELF    760ba000-79aad000    Deferred        libllvm-5.0.so.1
ELF    79aad000-7a800000    Dwarf           r300_dri.so
ELF    7a800000-7a939000    Deferred        opengl32<elf>
  \-PE    7a820000-7a939000    \               opengl32
ELF    7ac00000-7ac87000    Deferred        riched20<elf>
  \-PE    7ac10000-7ac87000    \               riched20
ELF    7b400000-7b7f1000    Deferred        kernel32<elf>
  \-PE    7b420000-7b7f1000    \               kernel32
ELF    7bc00000-7bcf9000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcf9000    \               ntdll
ELF    7c000000-7c003000    Deferred        <wine-loader>
ELF    7cb3d000-7cb84000    Deferred        usp10<elf>
  \-PE    7cb40000-7cb84000    \               usp10
ELF    7cc84000-7cc9a000    Deferred        libgpg-error.so.0
ELF    7cc9a000-7cd0f000    Deferred        libpcre.so.3
ELF    7cd0f000-7cdbe000    Deferred        libgcrypt.so.20
ELF    7cdbe000-7cde4000    Deferred        liblzma.so.5
ELF    7cde4000-7ce0a000    Deferred        libselinux.so.1
ELF    7ce0a000-7ce98000    Deferred        libsystemd.so.0
ELF    7ce98000-7cef2000    Deferred        libdbus-1.so.3
ELF    7cef2000-7cf7e000    Deferred        libgmp.so.10
ELF    7cf7e000-7cfb3000    Deferred        libhogweed.so.4
ELF    7cfb3000-7cff0000    Deferred        libnettle.so.6
ELF    7cff0000-7d005000    Deferred        libtasn1.so.6
ELF    7d005000-7d039000    Deferred        libidn.so.11
ELF    7d039000-7d09a000    Deferred        libp11-kit.so.0
ELF    7d09a000-7d0cb000    Deferred        libk5crypto.so.3
ELF    7d0cb000-7d1a1000    Deferred        libkrb5.so.3
ELF    7d1a1000-7d2f9000    Deferred        libgnutls.so.30
ELF    7d2f9000-7d34b000    Deferred        libgssapi_krb5.so.2
ELF    7d34b000-7d3d2000    Deferred        libcups.so.2
ELF    7d42b000-7d462000    Deferred        libtxc_dxtn.so
ELF    7d462000-7d47e000    Deferred        libbsd.so.0
ELF    7d47e000-7d4a1000    Deferred        libtinfo.so.5
ELF    7d4a1000-7d4d8000    Deferred        libedit.so.2
ELF    7d4d8000-7d4f4000    Deferred        libelf.so.1
ELF    7d4f4000-7d500000    Deferred        libdrm_amdgpu.so.1
ELF    7d602000-7d610000    Deferred        libdrm_radeon.so.1
ELF    7d610000-7d61a000    Deferred        libdrm_nouveau.so.2
ELF    7d61a000-7d62a000    Deferred        libsensors.so.4
ELF    7d62a000-7d63e000    Deferred        libdrm.so.2
ELF    7d63e000-7d644000    Deferred        libxcb-dri2.so.0
ELF    7d644000-7d65f000    Deferred        libxcb-glx.so.0
ELF    7d65f000-7d662000    Deferred        libx11-xcb.so.1
ELF    7d662000-7d666000    Deferred        libxdamage.so.1
ELF    7d666000-7d684000    Deferred        libglapi.so.0
ELF    7d684000-7d68c000    Deferred        libxcb-sync.so.1
ELF    7d68c000-7d690000    Deferred        libxcb-present.so.0
ELF    7d690000-7d700000    Deferred        libgl.so.1
ELF    7d802000-7d806000    Deferred        libxcb-dri3.so.0
ELF    7d806000-7d80f000    Deferred        libffi.so.6
ELF    7d80f000-7d814000    Deferred        libkeyutils.so.1
ELF    7d814000-7d821000    Deferred        libkrb5support.so.0
ELF    7d821000-7d835000    Deferred        libavahi-client.so.3
ELF    7d835000-7d838000    Deferred        libxshmfence.so.1
ELF    7d838000-7d8b0000    Dwarf           ddraw<elf>
  \-PE    7d840000-7d8b0000    \               ddraw
ELF    7d915000-7d91a000    Deferred        libcom_err.so.2
ELF    7d91a000-7d928000    Deferred        libavahi-common.so.3
ELF    7d947000-7d94e000    Deferred        libxfixes.so.3
ELF    7d94e000-7d95a000    Deferred        libxcursor.so.1
ELF    7d95a000-7d96d000    Deferred        libxi.so.6
ELF    7d96d000-7d971000    Deferred        libxcomposite.so.1
ELF    7d971000-7d97e000    Deferred        libxrandr.so.2
ELF    7d97e000-7d98a000    Deferred        libxrender.so.1
ELF    7d98a000-7d991000    Deferred        libxxf86vm.so.1
ELF    7d991000-7d995000    Deferred        libxinerama.so.1
ELF    7d995000-7d99c000    Deferred        libxdmcp.so.6
ELF    7d99c000-7d9a0000    Deferred        libxau.so.6
ELF    7d9a0000-7d9c6000    Deferred        libxcb.so.1
ELF    7d9c6000-7db11000    Deferred        libx11.so.6
ELF    7db11000-7db26000    Deferred        libxext.so.6
ELF    7db26000-7db43000    Deferred        libgcc_s.so.1
ELF    7db45000-7dbd7000    Deferred        winex11<elf>
  \-PE    7db50000-7dbd7000    \               winex11
ELF    7dc39000-7dc63000    Deferred        libexpat.so.1
ELF    7dc63000-7dcac000    Deferred        libfontconfig.so.1
ELF    7dccb000-7dd67000    Deferred        libfreetype.so.6
ELF    7dd67000-7dd80000    Deferred        libresolv.so.2
ELF    7dd86000-7dd9f000    Deferred        libz.so.1
ELF    7dd9f000-7ddc8000    Deferred        iphlpapi<elf>
  \-PE    7ddb0000-7ddc8000    \               iphlpapi
ELF    7ddc8000-7de06000    Deferred        ws2_32<elf>
  \-PE    7ddd0000-7de06000    \               ws2_32
ELF    7de06000-7de20000    Deferred        wsock32<elf>
  \-PE    7de10000-7de20000    \               wsock32
ELF    7de20000-7de4c000    Deferred        msacm32<elf>
  \-PE    7de30000-7de4c000    \               msacm32
ELF    7de4c000-7df06000    Deferred        winmm<elf>
  \-PE    7de50000-7df06000    \               winmm
ELF    7df06000-7df80000    Deferred        shlwapi<elf>
  \-PE    7df10000-7df80000    \               shlwapi
ELF    7df80000-7e1e1000    Deferred        shell32<elf>
  \-PE    7df90000-7e1e1000    \               shell32
ELF    7e1e1000-7e328000    Deferred        oleaut32<elf>
  \-PE    7e200000-7e328000    \               oleaut32
ELF    7e328000-7e3d7000    Deferred        msvcr71<elf>
  \-PE    7e340000-7e3d7000    \               msvcr71
ELF    7e3d7000-7e52c000    Deferred        msvcp71<elf>
  \-PE    7e420000-7e52c000    \               msvcp71
ELF    7e52c000-7e551000    Deferred        imm32<elf>
  \-PE    7e530000-7e551000    \               imm32
ELF    7e551000-7e5d8000    Deferred        rpcrt4<elf>
  \-PE    7e560000-7e5d8000    \               rpcrt4
ELF    7e5d8000-7e742000    Deferred        ole32<elf>
  \-PE    7e5f0000-7e742000    \               ole32
ELF    7e742000-7e75d000    Deferred        dinput8<elf>
  \-PE    7e750000-7e75d000    \               dinput8
ELF    7e75d000-7e814000    Deferred        msvcrt<elf>
  \-PE    7e770000-7e814000    \               msvcrt
ELF    7e814000-7ea02000    Deferred        user32<elf>
  \-PE    7e830000-7ea02000    \               user32
ELF    7ea02000-7eb37000    Deferred        gdi32<elf>
  \-PE    7ea10000-7eb37000    \               gdi32
ELF    7eb37000-7ec8b000    Dwarf           wined3d<elf>
  \-PE    7eb50000-7ec8b000    \               wined3d
ELF    7ec8b000-7ecca000    Deferred        d3d9<elf>
  \-PE    7ec90000-7ecca000    \               d3d9
ELF    7ecca000-7ed47000    Deferred        advapi32<elf>
  \-PE    7ece0000-7ed47000    \               advapi32
ELF    7ef47000-7ef5a000    Deferred        libnss_files.so.2
ELF    7ef5a000-7ef67000    Deferred        libnss_nis.so.2
ELF    7ef67000-7ef82000    Deferred        libnsl.so.1
ELF    7ef82000-7ef8c000    Deferred        libnss_compat.so.2
ELF    7ef8c000-7efe1000    Deferred        libm.so.6
ELF    7efe7000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f7b27000-f7b2c000    Deferred        libdl.so.2
ELF    f7b2c000-f7ce2000    Deferred        libc.so.6
ELF    f7ce2000-f7cff000    Deferred        libpthread.so.0
ELF    f7d15000-f7d1e000    Deferred        librt.so.1
ELF    f7d1e000-f7ed5000    Dwarf           libwine.so.1
ELF    f7ed6000-f7efb000    Deferred        ld-linux.so.2
ELF    f7efe000-f7eff000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001d    0
    00000013    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    0000001c    0
    00000017    0
    00000016    0
    00000012    0
0000001a plugplay.exe
    0000001f    0
    0000001e    0
    0000001b    0
00000028 explorer.exe
    0000002c    0
    0000002b    0
    0000002a    0
    00000029    0
0000002e inse17.tmp
    00000040    0
    00000039    0
    00000035    0
    00000034    0
    0000002f    0
0000004a ins9e40.tmp
    0000005c    0
    00000055    0
    00000051    0
    00000050    0
    0000004b    0
00000064 (D) C:\Program Files\Microsoft Games\Fable - The Lost Chapters\Fable.exe
    0000007b    1
    00000065    0 <==
System information:
    Wine build: wine-3.0
    Platform: i386
    Version: Windows 7
    Host system: Linux
    Host version: 4.13.0-45-generic

```

---

### Post by sakura1604u on 2018-06-25
```
0068:err:aspi:SCSI_OpenDevice Failed to open device /dev/sg0: Permission denied
```

This seems to be related to CD-Drive read error (looking at other posts around the webs). Now I must mention, when I put a disk in, I can see it, open it and see files fine which means the disk drive is working, but every time I try to install a game on PlayOnLinux (Fable, NFS U2) I get the following message:

Error: Unable to find the CD-ROM

I don't know if this was worth mentioning but I figure too much info is better then not enough.


Edit: This has not happened before but I just put my disk in (Fable Disk 1) opened it and saw this:

[IMG]http://i63.tinypic.com/28rcrxz.png[/IMG]

Over the last few days when I have opened that disk it has had the correct Fable Files in it.


Edit:
I took the disk out, restarted, put the disk back in and now I can see the files again, however this has not helped.

The problem seems to lie here somewhere but I could be wrong
```
0099:fixme:atl:AtlAxWinInit version 0300 semi-stub
0099:fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
0099:fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 1.
0099:err:aspi:SCSI_OpenDevice Failed to open device /dev/sg1: Permission denied
0099:fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 2.
0017:fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d004 (device=4 access=3 func=401 method=0)
0017:fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d004 (device=4 access=3 func=401 method=0)
wine: Unhandled page fault on read access to 0x00000008 at address 0x7d93f337 (thread 0096), starting debugger... 
```

---

### Post by sakura1604u on 2018-06-25
[SIZE=2]```
sudo sg_map
/dev/sg0  /dev/sr0
/dev/sg1  /dev/sda
sudo lsscsi -l
[0:0:0:0]    cd/dvd  TSSTcorp CDDVDW TS-L632H  TO01  /dev/sr0 
  state=running queue_depth=1 scsi_level=6 type=5 device_blocked=0 timeout=30
[2:0:0:0]    disk    ATA      TOSHIBA MK1652GS 0M    /dev/sda 
  state=running queue_depth=31 scsi_level=6 type=0 device_blocked=0 timeout=30

```

[SIZE=2]TOSHIBA MK1652GS is my HDD... does this mean that something does not have permission to access my HDD?

Edit:[/SIZE][/SIZE] Giving rwx to all has got rid of the error:
```

0099:err:aspi:SCSI_OpenDevice Failed to open device /dev/sg1: Permission denied

```
but other then that one error not appearing, nothing has changed... so much hassle for one little game *sigh*


Edit: This line of code seems to be when it crashes every time... 
```
wine: Unhandled page fault on read access to 0x00000008 at address 0x7d93f337 (thread 0096)
```

Does anyone know what it means? I cannot find anything on it, there are a few posts on 0x00000004 but not 08

---

