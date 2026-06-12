---
title: "Wine WPS Office Install  Failed"
date: 2018-01-17
forum: Wine
---

### Post by wcrump on 2018-01-17
I have Wine installed in Lubuntu.  I downloaded the Windows installer for WPS Office 2016 free edition and the process failed.  Here are the details:

  ```
                      Unhandled exception: page fault on read access to 0x00000100 in 32-bit code (0x7ee92a56).
 Register dump:
  CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
  EIP:7ee92a56 ESP:0033f838 EBP:0033f838 EFLAGS:00210206(  R- --  I   - -P- )
  EAX:00a473b0 EBX:7ee512e0 ECX:0033f83c EDX:00000100
  ESI:00a465c8 EDI:00a47380
 Stack dump:
 0x0033f838:  0033f844 1005838d 00000100 0033f88c
 0x0033f848:  100582ed 00a473b0 00000100 00a473a4
 0x0033f858:  00a46bb8 00a473a0 00a46ba0 00a464d0
 0x0033f868:  10058229 54c442f6 00000001 00a355d8
 0x0033f878:  00000000 00a355d8 0033f8b0 110f0eb3
 0x0033f888:  ffffffff 0033f8bc 10057cb0 00000001
 Backtrace:
 =>0 0x7ee92a56 (0x0033f838)
   1 0x1005838d in kso (+0x5838c) (0x0033f844)
   2 0x100582ed in kso (+0x582ec) (0x0033f88c)
   3 0x10057cb0 in kso (+0x57caf) (0x0033f8bc)
   4 0x10057c26 in kso (+0x57c25) (0x0033f8ec)
   5 0x10054ce1 in kso (+0x54ce0) (0x0033f928)
   6 0x10054bf1 in kso (+0x54bf0) (0x0033f934)
   7 0x10054757 in kso (+0x54756) (0x0033f99c)
   8 0x00402090 in ksomisc (+0x208f) (0x0033f9d4)
   9 0x0044eb18 in ksomisc (+0x4eb17) (0x0033fdbc)
   10 0x004532dd in ksomisc (+0x532dc) (0x0033fe50)
   11 0x7b85e8ac in kernel32 (+0x4e8ab) (0x0033fe68)
   12 0x7b85f87a in kernel32 (+0x4f879) (0x0033fe98)
   13 0x7bc802fc (0x0033feb8)
   14 0x7bc832af (0x0033ffa8)
   15 0x7bc802da (0x0033ffc8)
   16 0x7bc52d47 (0x0033ffe8)
 0x7ee92a56: cmpw    $0,0x0(%edx)
 Modules:
 Module    Address            Debug info    Name (44 modules)
 PE      340000-  387000    Deferred        ssleay32
 PE      390000-  3d4000    Deferred        kdownload
 PE      400000-  4ec000    Export          ksomisc
 PE      4f0000-  63e000    Deferred        libeay32
 PE      640000-  684000    Deferred        curls
 PE      690000-  856000    Deferred        xercesc3
 PE    10000000-11f99000    Export          kso
 PE    64000000-640df000    Deferred        qtnetwork4
 PE    67000000-678ba000    Deferred        qtcore4
 PE    7b810000-7b9b0000    Export          kernel32
 PE    7bc10000-7bc14000    Deferred        ntdll
 PE    7df00000-7df04000    Deferred        uxtheme
 PE    7e130000-7e134000    Deferred        winex11
 PE    7e360000-7e364000    Deferred        dbghelp
 PE    7e3c0000-7e3c3000    Deferred        imagehlp
 PE    7e3d0000-7e3d3000    Deferred        userenv
 PE    7e3f0000-7e3f4000    Deferred        iphlpapi
 PE    7ebd0000-7ebd3000    Deferred        msimg32
 PE    7ebe0000-7ebf9000    Deferred        wldap32
 PE    7ec40000-7ec81000    Deferred        crypt32
 PE    7ed40000-7ed43000    Deferred        msvcp100
 PE    7ee20000-7ee24000    Deferred        msvcr100
 PE    7eee0000-7eee9000    Deferred        msacm32
 PE    7ef10000-7ef88000    Deferred        winmm
 PE    7efc0000-7efc4000    Deferred        imm32
 PE    7eff0000-7f089000    Deferred        comdlg32
 PE    7f0d0000-7f0da000    Deferred        winspool
 PE    7f110000-7f114000    Deferred        cabinet
 PE    7f130000-7f15f000    Deferred        comctl32
 PE    7f230000-7f234000    Deferred        ws2_32
 PE    7f260000-7f26a000    Deferred        mpr
 PE    7f2b0000-7f2c8000    Deferred        wininet
 PE    7f320000-7f331000    Deferred        urlmon
 PE    7f3c0000-7f3db000    Deferred        msi
 PE    7f4c0000-7f4c8000    Deferred        oleaut32
 PE    7f5e0000-7f5e4000    Deferred        rpcrt4
 PE    7f670000-7f678000    Deferred        ole32
 PE    7f7a0000-7f7a8000    Deferred        shlwapi
 PE    7f810000-7f96f000    Deferred        shell32
 PE    7fa40000-7fa44000    Deferred        version
 PE    7fa70000-7fa74000    Deferred        advapi32
 PE    7fae0000-7fae7000    Deferred        gdi32
 PE    7fc00000-7fc3b000    Deferred        user32
 PE    7ffd0000-7ffd4000    Deferred        psapi
 Threads:
 process  tid      prio (all id:s are in hex)
 00000008 wpsoffice_free_10.2.0.5978_en.exe
     00000009    0
 0000000e services.exe
     00000031    0
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
     0000003d    0
     0000003c    0
     0000003a    0
     00000038    0
     00000036    0
     00000034    0
     00000032    0
     0000002e    0
     00000028    0
     00000025    0
     00000023    0
     00000022    0
 00000026 wpsoffice_free_10.2.0.5978_en.exe
     00000042    0
     00000045    0
     00000041    0
     00000040    0
     00000027    0
 0000003e wpsoffice_free_10.2.0.5978_en.exe
     0000003f    0
 00000030 (D) C:\users\administrator\Local Settings\Application Data\Kingsoft\WPS Office\10.2.0.5978\office6\ksomisc.exe
     0000000d    0 <==
 System information:
     Wine build: wine-1.8.7 (Ubuntu 1.8.7-1ubuntu1)
     Platform: i386
     Version: Windows XP
     Host system: Linux
     Host version: 4.10.0-42-generic
```

How do I get WPS Office to install in Lubuntu with Wine?

---

### Post by QIII on 2018-01-17
Moved to the Wine sub-forum.

---

### Post by litlesam on 2018-01-17
Hi, Not sure if you are aware that you can download WPS 32 bit for Linux, Wine is not need for the Linux version.

Please see attached. [WPS Linux]("http://wps-community.org/")

---

