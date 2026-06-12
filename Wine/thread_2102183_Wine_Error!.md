---
title: "Wine Error!"
date: 2013-01-06
forum: Wine
---

### Post by penguinprogrammer on 2013-01-06
Hey, I installed and attempted to run a windows game on wine. It showed the loading screen, then crashed and gave me this lengthy crash report:

```
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x004076bf).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:004076bf ESP:0032f9a8 EBP:062c4d90 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:7b895000 ECX:00000000 EDX:00000000
 ESI:0032fbfc EDI:062c4f6c
Stack dump:
0x0032f9a8:  00000000 0032fbf0 0032fbf0 00000002
0x0032f9b8:  00000254 00892744 00000483 0040806a
0x0032f9c8:  062c4d90 0032fe60 00885627 00000000
0x0032f9d8:  00402b90 0032fde0 cccccc00 505c3a43
0x0032f9e8:  72676f72 46206d61 73656c69 47454c5c
0x0032f9f8:  654d204f 5c616964 4f47454c 6c734920
Backtrace:
=>0 0x004076bf in lego island 2 (+0x76bf) (0x062c4d90)
0x004076bf: movl    0x0(%eax),%ecx
Modules:
Module    Address            Debug info    Name (117 modules)
PE      400000- 5e8a000    Export          lego island 2
PE    21100000-2115c000    Deferred        mss32
PE    22100000-22111000    Deferred        mssa3d.m3d
PE    22200000-22212000    Deferred        mssa3d2.m3d
PE    22300000-2230d000    Deferred        mssds3ds.m3d
PE    22400000-22411000    Deferred        mssds3dh.m3d
PE    22500000-22511000    Deferred        msseax.m3d
PE    22600000-22612000    Deferred        mssfast.m3d
PE    22700000-22713000    Deferred        mssdolby.m3d
PE    22900000-2290e000    Deferred        mssdx7sl.m3d
PE    22a00000-22a0e000    Deferred        mssdx7sh.m3d
PE    22b00000-22b0f000    Deferred        mssdx7sn.m3d
PE    22c00000-22c14000    Deferred        msseax2.m3d
PE    22d00000-22d5f000    Deferred        mssrsx.m3d
PE    24100000-2410a000    Deferred        lowpass.flt
PE    24200000-2420a000    Deferred        highpass.flt
PE    24300000-2430a000    Deferred        bandpass.flt
PE    24400000-2440a000    Deferred        reverb1.flt
PE    24500000-2450d000    Deferred        reverb2.flt
PE    24600000-2460e000    Deferred        reverb3.flt
PE    24700000-2470a000    Deferred        reson.flt
PE    24800000-2480d000    Deferred        phaser.flt
PE    24900000-2490a000    Deferred        parmeq.flt
PE    24a00000-24a0a000    Deferred        mdelay.flt
PE    24b00000-24b0b000    Deferred        sdelay.flt
PE    24c00000-24c0a000    Deferred        ringmod.flt
PE    24d00000-24d0a000    Deferred        flange.flt
PE    24e00000-24e0a000    Deferred        chorus.flt
PE    24f00000-24f0d000    Deferred        shelfeq.flt
PE    25100000-2510a000    Deferred        compress.flt
PE    25200000-2520a000    Deferred        autopan.flt
PE    25300000-2530a000    Deferred        laginter.flt
PE    25400000-25408000    Deferred        capture.flt
PE    26400000-2642a000    Deferred        mssv29.asi
PE    26500000-26522000    Deferred        mssv24.asi
PE    26600000-26625000    Deferred        mssv12.asi
PE    26f00000-26f26000    Deferred        mp3dec.asi
ELF    7b800000-7ba29000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba29000    \               kernel32
ELF    7bc00000-7bcc3000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c775000-7c7b8000    Deferred        dinput<elf>
  \-PE    7c780000-7c7b8000    \               dinput
ELF    7d9ef000-7d9fa000    Deferred        libpciaccess.so.0
ELF    7d9fa000-7da18000    Deferred        libgcc_s.so.1
ELF    7dbf2000-7dc14000    Deferred        libdrm_intel.so.1
ELF    7dc14000-7dfb2000    Deferred        libdricore9.0.0.so.1
ELF    7dfb2000-7e079000    Deferred        i965_dri.so
ELF    7e079000-7e091000    Deferred        libxcb-glx.so.0
ELF    7e091000-7e0a7000    Deferred        libglapi.so.0
ELF    7e112000-7e170000    Deferred        libgl.so.1
ELF    7e1b6000-7e1ea000    Deferred        uxtheme<elf>
  \-PE    7e1c0000-7e1ea000    \               uxtheme
ELF    7e1ea000-7e1f1000    Deferred        libxfixes.so.3
ELF    7e1f1000-7e1fc000    Deferred        libxcursor.so.1
ELF    7e205000-7e212000    Deferred        libdrm.so.2
ELF    7e266000-7e28e000    Deferred        libexpat.so.1
ELF    7e28e000-7e2c6000    Deferred        libfontconfig.so.1
ELF    7e2c6000-7e2d6000    Deferred        libxi.so.6
ELF    7e2d6000-7e2e1000    Deferred        libxrandr.so.2
ELF    7e2e1000-7e2eb000    Deferred        libxrender.so.1
ELF    7e2eb000-7e2f1000    Deferred        libxxf86vm.so.1
ELF    7e2f1000-7e313000    Deferred        imm32<elf>
  \-PE    7e300000-7e313000    \               imm32
ELF    7e313000-7e335000    Deferred        libxcb.so.1
ELF    7e335000-7e33b000    Deferred        libuuid.so.1
ELF    7e33b000-7e355000    Deferred        libice.so.6
ELF    7e355000-7e48b000    Deferred        libx11.so.6
ELF    7e48b000-7e49d000    Deferred        libxext.so.6
ELF    7e49d000-7e4a6000    Deferred        libsm.so.6
ELF    7e4a8000-7e4b1000    Deferred        librt.so.1
ELF    7e4be000-7e552000    Deferred        winex11<elf>
  \-PE    7e4d0000-7e552000    \               winex11
ELF    7e552000-7e56b000    Deferred        libz.so.1
ELF    7e56b000-7e605000    Deferred        libfreetype.so.6
ELF    7e605000-7e62d000    Deferred        msacm32<elf>
  \-PE    7e610000-7e62d000    \               msacm32
ELF    7e62d000-7e6da000    Deferred        winmm<elf>
  \-PE    7e630000-7e6da000    \               winmm
ELF    7e6da000-7e6f6000    Deferred        dinput8<elf>
  \-PE    7e6e0000-7e6f6000    \               dinput8
ELF    7e6f6000-7e82a000    Deferred        wined3d<elf>
  \-PE    7e700000-7e82a000    \               wined3d
ELF    7e82a000-7e892000    Deferred        ddraw<elf>
  \-PE    7e830000-7e892000    \               ddraw
ELF    7e892000-7e98b000    Deferred        comctl32<elf>
  \-PE    7e8a0000-7e98b000    \               comctl32
ELF    7e98b000-7ea01000    Deferred        rpcrt4<elf>
  \-PE    7e9a0000-7ea01000    \               rpcrt4
ELF    7ea01000-7eb08000    Deferred        ole32<elf>
  \-PE    7ea20000-7eb08000    \               ole32
ELF    7eb08000-7eb21000    Deferred        version<elf>
  \-PE    7eb10000-7eb21000    \               version
ELF    7eb21000-7eb83000    Deferred        advapi32<elf>
  \-PE    7eb30000-7eb83000    \               advapi32
ELF    7eb83000-7ec40000    Deferred        gdi32<elf>
  \-PE    7eb90000-7ec40000    \               gdi32
ELF    7ec40000-7ed80000    Deferred        user32<elf>
  \-PE    7ec50000-7ed80000    \               user32
ELF    7ef80000-7ef8d000    Deferred        libnss_files.so.2
ELF    7ef8d000-7ef99000    Deferred        libnss_nis.so.2
ELF    7ef99000-7efb3000    Deferred        libnsl.so.1
ELF    7efb3000-7efbc000    Deferred        libnss_compat.so.2
ELF    7efbc000-7efe8000    Deferred        libm.so.6
ELF    7efea000-7efed000    Deferred        libx11-xcb.so.1
ELF    7efed000-7eff1000    Deferred        libxdamage.so.1
ELF    7eff1000-7eff5000    Deferred        libxcomposite.so.1
ELF    7eff5000-7eff9000    Deferred        libxinerama.so.1
ELF    7eff9000-7f000000    Deferred        libxdmcp.so.6
ELF    b73f0000-b73f4000    Deferred        libxau.so.6
ELF    b73f5000-b73fa000    Deferred        libdl.so.2
ELF    b73fa000-b75a4000    Deferred        libc.so.6
ELF    b75a5000-b75c0000    Deferred        libpthread.so.0
ELF    b75d8000-b771a000    Dwarf           libwine.so.1
ELF    b771c000-b773e000    Deferred        ld-linux.so.2
ELF    b773e000-b773f000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\LEGO Media\LEGO Island 2\LEGO Island 2.exe
    00000024    0
    00000009    0 <==
0000000e services.exe
    0000001f    0
    0000001e    0
    00000019    0
    00000018    0
    00000017    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    00000020    0
    0000001a    0
    00000014    0
    00000013    0
0000001b plugplay.exe
    00000021    0
    0000001d    0
    0000001c    0
00000022 explorer.exe
    00000023    0
System information:
    Wine build: wine-1.4.1
    Platform: i386
    Host system: Linux
    Host version: 3.5.0-21-generic
```

If anyone knows what this means please tell me,
Thanks. :confused:

---

### Post by Calinou on 2013-01-06
Don't tell us which game it is! Spoiler alert! :)

---

### Post by Toz on 2013-01-06
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=6130]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=6130")
^^^
Doesn't look promising.

Moving this thread to the Wine section.

---

### Post by penguinprogrammer on 2013-01-06
OK, on Wine HQ, They rate it garbage because it doesn't run. Oh well :(
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=6130](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6130)

---

