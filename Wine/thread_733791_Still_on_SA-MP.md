---
title: "Still on SA-MP"
date: 2008-03-24
forum: Wine
---

### Post by Morph-------------- on 2008-03-24
Ok so i got the SA-MP window working now (thanks to happyhamster)
But it doesn't seem to start GTA:SA in any way and i don't get it to work. I'm trying to start it through a mounted Windows partition but this is what i get in the terminal:

```
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
wine: Unhandled page fault on read access to 0x00000010 at address 0x7eacbb1d (thread 0010), starting debugger...
Unhandled exception: page fault on read access to 0x00000010 in 32-bit code (0x7eacbb1d).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7eacbb1d ESP:0178f2d4 EBP:0178f2fc EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7eb2c764 ECX:00000003 EDX:7eb4927c
 ESI:00000000 EDI:00000000
Stack dump:
0x0178f2d4:  7eb47860 00129bf8 0178f2fc 7bc401a1
0x0178f2e4:  0000001c 00020000 00129c88 7eb2c764
0x0178f2f4:  00129c00 00000000 0178f33c 7ead328b
0x0178f304:  00000003 7eb47244 7eb1c9f8 7eb1c674
0x0178f314:  0006006a 00000000 0178f33c 7eafd598
0x0178f324:  7eb478a0 0006006a 7ead326d 7eb2c764
Backtrace:
=>1 0x7eacbb1d CreateMenu+0x3d() [/build/buildd/wine-0.9.46/dlls/user32/user_private.h:39] in user32 (0x0178f2fc)
  2 0x7ead328b MENU_GetSysMenu+0x2b(hWnd=0x6006a, hPopupMenu=<register EDI not in topmost frame>) [/build/buildd/wine-0.9.46/dlls/user32/menu.c:448] in user32 (0x0178f33c)
  3 0x7ead35aa SetSystemMenu+0x4a(hwnd=<register EDI not in topmost frame>, hMenu=0x0) [/build/buildd/wine-0.9.46/dlls/user32/menu.c:4081] in user32 (0x0178f35c)
  4 0x7eb0275b WIN_CreateWindowEx+0x12fb(cs=0x178f5fc, classAtom=0xc058, flags=0x20) [/build/buildd/wine-0.9.46/dlls/user32/win.c:1007] in user32 (0x0178f5bc)
  5 0x7eb03312 CreateWindowExA+0x102(exStyle=0x0, className=0x7d38f69b, windowName=0x7d38f687, style=0xcf0000, x=0xa, y=0xa, width=0xa, height=0xa, parent=0x0, menu=0x0, instance=0x0, data=0x0) [/build/buildd/wine-0.9.46/dlls/user32/win.c:1235] in user32 (0x0178f73c)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
  6 0x7d31c607 InitAdapters+0x20c7() [/build/buildd/wine-0.9.46/dlls/wined3d/directx.c:218] in wined3d (0x0178fb5c)
  7 0x7d382312 WineDirect3DCreate+0x22(SDKVersion=0x0, dxVersion=0x7, parent=0x126490) [/build/buildd/wine-0.9.46/dlls/wined3d/wined3d_main.c:52] in wined3d (0x0178fb8c)
  8 0x7d4827e3 DDRAW_Create+0x283(guid=<is not available>, DD=0x178fc6c, UnkOuter=0x0, iid=0x859694) [/build/buildd/wine-0.9.46/dlls/ddraw/main.c:193] in ddraw (0x0178fbfc)
  9 0x7d4830ca DirectDrawCreateEx+0x10a(GUID=0x0, DD=0x178fc6c, iid=0x859694, UnkOuter=0x0) [/build/buildd/wine-0.9.46/dlls/ddraw/main.c:383] in ddraw (0x0178fc4c)
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature 088d8601 in module L"gta_sa"
  10 0x007456af in gta_sa (+0x3456af) (0x7b866120)
  11 0xfb0f6ee8 (0x53e58955)
  12 0x00000000 (0x00000000)
0x7eacbb1d CreateMenu+0x3d [/build/buildd/wine-0.9.46/dlls/user32/user_private.h:39] in user32: movzwl  0x10(%esi),%edi
Unable to open file '/build/buildd/wine-0.9.46/dlls/user32/user_private.h'
Modules:
Module  Address                 Debug info      Name (73 modules)
PE        360000-  371000       Deferred        vorbisfile
PE        380000-  389000       Deferred        ogg
PE        390000-  3c0000       Deferred        eax
PE        400000- 1577000       Export          gta_sa
PE       18a0000- 19a8000       Deferred        vorbis
PE      10000000-10070000       Deferred        samp
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d2cc000-7d3ac000       Dwarf           wined3d<elf>
  \-PE  7d2e0000-7d3ac000       \               wined3d
ELF     7d451000-7d4a6000       Dwarf           ddraw<elf>
  \-PE  7d460000-7d4a6000       \               ddraw
ELF     7d4a6000-7d4cd000       Deferred        msacm32<elf>
  \-PE  7d4b0000-7d4cd000       \               msacm32
ELF     7d4cd000-7d526000       Deferred        rpcrt4<elf>
  \-PE  7d4e0000-7d526000       \               rpcrt4
ELF     7d526000-7d5c7000       Deferred        ole32<elf>
  \-PE  7d540000-7d5c7000       \               ole32
ELF     7d5c7000-7d655000       Deferred        winmm<elf>
  \-PE  7d5d0000-7d655000       \               winmm
ELF     7d65b000-7d670000       Deferred        midimap<elf>
  \-PE  7d660000-7d670000       \               midimap
ELF     7d670000-7d6aa000       Deferred        wineoss<elf>
  \-PE  7d680000-7d6aa000       \               wineoss
ELF     7d6aa000-7d6af000       Deferred        libxfixes.so.3
ELF     7d6af000-7d6b8000       Deferred        libxcursor.so.1
ELF     7d6b8000-7d6d5000       Deferred        imm32<elf>
  \-PE  7d6c0000-7d6d5000       \               imm32
ELF     7d6d5000-7d6db000       Deferred        libxrandr.so.2
ELF     7d6db000-7d6e3000       Deferred        libxrender.so.1
ELF     7dc8d000-7dc8f000       Deferred        libnvidia-tls.so.1
ELF     7dc8f000-7e627000       Deferred        libglcore.so.1
ELF     7e627000-7e6bd000       Deferred        libgl.so.1
ELF     7e6bd000-7e6c2000       Deferred        libxdmcp.so.6
ELF     7e6c2000-7e6c5000       Deferred        libxau.so.6
ELF     7e6c5000-7e7b6000       Deferred        libx11.so.6
ELF     7e7b6000-7e7c4000       Deferred        libxext.so.6
ELF     7e7c4000-7e7c9000       Deferred        libxxf86vm.so.1
ELF     7e7c9000-7e7e1000       Deferred        libice.so.6
ELF     7e7e1000-7e7e9000       Deferred        libsm.so.6
ELF     7e7f8000-7e883000       Deferred        winex11<elf>
  \-PE  7e810000-7e883000       \               winex11
ELF     7e8d9000-7e8f9000       Deferred        libexpat.so.1
ELF     7e8f9000-7e924000       Deferred        libfontconfig.so.1
ELF     7e924000-7e939000       Deferred        libz.so.1
ELF     7e939000-7e9a9000       Deferred        libfreetype.so.6
ELF     7e9a9000-7ea44000       Deferred        gdi32<elf>
  \-PE  7e9c0000-7ea44000       \               gdi32
ELF     7ea44000-7eb82000       Dwarf           user32<elf>
  \-PE  7ea60000-7eb82000       \               user32
ELF     7eb88000-7eba0000       Deferred        msacm32<elf>
  \-PE  7eb90000-7eba0000       \               msacm32
ELF     7eba0000-7ebb3000       Deferred        libresolv.so.2
ELF     7ebb3000-7ebd1000       Deferred        iphlpapi<elf>
  \-PE  7ebc0000-7ebd1000       \               iphlpapi
ELF     7ebd1000-7ebfe000       Deferred        ws2_32<elf>
  \-PE  7ebe0000-7ebfe000       \               ws2_32
ELF     7ebfe000-7ec09000       Deferred        libgcc_s.so.1
ELF     7ec18000-7ec61000       Deferred        advapi32<elf>
  \-PE  7ec20000-7ec61000       \               advapi32
ELF     7ee72000-7ee7d000       Deferred        libnss_files.so.2
ELF     7ee7d000-7ee95000       Deferred        libnsl.so.1
ELF     7ee95000-7ee9e000       Deferred        libnss_compat.so.2
ELF     7efcc000-7eff1000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7c5b000-b7c5f000       Deferred        libdl.so.2
ELF     b7c5f000-b7da9000       Deferred        libc.so.6
ELF     b7daa000-b7dc2000       Deferred        libpthread.so.0
ELF     b7dd1000-b7ee5000       Deferred        libwine.so.1
ELF     b7ee7000-b7f03000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000f (D) C:\Rockstar Games\GTA San Andreas\gta_sa.exe
        00000012    0
        00000010    0 <==
0000000a 
        0000000c    0
        0000000b    0
00000008 
        00000009    0

```

Well it seems to start GTA maybe but it certainly doesn't, any help on this?

Wine version: wine-0.9.46

---

