---
title: "Page Fault libgl.so - Lubuntu 17.10 Wine 2.22 Nvidia GPU"
date: 2017-12-08
forum: Wine
---

### Post by mccarty.geoff on 2017-12-08
EDIT: Withdraw support request due to circuit failure on that computer. No help needed.

Page fault loading game Darkest Hour a relatively old program light on ddraw graphics. Runs well though on another system in 64bit Lubuntu 16.04 with very old Intel graphics adapter. I suspect a problem with Nvidia Proprietary 380.90 driver symlinks and have tested with PPA versions and others available to 'Additional Drivers' (excepting Nvidia's .run installation). All the required packages and driver source files seemed to be installed and unconflicted though.
Using Lubuntu 17.10 64bit with GT420 GPU. Wine 2.22 (current development) in 32bit prefix. Installed by release key method. No changes from default. No use of wrapper program or winetricks. Have posted similar report to WineHQ forums.
Please help me getting WINE to run on this 64bit system with Nvidia drivers if you can.

```
Unhandled exception: page fault on write access to 0x7c002fd4 in 32-bit code (0x7da996da).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7da996da ESP:02a4d920 EBP:00000014 EFLAGS:00010202(  R- --  I   - - - )
 EAX:7df22d70 EBX:7c002fd4 ECX:7df22d70 EDX:00000000
 ESI:7db07430 EDI:7c0005f9
Stack dump:
0x02a4d920:  f7f87920 7c0008b4 00000149 7cdebe28
0x02a4d930:  7cdeb6f0 00000000 f7f87920 00000012
0x02a4d940:  00000016 7cddf120 7c00082c 7da9a91c
0x02a4d950:  7c0008b4 00000014 7db07320 7cddf120
0x02a4d960:  00000000 80000001 f7f87920 0000012c
0x02a4d970:  f7b97000 7cd583d0 f7b93e20 0000000d
000c: sel=0067 base=00000000 limit=00000000 16-bit r-x
Backtrace:
=>0 0x7da996da in libgl.so.1 (+0xa96da) (0x00000014)
  1 0x7da9a91c in libgl.so.1 (+0xaa91b) (0x7c00082c)
  2 0x7daa54c1 in libgl.so.1 (+0xb54c0) (0x7daa17d0)
  3 0x7da3e5c3 in libgl.so.1 (+0x4e5c2) (0x7cdba930)
  4 0xf7f709f1 in ld-linux.so.2 (+0xf9f0) (0x7cdba930)
  5 0xf7f70b5e in ld-linux.so.2 (+0xfb5d) (0xffc984b4)
  6 0xf7f74cfa in ld-linux.so.2 (+0x13cf9) (0x02a4dca8)
  7 0xf7ccae2b _dl_catch_error+0x9a() in libc.so.6 (0x02a4de18)
  8 0xf7f74579 in ld-linux.so.2 (+0x13578) (0x02a4de18)
  9 0xf7b93cc7 GLIBC_2+0xcc6() in libdl.so.2 (0xffc984b4)
  10 0xf7ccae2b _dl_catch_error+0x9a() in libc.so.6 (0x02a4dfac)
  11 0xf7b94422 in libdl.so.2 (+0x1421) (0x02a4dfac)
  12 0xf7b93d6e GLIBC_2+0xd6d() in libdl.so.2 (0x02a4e008)
  13 0xf7daf72f wine_dlopen+0x2e() in libwine.so.1 (0x02a4e008)
  14 0x7e1cd3d8 in winex11 (+0x2d3d7) (0x02a4e218)
  15 0x7bc8758c RtlRunOnceExecuteOnce+0x4b() in ntdll (0x02a4e268)
  16 0x7b478871 InitOnceExecuteOnce+0x20() in kernel32 (0x02a4e298)
  17 0x7e1d0c27 in winex11 (+0x30c26) (0x02a4e2c8)
  18 0x7e1c0094 in winex11 (+0x20093) (0x02a4e2e8)
  19 0x7ea11cce __wine_get_wgl_driver+0x4d() in gdi32 (0x02a4e318)
  20 0x7eb0b385 in wined3d (+0x4b384) (0x02a4e788)
  21 0x7eb0fe2f in wined3d (+0x4fe2e) (0x02a4e7a8)
  22 0x7eb87421 wined3d_create+0x50() in wined3d (0x02a4e7d8)
  23 0x7ec0f974 in ddraw (+0xf973) (0x02a4e998)
  24 0x7ec200f1 in ddraw (+0x200f0) (0x02a4e9d8)
  25 0x7ec20a44 DirectDrawCreate+0x53() in ddraw (0x02a4ea18)
  26 0x00571f8e in darkest hour (+0x171f8d) (0x02a4fde4)
  27 0x0078e498 in darkest hour (+0x38e497) (0x02a4fe70)
  28 0x7b46196c call_process_entry+0xb() in kernel32 (0x02a4fe88)
  29 0x7b462aa4 in kernel32 (+0x52aa3) (0x02a4fec8)
  30 0x7bc7d9bc call_thread_func_wrapper+0xb() in ntdll (0x02a4fedc)
  31 0x7bc80bc6 in ntdll (+0x70bc5) (0x02a4ffcc)
  32 0x7bc7d99a RtlRaiseException+0x49() in ntdll (0x02a4ffec)
0x7da996da: movl    %eax,0x0(%ebx)
Modules:
Module    Address            Debug info    Name (70 modules)
PE      400000-  d6c000    Export          darkest hour
ELF    78802000-7a800000    Deferred        libnvidia-glcore.so.384.90
ELF    7a800000-7a93d000    Deferred        opengl32<elf>
  \-PE    7a820000-7a93d000    \               opengl32
ELF    7b400000-7b7ea000    Dwarf           kernel32<elf>
  \-PE    7b410000-7b7ea000    \               kernel32
ELF    7bc00000-7bcfa000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcfa000    \               ntdll
ELF    7c000000-7c004000    Deferred        <wine-loader>
ELF    7d9f0000-7db08000    Dwarf           libgl.so.1
ELF    7df21000-7df26000    Deferred        libnvidia-tls.so.384.90
ELF    7df6c000-7df73000    Deferred        libxfixes.so.3
ELF    7df73000-7df7f000    Deferred        libxcursor.so.1
ELF    7df7f000-7df92000    Deferred        libxi.so.6
ELF    7df92000-7df96000    Deferred        libxcomposite.so.1
ELF    7df96000-7dfa3000    Deferred        libxrandr.so.2
ELF    7dfa3000-7dfaf000    Deferred        libxrender.so.1
ELF    7dfaf000-7dfb6000    Deferred        libxxf86vm.so.1
ELF    7dfb6000-7dfba000    Deferred        libxinerama.so.1
ELF    7dfba000-7dfc4000    Deferred        librt.so.1
ELF    7dfc4000-7dfdf000    Deferred        libbsd.so.0
ELF    7dfdf000-7dfe6000    Deferred        libxdmcp.so.6
ELF    7dfe6000-7dfea000    Deferred        libxau.so.6
ELF    7dfea000-7e016000    Deferred        libxcb.so.1
ELF    7e016000-7e161000    Deferred        libx11.so.6
ELF    7e161000-7e176000    Deferred        libxext.so.6
ELF    7e192000-7e21e000    Dwarf           winex11<elf>
  \-PE    7e1a0000-7e21e000    \               winex11
ELF    7e21e000-7e242000    Deferred        imm32<elf>
  \-PE    7e220000-7e242000    \               imm32
ELF    7e270000-7e29b000    Deferred        libexpat.so.1
ELF    7e29b000-7e2e4000    Deferred        libfontconfig.so.1
ELF    7e2e4000-7e31e000    Deferred        libpng16.so.16
ELF    7e31e000-7e33d000    Deferred        libz.so.1
ELF    7e33d000-7e3f9000    Deferred        libfreetype.so.6
ELF    7e415000-7e440000    Deferred        msacm32<elf>
  \-PE    7e420000-7e440000    \               msacm32
ELF    7e440000-7e4f9000    Deferred        winmm<elf>
  \-PE    7e450000-7e4f9000    \               winmm
ELF    7e4f9000-7e57b000    Deferred        rpcrt4<elf>
  \-PE    7e500000-7e57b000    \               rpcrt4
ELF    7e57b000-7e6d5000    Deferred        ole32<elf>
  \-PE    7e590000-7e6d5000    \               ole32
ELF    7e6d5000-7e720000    Deferred        dsound<elf>
  \-PE    7e6e0000-7e720000    \               dsound
ELF    7e720000-7e902000    Deferred        user32<elf>
  \-PE    7e730000-7e902000    \               user32
ELF    7e902000-7e97a000    Deferred        advapi32<elf>
  \-PE    7e910000-7e97a000    \               advapi32
ELF    7e97a000-7eaa8000    Dwarf           gdi32<elf>
  \-PE    7e990000-7eaa8000    \               gdi32
ELF    7eaa8000-7ebef000    Dwarf           wined3d<elf>
  \-PE    7eac0000-7ebef000    \               wined3d
ELF    7ebef000-7ec64000    Dwarf           ddraw<elf>
  \-PE    7ec00000-7ec64000    \               ddraw
ELF    7ec64000-7ec9f000    Deferred        ws2_32<elf>
  \-PE    7ec70000-7ec9f000    \               ws2_32
ELF    7ec9f000-7ecb2000    Deferred        libnss_files.so.2
ELF    7ecb2000-7ecc0000    Deferred        libnss_nis.so.2
ELF    7ecc0000-7ecdb000    Deferred        libnsl.so.1
ELF    7ecdb000-7ece5000    Deferred        libnss_compat.so.2
ELF    7eee5000-7efe4000    Deferred        libm.so.6
ELF    7efe6000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f7b93000-f7b98000    Dwarf           libdl.so.2
ELF    f7b98000-f7d6e000    Dwarf           libc.so.6
ELF    f7d6e000-f7d8d000    Deferred        libpthread.so.0
ELF    f7da9000-f7f5f000    Dwarf           libwine.so.1
ELF    f7f61000-f7f88000    Dwarf           ld-linux.so.2
ELF    f7f8b000-f7f8c000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000022    0
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
00000020 winedevice.exe
    00000027    0
    00000024    0
    00000023    0
    00000021    0
00000028 explorer.exe
    0000002f    0
    0000002e    0
    0000002d    0
    0000002c    0
    00000029    0
00000032 Darkest Hour Launcher.exe
    00000035    0
    00000034    0
    00000033    0
0000003e (D) C:\GOG Games\Darkest Hour\Darkest Hour.exe
    0000003f    0 <==
System information:
    Wine build: wine-2.22
    Platform: i386
    Version: Windows XP
    Host system: Linux
    Host version: 4.13.0-19-generic

```

---

