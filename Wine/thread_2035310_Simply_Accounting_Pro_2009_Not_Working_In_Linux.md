---
title: "Simply Accounting Pro 2009 Not Working In Linux"
date: 2012-07-30
forum: Wine
---

### Post by Katniss Everdeen on 2012-07-30
My Dad is switching to Linux. His main computer, still has Windows on  one HDD. There are two HDD's in his computer, one with Ubuntu, and one  with Windows XP. The only reason why he still has Windows, is because of  Simply Accounting, which we can't seem to get to import the data into  any other app.


 I installed Wine and installed Simple Accounting Pro 2009. It  successfully installed. Last year when I tried it, it wouldn't even get  to the install screen.


 Unfortunately, when I try to open it, it crashes. I get this error: [http://i49.tinypic.com/153a3q8.png](http://i49.tinypic.com/153a3q8.png)


I've updated Wine, and it now gives a report log. Here is the error report log:

> Unhandled exception: page fault on read access to 0x06000079 in 32-bit code (0x06000079).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:06000079 ESP:0033e8a0 EBP:000004c0 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:03eea360 EBX:7e9cf6d0 ECX:00000057 EDX:00000057
 ESI:00b32510 EDI:00ed0000
Stack dump:
0x0033e8a0:  0059ae46 00000057 5d2c511e 00148fa4
0x0033e8b0:  00000000 038a15cc 00000000 0033f5e4
0x0033e8c0:  00000000 00000000 0033f5d8 00000057
0x0033e8d0:  00000000 00000003 7e3a1bb0 0000002f
0x0033e8e0:  7de246b6 00eb2808 7e390d82 03897438
0x0033e8f0:  00000010 0000000d 00000003 00000003
Backtrace:
=>0 0x06000079 (0x000004c0)
0x06000079: addb    %al,0x0(%eax)
Modules:
Module    Address            Debug info    Name (138 modules)
PE      340000-  355000    Deferred        simplyaccounting_utils
PE      360000-  367000    Deferred        simplyaccounting_reg
PE      370000-  37b000    Deferred        simplyaccounting_glblsui
PE      380000-  388000    Deferred        simplyaccounting_error
PE      390000-  396000    Deferred        simplyaccounting_tlsmgr
PE      3a0000-  3a9000    Deferred        simplyaccounting_listutil
PE      3b0000-  3e1000    Deferred        simplyaccounting_dblyr
PE      3f0000-  3ff000    Deferred        simplyaccounting_mkcab
PE      400000-  b3d000    Deferred        simplyaccounting
PE      b40000-  ece000    Deferred        simplyaccounting_bus
PE      ed0000- 14dc000    Deferred        simplyaccounting_resdlg
PE     14e0000- 16d3000    Deferred        simplyaccounting_resstr
PE     16e0000- 18dc000    Deferred        simplyaccounting_resstrsp
PE     18e0000- 1b0b000    Deferred        simplyaccounting_resstrfr
PE     1b10000- 2125000    Deferred        simplyaccounting_resdlgfr
PE     2130000- 26aa000    Deferred        simplyaccounting_resdlgsp
PE     26b0000- 2921000    Deferred        simplyaccounting_io
PE     2930000- 2972000    Deferred        simplyaccounting_dbdrv
PE     2980000- 2994000    Deferred        simplyaccounting_filever
PE     29a0000- 29b1000    Deferred        simplyaccounting_updchk
PE     29c0000- 2c9b000    Deferred        simplyaccounting_rpt
PE     2ca0000- 2d55000    Deferred        simplyaccounting_prljour
PE     2d60000- 2e51000    Deferred        simplyaccounting_imprt
PE     2e60000- 2e90000    Deferred        simplyaccounting_cato3cnt
PE     2e90000- 2eeb000    Deferred        cfx2032
PE     2ef0000- 33eb000    Deferred        simplyaccounting_rptcen
PE     33f0000- 380f000    Deferred        simplyaccounting_rptcenfr
PE     3ee0000- 3f16000    Deferred        simply.interoptomanaged
PE    10000000-10016000    Deferred        simplyaccounting_qiflib
PE    78130000-781cb000    Deferred        msvcr80
PE    781d0000-782df000    Deferred        mfc80
ELF    7b800000-7ba15000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba15000    \               kernel32
ELF    7bc00000-7bcc3000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
PE    7c420000-7c4a7000    Deferred        msvcp80
PE    7c4c0000-7c53d000    Deferred        msvcm80
PE    7c630000-7c64b000    Deferred        atl80
ELF    7d74c000-7d760000    Deferred        psapi<elf>
  \-PE    7d750000-7d760000    \               psapi
ELF    7d760000-7d7be000    Deferred        dbghelp<elf>
  \-PE    7d770000-7d7be000    \               dbghelp
ELF    7d7be000-7d7ee000    Deferred        mscoree<elf>
  \-PE    7d7c0000-7d7ee000    \               mscoree
ELF    7d7f3000-7d82b000    Deferred        usp10<elf>
  \-PE    7d800000-7d82b000    \               usp10
ELF    7d82b000-7d846000    Deferred        spoolss<elf>
  \-PE    7d830000-7d846000    \               spoolss
ELF    7d846000-7d867000    Deferred        localspl<elf>
  \-PE    7d850000-7d867000    \               localspl
ELF    7d867000-7d870000    Deferred        librt.so.1
ELF    7d870000-7d8b9000    Deferred        libdbus-1.so.3
ELF    7d8b9000-7d93e000    Deferred        libgcrypt.so.11
ELF    7d93e000-7da0d000    Deferred        libkrb5.so.3
ELF    7da0d000-7dad1000    Deferred        libgnutls.so.26
ELF    7dbd2000-7dbd7000    Deferred        libgpg-error.so.0
ELF    7dbd7000-7dbef000    Deferred        libresolv.so.2
ELF    7dbef000-7dc01000    Deferred        libp11-kit.so.0
ELF    7dc01000-7dc13000    Deferred        libtasn1.so.3
ELF    7dc13000-7dc1c000    Deferred        libkrb5support.so.0
ELF    7dc1c000-7dc44000    Deferred        libk5crypto.so.3
ELF    7dc44000-7dc56000    Deferred        libavahi-client.so.3
ELF    7dc56000-7dc94000    Deferred        libgssapi_krb5.so.2
ELF    7dc94000-7dce7000    Deferred        libcups.so.2
ELF    7dce9000-7dcfc000    Deferred        gnome-keyring-pkcs11.so
ELF    7dd2a000-7dd5e000    Deferred        uxtheme<elf>
  \-PE    7dd30000-7dd5e000    \               uxtheme
ELF    7dd5e000-7dd64000    Deferred        libxfixes.so.3
ELF    7dd64000-7dd6f000    Deferred        libxcursor.so.1
ELF    7dd6f000-7dd74000    Deferred        libcom_err.so.2
ELF    7dd74000-7dd82000    Deferred        libavahi-common.so.3
ELF    7dde8000-7de12000    Deferred        libexpat.so.1
ELF    7de12000-7de46000    Deferred        libfontconfig.so.1
ELF    7de46000-7de56000    Deferred        libxi.so.6
ELF    7de56000-7de5a000    Deferred        libxcomposite.so.1
ELF    7de5a000-7de63000    Deferred        libxrandr.so.2
ELF    7de63000-7de6d000    Deferred        libxrender.so.1
ELF    7de6d000-7de73000    Deferred        libxxf86vm.so.1
ELF    7de73000-7de77000    Deferred        libxinerama.so.1
ELF    7de77000-7de99000    Deferred        imm32<elf>
  \-PE    7de80000-7de99000    \               imm32
ELF    7de99000-7deba000    Deferred        libxcb.so.1
ELF    7deba000-7ded4000    Deferred        libice.so.6
ELF    7ded4000-7e008000    Deferred        libx11.so.6
ELF    7e008000-7e01a000    Deferred        libxext.so.6
ELF    7e01a000-7e01e000    Deferred        libkeyutils.so.1
ELF    7e02f000-7e0c2000    Deferred        winex11<elf>
  \-PE    7e040000-7e0c2000    \               winex11
ELF    7e0c2000-7e15c000    Deferred        libfreetype.so.6
ELF    7e15c000-7e196000    Deferred        winspool<elf>
  \-PE    7e160000-7e196000    \               winspool
ELF    7e196000-7e275000    Deferred        comdlg32<elf>
  \-PE    7e1a0000-7e275000    \               comdlg32
ELF    7e275000-7e367000    Deferred        oleaut32<elf>
  \-PE    7e290000-7e367000    \               oleaut32
ELF    7e3ac000-7e3b3000    Deferred        libxdmcp.so.6
ELF    7e3b3000-7e3b7000    Deferred        libxau.so.6
ELF    7e3b7000-7e42c000    Deferred        rpcrt4<elf>
  \-PE    7e3c0000-7e42c000    \               rpcrt4
ELF    7e42c000-7e534000    Deferred        ole32<elf>
  \-PE    7e440000-7e534000    \               ole32
ELF    7e534000-7e5c1000    Deferred        msvcrt<elf>
  \-PE    7e550000-7e5c1000    \               msvcrt
ELF    7e5c1000-7e6b9000    Deferred        comctl32<elf>
  \-PE    7e5d0000-7e6b9000    \               comctl32
ELF    7e6b9000-7e8ca000    Deferred        shell32<elf>
  \-PE    7e6d0000-7e8ca000    \               shell32
ELF    7e8ca000-7e934000    Deferred        shlwapi<elf>
  \-PE    7e8e0000-7e934000    \               shlwapi
ELF    7e934000-7e94d000    Deferred        version<elf>
  \-PE    7e940000-7e94d000    \               version
ELF    7e94d000-7e9ad000    Deferred        advapi32<elf>
  \-PE    7e960000-7e9ad000    \               advapi32
ELF    7e9ad000-7ea6a000    Deferred        gdi32<elf>
  \-PE    7e9c0000-7ea6a000    \               gdi32
ELF    7ea6a000-7ebaa000    Deferred        user32<elf>
  \-PE    7ea80000-7ebaa000    \               user32
ELF    7ebaa000-7ebd0000    Deferred        mpr<elf>
  \-PE    7ebb0000-7ebd0000    \               mpr
ELF    7ebd0000-7ebe6000    Deferred        libz.so.1
ELF    7ebe6000-7ec55000    Deferred        wininet<elf>
  \-PE    7ebf0000-7ec55000    \               wininet
ELF    7ec55000-7ec6f000    Deferred        libnsl.so.1
ELF    7ec6f000-7ec78000    Deferred        libnss_compat.so.2
ELF    7ec79000-7ec8d000    Deferred        lz32<elf>
  \-PE    7ec80000-7ec8d000    \               lz32
ELF    7efbf000-7efeb000    Deferred        libm.so.6
ELF    7efed000-7eff3000    Deferred        libuuid.so.1
ELF    7eff3000-7f000000    Deferred        libnss_files.so.2
ELF    b7452000-b745b000    Deferred        libsm.so.6
ELF    b745c000-b7461000    Deferred        libdl.so.2
ELF    b7461000-b7606000    Deferred        libc.so.6
ELF    b7607000-b7622000    Deferred        libpthread.so.0
ELF    b762b000-b7637000    Deferred        libnss_nis.so.2
ELF    b7637000-b7779000    Dwarf           libwine.so.1
ELF    b777b000-b779d000    Deferred        ld-linux.so.2
ELF    b779d000-b779e000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000031    0
    0000001e    0
    00000018    0
    00000017    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001a    0
    00000019    0
    00000014    0
    00000013    0
0000001b plugplay.exe
    00000020    0
    0000001d    0
    0000001c    0
00000023 explorer.exe
    00000024    0
00000032 (D) C:\Program Files\Simply Accounting Pro 2009\SimplyAccounting.exe
    00000033    0 <==
System information:
    Wine build: wine-1.4
    Platform: i386
    Host system: Linux
    Host version: 3.2.0-27-generic-pae

---

### Post by Mark Phelps on 2012-07-31
Did you read the WineHQ page for this app?  I've linked it below ...

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=819]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=819")

The ratings are GARBAGE -- except for a 6-year old Demo version.

Simply put, you're wasting your time.

---

### Post by oldos2er on 2012-07-31
Moved to Wine.

---

### Post by mike555 on 2012-07-31
He might want to try GnuCash , free and cross platform

---

### Post by Katniss Everdeen on 2012-09-10
> **mike555 said:**
> He might want to try GnuCash , free and cross platform

I've tried backing up the data from Simply Accounting in many formats, last year. Unfortunnately, all of the the programs I found in Ubuntu Software Centre, (GNUCash encluded), won't except them. I think it has something to do with the format, the way the data is in Simply Accounting, so that it's only compatible with Simply Accounting. I will work on trying to find more alternative ways to see if the data can be imported, like web based accounting programs or something.

---

