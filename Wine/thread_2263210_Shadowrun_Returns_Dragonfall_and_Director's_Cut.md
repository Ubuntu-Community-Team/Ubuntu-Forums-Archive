---
title: "Shadowrun Returns Dragonfall and Director's Cut"
date: 2015-01-30
forum: Wine
---

### Post by dabu on 2015-01-30
Hello everyone,

first I'm new to ubuntu, second I apologize if any forum rules were broken.

I'm running Ubuntu 14.04 LTS 64-bit, under processor it states AMD A10-5757M APU with Radeon(tm) HD Graphics × 4, g, and graphics Gallium 0.4 on AMD ARUBA (the laptop states "AMD Radeon HD 8750M with 2 GB dedicated VRAM".

I've install Wine, winetricks and Q4Wine no problem.

Also I've installed Shadowrun Returns and ran trought the game with multiple characters, and TF2 works better and faster that on Win XP.

So when i found out Dragonfall came near a year ago naturally i got my hands on isos of Dragonfall and  Director's Cut (separately).

Wine has no trouble installing both of these trough path i choose.

The problem with both of them is the same.

When I try to run either of the games a separate window pops up and instead of maximizing it and starting the game it sends an program error report (same for both).

I've been at this for a couple of weeks now and in the process learned about native and builtin dlls, every  combination i found online about setting things right in the winecfg GUI, AppDb, [https://bugs.winehq.org/show_bug.cgi?id=27963](https://bugs.winehq.org/show_bug.cgi?id=27963), wine prefixes, even tryed messing with the regedit command to no avail.

The program error is the same "Unhandled exception: unimplemented function USER32.dll.RegisterTouchWindow called in 32-bit code (0x7bc4e590)."

```
The backtrace.txt is as follows:

"
Unhandled exception: unimplemented function USER32.dll.RegisterTouchWindow called in 32-bit code (0x7bc4e590).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7bc4e590 ESP:0033f530 EBP:0033f594 EFLAGS:00000206(   - --  I   - -P- )
 EAX:015b396a EBX:7bcbf000 ECX:00000000 EDX:00040118
 ESI:0033f53c EDI:7e9476d0
Stack dump:
0x0033f530:  00000000 0033f2e4 000000a8 80000100
0x0033f540:  00000001 00000000 7bc4e590 00000002
0x0033f550:  015b39de 015b396a 7e913531 51728900
0x0033f560:  00110000 00000000 0852fb60 024a2bd8
0x0033f570:  00000042 7e9476d0 0033f598 7e9476f9
0x0033f580:  015b0000 00000042 00000000 024a2bd8
000c: sel=0067 base=00000000 limit=00000000 32-bit rw-
Backtrace:
=>0 0x7bc4e590 call_dll_entry_point+0x480() in ntdll (0x0033f594)
  1 0x015c004b (0x0033f648)
  2 0x024a5ab4 (0x0033f688)
  3 0x024a5656 (0x0033f6c8)
  4 0x024a2b80 (0x0033f6e8)
  5 0x024a2c19 (0x0033f730)
  6 0x100efca1 in mono (+0xefca0) (0x0033f760)
  7 0x1005d613 in mono (+0x5d612) (0x0033f784)
  8 0x0062bcf8 in shadowrun (+0x22bcf7) (0x0033f7a0)
  9 0x0062b615 in shadowrun (+0x22b614) (0x0033f7dc)
  10 0x0062b5c1 in shadowrun (+0x22b5c0) (0x0033f7f0)
  11 0x0060b3ca in shadowrun (+0x20b3c9) (0x0033f8a4)
  12 0x0061faa1 in shadowrun (+0x21faa0) (0x0033f914)
  13 0x006208eb in shadowrun (+0x2208ea) (0x0033f948)
  14 0x0072c4e7 in shadowrun (+0x32c4e6) (0x0033f958)
  15 0x024a2aff (0x0033f998)
  16 0x024a2abc (0x0033f9b8)
  17 0x024a2a4b (0x0033f9d8)
  18 0x0248ebf9 (0x0033fa18)
  19 0x100efca1 in mono (+0xefca0) (0x0033fa48)
  20 0x1005d613 in mono (+0x5d612) (0x0033fa6c)
  21 0x0061fc99 in shadowrun (+0x21fc98) (0x0033fae4)
  22 0x0061ff88 in shadowrun (+0x21ff87) (0x0033fb24)
  23 0x0062037f in shadowrun (+0x22037e) (0x0033fb38)
  24 0x0056e88e in shadowrun (+0x16e88d) (0x0033fba4)
  25 0x005f77cd in shadowrun (+0x1f77cc) (0x0033fc64)
  26 0x0068e8fd in shadowrun (+0x28e8fc) (0x0033fca0)
  27 0x0069007b in shadowrun (+0x29007a) (0x0033fdb8)
  28 0x007d79e8 in shadowrun (+0x3d79e7) (0x0033fdd0)
  29 0x008092f0 in shadowrun (+0x4092ef) (0x0033fe60)
  30 0x7b85e5cc call_process_entry+0xb() in kernel32 (0x0033fe78)
  31 0x7b85f653 in kernel32 (+0x4f652) (0x0033feb8)
  32 0x7bc799b0 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  33 0x7bc7c93d call_thread_func+0x7c() in ntdll (0x0033ffa8)
  34 0x7bc7998e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  35 0x7bc4e8fe call_dll_entry_point+0x7ed() in ntdll (0x0033ffe8)
  36 0xf761950d wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  37 0xf76195cb wine_switch_to_stack+0x2a() in libwine.so.1 (0xffef4158)
  38 0x7bc541e2 LdrInitializeThunk+0x3a1() in ntdll (0xffef41b8)
  39 0x7b865bdd __wine_kernel_init+0xa0c() in kernel32 (0xffef52d8)
  40 0x7bc547a3 __wine_process_init+0x192() in ntdll (0xffef5368)
  41 0xf7616c70 wine_init+0x30f() in libwine.so.1 (0xffef53c8)
  42 0x7bf00fdc main+0xfb() in <wine-loader> (0xffef5818)
  43 0xf7431a83 __libc_start_main+0xf2() in libc.so.6 (0x00000000)
0x7bc4e590 call_dll_entry_point+0x480 in ntdll: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (147 modules)
PE      400000-  e89000    Export          shadowrun
PE     15b0000- 15b8000    Deferred        intelunityplugin
PE    10000000-1022e000    Export          mono
ELF    7b800000-7ba5b000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba5b000    \               kernel32
ELF    7bc00000-7bcdb000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcdb000    \               ntdll
ELF    7bf00000-7bf04000    Dwarf           <wine-loader>
ELF    7d718000-7d74f000    Deferred        uxtheme<elf>
  \-PE    7d720000-7d74f000    \               uxtheme
ELF    7d750000-7d756000    Deferred        libxfixes.so.3
ELF    7d758000-7d763000    Deferred        libxcursor.so.1
ELF    7d768000-7d779000    Deferred        libxi.so.6
ELF    7d780000-7d784000    Deferred        libxcomposite.so.1
ELF    7d788000-7d793000    Deferred        libxrandr.so.2
ELF    7d798000-7d7a3000    Deferred        libxrender.so.1
ELF    7d7a8000-7d7ae000    Deferred        libxxf86vm.so.1
ELF    7d7b0000-7d7b4000    Deferred        libxinerama.so.1
ELF    7d7b8000-7d7bf000    Deferred        libxdmcp.so.6
ELF    7d7c0000-7d7c4000    Deferred        libxau.so.6
ELF    7d7c8000-7d7ea000    Deferred        libxcb.so.1
ELF    7d7f0000-7d924000    Deferred        libx11.so.6
ELF    7d928000-7d93b000    Deferred        libxext.so.6
ELF    7d960000-7d9f2000    Deferred        winex11<elf>
  \-PE    7d970000-7d9f2000    \               winex11
ELF    7db88000-7dbb1000    Deferred        libexpat.so.1
ELF    7dbb8000-7dbf3000    Deferred        libfontconfig.so.1
ELF    7dc18000-7dc40000    Deferred        libpng12.so.0
ELF    7dc40000-7dc5a000    Deferred        libz.so.1
ELF    7dc60000-7dd00000    Deferred        libfreetype.so.6
ELF    7dd20000-7dd5d000    Deferred        winhttp<elf>
  \-PE    7dd30000-7dd5d000    \               winhttp
ELF    7dd60000-7dd86000    Deferred        iphlpapi<elf>
  \-PE    7dd70000-7dd86000    \               iphlpapi
ELF    7dd88000-7debe000    Deferred        oleaut32<elf>
  \-PE    7dda0000-7debe000    \               oleaut32
ELF    7dee8000-7df15000    Deferred        netapi32<elf>
  \-PE    7def0000-7df15000    \               netapi32
ELF    7df18000-7df30000    Deferred        libresolv.so.2
ELF    7df38000-7df4e000    Deferred        hid<elf>
  \-PE    7df40000-7df4e000    \               hid
ELF    7df50000-7df70000    Deferred        dnsapi<elf>
  \-PE    7df60000-7df70000    \               dnsapi
ELF    7df70000-7df95000    Deferred        imm32<elf>
  \-PE    7df80000-7df95000    \               imm32
ELF    7df98000-7dfce000    Deferred        ws2_32<elf>
  \-PE    7dfa0000-7dfce000    \               ws2_32
ELF    7dfd0000-7dffb000    Deferred        msacm32<elf>
  \-PE    7dfe0000-7dffb000    \               msacm32
ELF    7e000000-7e0ba000    Deferred        winmm<elf>
  \-PE    7e010000-7e0ba000    \               winmm
ELF    7e0c0000-7e1cf000    Deferred        opengl32<elf>
  \-PE    7e0e0000-7e1cf000    \               opengl32
ELF    7e1d0000-7e2d7000    Deferred        comctl32<elf>
  \-PE    7e1e0000-7e2d7000    \               comctl32
ELF    7e2d8000-7e50b000    Deferred        shell32<elf>
  \-PE    7e2f0000-7e50b000    \               shell32
ELF    7e510000-7e58a000    Deferred        shlwapi<elf>
  \-PE    7e520000-7e58a000    \               shlwapi
ELF    7e590000-7e611000    Deferred        rpcrt4<elf>
  \-PE    7e5a0000-7e611000    \               rpcrt4
ELF    7e618000-7e754000    Deferred        ole32<elf>
  \-PE    7e630000-7e754000    \               ole32
ELF    7e758000-7e7ca000    Deferred        advapi32<elf>
  \-PE    7e760000-7e7ca000    \               advapi32
ELF    7e7d0000-7e8ed000    Deferred        gdi32<elf>
  \-PE    7e7e0000-7e8ed000    \               gdi32
ELF    7e8f0000-7ea4a000    Deferred        user32<elf>
  \-PE    7e900000-7ea4a000    \               user32
ELF    7ea50000-7ea5d000    Deferred        libnss_files.so.2
ELF    7ea60000-7ea6c000    Deferred        libnss_nis.so.2
ELF    7ea70000-7ea89000    Deferred        libnsl.so.1
ELF    7ea90000-7eaaa000    Deferred        version<elf>
  \-PE    7eaa0000-7eaaa000    \               version
ELF    7ef98000-7efde000    Deferred        libm.so.6
ELF    7eff0000-7eff9000    Deferred        libnss_compat.so.2
PE    efca0000-efca4000    Deferred        msvcrt
ELF    f0118000-f0150000    Deferred        msvcr100<elf>
  \-PE    f0120000-f0150000    \               msvcr100
ELF    f0150000-f0167000    Deferred        powrprof<elf>
  \-PE    f0160000-f0167000    \               powrprof
ELF    f0168000-f017d000    Deferred        d3d11<elf>
  \-PE    f0170000-f017d000    \               d3d11
ELF    f0180000-f0195000    Deferred        xinput1_3<elf>
  \-PE    f0190000-f0195000    \               xinput1_3
ELF    f41a0000-f41e9000    Deferred        dsound<elf>
  \-PE    f41b0000-f41e9000    \               dsound
ELF    f41f0000-f41f9000    Deferred        libogg.so.0
ELF    f4200000-f422c000    Deferred        libvorbis.so.0
ELF    f4230000-f43a8000    Deferred        libvorbisenc.so.2
ELF    f43a8000-f43dc000    Deferred        libflac.so.8
ELF    f43e0000-f43e7000    Deferred        libasyncns.so.0
ELF    f43e8000-f445a000    Deferred        libsndfile.so.1
ELF    f4460000-f446a000    Deferred        libwrap.so.0
ELF    f4470000-f44df000    Deferred        libpulsecommon-4.0.so
ELF    f44e0000-f452f000    Deferred        libpulse.so.0
ELF    f4540000-f4547000    Deferred        libasound_module_pcm_pulse.so
ELF    f4550000-f4646000    Deferred        libasound.so.2
ELF    f4650000-f465b000    Deferred        libjson-c.so.2
ELF    f4668000-f4698000    Deferred        winealsa<elf>
  \-PE    f4670000-f4698000    \               winealsa
ELF    f4698000-f46ba000    Deferred        mmdevapi<elf>
  \-PE    f46a0000-f46ba000    \               mmdevapi
ELF    f4848000-f487a000    Deferred        wbemprox<elf>
  \-PE    f4850000-f487a000    \               wbemprox
ELF    f4c98000-f4cbf000    Deferred        dxgi<elf>
  \-PE    f4ca0000-f4cbf000    \               dxgi
ELF    f4d30000-f4d67000    Deferred        libtxc_dxtn.so
ELF    f4d68000-f4d8a000    Deferred        libtinfo.so.5
ELF    f4d90000-f4d97000    Deferred        libffi.so.6
ELF    f4d98000-f4db5000    Deferred        libgcc_s.so.1
ELF    f4ea8000-f6862000    Deferred        libllvm-3.4.so.1
ELF    f6868000-f6876000    Deferred        libdrm_radeon.so.1
ELF    f6878000-f6c53000    Deferred        libgallium.so.0
ELF    f6c78000-f7062000    Deferred        r600_dri.so
ELF    f7068000-f7071000    Deferred        librt.so.1
ELF    f7078000-f70c3000    Deferred        libdbus-1.so.3
ELF    f70c8000-f70d2000    Deferred        libnih-dbus.so.1
ELF    f70d8000-f70f1000    Deferred        libnih.so.1
ELF    f70f8000-f7116000    Deferred        libcgmanager.so.0
ELF    f7120000-f7138000    Deferred        libelf.so.1
ELF    f7138000-f7145000    Deferred        libdrm.so.2
ELF    f7148000-f714b000    Deferred        libxshmfence.so.1
ELF    f7150000-f7157000    Deferred        libxcb-sync.so.1
ELF    f7158000-f715c000    Deferred        libxcb-present.so.0
ELF    f7160000-f7164000    Deferred        libxcb-dri3.so.0
ELF    f7168000-f716e000    Deferred        libxcb-dri2.so.0
ELF    f7170000-f7188000    Deferred        libxcb-glx.so.0
ELF    f7188000-f718b000    Deferred        libx11-xcb.so.1
ELF    f7190000-f71a8000    Deferred        libglapi.so.0
ELF    f71a8000-f7208000    Deferred        libgl.so.1
ELF    f7210000-f7223000    Deferred        libudev.so.1
ELF    f7228000-f7368000    Deferred        wined3d<elf>
  \-PE    f7240000-f7368000    \               wined3d
ELF    f7368000-f73a5000    Deferred        d3d9<elf>
  \-PE    f7370000-f73a5000    \               d3d9
ELF    f73f8000-f740d000    Deferred        mswsock<elf>
  \-PE    f7400000-f740d000    \               mswsock
ELF    f7418000-f75c7000    Dwarf           libc.so.6
ELF    f75c8000-f75cd000    Deferred        libdl.so.2
ELF    f75d0000-f75ec000    Deferred        libpthread.so.0
ELF    f75f0000-f75f4000    Deferred        libxdamage.so.1
ELF    f75f8000-f760c000    Deferred        psapi<elf>
  \-PE    f7600000-f760c000    \               psapi
ELF    f7610000-f77c5000    Dwarf           libwine.so.1
ELF    f77c8000-f77ea000    Deferred        ld-linux.so.2
ELF    f77eb000-f77ec000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001f    0
    0000001e    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001d    0
    0000001a    0
    00000017    0
    00000013    0
0000001b plugplay.exe
    00000021    0
    00000020    0
    0000001c    0
00000022 explorer.exe
    00000024    0
    00000023    0
00000025 Dragonfall.exe
    0000003e    2
    0000003d   15
    0000003c   15
    0000003b    0
    00000036    0
    00000031    0
    00000030   -2
    0000002f    0
    0000002e    0
    0000002d    0
    0000002c    0
    0000002b    0
    0000002a    0
    00000029    0
    00000028    0
    00000027    0
00000019 Shadowrun.exe
    00000065    0
    00000064    2
    00000062   15
    00000060   15
    0000005e    0
    00000054    0
    00000049    0
    0000000d   -2
    00000037    0
    0000003a    0
    00000035    0
    00000033    0
    00000032    0
    00000043    0
    00000040    0
    00000046    0
    00000042    0
00000018 (D) Z:\home\hermes\Desktop\Shadowrun Returns\Shadowrun.exe
    00000066    0
    00000063    2
    00000061   15
    0000005f   15
    0000005d    0
    00000053    0
    0000004a    0
    00000048   -2
    00000038    0
    00000041    0
    00000047    0
    0000003f    0
    0000000b    0
    00000009    0
    00000016    0
    00000039    0
    00000045    0 <==
0000004c winedbg.exe
    0000004d    0
System information:
    Wine build: wine-1.6.2
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.13.0-44-generic

"
```

Any toughts?

Aditionaly, I've found some solutions in the form of a "stub" of code to be added to the .dlls but dont have a clue how to do it and where.
[http://source.winehq.org/git/wine.git/commitdiff/6458aca761f56dffcdf117e81450720c26a0c53f#patch1](http://source.winehq.org/git/wine.git/commitdiff/6458aca761f56dffcdf117e81450720c26a0c53f#patch1)


Any toughts or ideas, even tips to some basics of this whole mess would be appreciated.

---

### Post by dabu on 2015-02-03
P.S. 
I've uninstalled and reinstalled wine before attempts. Also I've downloaded a new iso of Shadowrun Returns(worked before)+Dragonfall+patch 2.2. All 3 were installed with no issue. When I try starting Shadowrun Returns it returns the same RegisterTouchWindow program error. Learned how to patch source code with git commands having trouble pasting patch.txt into wine  source folder because:
a)I use sudo for root actions
b)Not sure wich one it is, whereis command return four different locations.

---

### Post by 3246251196 on 2015-02-05
Hi, I love these games too but they are completely available for the GNU/Linux platform and they play very nicely. So just install Steam and download the game; no need for wine.

---

