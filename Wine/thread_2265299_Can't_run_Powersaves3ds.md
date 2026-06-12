---
title: "Can't run Powersaves3ds"
date: 2015-02-14
forum: Wine
---

### Post by Brandon210395 on 2015-02-14
Hello, I just moved to Ubuntu from windows 8 64b, and I am having this problem while trying to run a  .exe program using Wine
after I installed the program, I tried to run the program and got an error:
```
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0049b56c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0049b56c ESP:0033d500 EBP:0033d584 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:0033d64c ECX:00000000 EDX:001f5608
 ESI:00ca7388 EDI:00ca7378
Stack dump:
0x0033d500:  239fb08d 00ca7378 00b654a4 0033d64c
0x0033d510:  00ca7378 0033d554 00521874 00000008
0x0033d520:  0051da25 0051da1f 0033d550 0000003c
0x0033d530:  00000000 0033d5d4 00000000 001f4bc0
0x0033d540:  00000000 0033d57c 00529d60 00000000
0x0033d550:  00ca0000 001f4b80 ffffffff 01555060
Backtrace:
=>0 0x0049b56c in powersaves3ds (+0x9b56c) (0x0033d584)
  1 0x0049d02a in powersaves3ds (+0x9d029) (0x0033d5b0)
  2 0x0049c82d in powersaves3ds (+0x9c82c) (0x0033d5e4)
  3 0x004c91c4 in powersaves3ds (+0xc91c3) (0x0033d610)
  4 0x004c8f26 in powersaves3ds (+0xc8f25) (0x0033d624)
  5 0x00497c65 in powersaves3ds (+0x97c64) (0x0033d664)
  6 0x0049835c in powersaves3ds (+0x9835b) (0x0033d67c)
  7 0x004985ec in powersaves3ds (+0x985eb) (0x0033d690)
  8 0x004985cf in powersaves3ds (+0x985ce) (0x0033d6a8)
  9 0x004cdd36 in powersaves3ds (+0xcdd35) (0x0033d718)
  10 0x004dea09 in powersaves3ds (+0xdea08) (0x0033d780)
  11 0x004b81ec in powersaves3ds (+0xb81eb) (0x0033d7c0)
  12 0x004b8542 in powersaves3ds (+0xb8541) (0x0033d824)
  13 0x004dd94c in powersaves3ds (+0xdd94b) (0x0033d878)
  14 0x004e3297 in powersaves3ds (+0xe3296) (0x0033f90c)
  15 0x004e2edd in powersaves3ds (+0xe2edc) (0x0033f998)
  16 0x004e412a in powersaves3ds (+0xe4129) (0x0033f9bc)
  17 0x004e4004 in powersaves3ds (+0xe4003) (0x0033f9d8)
  18 0x7ec514ea WINPROC_wrapper+0x19() in user32 (0x0033fa08)
  19 0x7ec51c26 in user32 (+0xa1c25) (0x0033fa58)
  20 0x7ec54383 in user32 (+0xa4382) (0x0033faa8)
  21 0x7ec15425 DispatchMessageW+0xb4() in user32 (0x0033fba8)
  22 0x0046e079 in powersaves3ds (+0x6e078) (0x0033fbe4)
  23 0x0046d4e8 in powersaves3ds (+0x6d4e7) (0x0033fc00)
  24 0x004bac00 in powersaves3ds (+0xbabff) (0x0033fc3c)
  25 0x004b7cfa in powersaves3ds (+0xb7cf9) (0x0033fc54)
  26 0x0041492e in powersaves3ds (+0x1492d) (0x0033fc80)
  27 0x0041fac5 in powersaves3ds (+0x1fac4) (0x0033fcb4)
  28 0x0041ed64 in powersaves3ds (+0x1ed63) (0x0033fd48)
  29 0x0046d336 in powersaves3ds (+0x6d335) (0x0033fd7c)
  30 0x0046d4e8 in powersaves3ds (+0x6d4e7) (0x0033fd98)
  31 0x004e0e39 in powersaves3ds (+0xe0e38) (0x0033fdcc)
  32 0x004209bc in powersaves3ds (+0x209bb) (0x0033fe60)
  33 0x7b85e5cc call_process_entry+0xb() in kernel32 (0x0033fe78)
  34 0x7b85f653 in kernel32 (+0x4f652) (0x0033feb8)
  35 0x7bc799b0 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  36 0x7bc7c93d call_thread_func+0x7c() in ntdll (0x0033ffa8)
  37 0x7bc7998e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  38 0x7bc4e8fe call_dll_entry_point+0x7ed() in ntdll (0x0033ffe8)
  39 0xb757950d wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  40 0xb75795cb wine_switch_to_stack+0x2a() in libwine.so.1 (0xbf8d30c8)
  41 0x7bc541e2 LdrInitializeThunk+0x3a1() in ntdll (0xbf8d3128)
  42 0x7b865bdd __wine_kernel_init+0xa0c() in kernel32 (0xbf8d4248)
  43 0x7bc547a3 __wine_process_init+0x192() in ntdll (0xbf8d42d8)
  44 0xb7576c70 wine_init+0x30f() in libwine.so.1 (0xbf8d4338)
  45 0x7bf00fdc main+0xfb() in <wine-loader> (0xbf8d4788)
  46 0xb73a1a83 __libc_start_main+0xf2() in libc.so.6 (0x00000000)
0x0049b56c: movl    0x0(%eax),%ecx
Modules:
Module    Address            Debug info    Name (125 modules)
PE      400000-  b90000    Export          powersaves3ds
ELF    7b800000-7ba5b000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba5b000    \               kernel32
ELF    7bc00000-7bcdb000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcdb000    \               ntdll
ELF    7bf00000-7bf04000    Dwarf           <wine-loader>
ELF    7d918000-7d94f000    Deferred        uxtheme<elf>
  \-PE    7d920000-7d94f000    \               uxtheme
ELF    7d94f000-7d955000    Deferred        libxfixes.so.3
ELF    7d955000-7d960000    Deferred        libxcursor.so.1
ELF    7d960000-7d971000    Deferred        libxi.so.6
ELF    7d971000-7d975000    Deferred        libxcomposite.so.1
ELF    7d975000-7d980000    Deferred        libxrandr.so.2
ELF    7d980000-7d98b000    Deferred        libxrender.so.1
ELF    7d98b000-7d991000    Deferred        libxxf86vm.so.1
ELF    7d991000-7d995000    Deferred        libxinerama.so.1
ELF    7d995000-7d99c000    Deferred        libxdmcp.so.6
ELF    7d99c000-7d9a0000    Deferred        libxau.so.6
ELF    7d9a0000-7d9c2000    Deferred        libxcb.so.1
ELF    7d9c2000-7daf6000    Deferred        libx11.so.6
ELF    7daf6000-7db09000    Deferred        libxext.so.6
ELF    7db20000-7dbb2000    Deferred        winex11<elf>
  \-PE    7db30000-7dbb2000    \               winex11
ELF    7dc0c000-7dc35000    Deferred        libexpat.so.1
ELF    7dc35000-7dc70000    Deferred        libfontconfig.so.1
ELF    7dc70000-7dc98000    Deferred        libpng12.so.0
ELF    7dc98000-7dd38000    Deferred        libfreetype.so.6
ELF    7dd4f000-7dd74000    Deferred        imm32<elf>
  \-PE    7dd60000-7dd74000    \               imm32
ELF    7dd74000-7dd9f000    Deferred        msacm32<elf>
  \-PE    7dd80000-7dd9f000    \               msacm32
ELF    7dd9f000-7de59000    Deferred        winmm<elf>
  \-PE    7ddb0000-7de59000    \               winmm
ELF    7de59000-7de6f000    Deferred        hid<elf>
  \-PE    7de60000-7de6f000    \               hid
ELF    7de6f000-7dfab000    Deferred        ole32<elf>
  \-PE    7de90000-7dfab000    \               ole32
ELF    7dfab000-7e0b2000    Deferred        comctl32<elf>
  \-PE    7dfb0000-7e0b2000    \               comctl32
ELF    7e0b2000-7e12c000    Deferred        shlwapi<elf>
  \-PE    7e0c0000-7e12c000    \               shlwapi
ELF    7e12c000-7e35f000    Deferred        shell32<elf>
  \-PE    7e140000-7e35f000    \               shell32
ELF    7e35f000-7e366000    Deferred        libffi.so.6
ELF    7e366000-7e397000    Deferred        libcrypt.so.1
ELF    7e397000-7e454000    Deferred        libsqlite3.so.0
ELF    7e454000-7e49b000    Deferred        libhx509.so.5
ELF    7e49b000-7e4aa000    Deferred        libheimbase.so.1
ELF    7e4aa000-7e4d3000    Deferred        libwind.so.0
ELF    7e4d3000-7e50f000    Deferred        libp11-kit.so.0
ELF    7e50f000-7e523000    Deferred        libtasn1.so.6
ELF    7e523000-7e53d000    Deferred        libz.so.1
ELF    7e53d000-7e553000    Deferred        libroken.so.18
ELF    7e553000-7e588000    Deferred        libhcrypto.so.4
ELF    7e588000-7e62e000    Deferred        libasn1.so.8
ELF    7e62e000-7e6b4000    Deferred        libkrb5.so.26
ELF    7e6b4000-7e6bd000    Deferred        libheimntlm.so.0
ELF    7e6bd000-7e743000    Deferred        libgcrypt.so.11
ELF    7e743000-7e809000    Deferred        libgnutls.so.26
ELF    7e809000-7e845000    Deferred        libgssapi.so.3
ELF    7e845000-7e860000    Deferred        libsasl2.so.2
ELF    7e860000-7e878000    Deferred        libresolv.so.2
ELF    7e878000-7e887000    Deferred        liblber-2.4.so.2
ELF    7e887000-7e8d9000    Deferred        libldap_r-2.4.so.2
ELF    7e8d9000-7e93d000    Deferred        wldap32<elf>
  \-PE    7e8e0000-7e93d000    \               wldap32
ELF    7e93d000-7e973000    Deferred        ws2_32<elf>
  \-PE    7e940000-7e973000    \               ws2_32
ELF    7e973000-7e9f4000    Deferred        rpcrt4<elf>
  \-PE    7e980000-7e9f4000    \               rpcrt4
ELF    7e9f4000-7ea0e000    Deferred        version<elf>
  \-PE    7ea00000-7ea0e000    \               version
ELF    7ea0e000-7ea80000    Deferred        advapi32<elf>
  \-PE    7ea20000-7ea80000    \               advapi32
ELF    7ea80000-7eb9d000    Deferred        gdi32<elf>
  \-PE    7ea90000-7eb9d000    \               gdi32
ELF    7eb9d000-7ecf7000    Dwarf           user32<elf>
  \-PE    7ebb0000-7ecf7000    \               user32
ELF    7ecf7000-7ed68000    Deferred        setupapi<elf>
  \-PE    7ed00000-7ed68000    \               setupapi
ELF    7ed68000-7ed75000    Deferred        libnss_files.so.2
ELF    7ed75000-7ed81000    Deferred        libnss_nis.so.2
ELF    7ed81000-7ed9a000    Deferred        libnsl.so.1
ELF    7ed9a000-7eda3000    Deferred        libnss_compat.so.2
ELF    7efa3000-7efe9000    Deferred        libm.so.6
ELF    7efec000-7f000000    Deferred        normaliz<elf>
  \-PE    7eff0000-7f000000    \               normaliz
ELF    b69d0000-b69f4000    Deferred        dwrite<elf>
  \-PE    b69e0000-b69f4000    \               dwrite
ELF    b69f4000-b69fd000    Deferred        libogg.so.0
ELF    b69fd000-b6a29000    Deferred        libvorbis.so.0
ELF    b6a29000-b6ba1000    Deferred        libvorbisenc.so.2
ELF    b6ba1000-b6bd5000    Deferred        libflac.so.8
ELF    b6bd5000-b6bde000    Deferred        librt.so.1
ELF    b6bde000-b6be5000    Deferred        libasyncns.so.0
ELF    b6be5000-b6c57000    Deferred        libsndfile.so.1
ELF    b6c57000-b6c61000    Deferred        libwrap.so.0
ELF    b6c61000-b6cac000    Deferred        libdbus-1.so.3
ELF    b6cac000-b6d1b000    Deferred        libpulsecommon-4.0.so
ELF    b6d1b000-b6d6a000    Deferred        libpulse.so.0
ELF    b6d6a000-b6ea0000    Deferred        oleaut32<elf>
  \-PE    b6d80000-b6ea0000    \               oleaut32
ELF    b7202000-b720d000    Deferred        libjson-c.so.2
ELF    b7224000-b724c000    Deferred        winepulse<elf>
  \-PE    b7230000-b724c000    \               winepulse
ELF    b724c000-b726e000    Deferred        mmdevapi<elf>
  \-PE    b7250000-b726e000    \               mmdevapi
ELF    b726e000-b72b7000    Deferred        dsound<elf>
  \-PE    b7270000-b72b7000    \               dsound
ELF    b72b7000-b72ca000    Deferred        gnome-keyring-pkcs11.so
ELF    b72ca000-b72fa000    Deferred        p11-kit-trust.so
ELF    b72fa000-b7320000    Deferred        iphlpapi<elf>
  \-PE    b7300000-b7320000    \               iphlpapi
ELF    b7320000-b734d000    Deferred        netapi32<elf>
  \-PE    b7330000-b734d000    \               netapi32
ELF    b734d000-b7380000    Deferred        secur32<elf>
  \-PE    b7350000-b7380000    \               secur32
ELF    b7382000-b7387000    Deferred        libgpg-error.so.0
ELF    b7388000-b7537000    Dwarf           libc.so.6
ELF    b7537000-b753c000    Deferred        libdl.so.2
ELF    b753d000-b7559000    Deferred        libpthread.so.0
ELF    b755a000-b755f000    Deferred        libcom_err.so.2
ELF    b7570000-b7725000    Dwarf           libwine.so.1
ELF    b7727000-b7749000    Deferred        ld-linux.so.2
ELF    b7749000-b774a000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001e    0
    0000001d    0
    00000018    0
    00000016    0
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
0000002a (D) C:\Program Files\Action Replay PowerSaves 3DS\PowerSaves3DS.exe
    00000034    1
    00000033    2
    00000032   15
    00000031   15
    00000030    0
    0000002f    0
    0000002e   15
    0000002d    0
    0000002c    0
    0000002b    0 <==
System information:
    Wine build: wine-1.6.2
    Platform: i386
    Host system: Linux
    Host version: 3.13.0-32-generic


``` 
can anybody help me?

---

### Post by Holger_Gehrke on 2015-02-14
That's the software for an Action Replay for the Nintendo 3DS, right ? It probably tried to talk to the driver for the Action Replay hardware, failed and crashed. There's no entry for this in the Wine Application Database at winehq.org (which is neither a good nor a bad sign in and of itself), but the best-rated action replay software in the db is one for the DSi in which everything but the connection to the hardware works - which makes it basically useless.

---

### Post by Brandon210395 on 2015-02-14
> **Holger_Gehrke said:**
> That's the software for an Action Replay for the Nintendo 3DS, right ? It probably tried to talk to the driver for the Action Replay hardware, failed and crashed. There's no entry for this in the Wine Application Database at winehq.org (which is neither a good nor a bad sign in and of itself), but the best-rated action replay software in the db is one for the DSi in which everything but the connection to the hardware works - which makes it basically useless.

Well how can I make wine recognize USB devices?
Thanks for helping me!

---

### Post by overdrank on 2015-02-14
Hi and welcome, moved to Wine :)

---

