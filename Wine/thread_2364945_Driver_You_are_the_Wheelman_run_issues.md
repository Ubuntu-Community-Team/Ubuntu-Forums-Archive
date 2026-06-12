---
title: "Driver: You are the Wheelman run issues"
date: 2017-06-30
forum: Wine
---

### Post by rotorspec on 2017-06-30
I was wondering if any one can help with my problem. I installed the game Driver, using WineTricks, with no problem. Trying to launch game.exe results with this error log:

```
Unhandled exception: inexact float result in 32-bit code (0x7ef97e43).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7ef97e43 ESP:0033ef24 EBP:0033ef78 EFLAGS:00010202(  R- --  I   - - - )
 EAX:00000001 EBX:7eba0000 ECX:0033eed0 EDX:00000440
 ESI:0013e738 EDI:0033efb4
Stack dump:
0x0033ef24:  00000440 00330040 7eb618c3 00000000
0x0033ef34:  3fe00000 00000000 00000000 00000000
0x0033ef44:  00000000 00000000 00000000 00000000
0x0033ef54:  3fe00000 00000001 00000000 00000000
0x0033ef64:  7eb61846 0033ef90 7e19a000 7e187b40
0x0033ef74:  0013e948 0033efc8 7e14126a 00000000
000c: sel=0067 base=00000000 limit=00000000 32-bit --x
Backtrace:
=>0 0x7ef97e43 floor+0x23() in libm.so.6 (0x0033ef78)
  1 0x7eb618c3 LPtoDP+0x92() in gdi32 (0x0033ef78)
  2 0x7e14126a in winex11 (+0x21269) (0x0033efc8)
  3 0x7e172b35 in winex11 (+0x52b34) (0x0033f0b8)
  4 0x7eb4ac42 in gdi32 (+0x5ac41) (0x0033f158)
  5 0x7eb601cd SelectObject+0xec() in gdi32 (0x0033f198)
  6 0x7eb09480 in gdi32 (+0x1947f) (0x0033f1c8)
  7 0x7eb14ff6 in gdi32 (+0x24ff5) (0x0033f638)
  8 0x7eb07602 __wine_set_visible_region+0xe1() in gdi32 (0x0033f688)
  9 0x7ec793ea in user32 (+0x693e9) (0x0033f7a8)
  10 0x7ec7a032 GetDCEx+0x471() in user32 (0x0033f7d8)
  11 0x7ec7a60e GetDC+0x4d() in user32 (0x0033f808)
  12 0x7ec3b1ba GetDialogBaseUnits+0x59() in user32 (0x0033f858)
  13 0x7ec3b5f6 in user32 (+0x2b5f5) (0x0033fb78)
  14 0x7ec3e158 DialogBoxIndirectParamAorW+0x37() in user32 (0x0033fba8)
  15 0x7ec3e202 DialogBoxIndirectParamW+0x31() in user32 (0x0033fbe8)
  16 0x7ec74e66 MessageBoxIndirectW+0x85() in user32 (0x0033fc48)
  17 0x7ec7519c MessageBoxIndirectA+0xbb() in user32 (0x0033fcd8)
  18 0x7ec752e5 MessageBoxExA+0x74() in user32 (0x0033fd38)
  19 0x7ec7533f MessageBoxA+0x2e() in user32 (0x0033fd78)
  20 0x005246a6 in game (+0x1246a5) (0x0033fd94)
  21 0x005243bd in game (+0x1243bc) (0x0033fdb0)
  22 0x00530533 in game (+0x130532) (0x0033fe40)
  23 0x7b85a3fc call_process_entry+0xb() in kernel32 (0x0033fe58)
  24 0x7b85b3ea ExitProcess+0xfe9() in kernel32 (0x0033fe88)
  25 0x7bc7703c call_thread_func_wrapper+0xb() in ntdll (0x0033fea8)
  26 0x7bc79e5d call_thread_func+0xfc() in ntdll (0x0033ffa8)
  27 0x7bc7701a RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  28 0x7bc4d277 call_dll_entry_point+0x756() in ntdll (0x0033ffe8)
  29 0xf758033d wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  30 0xf75804a0 wine_switch_to_stack+0x1f() in libwine.so.1 (0xffee91e8)
  31 0x7bc528d7 LdrInitializeThunk+0x336() in ntdll (0xffee9248)
  32 0x7b861029 __wine_kernel_init+0x888() in kernel32 (0xffeea3b8)
  33 0x7bc52e33 __wine_process_init+0x152() in ntdll (0xffeea428)
  34 0xf757ddff wine_init+0x30e() in libwine.so.1 (0xffeea488)
  35 0x7bf00d42 main+0x81() in <wine-loader> (0xffeea8d8)
  36 0xf739e637 __libc_start_main+0xf6() in libc.so.6 (0x00000000)
0x7ef97e43 floor+0x23 in libm.so.6: fldcw    0x4(%esp)
Modules:
Module    Address            Debug info    Name (69 modules)
PE      400000- 1332000    Export          game
ELF    7b800000-7ba54000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba54000    \               kernel32
ELF    7bc00000-7bcda000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcda000    \               ntdll
ELF    7bf00000-7bf04000    Dwarf           <wine-loader>
ELF    7dec4000-7dee8000    Deferred        imm32<elf>
  \-PE    7ded0000-7dee8000    \               imm32
ELF    7dee8000-7df1d000    Deferred        uxtheme<elf>
  \-PE    7def0000-7df1d000    \               uxtheme
ELF    7df1d000-7df24000    Deferred        libxfixes.so.3
ELF    7df24000-7df2f000    Deferred        libxcursor.so.1
ELF    7df2f000-7df42000    Deferred        libxi.so.6
ELF    7df42000-7df46000    Deferred        libxcomposite.so.1
ELF    7df46000-7df53000    Deferred        libxrandr.so.2
ELF    7df53000-7df5f000    Deferred        libxrender.so.1
ELF    7df5f000-7df66000    Deferred        libxxf86vm.so.1
ELF    7df66000-7df6a000    Deferred        libxinerama.so.1
ELF    7df6a000-7df71000    Deferred        libxdmcp.so.6
ELF    7df71000-7df75000    Deferred        libxau.so.6
ELF    7df75000-7df9b000    Deferred        libxcb.so.1
ELF    7df9b000-7e0e6000    Deferred        libx11.so.6
ELF    7e0e6000-7e0fb000    Deferred        libxext.so.6
ELF    7e118000-7e1a5000    Dwarf           winex11<elf>
  \-PE    7e120000-7e1a5000    \               winex11
ELF    7e21d000-7e247000    Deferred        libexpat.so.1
ELF    7e247000-7e290000    Deferred        libfontconfig.so.1
ELF    7e290000-7e2bb000    Deferred        libpng12.so.0
ELF    7e2bb000-7e2d6000    Deferred        libz.so.1
ELF    7e2d6000-7e386000    Deferred        libfreetype.so.6
ELF    7e3a3000-7e498000    Deferred        comctl32<elf>
  \-PE    7e3b0000-7e498000    \               comctl32
ELF    7e498000-7e4e1000    Deferred        dinput<elf>
  \-PE    7e4a0000-7e4e1000    \               dinput
ELF    7e4e1000-7e528000    Deferred        dsound<elf>
  \-PE    7e4f0000-7e528000    \               dsound
ELF    7e528000-7e646000    Deferred        opengl32<elf>
  \-PE    7e540000-7e646000    \               opengl32
ELF    7e646000-7e778000    Deferred        wined3d<elf>
  \-PE    7e650000-7e778000    \               wined3d
ELF    7e778000-7e7eb000    Deferred        ddraw<elf>
  \-PE    7e780000-7e7eb000    \               ddraw
ELF    7e7eb000-7e815000    Deferred        msacm32<elf>
  \-PE    7e7f0000-7e815000    \               msacm32
ELF    7e815000-7e8cd000    Deferred        winmm<elf>
  \-PE    7e820000-7e8cd000    \               winmm
ELF    7e8cd000-7e949000    Deferred        rpcrt4<elf>
  \-PE    7e8e0000-7e949000    \               rpcrt4
ELF    7e949000-7ea78000    Deferred        ole32<elf>
  \-PE    7e960000-7ea78000    \               ole32
ELF    7ea78000-7eae4000    Deferred        advapi32<elf>
  \-PE    7ea80000-7eae4000    \               advapi32
ELF    7eae4000-7ebfb000    Dwarf           gdi32<elf>
  \-PE    7eaf0000-7ebfb000    \               gdi32
ELF    7ebfb000-7ed49000    Dwarf           user32<elf>
  \-PE    7ec10000-7ed49000    \               user32
ELF    7ed49000-7ed5c000    Deferred        libnss_files.so.2
ELF    7ed5c000-7ed69000    Deferred        libnss_nis.so.2
ELF    7ed69000-7ed84000    Deferred        libnsl.so.1
ELF    7ed84000-7ed8e000    Deferred        libnss_compat.so.2
ELF    7ef8e000-7efe3000    Dwarf           libm.so.6
ELF    7efe7000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f7381000-f7386000    Deferred        libdl.so.2
ELF    f7386000-f753c000    Dwarf           libc.so.6
ELF    f753d000-f755a000    Deferred        libpthread.so.0
ELF    f7577000-f772c000    Dwarf           libwine.so.1
ELF    f772e000-f7753000    Deferred        ld-linux.so.2
ELF    f7755000-f7756000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000002f    0
    0000001d    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001c    0
    00000019    0
    00000017    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001f    0
    0000001b    0
00000021 explorer.exe
    00000023    0
    00000022    0
0000003d notepad.exe
    0000003e    0
00000042 (D) Z:\home\rotorspec\Desktop\Driver\Game.exe
    00000041    0 <==
System information:
    Wine build: wine-1.6.2
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 4.8.0-58-generic
```

Is this possibly due to running Ubuntu 16.04 64-bit, Nvidia issue, or Wine not wanting to play nice? Thanks!

---

### Post by howefield on 2017-06-30
Moved to the "*Wine*" forum.

---

### Post by sccman on 2017-07-07
It may be because your current Wine virtual drive is 64-bit when the game is 32-bit. Wine should be able to run 32-bit applications if ran in a 32-bit virtual drive. Try Croll's answer:

[https://askubuntu.com/questions/514931/trying-to-switch-to-32-bit-wineprefix-from-64-bit-wine-1-6-2-trusty-14-04](https://askubuntu.com/questions/514931/trying-to-switch-to-32-bit-wineprefix-from-64-bit-wine-1-6-2-trusty-14-04)

---

