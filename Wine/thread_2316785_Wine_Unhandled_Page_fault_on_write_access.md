---
title: "Wine: Unhandled Page fault on write access"
date: 2016-03-10
forum: Wine
---

### Post by Ice3oy on 2016-03-10
Hello there, this is actually my first post, most of my problems, before this one have been easily handled by myself, but I am at a loss here.

[B]Wine version: 1.9
[/B]I play most of my games through **PlayOnLinux** and I'm using version **4.2.10** 

The Game I played was **Hellboy Dogs of the Night**, a game not played by a lot of people, therefore not many solutions or even problems are known.

I got the following Error Message:

```
Unhandled exception: page fault on write access to 0x00000004 in 32-bit code (0x7bc514be).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7bc514be ESP:0032fad0 EBP:0032fae8 EFLAGS:00010202(  R- --  I   - - - )
 EAX:03ff0000 EBX:7bcd4000 ECX:04ab5c58 EDX:04ab5330
 ESI:00000000 EDI:00000000
Stack dump:
0x0032fad0:  04ab5c58 00000002 04ab5340 7bcd4000
0x0032fae0:  04ab5330 03ff0000 0032fb48 7bc51643
0x0032faf0:  00000928 009e0000 0032fb48 7bc50e2b
0x0032fb00:  04ab7b58 00000018 0032fb6c 7bc3e5e3
0x0032fb10:  0032fb30 00000060 0032fb7c 7bc510fe
0x0032fb20:  0032fb40 00000928 0032fb8c 04ab59f8
Backtrace:
=>0 0x7bc514be in ntdll (+0x414be) (0x0032fae8)
  1 0x7bc51643 in ntdll (+0x41642) (0x0032fb48)
  2 0x7bc51d7f RtlFreeHeap+0x8e() in ntdll (0x0032fba8)
  3 0x0048a9cb in hellboy (+0x8a9ca) (0x0032fc00)
  4 0x0040629d in hellboy (+0x629c) (0x0032fc10)
  5 0x00414e98 in hellboy (+0x14e97) (0x0032fc24)
  6 0x00415896 in hellboy (+0x15895) (0x0032fc34)
  7 0x00444395 in hellboy (+0x44394) (0x0032fc50)
  8 0x0044437c in hellboy (+0x4437b) (0x0032fc7c)
  9 0x0044437c in hellboy (+0x4437b) (0x0032fca8)
  10 0x0044437c in hellboy (+0x4437b) (0x0032fcd4)
  11 0x00444466 in hellboy (+0x44465) (0x0032fd00)
  12 0x00457e0d in hellboy (+0x57e0c) (0x0032fd3c)
  13 0x00457953 in hellboy (+0x57952) (0x0032fd58)
  14 0x0045a016 in hellboy (+0x5a015) (0x0032fd70)
  15 0x00452214 in hellboy (+0x52213) (0x0032fdd4)
  16 0x0048ca4b in hellboy (+0x8ca4a) (0x0032fe60)
  17 0x7b8630ec call_process_entry+0xb() in kernel32 (0x0032fe78)
  18 0x7b8643ab in kernel32 (+0x543aa) (0x0032feb8)
  19 0x7bc832a0 call_thread_func_wrapper+0xb() in ntdll (0x0032fed8)
  20 0x7bc864bd call_thread_func+0x7c() in ntdll (0x0032ffa8)
  21 0x7bc8327e RtlRaiseException+0x21() in ntdll (0x0032ffc8)
  22 0x7bc54abe call_dll_entry_point+0x36d() in ntdll (0x0032ffe8)
  23 0xf75542bd wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  24 0xf755437b wine_switch_to_stack+0x2a() in libwine.so.1 (0xfff4bd48)
  25 0x7bc5ae81 LdrInitializeThunk+0x240() in ntdll (0xfff4bd98)
  26 0x7b86ade0 __wine_kernel_init+0xbcf() in kernel32 (0xfff4ceb8)
  27 0x7bc5bdf3 __wine_process_init+0x182() in ntdll (0xfff4cf48)
  28 0xf7551f5a wine_init+0x299() in libwine.so.1 (0xfff4cfa8)
  29 0x7bf00d7b main+0x8a() in <wine-loader> (0xfff4d3f8)
  30 0xf7372a83 __libc_start_main+0xf2() in libc.so.6 (0x00000000)
0x7bc514be: movl    %edi,0x4(%esi)
Modules:
Module    Address            Debug info    Name (104 modules)
PE      400000-  5ae000    Export          hellboy
PE    21000000-21056000    Deferred        mss32
PE    26000000-26010000    Deferred        mssa3d.m3d
PE    28000000-2800d000    Deferred        mssds3ds.m3d
PE    2a000000-2a010000    Deferred        msseax.m3d
ELF    7857b000-7a800000    Deferred        libnvidia-glcore.so.361.28
ELF    7a800000-7a92d000    Deferred        opengl32<elf>
  \-PE    7a820000-7a92d000    \               opengl32
ELF    7b800000-7ba6a000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba6a000    \               kernel32
ELF    7bc00000-7bcf1000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcf1000    \               ntdll
ELF    7bf00000-7bf04000    Dwarf           <wine-loader>
ELF    7ca58000-7ca70000    Deferred        libresolv.so.2
ELF    7ca70000-7ca9c000    Deferred        libvorbis.so.0
ELF    7cb9f000-7cc2a000    Deferred        libvorbisenc.so.2
ELF    7cc2a000-7cc9c000    Deferred        libsndfile.so.1
ELF    7cda4000-7cdd8000    Deferred        libflac.so.8
ELF    7d15e000-7d1a9000    Deferred        libdbus-1.so.3
ELF    7d1a9000-7d218000    Deferred        libpulsecommon-4.0.so
ELF    7d3dc000-7d3e5000    Deferred        libogg.so.0
ELF    7d3e5000-7d3ee000    Deferred        librt.so.1
ELF    7d3ee000-7d3f5000    Deferred        libasyncns.so.0
ELF    7d3f5000-7d444000    Deferred        libpulse.so.0
ELF    7d447000-7d464000    Deferred        libgcc_s.so.1
ELF    7d46b000-7d494000    Deferred        winepulse<elf>
  \-PE    7d470000-7d494000    \               winepulse
ELF    7d698000-7d7a7000    Deferred        libgl.so.1
ELF    7d8a0000-7d8ab000    Deferred        libjson-c.so.2
ELF    7d8ab000-7d8cf000    Deferred        mmdevapi<elf>
  \-PE    7d8b0000-7d8cf000    \               mmdevapi
ELF    7da59000-7da63000    Deferred        libwrap.so.0
ELF    7db1d000-7db56000    Deferred        uxtheme<elf>
  \-PE    7db20000-7db56000    \               uxtheme
ELF    7db56000-7db5c000    Deferred        libxfixes.so.3
ELF    7db5c000-7db67000    Deferred        libxcursor.so.1
ELF    7db67000-7db77000    Deferred        libxi.so.6
ELF    7db77000-7db7b000    Deferred        libxcomposite.so.1
ELF    7db7b000-7db86000    Deferred        libxrandr.so.2
ELF    7db86000-7db91000    Deferred        libxrender.so.1
ELF    7db91000-7db97000    Deferred        libxxf86vm.so.1
ELF    7db97000-7db9b000    Deferred        libxinerama.so.1
ELF    7db9b000-7dba2000    Deferred        libxdmcp.so.6
ELF    7dba2000-7dba6000    Deferred        libxau.so.6
ELF    7dba6000-7dbc8000    Deferred        libxcb.so.1
ELF    7dbc8000-7dcfc000    Deferred        libx11.so.6
ELF    7dcfc000-7dd0f000    Deferred        libxext.so.6
ELF    7dd2f000-7dd34000    Deferred        libnvidia-tls.so.361.28
ELF    7dd36000-7ddcb000    Deferred        winex11<elf>
  \-PE    7dd40000-7ddcb000    \               winex11
ELF    7ddcb000-7ddf0000    Deferred        imm32<elf>
  \-PE    7ddd0000-7ddf0000    \               imm32
ELF    7df00000-7df29000    Deferred        libexpat.so.1
ELF    7df29000-7df64000    Deferred        libfontconfig.so.1
ELF    7df64000-7df8c000    Deferred        libpng12.so.0
ELF    7df8c000-7dfa6000    Deferred        libz.so.1
ELF    7dfa6000-7e046000    Deferred        libfreetype.so.6
ELF    7e06d000-7e125000    Deferred        msvcrt<elf>
  \-PE    7e080000-7e125000    \               msvcrt
ELF    7e125000-7e1a0000    Deferred        shlwapi<elf>
  \-PE    7e130000-7e1a0000    \               shlwapi
ELF    7e1a0000-7e2e3000    Deferred        oleaut32<elf>
  \-PE    7e1c0000-7e2e3000    \               oleaut32
ELF    7e2e3000-7e310000    Deferred        msvfw32<elf>
  \-PE    7e2f0000-7e310000    \               msvfw32
ELF    7e310000-7e35e000    Deferred        dsound<elf>
  \-PE    7e320000-7e35e000    \               dsound
ELF    7e35e000-7e45b000    Deferred        quartz<elf>
  \-PE    7e370000-7e45b000    \               quartz
ELF    7e45b000-7e486000    Deferred        msacm32<elf>
  \-PE    7e460000-7e486000    \               msacm32
ELF    7e486000-7e541000    Deferred        winmm<elf>
  \-PE    7e490000-7e541000    \               winmm
ELF    7e541000-7e5c6000    Deferred        rpcrt4<elf>
  \-PE    7e550000-7e5c6000    \               rpcrt4
ELF    7e5c6000-7e70c000    Deferred        ole32<elf>
  \-PE    7e5e0000-7e70c000    \               ole32
ELF    7e70c000-7e818000    Deferred        comctl32<elf>
  \-PE    7e710000-7e818000    \               comctl32
ELF    7e818000-7e864000    Deferred        dinput<elf>
  \-PE    7e820000-7e864000    \               dinput
ELF    7e864000-7e9c3000    Deferred        user32<elf>
  \-PE    7e880000-7e9c3000    \               user32
ELF    7e9c3000-7ea3d000    Deferred        advapi32<elf>
  \-PE    7e9d0000-7ea3d000    \               advapi32
ELF    7ea3d000-7eb5f000    Deferred        gdi32<elf>
  \-PE    7ea50000-7eb5f000    \               gdi32
ELF    7eb5f000-7ecb7000    Deferred        wined3d<elf>
  \-PE    7eb70000-7ecb7000    \               wined3d
ELF    7ecb7000-7ed2e000    Deferred        ddraw<elf>
  \-PE    7ecc0000-7ed2e000    \               ddraw
ELF    7ef6d000-7ef7a000    Deferred        libnss_files.so.2
ELF    7ef7a000-7ef93000    Deferred        libnsl.so.1
ELF    7ef93000-7efd9000    Deferred        libm.so.6
ELF    7efe6000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f7354000-f7359000    Deferred        libdl.so.2
ELF    f7359000-f7507000    Dwarf           libc.so.6
ELF    f7508000-f7524000    Deferred        libpthread.so.0
ELF    f7524000-f7530000    Deferred        libnss_nis.so.2
ELF    f7542000-f754b000    Deferred        libnss_compat.so.2
ELF    f754b000-f7701000    Dwarf           libwine.so.1
ELF    f7703000-f7725000    Deferred        ld-linux.so.2
ELF    f7725000-f7726000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files (x86)\Cryo Interactive\Hellboy\hellboy.exe
    00000030   15
    0000002f   15
    0000002d    0
    00000028   15
    00000027    0
    00000026    0
    00000009    0 <==
0000000e services.exe
    0000001e    0
    0000001d    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001c    0
    00000019    0
    00000018    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001f    0
    0000001b    0
00000021 explorer.exe
    00000025    0
    00000024    0
    00000023    0
    00000022    0
System information:
    Wine build: wine-1.9.1
    Platform: i386 (WOW64)
    Version: Windows XP
    Host system: Linux
    Host version: 3.13.0-79-generic
```

I hope someone can help me and if so I thank you in advance

---

### Post by Bucky Ball on 2016-03-10
*Thread moved to **Wine**.*

Welcome. Please use code tags for terminal output. See the link in my signature at the bottom of this post.

---

