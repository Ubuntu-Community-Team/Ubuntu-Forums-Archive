---
title: "crash: &quot;Winevdm.exe encountered error&quot;"
date: 2014-12-24
forum: Wine
---

### Post by novotnyw on 2014-12-24
Hello,

I try to run old and really specific app in wine. The app is a software for medical device, it currently needs it's own old computer with Win95 and I would like to run the software on modern PC with linux and make the old PC redundant.

I created fresh install of Xubuntu 14.04 i386 (32-bit), kernel is version 3.16.0.28-gemeric, installed wine1.7 from ubuntu-wine.

Next I moved the application by simply copying it into wine drive_c, added it as a new app into winecfg, setted running environment to Win95 and executed. The app starts good, I have minor problem with menus, when I drag the app window somewhere else from initial position and then roll out menu, the menu appears on initial window position, but this has low importance.

The main problem is when I try to add new patient, the application crashes with wine crash dialog anouncing that "The program winevdm.exe has encountered a serious problem, and needs to close...".

From my current research, this was in time of Ubuntu 11.04 related to some incompatibility with wine and libfontconfig1 as mentioned [here]("http://ubuntuforums.org/archive/index.php/t-1752736.html"), but the solution proposed there I was not able to repeat in Xubuntu 14.04.

When running wine from console, it outputs this:
```

fixme:toolhelp:InterruptRegister16 (11bf, 0x11cf00c2), stub.
wine: Unhandled page fault on read access to 0x000014d8 at address 0x7e969164 (thread 002e), starting debugger...
Unhandled exception: page fault on read access to 0x000014d8 in 32-bit code (0x7e969164).
fixme:dbghelp:addr_to_linear Failed to linearize address 00de:d568 (mode 0)
Register dump:
 CS:0073 SS:126f DS:126f ES:126f FS:0033 GS:003b
 EIP:7e969164 ESP:00de6256 EBP:00006292 EFLAGS:00010216(  R- --  I   -A-P- )
 EAX:0000126e EBX:00000000 ECX:00000000 EDX:00000000
 ESI:00000000 EDI:00000000
Stack dump:
0x126f:0x6256:  2214 14df 0468 101f 0000 0000 0000 0002
0x126f:0x6266:  00a0 e5c8 00de 0010 13df 004d 0000 62a0
0x126f:0x6276:  0000 126f 10ff 0033 003b 084c 0000 10f7
Backtrace:
=>0 0x7e969164 in krnl386.exe16 (+0x9164) (0x0041c6aa)
0x7e969164: lret    
Modules:
Module    Address            Debug info    Name (116 modules)
ELF    7b800000-7ba60000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba60000    \               kernel32
ELF    7bc00000-7bce7000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bce7000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d509000-7d512000    Deferred        libffi.so.6
ELF    7d512000-7d529000    Deferred        libresolv.so.2
ELF    7d529000-7d52e000    Deferred        libkeyutils.so.1
ELF    7d52e000-7d584000    Deferred        libdbus-1.so.3
ELF    7d584000-7d60f000    Deferred        libgmp.so.10
ELF    7d60f000-7d63e000    Deferred        libhogweed.so.2
ELF    7d63e000-7d673000    Deferred        libnettle.so.4
ELF    7d673000-7d686000    Deferred        libtasn1.so.6
ELF    7d686000-7d6c2000    Deferred        libp11-kit.so.0
ELF    7d6c2000-7d6cf000    Deferred        libkrb5support.so.0
ELF    7d6cf000-7d701000    Deferred        libk5crypto.so.3
ELF    7d701000-7d7d5000    Deferred        libkrb5.so.3
ELF    7d7d5000-7d7e9000    Deferred        libavahi-client.so.3
ELF    7d7e9000-7d916000    Deferred        libgnutls-deb0.so.28
ELF    7d916000-7d966000    Deferred        libgssapi_krb5.so.2
ELF    7d966000-7d9e1000    Deferred        libcups.so.2
ELF    7d9f6000-7da2d000    Deferred        uxtheme<elf>
  \-PE    7da00000-7da2d000    \               uxtheme
ELF    7da2d000-7da34000    Deferred        libxfixes.so.3
ELF    7da34000-7da3f000    Deferred        libxcursor.so.1
ELF    7da3f000-7da51000    Deferred        libxi.so.6
ELF    7da51000-7da55000    Deferred        libxcomposite.so.1
ELF    7da55000-7da60000    Deferred        libxrandr.so.2
ELF    7da60000-7da6b000    Deferred        libxrender.so.1
ELF    7da6b000-7da71000    Deferred        libxxf86vm.so.1
ELF    7da71000-7da75000    Deferred        libxinerama.so.1
ELF    7da75000-7da7c000    Deferred        libxdmcp.so.6
ELF    7da7c000-7da9e000    Deferred        libxcb.so.1
ELF    7da9e000-7dbe9000    Deferred        libx11.so.6
ELF    7dbe9000-7dbfc000    Deferred        libxext.so.6
ELF    7dbfc000-7dc90000    Deferred        winex11<elf>
  \-PE    7dc10000-7dc90000    \               winex11
ELF    7dc90000-7dcd3000    Deferred        winspool<elf>
  \-PE    7dca0000-7dcd3000    \               winspool
ELF    7dcd3000-7dddc000    Deferred        comctl32<elf>
  \-PE    7dce0000-7dddc000    \               comctl32
ELF    7dddc000-7e013000    Deferred        shell32<elf>
  \-PE    7ddf0000-7e013000    \               shell32
ELF    7e013000-7e100000    Deferred        comdlg32<elf>
  \-PE    7e020000-7e100000    \               comdlg32
ELF    7e202000-7e206000    Deferred        libxau.so.6
ELF    7e206000-7e20b000    Deferred        libcom_err.so.2
ELF    7e20b000-7e219000    Deferred        libavahi-common.so.3
ELF    7e21b000-7e295000    Deferred        shlwapi<elf>
  \-PE    7e230000-7e295000    \               shlwapi
ELF    7e295000-7e2ac000    Deferred        commdlg.dll16.so
PE    7e2a0000-7e2ac000    Deferred        commdlg.dll16
ELF    7e2ac000-7e2c1000    Deferred        win87em.dll16.so
PE    7e2b0000-7e2c1000    Deferred        win87em.dll16
ELF    7e2c1000-7e2d8000    Deferred        toolhelp.dll16.so
PE    7e2d0000-7e2d8000    Deferred        toolhelp.dll16
ELF    7e304000-7e319000    Deferred        sound.drv16.so
PE    7e310000-7e319000    Deferred        sound.drv16
ELF    7e319000-7e344000    Deferred        msacm32<elf>
  \-PE    7e320000-7e344000    \               msacm32
ELF    7e344000-7e3c8000    Deferred        rpcrt4<elf>
  \-PE    7e350000-7e3c8000    \               rpcrt4
ELF    7e3c8000-7e50a000    Deferred        ole32<elf>
  \-PE    7e3e0000-7e50a000    \               ole32
ELF    7e50a000-7e5c3000    Deferred        winmm<elf>
  \-PE    7e510000-7e5c3000    \               winmm
ELF    7e5c3000-7e5ef000    Deferred        mmsystem.dll16.so
PE    7e5d0000-7e5ef000    Deferred        mmsystem.dll16
ELF    7e5ef000-7e603000    Deferred        mouse.drv16.so
PE    7e5f0000-7e603000    Deferred        mouse.drv16
ELF    7e603000-7e618000    Deferred        keyboard.drv16.so
PE    7e610000-7e618000    Deferred        keyboard.drv16
ELF    7e618000-7e62d000    Deferred        display.drv16.so
PE    7e620000-7e62d000    Deferred        display.drv16
ELF    7e62d000-7e655000    Deferred        mpr<elf>
  \-PE    7e630000-7e655000    \               mpr
ELF    7e655000-7e6a5000    Deferred        user.exe16.so
PE    7e660000-7e6a5000    Deferred        user.exe16
ELF    7e6a5000-7e6d8000    Deferred        gdi.exe16.so
PE    7e6b0000-7e6d8000    Deferred        gdi.exe16
ELF    7e6d8000-7e6ed000    Deferred        comm.drv16.so
PE    7e6e0000-7e6ed000    Deferred        comm.drv16
ELF    7e6ed000-7e702000    Deferred        system.drv16.so
PE    7e6f0000-7e702000    Deferred        system.drv16
ELF    7e702000-7e727000    Deferred        imm32<elf>
  \-PE    7e710000-7e727000    \               imm32
ELF    7e7a5000-7e7ce000    Deferred        libexpat.so.1
ELF    7e7ce000-7e80a000    Deferred        libfontconfig.so.1
ELF    7e80a000-7e836000    Deferred        libpng12.so.0
ELF    7e836000-7e850000    Deferred        libz.so.1
ELF    7e850000-7e900000    Deferred        libfreetype.so.6
ELF    7e900000-7e923000    Deferred        libtinfo.so.5
ELF    7e923000-7e94b000    Deferred        libncurses.so.5
ELF    7e94b000-7e9f7000    Dwarf           krnl386.exe16.so
PE    7e960000-7e9f7000    DIA             krnl386.exe16
ELF    7e9f7000-7ea11000    Deferred        version<elf>
  \-PE    7ea00000-7ea11000    \               version
ELF    7ea11000-7ea84000    Deferred        advapi32<elf>
  \-PE    7ea20000-7ea84000    \               advapi32
ELF    7ea84000-7eba3000    Deferred        gdi32<elf>
  \-PE    7ea90000-7eba3000    \               gdi32
ELF    7eba3000-7ecff000    Deferred        user32<elf>
  \-PE    7ebc0000-7ecff000    \               user32
ELF    7ecff000-7ed16000    Deferred        winevdm<elf>
  \-PE    7ed00000-7ed16000    \               winevdm
ELF    7ed16000-7ed23000    Deferred        libnss_files.so.2
ELF    7ed23000-7ed2f000    Deferred        libnss_nis.so.2
ELF    7ed2f000-7ed48000    Deferred        libnsl.so.1
ELF    7efa5000-7efeb000    Deferred        libm.so.6
ELF    b73c4000-b73cd000    Deferred        libnss_compat.so.2
ELF    b73ce000-b757c000    Deferred        libc.so.6
ELF    b757c000-b7581000    Deferred        libdl.so.2
ELF    b7582000-b759f000    Deferred        libpthread.so.0
ELF    b75b4000-b776a000    Dwarf           libwine.so.1
ELF    b776c000-b778e000    Deferred        ld-linux.so.2
ELF    b778e000-b778f000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 winecfg.exe
    00000009    0
0000000e services.exe
    0000001d    0
    0000001c    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001b    0
    00000018    0
    00000017    0
    00000013    0
00000019 plugplay.exe
    0000001f    0
    0000001e    0
    0000001a    0
00000020 explorer.exe
    00000021    0
0000002c (D) C:\windows\system32\winevdm.exe
    0000002f    0
    0000002e    0 <==
    0000002d    0

```

---

### Post by Mark Phelps on 2014-12-26
You could try looking up the app in the WineHQ database just to see if anyone else has tried it and has some testing results:  [http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

---

