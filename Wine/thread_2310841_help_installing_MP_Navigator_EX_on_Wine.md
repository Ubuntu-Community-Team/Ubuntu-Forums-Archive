---
title: "help installing MP Navigator EX on Wine"
date: 2016-01-22
forum: Wine
---

### Post by ardouronerous on 2016-01-22
The scanner that I'm using is a CanoScan LIDE 110, and I'm using MP  Navigator EX, the software that came with the scanner, on Windows XP via Virtualbox, to scan multiple  images with it, the software allows me to scan, e.g. four photos at once and it automatically auto crops the photos into four jpeg files,  instead  of me manually cropping the photos out, which is a pain staking  process, since I'm scanning lots of old photos.

I'd like to eliminate my use of Virtualbox, if I can. I've tried to install MP Navigator EX on Wine, but it doesn't install. Here's the output of backtrace.txt:

> Unhandled exception: page fault on read access to 0x00000009 in 32-bit code (0xb7456e86).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7456e86 ESP:0176d474 EBP:0176d4f8 EFLAGS:00010287(  R- --  I S - -P-C)
 EAX:00000000 EBX:7b8c1398 ECX:00000001 EDX:00003409
 ESI:ffffffff EDI:00000001
Stack dump:
0x0176d474:  00000009 ffffffff 7b8565ea 00000001
0x0176d484:  00000000 00000000 00000000 64616552
0x0176d494:  742e656d 00007478 00000000 00000000
0x0176d4a4:  00000000 00000000 00000000 7ffd4000
0x0176d4b4:  00003409 00000000 7b8522ae 40000001
0x0176d4c4:  00000000 00000001 00570034 00000000
Backtrace:
=>0 0xb7456e86 in libc.so.6 (+0x82e86) (0x0176d4f8)
  1 0x7b8565ea CompareStringA+0x359() in kernel32 (0x0176d4f8)
  2 0x7b856976 lstrcmpiA+0x65() in kernel32 (0x0176d548)
  3 0x0040c83d in setup (+0xc83c) (0x7b856910)
  4 0xfff0e483 (0x04244c8d)
0xb7456e86: repe movq    0x0(%edi),%mm1
Modules:
Module    Address            Debug info    Name (93 modules)
PE      400000-  45c000    Export          setup
PE    10000000-1000c000    Deferred        setuprsc
ELF    7b800000-7ba6b000    Dwarf           kernel32<elf>
  \-PE    7b820000-7ba6b000    \               kernel32
ELF    7bc00000-7bcf0000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcf0000    \               ntdll
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
ELF    7d83d000-7d881000    Deferred        usp10<elf>
  \-PE    7d840000-7d881000    \               usp10
ELF    7da09000-7da29000    Deferred        cabinet<elf>
  \-PE    7da10000-7da29000    \               cabinet
ELF    7da29000-7da9a000    Deferred        setupapi<elf>
  \-PE    7da30000-7da9a000    \               setupapi
ELF    7da9a000-7daae000    Deferred        libtasn1.so.6
ELF    7daae000-7dade000    Deferred        p11-kit-trust.so
ELF    7dade000-7dae5000    Deferred        libffi.so.6
ELF    7dae5000-7daea000    Deferred        libgpg-error.so.0
ELF    7daea000-7db02000    Deferred        libresolv.so.2
ELF    7db02000-7db4d000    Deferred        libdbus-1.so.3
ELF    7db4d000-7db89000    Deferred        libp11-kit.so.0
ELF    7db89000-7dc0e000    Deferred        libgcrypt.so.11
ELF    7dc0e000-7dc20000    Deferred        libtasn1.so.3
ELF    7dc20000-7dc2c000    Deferred        libkrb5support.so.0
ELF    7dc2c000-7dc5c000    Deferred        libk5crypto.so.3
ELF    7dc5c000-7dd1a000    Deferred        libkrb5.so.3
ELF    7dd1a000-7dd2c000    Deferred        libavahi-client.so.3
ELF    7dd2c000-7ddf5000    Deferred        libgnutls.so.26
ELF    7ddf5000-7de3b000    Deferred        libgssapi_krb5.so.2
ELF    7de3b000-7dea8000    Deferred        libcups.so.2
ELF    7deb0000-7dec3000    Deferred        gnome-keyring-pkcs11.so
ELF    7dec3000-7defc000    Deferred        uxtheme<elf>
  \-PE    7ded0000-7defc000    \               uxtheme
ELF    7defc000-7df02000    Deferred        libxfixes.so.3
ELF    7df02000-7df0d000    Deferred        libxcursor.so.1
ELF    7df0d000-7df1d000    Deferred        libxi.so.6
ELF    7df1d000-7df21000    Deferred        libxcomposite.so.1
ELF    7df21000-7df2c000    Deferred        libxrandr.so.2
ELF    7df2c000-7df37000    Deferred        libxrender.so.1
ELF    7df37000-7df3d000    Deferred        libxxf86vm.so.1
ELF    7df3d000-7df41000    Deferred        libxinerama.so.1
ELF    7df41000-7df48000    Deferred        libxdmcp.so.6
ELF    7df48000-7df4c000    Deferred        libxau.so.6
ELF    7df4c000-7df6e000    Deferred        libxcb.so.1
ELF    7df6e000-7e0a2000    Deferred        libx11.so.6
ELF    7e0a2000-7e0b5000    Deferred        libxext.so.6
ELF    7e0b7000-7e0bb000    Deferred        libkeyutils.so.1
ELF    7e0bb000-7e0c0000    Deferred        libcom_err.so.2
ELF    7e0c0000-7e0ce000    Deferred        libavahi-common.so.3
ELF    7e0d0000-7e164000    Deferred        winex11<elf>
  \-PE    7e0e0000-7e164000    \               winex11
ELF    7e164000-7e188000    Deferred        imm32<elf>
  \-PE    7e170000-7e188000    \               imm32
ELF    7e1cc000-7e1f5000    Deferred        libexpat.so.1
ELF    7e1f5000-7e230000    Deferred        libfontconfig.so.1
ELF    7e230000-7e258000    Deferred        libpng12.so.0
ELF    7e258000-7e271000    Deferred        libz.so.1
ELF    7e271000-7e311000    Deferred        libfreetype.so.6
ELF    7e32c000-7e3b2000    Deferred        rpcrt4<elf>
  \-PE    7e340000-7e3b2000    \               rpcrt4
ELF    7e3b2000-7e4f8000    Deferred        ole32<elf>
  \-PE    7e3d0000-7e4f8000    \               ole32
ELF    7e4f8000-7e532000    Deferred        oledlg<elf>
  \-PE    7e500000-7e532000    \               oledlg
ELF    7e532000-7e574000    Deferred        winspool<elf>
  \-PE    7e540000-7e574000    \               winspool
ELF    7e574000-7e680000    Deferred        comctl32<elf>
  \-PE    7e580000-7e680000    \               comctl32
ELF    7e680000-7e6fb000    Deferred        shlwapi<elf>
  \-PE    7e690000-7e6fb000    \               shlwapi
ELF    7e6fb000-7e946000    Deferred        shell32<elf>
  \-PE    7e710000-7e946000    \               shell32
ELF    7e946000-7ea35000    Deferred        comdlg32<elf>
  \-PE    7e950000-7ea35000    \               comdlg32
ELF    7ea35000-7eaaf000    Deferred        advapi32<elf>
  \-PE    7ea40000-7eaaf000    \               advapi32
ELF    7eaaf000-7ebd0000    Deferred        gdi32<elf>
  \-PE    7eac0000-7ebd0000    \               gdi32
ELF    7ebd0000-7ed2e000    Deferred        user32<elf>
  \-PE    7ebe0000-7ed2e000    \               user32
ELF    7ed2e000-7ed3b000    Deferred        libnss_files.so.2
ELF    7ed3b000-7ed47000    Deferred        libnss_nis.so.2
ELF    7ed47000-7ed60000    Deferred        libnsl.so.1
ELF    7ef9f000-7efe5000    Deferred        libm.so.6
ELF    7efe7000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    b73c5000-b73ce000    Deferred        libnss_compat.so.2
ELF    b73cf000-b73d4000    Deferred        libdl.so.2
ELF    b73d4000-b7582000    Dwarf           libc.so.6
ELF    b7582000-b759e000    Deferred        libpthread.so.0
ELF    b75b1000-b75ba000    Deferred        librt.so.1
ELF    b75ba000-b7770000    Dwarf           libwine.so.1
ELF    b7772000-b7794000    Deferred        ld-linux.so.2
ELF    b7794000-b7795000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 mpnx_4_0-win-4_03-ea23_2.exe
    00000009    0
0000000e services.exe
    0000001d    0
    0000001c    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    00000020    0
    00000019    0
    00000018    0
    00000013    0
0000001a plugplay.exe
    0000001f    0
    0000001e    0
    0000001b    0
00000021 explorer.exe
    00000025    0
    00000024    0
    00000023    0
    00000022    0
00000026 (D) C:\users\xxxx\Temp\WZSE0.TMP\mpnx_4_0-win-4_03-ea23_2\Setup.exe
    00000028    0 <==
    00000027    0
System information:
    Wine build: wine-1.8
    Platform: i386
    Version: Windows XP
    Host system: Linux
    Host version: 3.13.0-76-generic


---

