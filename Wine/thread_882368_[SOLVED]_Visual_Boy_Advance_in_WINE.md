---
title: "[SOLVED] Visual Boy Advance in WINE?"
date: 2008-08-06
forum: Wine
---

### Post by Syndacate on 2008-08-06
Hey,

Does anybody know how to get Visual Boy Advance to work in WiNE?

I mean the Visual Boy Advance for Linux is pathetic - save/load state works when it wants to, the menus are all ***-backwards, windows don't shut down, games don't open up, weird errors happen, the list just goes on and on.

So I tried using WINE to run the Windows version.

It threw a DLL error on MFC42.DLL and then after I put that into the exectuable's directory it threw an error on MSVCP60.DLL - so I downloaded that into the directory, now I'm getting a new error when I go to open a game..and I can't fix this one.

Any help?

```

$ wine /home/syndacate/.wine/drive_c/Emu/VisualBoyAdvance.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x32ecc4,0x00000000), stub!

<main window is running>

<then I click on "File" >> "Open">

wine: Call from 0x5275ca to unimplemented function MFC42.DLL.6876, aborting
wine: Unimplemented function MFC42.DLL.6876 called at address 0x5275ca (thread 0009), starting debugger...
Unhandled exception: unimplemented function MFC42.DLL.6876 called in 32-bit code (0x7bc451ec).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc451ec ESP:0032f9f0 EBP:0032fa54 EFLAGS:00000206(   - 00      - -IP1)
 EAX:00001adc EBX:7bc88444 ECX:0032faac EDX:0032faac
 ESI:0032f9fc EDI:00147ed8
Stack dump:
0x0032f9f0:  00000006 00139d10 5f40889a 80000100
0x0032fa00:  00000001 00000000 005275ca 00000002
0x0032fa10:  00592d84 00001adc 0053dc50 00000045
0x0032fa20:  00000006 0032faac 0032fa5c 0053dd4a
0x0032fa30:  00000445 00000000 00147ed8 00147ed8
0x0032fa40:  00000001 00000445 7bc6773b 00000001
Backtrace:
=>1 0x7bc451ec in ntdll (+0x351ec) (0x0032fa54)
  2 0x005275ca in visualboyadvance (+0x1275ca) (0x0032fa8c)
  3 0x005256dc in visualboyadvance (+0x1256dc) (0x0032fb4c)
  4 0x0052bd44 in visualboyadvance (+0x12bd44) (0x0032fb64)
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file "MFC42.dbg" ("")
  5 0x5f4039db in mfc42 (+0x39db) (0x0032fb94)
  6 0x5f411e08 in mfc42 (+0x11e08) (0x0032fbe4)
  7 0x5f4023ed in mfc42 (+0x23ed) (0x0032fc64)
  8 0x5f40230b in mfc42 (+0x230b) (0x0032fc84)
  9 0x5f402294 in mfc42 (+0x2294) (0x0032fce4)
  10 0x5f40221f in mfc42 (+0x221f) (0x0032fd00)
  11 0x5f4021d6 in mfc42 (+0x21d6) (0x0032fd2c)
  12 0x7ec865ba WINPROC_wrapper+0x1a() in user32 (0x0032fd5c)
  13 0x7ec86c9e WINPROC_wrapper+0x6fe() in user32 (0x0032fd9c)
  14 0x7ec8c071 in user32 (+0xac071) (0x0032fddc)
  15 0x7ec4e826 DispatchMessageA+0x96() in user32 (0x0032fe1c)
  16 0x5f40133b in mfc42 (+0x133b) (0x0060af34)
  17 0x00000111 (0x0001002a)
0x7bc451ec: subl        $4,%esp
Modules:
Module  Address                 Debug info      Name (113 modules)
PE        400000-  7d8000       Export          visualboyadvance
PE      5f400000-5f4ed000       Export          mfc42
ELF     7b800000-7b92d000       Deferred        kernel32<elf>
  \-PE  7b820000-7b92d000       \               kernel32
ELF     7bc00000-7bca4000       Export          ntdll<elf>
  \-PE  7bc10000-7bca4000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c38a000-7c48d000       Deferred        wined3d<elf>
  \-PE  7c3a0000-7c48d000       \               wined3d
ELF     7c48d000-7c4e4000       Deferred        ddraw<elf>
  \-PE  7c4a0000-7c4e4000       \               ddraw
ELF     7c5f5000-7c62c000       Deferred        dinput<elf>
  \-PE  7c600000-7c62c000       \               dinput
ELF     7c62c000-7c630000       Deferred        libgpg-error.so.0
ELF     7c630000-7c67d000       Deferred        libgcrypt.so.11
ELF     7c67d000-7c68d000       Deferred        libtasn1.so.3
ELF     7c68d000-7c690000       Deferred        libkeyutils.so.1
ELF     7c690000-7c698000       Deferred        libkrb5support.so.0
ELF     7c698000-7c6ca000       Deferred        libcrypt.so.1
ELF     7c6ca000-7c740000       Deferred        libgnutls.so.13
ELF     7c740000-7c763000       Deferred        libk5crypto.so.3
ELF     7c763000-7c7f0000       Deferred        libkrb5.so.3
ELF     7c7f0000-7c819000       Deferred        libgssapi_krb5.so.2
ELF     7ca90000-7cac3000       Deferred        libcups.so.2
ELF     7cb09000-7cb0c000       Deferred        libcom_err.so.2
ELF     7d4d9000-7d50c000       Deferred        uxtheme<elf>
  \-PE  7d4e0000-7d50c000       \               uxtheme
ELF     7d50c000-7d520000       Deferred        midimap<elf>
  \-PE  7d510000-7d520000       \               midimap
ELF     7d520000-7d5e3000       Deferred        libasound.so.2
ELF     7d5e3000-7d619000       Deferred        winealsa<elf>
  \-PE  7d5f0000-7d619000       \               winealsa
ELF     7d619000-7d622000       Deferred        libxcursor.so.1
ELF     7d622000-7d627000       Deferred        libxfixes.so.3
ELF     7d627000-7d62a000       Deferred        libxcomposite.so.1
ELF     7d62a000-7d630000       Deferred        libxrandr.so.2
ELF     7d630000-7d638000       Deferred        libxrender.so.1
ELF     7d638000-7d63b000       Deferred        libxinerama.so.1
ELF     7d63b000-7d652000       Deferred        msacm32<elf>
  \-PE  7d640000-7d652000       \               msacm32
ELF     7d652000-7d672000       Deferred        imm32<elf>
  \-PE  7d660000-7d672000       \               imm32
ELF     7d672000-7d709000       Deferred        winex11<elf>
  \-PE  7d680000-7d709000       \               winex11
ELF     7d753000-7d774000       Deferred        libexpat.so.1
ELF     7d774000-7d79e000       Deferred        libfontconfig.so.1
ELF     7d79e000-7d80e000       Deferred        libfreetype.so.6
ELF     7d825000-7d85b000       Deferred        winspool<elf>
  \-PE  7d830000-7d85b000       \               winspool
ELF     7d85b000-7d8b4000       Deferred        shlwapi<elf>
  \-PE  7d870000-7d8b4000       \               shlwapi
ELF     7d8b4000-7d9c7000       Deferred        shell32<elf>
  \-PE  7d8c0000-7d9c7000       \               shell32
ELF     7d9c7000-7da72000       Deferred        comdlg32<elf>
  \-PE  7d9d0000-7da72000       \               comdlg32
ELF     7da72000-7dadc000       Deferred        msvcrt<elf>
  \-PE  7da80000-7dadc000       \               msvcrt
ELF     7db40000-7db45000       Deferred        libxdmcp.so.6
ELF     7db45000-7db47000       Deferred        libnvidia-tls.so.1
ELF     7db47000-7e65c000       Deferred        libglcore.so.1
ELF     7e65c000-7e674000       Deferred        libxcb.so.1
ELF     7e674000-7e718000       Deferred        libgl.so.1
ELF     7e718000-7e7ff000       Deferred        libx11.so.6
ELF     7e7ff000-7e80d000       Deferred        libxext.so.6
ELF     7e80d000-7e825000       Deferred        libice.so.6
ELF     7e825000-7e83a000       Deferred        libz.so.1
ELF     7e83c000-7e8bd000       Deferred        opengl32<elf>
  \-PE  7e850000-7e8bd000       \               opengl32
ELF     7e8bd000-7e91e000       Deferred        rpcrt4<elf>
  \-PE  7e8d0000-7e91e000       \               rpcrt4
ELF     7e91e000-7e9c2000       Deferred        ole32<elf>
  \-PE  7e930000-7e9c2000       \               ole32
ELF     7e9c2000-7ea81000       Deferred        comctl32<elf>
  \-PE  7e9d0000-7ea81000       \               comctl32
ELF     7ea81000-7ea9a000       Deferred        version<elf>
  \-PE  7ea90000-7ea9a000       \               version
ELF     7ea9a000-7eac2000       Deferred        msvfw32<elf>
  \-PE  7eaa0000-7eac2000       \               msvfw32
ELF     7eac2000-7eae8000       Deferred        msacm32<elf>
  \-PE  7ead0000-7eae8000       \               msacm32
ELF     7eae8000-7eb23000       Deferred        avifil32<elf>
  \-PE  7eaf0000-7eb23000       \               avifil32
ELF     7eb23000-7ebbe000       Deferred        gdi32<elf>
  \-PE  7eb30000-7ebbe000       \               gdi32
ELF     7ebbe000-7ed05000       Export          user32<elf>
  \-PE  7ebe0000-7ed05000       \               user32
ELF     7ed05000-7ed97000       Deferred        winmm<elf>
  \-PE  7ed10000-7ed97000       \               winmm
ELF     7ed97000-7ede9000       Deferred        advapi32<elf>
  \-PE  7eda0000-7ede9000       \               advapi32
ELF     7ede9000-7edfc000       Deferred        libresolv.so.2
ELF     7edfd000-7edff000       Deferred        libxcb-xlib.so.0
ELF     7edff000-7ee13000       Deferred        lz32<elf>
  \-PE  7ee00000-7ee13000       \               lz32
ELF     7ee13000-7ee31000       Deferred        iphlpapi<elf>
  \-PE  7ee20000-7ee31000       \               iphlpapi
ELF     7ee31000-7ee5d000       Deferred        ws2_32<elf>
  \-PE  7ee40000-7ee5d000       \               ws2_32
ELF     7ee5d000-7ee77000       Deferred        wsock32<elf>
  \-PE  7ee60000-7ee77000       \               wsock32
ELF     7ef97000-7efa2000       Deferred        libnss_files.so.2
ELF     7efa2000-7efac000       Deferred        libnss_nis.so.2
ELF     7efac000-7efc4000       Deferred        libnsl.so.1
ELF     7efc4000-7efe9000       Deferred        libm.so.6
ELF     7efea000-7eff2000       Deferred        libsm.so.6
ELF     b7c90000-b7c95000       Deferred        libxxf86vm.so.1
ELF     b7c95000-b7c9e000       Deferred        libnss_compat.so.2
ELF     b7c9f000-b7ca3000       Deferred        libdl.so.2
ELF     b7ca3000-b7df2000       Deferred        libc.so.6
ELF     b7df3000-b7e0b000       Deferred        libpthread.so.0
ELF     b7e0c000-b7e0f000       Deferred        libxau.so.6
ELF     b7e22000-b7f58000       Deferred        libwine.so.1
ELF     b7f5a000-b7f76000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Emu\VisualBoyAdvance.exe
        00000019    0
        00000009    0 <==
0000000c
        00000012    0
        0000000e    0
        0000000d    0
0000000f
        00000016    0
        00000015    0
        00000011    0
        00000010    0
00000017
        00000018    0
Backtrace:
=>1 0x7bc451ec in ntdll (+0x351ec) (0x0032fa54)
  2 0x005275ca in visualboyadvance (+0x1275ca) (0x0032fa8c)
  3 0x005256dc in visualboyadvance (+0x1256dc) (0x0032fb4c)
  4 0x0052bd44 in visualboyadvance (+0x12bd44) (0x0032fb64)
  5 0x5f4039db in mfc42 (+0x39db) (0x0032fb94)
  6 0x5f411e08 in mfc42 (+0x11e08) (0x0032fbe4)
  7 0x5f4023ed in mfc42 (+0x23ed) (0x0032fc64)
  8 0x5f40230b in mfc42 (+0x230b) (0x0032fc84)
  9 0x5f402294 in mfc42 (+0x2294) (0x0032fce4)
  10 0x5f40221f in mfc42 (+0x221f) (0x0032fd00)
  11 0x5f4021d6 in mfc42 (+0x21d6) (0x0032fd2c)
  12 0x7ec865ba WINPROC_wrapper+0x1a() in user32 (0x0032fd5c)
  13 0x7ec86c9e WINPROC_wrapper+0x6fe() in user32 (0x0032fd9c)
  14 0x7ec8c071 in user32 (+0xac071) (0x0032fddc)
  15 0x7ec4e826 DispatchMessageA+0x96() in user32 (0x0032fe1c)
  16 0x5f40133b in mfc42 (+0x133b) (0x0060af34)
  17 0x00000111 (0x0001002a)
wine: Call from 0x5275ca to unimplemented function MFC42.DLL.6876, aborting
wine: Call from 0x5275ca to unimplemented function MFC42.DLL.6876, aborting

```

It looks like the DLL isn't written correctly or something.  Any help?

I Dl'ed that DLL off the web, maybe I'll try copying one out of the windows dirs.

EDIT:
PS:  This works fine in Windows XP (Home) SP2.

---

### Post by Syndacate on 2008-08-09
*bump

C'mon, Anybody?

---

### Post by Syndacate on 2008-08-10
*Bump,  Anybody?

I really wanna play GBA games in Ubuntu but the VBA emulators BLOWS :(.

Is there any other decent emulators for Ubuntu GBA?

---

### Post by Syndacate on 2008-08-10
Alright, I found the fix to my problem.

VisualBoyAdvance itself is fine - it's the VisualBoy Express front end that's been giving me issues.

I downloaded the source code for VisualBoyAdvance 1.7.2 and compiled it (you need "sdl-image1.2-dev" & "nasm" packages for the compilation.

After that, simply run it out of terminal with:
```
VisualBoyAdvance --throttle=<whatever u want throttle> -3 (size, 1-4) game.gba
```

It won't shut off, so use a diff terminal and use the program "xkill" and target the terminal it's running out of to shut it off.  If you want to save it, just use the save state hotkeys (shift + F1-8 = save state slots & F1-F8 = load state slots).

Good Luck, peeps.

---

