---
title: "Cain and Abel on Ubuntu 12.04 with Wine"
date: 2012-04-30
forum: Wine
---

### Post by theRadish on 2012-04-30
I am trying to run Cain and Abel on Ubuntu 12.04 with Wine. After  installation, when I launch Cain, it immediately says:

The program  Cain.exe has encountered a serious problem and needs to close. We are  sorry for the inconvenience.

When I click "Show Details" it says:
```
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb75b91a0).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b75b91a0 ESP:0033d888 EBP:7ddce3dc EFLAGS:00010282(  R- --  I S - - - )
 EAX:00000000 EBX:7df0fff4 ECX:a805d100 EDX:7ddce3dc
 ESI:7ddc7cc0 EDI:a805d100
Stack dump:
0x0033d888:  7df0fff4 7df096e2 7ddce3dc 00000000
0x0033d898:  a805d100 7bc3512f 00000003 00000000
0x0033d8a8:  ea017444 7e14fff4 00205598 0000002b
0x0033d8b8:  0033d8d8 00000001 7e1531e0 00205628
0x0033d8c8:  7df095a9 7e14fff4 00205598 0000002b
0x0033d8d8:  0033dac8 7e12fc38 7ddc7cc0 0400323e
Backtrace:
=>0 0xb75b91a0 in libc.so.6 (+0x1351a0) (0x7ddce3dc)
  1 0x7df096e2 XRenderAddGlyphs+0x141() in libxrender.so.1 (0x7ddce3dc)
  2 0x7e12fc38 in winex11 (+0x5fc37) (0x0033dac8)
  3 0x7e1307ff in winex11 (+0x607fe) (0x0033db88)
  4 0x7e848024 ExtTextOutW+0x1a33() in gdi32 (0x0033dd68)
  5 0x7e93b288 DrawTextExW+0x7c7() in user32 (0x0033e688)
  6 0x7e93cb9f DrawTextW+0x6e() in user32 (0x0033e6d8)
  7 0x7e90c802 in user32 (+0x5c801) (0x0033e7c8)
  8 0x7e910524 DrawMenuBarTemp+0x183() in user32 (0x0033e838)
  9 0x7e910702 in user32 (+0x60701) (0x0033e888)
  10 0x7e9238b6 in user32 (+0x738b5) (0x0033ed48)
  11 0x7e924365 in user32 (+0x74364) (0x0033ed78)
  12 0x7e8e0748 in user32 (+0x30747) (0x0033ee38)
  13 0x7e8e103e DefWindowProcA+0x1bd() in user32 (0x0033ee98)
  14 0x7e951f8a WINPROC_wrapper+0x19() in user32 (0x0033eec8)
  15 0x7e9526dc in user32 (+0xa26db) (0x0033ef18)
  16 0x7e954e6a CallWindowProcA+0x59() in user32 (0x0033ef68)
  17 0x006219f4 in cain (+0x2219f3) (0x0033ef88)
  18 0x0062de86 in cain (+0x22de85) (0x0033efa0)
  19 0x00553cee in cain (+0x153ced) (0x0033f048)
  20 0x00621af7 in cain (+0x221af6) (0x0033f068)
  21 0x00552bd7 in cain (+0x152bd6) (0x0033f0e8)
  22 0x0062451b in cain (+0x22451a) (0x0033f108)
  23 0x7e951f8a WINPROC_wrapper+0x19() in user32 (0x0033f138)
  24 0x7e9526dc in user32 (+0xa26db) (0x0033f188)
  25 0x7e9534ca in user32 (+0xa34c9) (0x0033f658)
  26 0x7e954da9 in user32 (+0xa4da8) (0x0033f6a8)
  27 0x7e914d31 in user32 (+0x64d30) (0x0033f718)
  28 0x7e91b866 in user32 (+0x6b865) (0x0033f798)
  29 0x7e91bcdc SendMessageW+0x4b() in user32 (0x0033f7e8)
  30 0x7e8f574c in user32 (+0x4574b) (0x0033f8f8)
  31 0x7e8f5a29 in user32 (+0x45a28) (0x0033f9b8)
  32 0x7e8f5b60 SetForegroundWindow+0x5f() in user32 (0x0033f9e8)
  33 0x7e0e9d01 in winex11 (+0x19d00) (0x0033fa68)
  34 0x7e0ece75 in winex11 (+0x1ce74) (0x0033fb28)
  35 0x7e0e9a91 in winex11 (+0x19a90) (0x0033fb68)
  36 0x7e0ebf1f in winex11 (+0x1bf1e) (0x0033fcb8)
  37 0x7e0ed33b in winex11 (+0x1d33a) (0x0033fcf8)
  38 0x7e91b28a PeekMessageW+0x59() in user32 (0x0033fd58)
  39 0x7e91b419 PeekMessageA+0xc8() in user32 (0x0033fd98)
  40 0x00629618 in cain (+0x229617) (0x0033fdcc)
  41 0x00681337 in cain (+0x281336) (0x0033fde0)
  42 0x00661601 in cain (+0x261600) (0x0033fe70)
  43 0x7b859cdc call_process_entry+0xb() in kernel32 (0x0033fe88)
  44 0x7b85af4f in kernel32 (+0x4af4e) (0x0033fec8)
  45 0x7bc71da0 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  46 0x7bc7485d call_thread_func+0x7c() in ntdll (0x0033ffa8)
  47 0x7bc71d7e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  48 0x7bc49f4e call_dll_entry_point+0x61d() in ntdll (0x0033ffe8)
0xb75b91a0: repe movq    0x0(%eax),%mm0
Modules:
Module    Address            Debug info    Name (117 modules)
PE      340000-  38c000    Deferred        wpcap
PE      400000-  966000    Export          cain
PE    10000000-10018000    Deferred        packet
ELF    7b800000-7ba15000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba15000    \               kernel32
ELF    7bc00000-7bcc3000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c933000-7c94f000    Deferred        pstorec<elf>
  \-PE    7c940000-7c94f000    \               pstorec
ELF    7d741000-7d779000    Deferred        usp10<elf>
  \-PE    7d750000-7d779000    \               usp10
ELF    7d779000-7d796000    Deferred        hnetcfg<elf>
  \-PE    7d780000-7d796000    \               hnetcfg
ELF    7d796000-7d7ef000    Deferred        riched20<elf>
  \-PE    7d7a0000-7d7ef000    \               riched20
ELF    7d7ef000-7d803000    Deferred        riched32<elf>
  \-PE    7d7f0000-7d803000    \               riched32
ELF    7d83d000-7d847000    Deferred        libltdl.so.7
ELF    7d847000-7d8b6000    Deferred        libodbc.so.1
ELF    7d9b6000-7d9c9000    Deferred        gnome-keyring-pkcs11.so
ELF    7d9c9000-7d9d2000    Deferred        librt.so.1
ELF    7d9d2000-7d9ea000    Deferred        libresolv.so.2
ELF    7d9ea000-7da33000    Deferred        libdbus-1.so.3
ELF    7da33000-7da45000    Deferred        libp11-kit.so.0
ELF    7da45000-7daca000    Deferred        libgcrypt.so.11
ELF    7daca000-7dadc000    Deferred        libtasn1.so.3
ELF    7dadc000-7dae5000    Deferred        libkrb5support.so.0
ELF    7dae5000-7db0d000    Deferred        libk5crypto.so.3
ELF    7db0d000-7dbdc000    Deferred        libkrb5.so.3
ELF    7dbdc000-7dbee000    Deferred        libavahi-client.so.3
ELF    7dbee000-7dcb2000    Deferred        libgnutls.so.26
ELF    7dcb2000-7dcf0000    Deferred        libgssapi_krb5.so.2
ELF    7dcf0000-7dd43000    Deferred        libcups.so.2
ELF    7dd83000-7ddb7000    Deferred        uxtheme<elf>
  \-PE    7dd90000-7ddb7000    \               uxtheme
ELF    7de17000-7de1c000    Deferred        libgpg-error.so.0
ELF    7de1c000-7de21000    Deferred        libcom_err.so.2
ELF    7de21000-7de2c000    Deferred        libxcursor.so.1
ELF    7de2c000-7de30000    Deferred        libkeyutils.so.1
ELF    7de30000-7de3e000    Deferred        libavahi-common.so.3
ELF    7de8c000-7deb6000    Deferred        libexpat.so.1
ELF    7deb6000-7deea000    Deferred        libfontconfig.so.1
ELF    7deea000-7defa000    Deferred        libxi.so.6
ELF    7defa000-7defe000    Deferred        libxcomposite.so.1
ELF    7defe000-7df07000    Deferred        libxrandr.so.2
ELF    7df07000-7df11000    Dwarf           libxrender.so.1
ELF    7df11000-7df17000    Deferred        libxxf86vm.so.1
ELF    7df17000-7df1b000    Deferred        libxinerama.so.1
ELF    7df1b000-7df3d000    Deferred        imm32<elf>
  \-PE    7df20000-7df3d000    \               imm32
ELF    7df3d000-7df44000    Deferred        libxdmcp.so.6
ELF    7df44000-7df65000    Deferred        libxcb.so.1
ELF    7df65000-7df7f000    Deferred        libice.so.6
ELF    7df7f000-7e0b3000    Deferred        libx11.so.6
ELF    7e0b3000-7e0c5000    Deferred        libxext.so.6
ELF    7e0c5000-7e158000    Dwarf           winex11<elf>
  \-PE    7e0d0000-7e158000    \               winex11
ELF    7e158000-7e16e000    Deferred        libz.so.1
ELF    7e16e000-7e208000    Deferred        libfreetype.so.6
ELF    7e20b000-7e211000    Deferred        libxfixes.so.3
ELF    7e21a000-7e242000    Deferred        msacm32<elf>
  \-PE    7e220000-7e242000    \               msacm32
ELF    7e242000-7e2ef000    Deferred        winmm<elf>
  \-PE    7e250000-7e2ef000    \               winmm
ELF    7e2ef000-7e327000    Deferred        winhttp<elf>
  \-PE    7e300000-7e327000    \               winhttp
ELF    7e327000-7e35f000    Deferred        oledlg<elf>
  \-PE    7e330000-7e35f000    \               oledlg
ELF    7e35f000-7e451000    Deferred        oleaut32<elf>
  \-PE    7e380000-7e451000    \               oleaut32
ELF    7e451000-7e4c6000    Deferred        rpcrt4<elf>
  \-PE    7e460000-7e4c6000    \               rpcrt4
ELF    7e4c6000-7e5ce000    Deferred        ole32<elf>
  \-PE    7e4e0000-7e5ce000    \               ole32
ELF    7e5ce000-7e5f4000    Deferred        odbc32<elf>
  \-PE    7e5d0000-7e5f4000    \               odbc32
ELF    7e5f4000-7e626000    Deferred        ws2_32<elf>
  \-PE    7e600000-7e626000    \               ws2_32
ELF    7e626000-7e651000    Deferred        netapi32<elf>
  \-PE    7e630000-7e651000    \               netapi32
ELF    7e651000-7e677000    Deferred        mpr<elf>
  \-PE    7e660000-7e677000    \               mpr
ELF    7e677000-7e699000    Deferred        iphlpapi<elf>
  \-PE    7e680000-7e699000    \               iphlpapi
ELF    7e699000-7e6d3000    Deferred        winspool<elf>
  \-PE    7e6a0000-7e6d3000    \               winspool
ELF    7e6d3000-7e7cb000    Deferred        comctl32<elf>
  \-PE    7e6e0000-7e7cb000    \               comctl32
ELF    7e7cb000-7e7e4000    Deferred        version<elf>
  \-PE    7e7d0000-7e7e4000    \               version
ELF    7e7e4000-7e8a1000    Dwarf           gdi32<elf>
  \-PE    7e7f0000-7e8a1000    \               gdi32
ELF    7e8a1000-7e9e1000    Dwarf           user32<elf>
  \-PE    7e8b0000-7e9e1000    \               user32
ELF    7e9e1000-7ea4b000    Deferred        shlwapi<elf>
  \-PE    7e9f0000-7ea4b000    \               shlwapi
ELF    7ea4b000-7ec5c000    Deferred        shell32<elf>
  \-PE    7ea60000-7ec5c000    \               shell32
ELF    7ec5c000-7ed3b000    Deferred        comdlg32<elf>
  \-PE    7ec60000-7ed3b000    \               comdlg32
ELF    7ed3b000-7ed9b000    Deferred        advapi32<elf>
  \-PE    7ed50000-7ed9b000    \               advapi32
ELF    7ef9b000-7efa8000    Deferred        libnss_files.so.2
ELF    7efa8000-7efc2000    Deferred        libnsl.so.1
ELF    7efc2000-7efee000    Deferred        libm.so.6
ELF    7efee000-7eff4000    Deferred        libuuid.so.1
ELF    7eff4000-7f000000    Deferred        libnss_nis.so.2
ELF    b7471000-b7475000    Deferred        libxau.so.6
ELF    b7475000-b747e000    Deferred        libnss_compat.so.2
ELF    b747f000-b7484000    Deferred        libdl.so.2
ELF    b7484000-b7629000    Dwarf           libc.so.6
ELF    b762a000-b7645000    Deferred        libpthread.so.0
ELF    b7646000-b764f000    Deferred        libsm.so.6
ELF    b7657000-b7799000    Dwarf           libwine.so.1
ELF    b779b000-b77bd000    Deferred        ld-linux.so.2
ELF    b77bd000-b77be000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001c    0
    00000046    0
    00000024    0
    00000018    0
    00000017    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    00000020    0
    00000019    0
    00000014    0
    00000013    0
00000021 plugplay.exe
    00000026    0
    00000023    0
    00000022    0
0000003b (D) C:\Program Files\Cain\Cain.exe
    0000003c    0 <==
0000003d explorer.exe
    0000003e    0
System information:
    Wine build: wine-1.4
    Platform: i386
    Host system: Linux
    Host version: 3.2.0-24-generic-pae

```Thanks ahead, any help is greatly appreciated.

---

### Post by oldos2er on 2012-04-30
Moved to Wine, thread title changed.

---

### Post by thatguruguy on 2012-04-30
According to [this]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2710"), Cain & Abel doesn't work particularly well on Wine.

I would guess that there is a Linux alternative that may work for you.  In fact, I could list some, but I'm not a fan of tools that crack passwords.

---

### Post by theRadish on 2012-04-30
I have looked at some alternatives, but Cain is the most user friendly and has the most functionality.

Thanks though :P

---

### Post by cogadh on 2012-05-01
It may be the most user friendly and have the most functionality, but it still won't work in Wine. You need to re-consider your alternatives or only run C&A in Windows.

---

