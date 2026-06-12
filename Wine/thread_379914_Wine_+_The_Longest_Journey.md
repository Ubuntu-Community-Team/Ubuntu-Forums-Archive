---
title: "Wine + The Longest Journey"
date: 2007-03-09
forum: Wine
---

### Post by Chicken001 on 2007-03-09
Okay. I've searched for hours, since I woke up, until I now (12 hours or so). 

I've been digging from Canada to Russia trying to frickin' get this game running. The game is The Longest Journey, not Dreamfall, the first game.

I'm trying to use Wine to get it running, I have compiled and installed Wine Successfully, added whole bunch of .DLLs afterwards because nothing worked. Followed thousands of trouble-shooting guides. No luck.

So basically, I am stumped. I have compiled Wine through the quick "wineinstall" function. It worked, a huge smile shined upon my face, I installed The Longest Journey, no problems. It finished with ease. I installed DirectX (not 9.0 because I couldn't get it working, an older version of DirectX said I already had an updated version so sure, what-ever). 

I launched the game and... A dialog box came up, "A DirectDraw related error occurred." I stumbled out of the chair and a dark cloud came above my head. 

Anyways, I ran it through the Terminal.
The following message is shown:

```
chicken001@chicken001:~$ cd '/home/chicken001/.wine/drive_c/Program Files/Funcom/The Longest Journey' 
chicken001@chicken001:~/.wine/drive_c/Program Files/Funcom/The Longest Journey$ sudo wine game.exe
err:ddraw:DDRAW_Create Couldn't load WineD3D - OpenGL libs not present?
wine: Unhandled page fault on read access to 0xfffffff4 at address 0x421eb9 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0xfffffff4 in 32-bit code (0x00421eb9).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00421eb9 ESP:0033e5b4 EBP:0033e63c EFLAGS:00210216(   - 00      -RIAP1)
 EAX:00000000 EBX:7ebfc5b4 ECX:fffffffd EDX:fffffff3
 ESI:0033f264 EDI:0001002a
Stack dump:
0x0033e5b4:  0033f264 00421d3d 00000000 00000000
0x0033e5c4:  00000000 0016bd28 0016bb48 0016bb98
0x0033e5d4:  00000000 000000a8 80000001 0016bb48
0x0033e5e4:  6c40deec 001b9284 001b929c 00000003
0x0033e5f4:  001b92a8 001b9280 0000000a 0033e850
0x0033e604:  0042c060 00000003 6c3bbe10 7ebd7a8a
Backtrace:
=>1 0x00421eb9 in game (+0x21eb9) (0x0033e63c)
  2 0x7ebd9998 call_dialog_proc+0x68(hwnd=<register EDI not in topmost frame>, msg=0x110, wp=0x0, lp=0x0, result=0x33e6ac, arg=0x6c3bbde2) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/winproc.c:474] in user32 (0x0033e67c)
  3 0x7ebdc06a WINPROC_CallDlgProcA+0x5a(func=0xffff0021, hwnd=0x1002a, msg=<register EDI not in topmost frame>, wParam=0x0, lParam=0x0) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/winproc.c:2322] in user32 (0x0033e6bc)
  4 0x7eb6cf1a DefDlgProcA+0x8a(hwnd=<register ESI not in topmost frame>, msg=<register EDI not in topmost frame>, wParam=0x0, lParam=0x0) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/defdlg.c:437] in user32 (0x0033e6ec)
  5 0x7ebd7a8a WINPROC_wrapper+0x1a() in user32 (0x0033e71c)
  6 0x7ebd821e call_window_proc+0x6e(hwnd=<register EDI not in topmost frame>, msg=0x110, wp=0x0, lp=0x0, result=0x33e78c, arg=0x7eb6ce90) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/winproc.c:452] in user32 (0x0033e75c)
  7 0x7ebdc17a CallWindowProcA+0x5a(func=0x7eb6ce90, hwnd=0x1002a, msg=<register EDI not in topmost frame>, wParam=<register ESI not in topmost frame>, lParam=0x0) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/winproc.c:2232] in user32 (0x0033e79c)
  8 0x6c3b9330 in mfc42 (+0x49330) (0x0033e7bc)
  9 0x6c3b89ab in mfc42 (+0x489ab) (0x0033e85c)
  10 0x6c3b99d5 in mfc42 (+0x499d5) (0x0033e87c)
  11 0x6c3b88ee in mfc42 (+0x488ee) (0x0033e8dc)
  12 0x6c3b8afb in mfc42 (+0x48afb) (0x0033e8fc)
  13 0x6c3e13a8 in mfc42 (+0x713a8) (0x0033e928)
  14 0x7ebd7a8a WINPROC_wrapper+0x1a() in user32 (0x0033e958)
  15 0x7ebd821e call_window_proc+0x6e(hwnd=<register EDI not in topmost frame>, msg=0x110, wp=0x0, lp=0x0, result=0x33ee9c, arg=0x6c3e136f) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/winproc.c:452] in user32 (0x0033e998)
  16 0x7ebdc8db WINPROC_CallProcWtoA+0x61b(callback=0x7ebd81b0, hwnd=0x1002a, msg=<register EDI not in topmost frame>, wParam=0x0, lParam=0x0, result=0x33ee9c, arg=0x6c3e136f) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/winproc.c:1259] in user32 (0x0033ee68)
  17 0x7ebdd4aa CallWindowProcW+0xaa(func=0xffff000d, hwnd=0x1002a, msg=0x110, wParam=<register ESI not in topmost frame>, lParam=0x0) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/winproc.c:2254] in user32 (0x0033eea8)
  18 0x7eba4818 call_window_proc+0x178(hwnd=<register ESI not in topmost frame>, msg=0x110, wparam=0x0, lparam=0x0, unicode=0x1, same_thread=0x1) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/message.c:1542] in user32 (0x0033ef18)
  19 0x7eba85b0 SendMessageTimeoutW+0x1a0(hwnd=<register ESI not in topmost frame>, msg=0x110, wparam=0x0, lparam=<register EDI not in topmost frame>, flags=0x0, timeout=0x0, res_ptr=0x33efc0) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/message.c:2404] in user32 (0x0033ef88)
  20 0x7eba8620 SendMessageW+0x50(hwnd=0x1002a, msg=0x110, wparam=0x0, lparam=0x0) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/message.c:2490] in user32 (0x0033efc8)
  21 0x7eb7246b DIALOG_CreateIndirect+0xadb(hInst=0x400000, dlgTemplate=<is not available>, owner=<is not available>, dlgProc=0x6c3bbde2, param=0x0, unicode=0x0, modal=0x0) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/dialog.c:663] in user32 (0x0033f148)
  22 0x7eb73506 CreateDialogIndirectParamAorW+0x36(hInst=0x400000, dlgTemplate=0x4444d8, owner=0x10028, dlgProc=0x6c3bbde2, param=0x0, flags=0x2) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/dialog.c:722] in user32 (0x0033f168)
  23 0x7eb73631 CreateDialogIndirectParamA+0x41(hInst=0x400000, dlgTemplate=0x4444d8, owner=0x10028, dlgProc=0x6c3bbde2, param=0x0) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/dialog.c:731] in user32 (0x0033f198)
  24 0x6c3bc23d in mfc42 (+0x4c23d) (0x0033f200)
  25 0x6c3bc4e2 in mfc42 (+0x4c4e2) (0x0033f244)
  26 0x004199b0 in game (+0x199b0) (0x0033f518)
  27 0x6c3b99d5 in mfc42 (+0x499d5) (0x0033f538)
  28 0x6c3b88ee in mfc42 (+0x488ee) (0x0033f598)
  29 0x6c3b8afb in mfc42 (+0x48afb) (0x0033f5b8)
  30 0x6c3e13a8 in mfc42 (+0x713a8) (0x0033f5e4)
  31 0x7ebd7a8a WINPROC_wrapper+0x1a() in user32 (0x0033f614)
  32 0x7ebd821e call_window_proc+0x6e(hwnd=<register EDI not in topmost frame>, msg=0x1, wp=0x0, lp=0x33fbe4, result=0x33f684, arg=0x6c3e136f) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/winproc.c:452] in user32 (0x0033f654)
  33 0x7ebdc17a CallWindowProcA+0x5a(func=0x6c3e136f, hwnd=0x10028, msg=<register EDI not in topmost frame>, wParam=<register ESI not in topmost frame>, lParam=0x33fbe4) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/winproc.c:2232] in user32 (0x0033f694)
  34 0x7eba4789 call_window_proc+0xe9(hwnd=<register ESI not in topmost frame>, msg=0x1, wparam=0x0, lparam=0x33fbe4, unicode=0x0, same_thread=0x1) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/message.c:1547] in user32 (0x0033f704)
  35 0x7eba8312 SendMessageTimeoutA+0x202(hwnd=<register ESI not in topmost frame>, msg=0x1, wparam=0x0, lparam=0x33fbe4, flags=0x0, timeout=0x0, res_ptr=0x33f7ac) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/message.c:2462] in user32 (0x0033f774)
  36 0x7eba83d0 SendMessageA+0x50(hwnd=0x10028, msg=0x1, wparam=0x0, lparam=0x33fbe4) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/message.c:2501] in user32 (0x0033f7b4)
  37 0x7e71208a X11DRV_CreateWindow+0xa9a(hwnd=0x10028, cs=<register EDI not in topmost frame>, unicode=0x0) [/home/chicken001/downloads/wine-0.9.32/dlls/winex11.drv/window.c:1130] in winex11 (0x0033f944)
  38 0x7ebd16e3 WIN_CreateWindowEx+0x603(cs=0x33fbe4, classAtom=0xc026, flags=0x20) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/win.c:1080] in user32 (0x0033fba4)
  39 0x7ebd2f92 CreateWindowExA+0x102(exStyle=0x200, className=0x167688, windowName=0x16b828, style=0xc80000, x=0x80000000, y=0x80000000, width=0x80000000, height=0x80000000, parent=0x0, menu=0x50, instance=0x400000, data=0x0) [/home/chicken001/downloads/wine-0.9.32/dlls/user32/win.c:1236] in user32 (0x0033fd24)
  40 0x6c3b9057 in mfc42 (+0x49057) (0x0033fd94)
  41 0x6c3d1467 in mfc42 (+0x61467) (0x0033fdd4)
  42 0x6c3d1677 in mfc42 (+0x61677) (0x0033fe14)
  43 0x0040cf5a in game (+0xcf5a) (0x0033ff08)
  44 0x7ee5a10e start_process+0xee(arg=0x0) [/home/chicken001/downloads/wine-0.9.32/dlls/kernel32/process.c:820] in kernel32 (0x0033ffe8)
  45 0xb7ec9627 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x00421eb9: movl        0x28(%eax,%edx,4),%ecx
Modules:
Module  Address                 Debug info      Name (73 modules)
PE      340000-35b000   Deferred        smackw32
PE      360000-391000   Deferred        binkw32
PE      3a0000-3ad000   Deferred        l_module
PE      3b0000-3bc000   Deferred        s_module
PE      400000-469000   Export          game
PE      470000-4e8000   Deferred        w_module
PE      4f0000-57a000   Deferred        audiere
PE      10000000-103b5000       Deferred        dx_module
PE      6c370000-6c46b000       Export          mfc42
PE      780c0000-78121000       Deferred        msvcp60
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e4c8000-7e4fa000       Deferred        uxtheme<elf>
  \-PE  7e4d0000-7e4fa000       \               uxtheme
ELF     7e4fa000-7e5b7000       Deferred        comctl32<elf>
  \-PE  7e500000-7e5b7000       \               comctl32
ELF     7e5b7000-7e5cc000       Deferred        midimap<elf>
  \-PE  7e5c0000-7e5cc000       \               midimap
ELF     7e61c000-7e634000       Deferred        msacm32<elf>
  \-PE  7e620000-7e634000       \               msacm32
ELF     7e634000-7e670000       Deferred        wineoss<elf>
  \-PE  7e640000-7e670000       \               wineoss
ELF     7e670000-7e675000       Deferred        libxfixes.so.3
ELF     7e675000-7e67d000       Deferred        libxrender.so.1
ELF     7e67d000-7e686000       Deferred        libxcursor.so.1
ELF     7e686000-7e6a3000       Deferred        imm32<elf>
  \-PE  7e690000-7e6a3000       \               imm32
ELF     7e6a3000-7e6c1000       Deferred        ximcp.so.2
ELF     7e6c1000-7e73c000       Dwarf           winex11<elf>
  \-PE  7e6d0000-7e73c000       \               winex11
ELF     7e73c000-7e7a1000       Deferred        msvcrt<elf>
  \-PE  7e750000-7e7a1000       \               msvcrt
ELF     7e7a1000-7e7b4000       Deferred        libresolv.so.2
ELF     7e7b4000-7e7d2000       Deferred        iphlpapi<elf>
  \-PE  7e7c0000-7e7d2000       \               iphlpapi
ELF     7e7d2000-7e827000       Deferred        rpcrt4<elf>
  \-PE  7e7e0000-7e827000       \               rpcrt4
ELF     7e827000-7e8c2000       Deferred        ole32<elf>
  \-PE  7e840000-7e8c2000       \               ole32
ELF     7e8c2000-7e8c7000       Deferred        libxdmcp.so.6
ELF     7e8c7000-7e990000       Deferred        libx11.so.6
ELF     7e990000-7e99d000       Deferred        libxext.so.6
ELF     7e99d000-7e9b5000       Deferred        libice.so.6
ELF     7e9b5000-7e9be000       Deferred        libsm.so.6
ELF     7e9ce000-7ea1e000       Deferred        ddraw<elf>
  \-PE  7e9e0000-7ea1e000       \               ddraw
ELF     7ea1e000-7ea32000       Deferred        lz32<elf>
  \-PE  7ea20000-7ea32000       \               lz32
ELF     7ea32000-7ea4c000       Deferred        version<elf>
  \-PE  7ea40000-7ea4c000       \               version
ELF     7ea4c000-7ea92000       Deferred        advapi32<elf>
  \-PE  7ea60000-7ea92000       \               advapi32
ELF     7ea92000-7eb17000       Deferred        gdi32<elf>
  \-PE  7eaa0000-7eb17000       \               gdi32
ELF     7eb17000-7ec51000       Dwarf           user32<elf>
  \-PE  7eb30000-7ec51000       \               user32
ELF     7ec51000-7ecdf000       Deferred        winmm<elf>
  \-PE  7ec60000-7ecdf000       \               winmm
ELF     7ede9000-7ef11000       Dwarf           kernel32<elf>
  \-PE  7ee00000-7ef11000       \               kernel32
ELF     7ef11000-7ef1c000       Deferred        libnss_files.so.2
ELF     7ef1c000-7ef26000       Deferred        libnss_nis.so.2
ELF     7ef26000-7ef3c000       Deferred        libnsl.so.1
ELF     7ef3c000-7ef45000       Deferred        libnss_compat.so.2
ELF     7ef45000-7ef6b000       Deferred        libm.so.6
ELF     7ef6b000-7f000000       Deferred        ntdll<elf>
  \-PE  7ef80000-7f000000       \               ntdll
ELF     b7d60000-b7d62000       Deferred        xlcutf8load.so.2
ELF     b7d62000-b7d65000       Deferred        libxau.so.6
ELF     b7d67000-b7d6b000       Deferred        libdl.so.2
ELF     b7d6b000-b7e9f000       Deferred        libc.so.6
ELF     b7e9f000-b7eb2000       Deferred        libpthread.so.0
ELF     b7ec2000-b7fd3000       Dwarf           libwine.so.1
ELF     b7fd5000-b7ff0000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000b    0
00000008 (D) C:\Program Files\Funcom\The Longest Journey\game.exe
        00000009    0 <==

```

When I run, the command,
```
wineprefixcreate
```
It gives the following message, 
```
chicken001@chicken001:~/.wine/drive_c/Program Files/Funcom/The Longest Journey$ wineprefixcreate
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d8.dll") not found
/home/chicken001/.wine updated successfully.

```


If anyone can help me please do!
I've updated the everything basically. I'm stumped. :popcorn:

---

### Post by renzokuken on 2007-03-09
firstly you dont need to use sudo to run a game with wine

```
chicken001@chicken001: wine game.exe
```

is the usual way to run stuff with wine, (after cd'ing to the correct directory)

---

### Post by Pkadjipag on 2009-04-29
I know this is an old thread but i'd really like playing The Longest Journey so is someone could help me I'd be really grateful. 

I installed it through wine and everything worked perfectly. The game doesn't start and when I get it through the terminal... I get a bunch of errors. I downloaded the dll files they told me were missing.

---

