---
title: "Age Of Empires 2 HD"
date: 2013-04-10
forum: Wine
---

### Post by ViliX64 on 2013-04-10
Hi, I am considering buying Age Of Empires 2 HD. Can I run it on Wine using Age Of Empires 2 setting?

---

### Post by ViliX64 on 2013-04-10
Well, the game does work (install it on PlayOnLinux).. the menu works fine, but in the game, I can't see the battleground, everything around it yes (money, wood status, map..), but the battleground not. Maybe it is just my Intel HD Graphic 2000.

---

### Post by SilFox on 2013-04-10
I have Steam running under wine with AoE 3 working perfect.
Few days ago installed (Steam) AoE 2 HD  but no luck:

```

Unhandled exception: C++ exception(object = 0x0033f4a4, type = 0x1009c200) in 32-bit code (0x7b83bd02).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b83bd02 ESP:0033f394 EBP:0033f408 EFLAGS:00000246(   - --  I  Z- -P- )
 EAX:7b826d2d EBX:7b8b6000 ECX:00000000 EDX:00000003
 ESI:00000003 EDI:00000000
Stack dump:
0x0033f394:  0033f444 0000000c 7bc37d93 e06d7363
0x0033f3a4:  00000001 00000000 7b83bd02 00000003
0x0033f3b4:  19930520 0033f4a4 1009c200 0033f3e0
0x0033f3c4:  7bcbe000 0033f438 7bc4b4d3 00000002
0x0033f3d4:  00147be8 0033f438 7bc4b4d3 00110060
0x0033f3e4:  00523120 100858ab 00110000 0033f404
Backtrace:
=>0 0x7b83bd02 in kernel32 (+0x2bd02) (0x0033f408)
  1 0x1008188f in setupengine (+0x8188e) (0x0033f450)
  2 0x10066e96 in setupengine (+0x66e95) (0x0033f4c0)
  3 0x1006380b in setupengine (+0x6380a) (0x0033f4e0)
  4 0x10061405 in setupengine (+0x61404) (0x0033f518)
  5 0x10035a52 in setupengine (+0x35a51) (0x0033f588)
  6 0x1006b83a in setupengine (+0x6b839) (0x0033fce8)
  7 0x1005faa0 in setupengine (+0x5fa9f) (0x0033fd58)
  8 0x100580de in setupengine (+0x580dd) (0x0033fdac)
  9 0x00402928 in setup (+0x2927) (0x0033fe40)
  10 0x7b86011c call_process_entry+0xb() in kernel32 (0x0033fe58)
  11 0x7b8614bb in kernel32 (+0x514ba) (0x0033fe98)
  12 0x7bc799e0 call_thread_func_wrapper+0xb() in ntdll (0x0033feb8)
  13 0x7bc7c9ff call_thread_func+0x9e() in ntdll (0x0033ff98)
  14 0x7bc799be RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  15 0x7bc4e2b1 call_dll_entry_point+0x530() in ntdll (0x0033ffe8)
  16 0xf76674cd wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  17 0xf76675ae wine_switch_to_stack+0x2d() in libwine.so.1 (0xffb01448)
  18 0x7bc53edf LdrInitializeThunk+0x3be() in ntdll (0xffb014b8)
  19 0x7b867d28 __wine_kernel_init+0xbf7() in kernel32 (0xffb025d8)
  20 0x7bc545bb __wine_process_init+0x18a() in ntdll (0xffb02668)
  21 0xf766500e wine_init+0x2ad() in libwine.so.1 (0xffb026d8)
  22 0x7bf00dbb main+0x8a() in <wine-loader> (0xffb02b28)
  23 0xf74ad7c3 __libc_start_main+0xf2() in libc.so.6 (0x00000000)
0x7b83bd02: movl    0xfffffff4(%ebp),%ecx
Modules:
Module    Address            Debug info    Name (87 modules)
PE      400000-  415000    Export          setup
PE    10000000-100c8000    Export          setupengine
PE    6cd00000-6cd24000    Deferred        sqmapi
PE    76080000-760d0000    Deferred        winhttp
ELF    7b800000-7ba45000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba45000    \               kernel32
ELF    7bc00000-7bcda000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcda000    \               ntdll
ELF    7bf00000-7bf04000    Dwarf           <wine-loader>
ELF    7dcd9000-7dd10000    Deferred        uxtheme<elf>
  \-PE    7dce0000-7dd10000    \               uxtheme
ELF    7dd10000-7dd16000    Deferred        libxfixes.so.3
ELF    7dd16000-7dd21000    Deferred        libxcursor.so.1
ELF    7dd21000-7dd31000    Deferred        libxi.so.6
ELF    7dd31000-7dd3c000    Deferred        libxrandr.so.2
ELF    7dd3c000-7dd46000    Deferred        libxrender.so.1
ELF    7dd46000-7dd4d000    Deferred        libxdmcp.so.6
ELF    7dd4d000-7dd6f000    Deferred        libxcb.so.1
ELF    7dd6f000-7dd75000    Deferred        libuuid.so.1
ELF    7dd75000-7dd8f000    Deferred        libice.so.6
ELF    7dd8f000-7dec6000    Deferred        libx11.so.6
ELF    7dec6000-7ded8000    Deferred        libxext.so.6
ELF    7deed000-7df83000    Deferred        winex11<elf>
  \-PE    7df00000-7df83000    \               winex11
ELF    7dfac000-7dfd5000    Deferred        libexpat.so.1
ELF    7dfd5000-7e00e000    Deferred        libfontconfig.so.1
ELF    7e00e000-7e01e000    Deferred        libbz2.so.1.0
ELF    7e01e000-7e0bb000    Deferred        libfreetype.so.6
ELF    7e0be000-7e0c7000    Deferred        libsm.so.6
ELF    7e0d0000-7e19e000    Deferred        crypt32<elf>
  \-PE    7e0e0000-7e19e000    \               crypt32
ELF    7e19e000-7e1d4000    Deferred        wintrust<elf>
  \-PE    7e1a0000-7e1d4000    \               wintrust
ELF    7e1d4000-7e20a000    Deferred        ws2_32<elf>
  \-PE    7e1e0000-7e20a000    \               ws2_32
ELF    7e20a000-7e230000    Deferred        iphlpapi<elf>
  \-PE    7e210000-7e230000    \               iphlpapi
ELF    7e230000-7e25d000    Deferred        netapi32<elf>
  \-PE    7e240000-7e25d000    \               netapi32
ELF    7e25d000-7e290000    Deferred        secur32<elf>
  \-PE    7e260000-7e290000    \               secur32
ELF    7e290000-7e33a000    Deferred        msvcrt<elf>
  \-PE    7e2a0000-7e33a000    \               msvcrt
ELF    7e33a000-7e352000    Deferred        userenv<elf>
  \-PE    7e340000-7e352000    \               userenv
ELF    7e352000-7e373000    Deferred        cabinet<elf>
  \-PE    7e360000-7e373000    \               cabinet
ELF    7e373000-7e39b000    Deferred        mpr<elf>
  \-PE    7e380000-7e39b000    \               mpr
ELF    7e39b000-7e3b2000    Deferred        libz.so.1
ELF    7e3b2000-7e42f000    Deferred        wininet<elf>
  \-PE    7e3c0000-7e42f000    \               wininet
ELF    7e42f000-7e4d4000    Deferred        urlmon<elf>
  \-PE    7e440000-7e4d4000    \               urlmon
ELF    7e4d4000-7e5d6000    Deferred        msi<elf>
  \-PE    7e4e0000-7e5d6000    \               msi
ELF    7e5d6000-7e715000    Deferred        oleaut32<elf>
  \-PE    7e5f0000-7e715000    \               oleaut32
ELF    7e715000-7e79a000    Deferred        rpcrt4<elf>
  \-PE    7e720000-7e79a000    \               rpcrt4
ELF    7e79a000-7e8dc000    Deferred        ole32<elf>
  \-PE    7e7b0000-7e8dc000    \               ole32
ELF    7e8dc000-7e9e7000    Deferred        comctl32<elf>
  \-PE    7e8e0000-7e9e7000    \               comctl32
ELF    7e9e7000-7ea60000    Deferred        shlwapi<elf>
  \-PE    7e9f0000-7ea60000    \               shlwapi
ELF    7ea60000-7ec93000    Deferred        shell32<elf>
  \-PE    7ea70000-7ec93000    \               shell32
ELF    7ec93000-7ecad000    Deferred        version<elf>
  \-PE    7eca0000-7ecad000    \               version
ELF    7ecad000-7edc9000    Deferred        gdi32<elf>
  \-PE    7ecc0000-7edc9000    \               gdi32
ELF    7edc9000-7ef2a000    Deferred        user32<elf>
  \-PE    7ede0000-7ef2a000    \               user32
ELF    7ef2a000-7ef9b000    Deferred        advapi32<elf>
  \-PE    7ef40000-7ef9b000    \               advapi32
ELF    7ef9b000-7efa8000    Deferred        libnss_files.so.2
ELF    7efa8000-7efeb000    Deferred        libm.so.6
ELF    7efec000-7f000000    Deferred        psapi<elf>
  \-PE    7eff0000-7f000000    \               psapi
ELF    f747a000-f747f000    Deferred        libdl.so.2
ELF    f7490000-f7494000    Deferred        libxau.so.6
ELF    f7494000-f7643000    Dwarf           libc.so.6
ELF    f7643000-f765e000    Deferred        libpthread.so.0
ELF    f765e000-f77a1000    Dwarf           libwine.so.1
ELF    f77a2000-f77c4000    Deferred        ld-linux.so.2
ELF    f77c4000-f77c5000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 Steam.exe
    00000054    0
    00000052    0
    0000004b    0
    00000028    0
    00000030    0
    00000031    0
    00000027    0
    00000032    0
    0000001f    0
    00000016    0
    00000039    0
    00000038    0
    00000036    0
    00000035    0
    0000000b    0
    00000013    0
    00000021    0
    00000020    0
    0000001d    0
    0000001c    0
    0000001b    0
    0000001a    0
    00000019    0
    00000018    0
    00000017    0
    0000000d    0
    00000047    0
    00000046    0
    00000045    0
    00000044    0
    00000043    0
    00000042    0
    00000041    0
    00000040    0
    0000003f    0
    0000003e    0
    0000003d    0
    0000003c    0
    0000003b    0
    0000003a    0
    00000037    0
    00000034    0
    00000033    0
    00000009    0
0000000e services.exe
    0000002e    0
    0000002d    0
    00000025    0
    00000010    0
    0000000f    0
00000014 explorer.exe
    00000015    0
00000022 winedevice.exe
    00000029    0
    00000024    0
    00000023    0
0000002a plugplay.exe
    0000002f    0
    0000002c    0
    0000002b    0
00000055 steamservice.exe
    00000056    0
00000057 vcredist_x86.exe
    00000059    0
    00000058    0
0000005a (D) C:\c306634c9ead62a56114e0be\Setup.exe
    0000005b    0 <==
System information:
    Wine build: wine-1.5.27

```

I hope someone will figure out how to make it work... :-)

---

### Post by ViliX64 on 2013-04-10
Well, it works (installing as AoE2 on PlayOnLinux) BUT what does not work is the very game (the active screen in the game, when you build buildings, troops etc..)

---

### Post by Voliax on 2013-04-24
I tried to run it like Windows 8 R2 & Windows 7 & XP mode on Wine. Menu is working fine but the game background is just a black screen.
 
Like this;
[[IMG=http://img16.imageshack.us/img16/4599/screenshotfrom201304250.png][/IMG]]("http://imageshack.us/photo/my-images/16/screenshotfrom201304250.png/")

If anyone knows how to solve this please help :(

---

### Post by SilFox on 2013-04-25
Found solution [HERE]("http://steamcommunity.com/app/221380/discussions/2/828935361270250345/") 

> Only a few minor tweaks you need to do to make it work, this is assuming you have steam running through wine already.

1. Install game
2. cd to "drive_c/Program\ Files/Steam/steamapps/common/Age2HD/"
3. Rename the "Launcher.exe" to "Launcher.bak" and "AoK HD.exe" to "Launcher.exe"
4. Inside of steam, add "-nostartup" to the launch options.
5. If your cpu automatically downclocks, disable that. For me, it was "sudo cpupower frequency-set -g performance"
6. Run the game, note that it will take several minutes to start up as the VS2012 redistributal and the directx fail to install, but it will run.

---

