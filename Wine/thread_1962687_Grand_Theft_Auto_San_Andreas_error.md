---
title: "Grand Theft Auto San Andreas error"
date: 2012-04-21
forum: Wine
---

### Post by WoaDmulL on 2012-04-21
I installed game with Play On Linux, it works,but when I start game, when the story line beggin it shows me this errors
```
Unhandled exception: page fault on read access to 0x000000ec in 32-bit code (0x20910ffb).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:20910ffb ESP:0177f820 EBP:0177fad4 EFLAGS:00010206(  R- --  I   - -P- )
 EAX:00000003 EBX:b778c6c0 ECX:7d99d000 EDX:7d9e99b0
 ESI:000000e8 EDI:0013c430
Stack dump:
0x0177f820:  7a999ff4 00000001 7a8dc0f5 000084c0
0x0177f830:  000000e8 00000000 00000258 00000258
0x0177f840:  00000002 07667f00 7bca6ff4 7bc3512f
0x0177f850:  03778fb8 00000010 0177f8b8 7bc4782a
0x0177f860:  07647ed0 7bca6ff4 0177f8c8 7bc47c46
0x0177f870:  00110060 00000000 00020018 00110060
Backtrace:
=>0 0x20910ffb in libglcore.so.1 (+0x910ffb) (0x0177fad4)
  1 0x7a8be5f3 wined3d_device_draw_indexed_primitive+0xd2() in wined3d (0x0177fb34)
  2 0x20f96014 in d3d9 (+0x16013) (0x0177fb84)
  3 0x007fa351 in gta_sa (+0x3fa350) (0x0336f178)
0x20910ffb: movl    0x4(%esi),%ebx
Modules:
Module    Address            Debug info    Name (159 modules)
PE      240000-  249000    Deferred        ogg
PE      250000-  358000    Deferred        vorbis
PE      360000-  390000    Deferred        eax
PE      400000- 1577000    Export          gta_sa
PE    10000000-10011000    Deferred        vorbisfile
ELF    20000000-20d40000    Export          libglcore.so.1
ELF    20d42000-20da8000    Deferred        ddraw<elf>
  \-PE    20d50000-20da8000    \               ddraw
ELF    20da8000-20dec000    Deferred        dsound<elf>
  \-PE    20db0000-20dec000    \               dsound
ELF    20dec000-20e11000    Deferred        winepulse<elf>
  \-PE    20df0000-20e11000    \               winepulse
ELF    20e11000-20e5f000    Deferred        libpulse.so.0
ELF    20e5f000-20e67000    Deferred        libjson.so.0
ELF    20e67000-20eb0000    Deferred        libdbus-1.so.3
ELF    20eb0000-20efe000    Deferred        libflac.so.8
ELF    20efe000-20f1a000    Deferred        dinput8<elf>
  \-PE    20f00000-20f1a000    \               dinput8
ELF    20f1a000-20f38000    Deferred        libgcc_s.so.1
ELF    20f38000-20f7c000    Deferred        dinput<elf>
  \-PE    20f40000-20f7c000    \               dinput
ELF    20f7c000-20fb4000    Dwarf           d3d9<elf>
  \-PE    20f80000-20fb4000    \               d3d9
ELF    20fb4000-20fc9000    Deferred        avicap32<elf>
  \-PE    20fc0000-20fc9000    \               avicap32
ELF    20fc9000-20fdf000    Deferred        midimap<elf>
  \-PE    20fd0000-20fdf000    \               midimap
ELF    20fdf000-2112c000    Deferred        libxml2.so.2
ELF    2112c000-2116b000    Deferred        libpcre.so.3
ELF    2116b000-211b2000    Deferred        libgstcoreelements.so
ELF    211b2000-211d0000    Deferred        libselinux.so.1
ELF    211d0000-211e8000    Deferred        libgstrtp-0.10.so.0
ELF    211e8000-21213000    Deferred        libgsttag-0.10.so.0
ELF    21213000-2121a000    Deferred        libgstcoreindexers.so
ELF    2121a000-2131f000    Deferred        libavformat.so.53
ELF    2131f000-213b9000    Deferred        libvpx.so.0
ELF    213b9000-213e3000    Deferred        libva.so.1
ELF    21524000-2152d000    Deferred        librt.so.1
ELF    22ea9000-22f0e000    Deferred        libpulsecommon-1.0.so
ELF    25045000-2507a000    Deferred        libgstmpegdemux.so
ELF    259a8000-25a4c000    Deferred        libgl.so.1
ELF    26a25000-26a50000    Deferred        libvorbis.so.0
ELF    2775a000-27767000    Deferred        libgstvideo-0.10.so.0
ELF    28cc7000-28dc0000    Deferred        libglib-2.0.so.0
ELF    29dce000-29f46000    Deferred        libvorbisenc.so.2
ELF    2e1c6000-2e1ce000    Deferred        libogg.so.0
ELF    2f556000-2f570000    Deferred        libtheoradec.so.1
ELF    3053a000-3109f000    Deferred        libavcodec.so.53
ELF    35b31000-35c2a000    Deferred        comctl32<elf>
  \-PE    35b40000-35c2a000    \               comctl32
ELF    3a3f7000-3a42d000    Deferred        winegstreamer<elf>
  \-PE    3a400000-3a42d000    \               winegstreamer
ELF    3c7fc000-3c84b000    Deferred        libgobject-2.0.so.0
ELF    3d12b000-3d147000    Deferred        libgstdecodebin2.so
ELF    41f2f000-41f88000    Deferred        libgstbase-0.10.so.0
ELF    41fbf000-42012000    Deferred        libgstffmpegcolorspace.so
ELF    42a26000-42b6c000    Deferred        libgio-2.0.so.0
ELF    431a1000-43212000    Deferred        libsndfile.so.1
ELF    433b0000-4341a000    Deferred        shlwapi<elf>
  \-PE    433c0000-4341a000    \               shlwapi
ELF    44236000-4427a000    Deferred        libtheoraenc.so.1
ELF    4710b000-47112000    Deferred        libffi.so.6
ELF    471db000-471fb000    Deferred        libgstpbutils-0.10.so.0
ELF    48f7a000-48fa5000    Deferred        msvfw32<elf>
  \-PE    48f80000-48fa5000    \               msvfw32
ELF    4b4f2000-4b5a0000    Deferred        libschroedinger-1.0.so.0
ELF    4cbe3000-4ccad000    Deferred        quartz<elf>
  \-PE    4cc00000-4ccad000    \               quartz
ELF    4e796000-4e7bc000    Deferred        libgstaudio-0.10.so.0
ELF    51c4e000-51c71000    Deferred        mmdevapi<elf>
  \-PE    51c50000-51c71000    \               mmdevapi
ELF    53814000-5382d000    Deferred        msacm32<elf>
  \-PE    53820000-5382d000    \               msacm32
ELF    5409c000-540b0000    Deferred        libgstaudioparsers.so
ELF    580e3000-58107000    Deferred        devenum<elf>
  \-PE    580f0000-58107000    \               devenum
ELF    59b45000-59b57000    Deferred        libgstinterfaces-0.10.so.0
ELF    5aac8000-5aae9000    Deferred        libspeex.so.1
ELF    60b14000-60b4e000    Deferred        libgstffmpeg.so
ELF    62af6000-62b1a000    Deferred        libgstbluetooth.so
ELF    64b75000-64b7f000    Deferred        libwrap.so.0
ELF    65e71000-65e78000    Deferred        libasyncns.so.0
ELF    68000000-68020000    Deferred        ld-linux.so.2
ELF    68020000-68162000    Dwarf           libwine.so.1
ELF    68162000-6817d000    Deferred        libpthread.so.0
ELF    6817d000-682fb000    Deferred        libc.so.6
ELF    682fb000-68300000    Deferred        libdl.so.2
ELF    68300000-6830a000    Deferred        libnss_compat.so.2
ELF    6830a000-68323000    Deferred        libnsl.so.1
ELF    68323000-6832f000    Deferred        libnss_nis.so.2
ELF    6832f000-6833c000    Deferred        libnss_files.so.2
ELF    6833c000-683e9000    Deferred        winmm<elf>
  \-PE    68340000-683e9000    \               winmm
ELF    683e9000-68529000    Deferred        user32<elf>
  \-PE    68400000-68529000    \               user32
ELF    68529000-685e7000    Deferred        gdi32<elf>
  \-PE    68540000-685e7000    \               gdi32
ELF    685e7000-68649000    Deferred        advapi32<elf>
  \-PE    685f0000-68649000    \               advapi32
ELF    68649000-68662000    Deferred        version<elf>
  \-PE    68650000-68662000    \               version
ELF    68662000-686d8000    Deferred        rpcrt4<elf>
  \-PE    68670000-686d8000    \               rpcrt4
ELF    686d8000-68700000    Deferred        msacm32<elf>
  \-PE    686e0000-68700000    \               msacm32
ELF    68700000-68797000    Deferred        libfreetype.so.6
ELF    68797000-687ac000    Deferred        libz.so.1
ELF    687ac000-687b5000    Deferred        libsm.so.6
ELF    687b5000-687c8000    Deferred        libxext.so.6
ELF    687c8000-688fe000    Deferred        libx11.so.6
ELF    688fe000-68918000    Deferred        libice.so.6
ELF    68918000-6891e000    Deferred        libuuid.so.1
ELF    6891e000-6893d000    Deferred        libxcb.so.1
ELF    6893d000-68941000    Deferred        libxau.so.6
ELF    68941000-68948000    Deferred        libxdmcp.so.6
ELF    68948000-6894c000    Deferred        libxinerama.so.1
ELF    6894c000-68952000    Deferred        libxxf86vm.so.1
ELF    68952000-6895d000    Deferred        libxrender.so.1
ELF    6895d000-68966000    Deferred        libxrandr.so.2
ELF    68966000-6896a000    Deferred        libxcomposite.so.1
ELF    6896a000-6897a000    Deferred        libxi.so.6
ELF    6897a000-689af000    Deferred        libfontconfig.so.1
ELF    689af000-689ba000    Deferred        libxcursor.so.1
ELF    689ba000-689c0000    Deferred        libxfixes.so.3
ELF    6a3f4000-6a3f6000    Deferred        libnvidia-tls.so.1
ELF    6b3f7000-6b4dd000    Deferred        libgstreamer-0.10.so.0
ELF    6b4f1000-6b4f6000    Deferred        libgmodule-2.0.so.0
ELF    6bb9f000-6bbd1000    Deferred        ws2_32<elf>
  \-PE    6bbb0000-6bbd1000    \               ws2_32
ELF    6d628000-6d636000    Deferred        libgsm.so.1
ELF    6db23000-6db4d000    Deferred        libm.so.6
ELF    6e1e7000-6e252000    Deferred        liboil-0.3.so.0
ELF    6e76e000-6e774000    Deferred        libgthread-2.0.so.0
ELF    6f672000-6f765000    Deferred        oleaut32<elf>
  \-PE    6f690000-6f765000    \               oleaut32
ELF    73b96000-73c29000    Deferred        winex11<elf>
  \-PE    73ba0000-73c29000    \               winex11
ELF    75ea3000-75ed4000    Deferred        libgstflump3dec.so
ELF    763f9000-7641b000    Deferred        imm32<elf>
  \-PE    76400000-7641b000    \               imm32
ELF    7671a000-76731000    Deferred        libresolv.so.2
ELF    772f2000-772fa000    Deferred        libgstmpegvideoparse.so
ELF    7796e000-77998000    Deferred        libexpat.so.1
ELF    77e2c000-77e39000    Deferred        libgstapp-0.10.so.0
ELF    783f1000-784f9000    Deferred        ole32<elf>
  \-PE    78410000-784f9000    \               ole32
ELF    78588000-78599000    Deferred        libbz2.so.1.0
ELF    7a86c000-7a99f000    Dwarf           wined3d<elf>
  \-PE    7a880000-7a99f000    \               wined3d
ELF    7ab2a000-7ab40000    Deferred        libgsttypefindfunctions.so
ELF    7ab68000-7ab89000    Deferred        libavutil.so.51
ELF    7b2ad000-7b33a000    Deferred        liborc-0.4.so.0
ELF    7b800000-7ba2a000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba2a000    \               kernel32
ELF    7bc00000-7bcc3000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d20f000-7d243000    Deferred        uxtheme<elf>
  \-PE    7d220000-7d243000    \               uxtheme
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000020    0
    0000001f    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001d    0
    0000001a    0
    00000014    0
    00000013    0
0000001b plugplay.exe
    00000021    0
    0000001e    0
    0000001c    0
00000022 explorer.exe
    00000023    0
00000024 (D) Z:\home\woadmull\RockStar Games\GTA San Andreas\gta_sa.exe
    0000003d    0
    0000003c    0
    0000003b   15
    0000002b    0
    00000029    0
    00000028    0
    00000027   15
    00000026    0
    00000025    0 <==
System information:
    Wine build: wine-1.5.2
    Platform: i386
    Host system: Linux
    Host version: 3.0.0-17-generic
```
Please, anyone , help me!
Thanks!

---

