---
title: "making deco online work on wine?"
date: 2007-11-06
forum: Wine
---

### Post by zizzdude on 2007-11-06
hey, I installed Deco Online on Ubuntu with wine, but I can't run it, saying it needed a particular dll library. As a result, I downloaded the dll file and put in in the same directory as the game. but I still can't run the game. Any ideas on how to make it work?

---

### Post by Ferrat on 2007-11-06
> **zizzdude said:**
> hey, I installed Deco Online on Ubuntu with wine, but I can't run it, saying it needed a particular dll library. As a result, I downloaded the dll file and put in in the same directory as the game. but I still can't run the game. Any ideas on how to make it work?

you need to add the lib in to wine

winecfg

tab Libraries
then type in the name of the lib -.dll
and press add

then see what it says when you try to launch it =)

---

### Post by zizzdude on 2007-11-06
ok, I added the library to wine, but it gave me this output:

wine: Call from 0x402968 to unimplemented function MFC42.DLL.6478, aborting
wine: Unimplemented function MFC42.DLL.6478 called at address 0x402968 (thread 0014), starting debugger...
Unhandled exception: unimplemented function MFC42.DLL.6478 called in 32-bit code (0x7bc4323c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc4323c ESP:0034d320 EBP:0034d384 EFLAGS:00200202(   - 00      - - I1)
 EAX:0000194e EBX:7bc8591c ECX:0034e008 EDX:00000000
 ESI:0034d32c EDI:0034d52c
Stack dump:
0x0034d320:  5f48f7a2 0034d83c 7bc648eb 80000100
0x0034d330:  00000001 00000000 00402968 00000002
0x0034d340:  00410e54 0000194e 0034d8fc 5f4cbe2c
0x0034d350:  5f4cbe2c 0034d340 0034d380 5f48f7a2
0x0034d360:  0034d52c 7bc648eb 0034d91c 00000000
0x0034d370:  00000020 0034d52c 0034d8fc 0034d93c
Backtrace:
=>1 0x7bc4323c in ntdll (+0x3323c) (0x0034d384)
  2 0x00402968 in deco (+0x2968) (0x0034d940)
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file MFC42.dbg ("")
  3 0x5f4c86bc in mfc42 (+0xc86bc) (0x5f4c86bc)
  4 0x5f4c86b0 in mfc42 (+0xc86b0) (0x00000000)
0x7bc4323c: subl        $4,%esp
Modules:
Module  Address                 Debug info      Name (74 modules)
PE        400000-  468000       Export          deco
PE      10000000-10012000       Deferred        zlib1
PE      5f400000-5f4ed000       Export          mfc42
PE      60000000-60018000       Deferred        rockbaseml
PE      63000000-6300a000       Deferred        bugslayerutilml
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca1000       Export          ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c7a2000-7c7bc000       Deferred        wsock32<elf>
  \-PE  7c7b0000-7c7bc000       \               wsock32
ELF     7c7bc000-7c815000       Deferred        rpcrt4<elf>
  \-PE  7c7d0000-7c815000       \               rpcrt4
ELF     7c815000-7c8b6000       Deferred        ole32<elf>
  \-PE  7c820000-7c8b6000       \               ole32
ELF     7c8b6000-7c8e8000       Deferred        uxtheme<elf>
  \-PE  7c8c0000-7c8e8000       \               uxtheme
ELF     7d26a000-7d26f000       Deferred        libxfixes.so.3
ELF     7d26f000-7d278000       Deferred        libxcursor.so.1
ELF     7d278000-7d295000       Deferred        imm32<elf>
  \-PE  7d280000-7d295000       \               imm32
ELF     7d295000-7d29d000       Deferred        libxrender.so.1
ELF     7db3d000-7db48000       Deferred        libgcc_s.so.1
ELF     7db48000-7db51000       Deferred        librt.so.1
ELF     7dc0b000-7e56e000       Deferred        fglrx_dri.so
ELF     7e56e000-7e60e000       Deferred        libgl.so.1
ELF     7e60e000-7e613000       Deferred        libxdmcp.so.6
ELF     7e613000-7e616000       Deferred        libxau.so.6
ELF     7e616000-7e707000       Deferred        libx11.so.6
ELF     7e707000-7e715000       Deferred        libxext.so.6
ELF     7e715000-7e71a000       Deferred        libxxf86vm.so.1
ELF     7e71a000-7e732000       Deferred        libice.so.6
ELF     7e732000-7e73a000       Deferred        libsm.so.6
ELF     7e73c000-7e742000       Deferred        libxrandr.so.2
ELF     7e749000-7e7d6000       Deferred        winex11<elf>
  \-PE  7e760000-7e7d6000       \               winex11
ELF     7e84a000-7e86a000       Deferred        libexpat.so.1
ELF     7e86a000-7e895000       Deferred        libfontconfig.so.1
ELF     7e895000-7e8aa000       Deferred        libz.so.1
ELF     7e8aa000-7e91a000       Deferred        libfreetype.so.6
ELF     7e91a000-7e92d000       Deferred        libresolv.so.2
ELF     7e93c000-7e95a000       Deferred        iphlpapi<elf>
  \-PE  7e940000-7e95a000       \               iphlpapi
ELF     7e95a000-7e987000       Deferred        ws2_32<elf>
  \-PE  7e960000-7e987000       \               ws2_32
ELF     7e987000-7e99c000       Deferred        psapi<elf>
  \-PE  7e990000-7e99c000       \               psapi
ELF     7e99c000-7e9e6000       Deferred        dbghelp<elf>
  \-PE  7e9b0000-7e9e6000       \               dbghelp
ELF     7e9e6000-7eaa5000       Deferred        comctl32<elf>
  \-PE  7e9f0000-7eaa5000       \               comctl32
ELF     7eaa5000-7eafd000       Deferred        shlwapi<elf>
  \-PE  7eab0000-7eafd000       \               shlwapi
ELF     7eafd000-7ec00000       Deferred        shell32<elf>
  \-PE  7eb10000-7ec00000       \               shell32
ELF     7ec00000-7ed3e000       Deferred        user32<elf>
  \-PE  7ec20000-7ed3e000       \               user32
ELF     7ed3e000-7ed87000       Deferred        advapi32<elf>
  \-PE  7ed50000-7ed87000       \               advapi32
ELF     7ed87000-7ee22000       Deferred        gdi32<elf>
  \-PE  7eda0000-7ee22000       \               gdi32
ELF     7ee22000-7ee8a000       Deferred        msvcrt<elf>
  \-PE  7ee30000-7ee8a000       \               msvcrt
ELF     7efa9000-7efb4000       Deferred        libnss_files.so.2
ELF     7efb4000-7efcc000       Deferred        libnsl.so.1
ELF     7efcc000-7eff1000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cc3000-b7ccc000       Deferred        libnss_compat.so.2
ELF     b7ccd000-b7cd1000       Deferred        libdl.so.2
ELF     b7cd1000-b7e1b000       Deferred        libc.so.6
ELF     b7e1c000-b7e34000       Deferred        libpthread.so.0
ELF     b7e43000-b7f57000       Deferred        libwine.so.1
ELF     b7f59000-b7f75000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000013 (D) C:\Program Files\Deco Online\Deco.exe
        00000014    0 <==
0000000a 
        0000000c    0
        0000000b    0
wine: Call from 0x402968 to unimplemented function MFC42.DLL.6478, aborting
wine: Call from 0x402968 to unimplemented function MFC42.DLL.6478, aborting


what do I do to prevent this? :(


EDIT:

ok, I took out the the library I added in to the directory, thinking it would solve the problem above. I also used wincfg to put in the library. but I get this error:

err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\Deco Online\\Deco.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Deco Online\\Deco.exe" failed, status c0000135

how do I get the library?

---

### Post by Detox06 on 2008-07-30
I was having a similar problem getting VisualBoyAdvance to work. Try downloading the .dll file, and putting it in the same directory as the .exe file. This worked for me.

---

### Post by ducttapeman13093 on 2009-09-16
i think im having the same problem with deco. and im a newb at linux so the prolly doesnt help :/ k so i downloaded the MFC42.dll and added it to wine, but i still get the same error. what else do i need to do?

---

