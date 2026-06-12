---
title: "Problem with steam and wine"
date: 2013-12-05
forum: Wine
---

### Post by griffgar96 on 2013-12-05
I am very new to ubuntu 12.04 or linux period and i was trying to install steam under wine as opposed to the linux beta because for some reason my computer will not play the games after i download them. However once I get steam running in wine if goes until the point where i put in a confimation code because it registers my machine as a new computer (which it is) and then when it says "steam working..." it crashes and i get an error message that says in short, " this can be caused by a problem in the program or a deficiency in Wine." and then this code pops up and I would just like to know if theres anything I can do to fix this Heres the code: ```
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x7bc51b48).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc51b48 ESP:06a8b2cc EBP:06a8b3b4 EFLAGS:00010216(  R- --  I   -A-P- )
 EAX:0000000c EBX:7bca6ff4 ECX:00000000 EDX:00000010
 ESI:06a8b408 EDI:00000000
Stack dump:
0x06a8b2cc:  06a8b328 06a8b320 7bc46923 00000030
0x06a8b2dc:  00000000 06a8b320 7bc68433 b772c6a0
0x06a8b2ec:  00000000 3868af44 00000028 001ac6d0
0x06a8b2fc:  00110000 00000010 7bc3512f 06a8b418
0x06a8b30c:  00000000 00000360 00000000 00110000
0x06a8b31c:  7bca6ff4 06a8b380 7bc472f3 00000000
Backtrace:
=>0 0x7bc51b48 NtAdjustPrivilegesToken+0xf8() in ntdll (0x06a8b3b4)
  1 0x7ea39e3b AdjustTokenPrivileges+0x4a() in advapi32 (0x06a8b3e4)
  2 0x38234dae in steamclient (+0x234dad) (0x06a8b430)
  3 0x382358e4 in steamclient (+0x2358e3) (0x06a8b708)
  4 0x381e8d49 in steamclient (+0x1e8d48) (0x06a8b770)
  5 0x381eacf2 in steamclient (+0x1eacf1) (0x06a8b7a4)
  6 0x380ee459 in steamclient (+0xee458) (0x06a8b90c)
  7 0x380ef0cc in steamclient (+0xef0cb) (0x06a8cad0)
  8 0x3845e478 in steamclient (+0x45e477) (0x06a8cbe8)
  9 0x3845eda0 in steamclient (+0x45ed9f) (0x06a8cc38)
  10 0x380eef36 in steamclient (+0xeef35) (0x06a8de00)
  11 0x3849d807 in steamclient (+0x49d806) (0x06a8e210)
  12 0x3849da24 in steamclient (+0x49da23) (0x06a8e224)
  13 0x38450239 in steamclient (+0x450238) (0x06a8e448)
  14 0x3841c3c3 in steamclient (+0x41c3c2) (0x06a8e46c)
  15 0x3846201c in steamclient (+0x46201b) (0x06a8e478)
  16 0x38461ca3 in steamclient (+0x461ca2) (0x06a8e504)
  17 0x3819a222 in steamclient (+0x19a221) (0x06a8e574)
  18 0x3819a370 in steamclient (+0x19a36f) (0x06a8e588)
  19 0x3f00ca4f in tier0_s (+0xca4e) (0x06a8e5b8)
  20 0x3f00db0c in tier0_s (+0xdb0b) (0x06a8e5dc)
  21 0x3f011b70 in tier0_s (+0x11b6f) (0x06a8ea18)
  22 0x7bc71d90 call_thread_func_wrapper+0xb() in ntdll (0x06a8ea28)
  23 0x7bc7486d call_thread_func+0x7c() in ntdll (0x06a8eaf8)
  24 0x7bc71d6e RtlRaiseException+0x21() in ntdll (0x06a8eb18)
  25 0x7bc7a748 in ntdll (+0x6a747) (0x06a8f368)
  26 0xb75d8d4c start_thread+0xcb() in libpthread.so.0 (0x06a8f468)
0x7bc51b48 NtAdjustPrivilegesToken+0xf8 in ntdll: movl    %edx,0x0(%edi)
Modules:
Module    Address            Debug info    Name (184 modules)
PE      400000-  63d000    Deferred        steam
PE     10d0000- 1187000    Deferred        sdl2
PE     43d0000- 44ea000    Deferred        chromehtml
PE     44f0000- 58cb000    Deferred        libcef
PE     70e0000- 73ed000    Deferred        steamservice
PE    10000000-100b4000    Deferred        crashhandler
PE    30000000-302c1000    Deferred        steam
PE    38000000-38881000    Export          steamclient
PE    3a000000-3aaf4000    Deferred        steamui
PE    3f000000-3f0ac000    Export          tier0_s
PE    3f200000-3f2b1000    Deferred        vgui2_s
PE    3f600000-3f64b000    Deferred        vstdlib_s
PE    3f800000-3f82e000    Deferred        filesystem_stdio
PE    4ad00000-4b67f000    Deferred        icudt
PE    60000000-60021000    Deferred        cserhelper
PE    65ec0000-66072000    Deferred        avcodec-53
PE    68b80000-68ba7000    Deferred        avutil-51
PE    6ab00000-6ab33000    Deferred        avformat-53
ELF    7b800000-7ba29000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba29000    \               kernel32
ELF    7bc00000-7bcc3000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c288000-7c400000    Deferred        libvorbisenc.so.2
ELF    7c4bf000-7c4d5000    Deferred        wbemprox<elf>
  \-PE    7c4c0000-7c4d5000    \               wbemprox
ELF    7c4d5000-7c4ea000    Deferred        hid<elf>
  \-PE    7c4e0000-7c4ea000    \               hid
ELF    7c4ea000-7c4f2000    Deferred        libogg.so.0
ELF    7c4f2000-7c51d000    Deferred        libvorbis.so.0
ELF    7c51d000-7c56b000    Deferred        libflac.so.8
ELF    7c56b000-7c572000    Deferred        libasyncns.so.0
ELF    7c572000-7c5e4000    Deferred        libsndfile.so.1
ELF    7c5e4000-7c5ee000    Deferred        libwrap.so.0
ELF    7c5ee000-7c653000    Deferred        libpulsecommon-1.1.so
ELF    7c653000-7c6a1000    Deferred        libpulse.so.0
ELF    7c6a1000-7c793000    Deferred        libasound.so.2
ELF    7c79e000-7c7a5000    Deferred        libasound_module_pcm_pulse.so
ELF    7c7a5000-7c7d1000    Deferred        winealsa<elf>
  \-PE    7c7b0000-7c7d1000    \               winealsa
ELF    7c7d1000-7c7f4000    Deferred        mmdevapi<elf>
  \-PE    7c7e0000-7c7f4000    \               mmdevapi
ELF    7c7f4000-7c838000    Deferred        dsound<elf>
  \-PE    7c800000-7c838000    \               dsound
ELF    7c838000-7c876000    Deferred        rsaenh<elf>
  \-PE    7c840000-7c876000    \               rsaenh
ELF    7c876000-7c893000    Deferred        pdh<elf>
  \-PE    7c880000-7c893000    \               pdh
ELF    7c893000-7c8ad000    Deferred        imagehlp<elf>
  \-PE    7c8a0000-7c8ad000    \               imagehlp
ELF    7c9b3000-7ca40000    Deferred        msvcrt<elf>
  \-PE    7c9d0000-7ca40000    \               msvcrt
ELF    7ca40000-7ca79000    Deferred        usp10<elf>
  \-PE    7ca50000-7ca79000    \               usp10
ELF    7ca79000-7ca8e000    Deferred        dhcpcsvc<elf>
  \-PE    7ca80000-7ca8e000    \               dhcpcsvc
ELF    7ca8e000-7cab9000    Deferred        netapi32<elf>
  \-PE    7ca90000-7cab9000    \               netapi32
ELF    7cab9000-7cae5000    Deferred        secur32<elf>
  \-PE    7cac0000-7cae5000    \               secur32
ELF    7cae5000-7cb69000    Deferred        urlmon<elf>
  \-PE    7caf0000-7cb69000    \               urlmon
ELF    7cb69000-7cbd0000    Deferred        setupapi<elf>
  \-PE    7cb70000-7cbd0000    \               setupapi
ELF    7cbd0000-7cbe8000    Deferred        userenv<elf>
  \-PE    7cbe0000-7cbe8000    \               userenv
ELF    7cce8000-7ccf3000    Deferred        libpciaccess.so.0
ELF    7cdd8000-7cdfb000    Deferred        libdrm_intel.so.1
ELF    7cdfb000-7d1bd000    Deferred        libdricore9.1.7.so.1
ELF    7d1bd000-7d298000    Deferred        i965_dri.so
ELF    7d298000-7d2a5000    Deferred        libdrm.so.2
ELF    7d2a5000-7d2aa000    Deferred        libxcb-dri2.so.0
ELF    7d2aa000-7d2c2000    Deferred        libxcb-glx.so.0
ELF    7d2c2000-7d2d8000    Deferred        libglapi.so.0
ELF    7d2d8000-7d332000    Deferred        libgl.so.1
ELF    7d332000-7d3ec000    Deferred        opengl32<elf>
  \-PE    7d350000-7d3ec000    \               opengl32
ELF    7d3ec000-7d400000    Deferred        msimg32<elf>
  \-PE    7d3f0000-7d400000    \               msimg32
ELF    7d500000-7d51e000    Deferred        libgcc_s.so.1
ELF    7d51e000-7d540000    Deferred        iphlpapi<elf>
  \-PE    7d520000-7d540000    \               iphlpapi
ELF    7d640000-7d653000    Deferred        gnome-keyring-pkcs11.so
ELF    7d653000-7d65c000    Deferred        librt.so.1
ELF    7d65c000-7d6a5000    Deferred        libdbus-1.so.3
ELF    7d6a5000-7d6b7000    Deferred        libp11-kit.so.0
ELF    7d6b7000-7d73c000    Deferred        libgcrypt.so.11
ELF    7d73c000-7d80b000    Deferred        libkrb5.so.3
ELF    7d8cf000-7d8d3000    Deferred        libxdamage.so.1
ELF    7d8d3000-7d8d8000    Deferred        libgpg-error.so.0
ELF    7d8d8000-7d8ea000    Deferred        libtasn1.so.3
ELF    7d8ea000-7d912000    Deferred        libk5crypto.so.3
ELF    7d912000-7d9d6000    Deferred        libgnutls.so.26
ELF    7d9d6000-7da14000    Deferred        libgssapi_krb5.so.2
ELF    7da14000-7da67000    Deferred        libcups.so.2
ELF    7da67000-7db46000    Deferred        comdlg32<elf>
  \-PE    7da70000-7db46000    \               comdlg32
ELF    7db46000-7dc00000    Deferred        crypt32<elf>
  \-PE    7db50000-7dc00000    \               crypt32
ELF    7dd03000-7dd07000    Deferred        libkeyutils.so.1
ELF    7dd07000-7dd19000    Deferred        libavahi-client.so.3
ELF    7dd19000-7dd53000    Deferred        winspool<elf>
  \-PE    7dd20000-7dd53000    \               winspool
ELF    7dd53000-7de00000    Deferred        winmm<elf>
  \-PE    7dd60000-7de00000    \               winmm
ELF    7df00000-7df03000    Deferred        libx11-xcb.so.1
ELF    7df03000-7df0c000    Deferred        libkrb5support.so.0
ELF    7df0c000-7df1a000    Deferred        libavahi-common.so.3
ELF    7df1a000-7df42000    Deferred        msacm32<elf>
  \-PE    7df20000-7df42000    \               msacm32
ELF    7df42000-7df5a000    Deferred        libresolv.so.2
ELF    7df5e000-7df66000    Deferred        libjson.so.0
ELF    7df6c000-7dfa4000    Deferred        winhttp<elf>
  \-PE    7df70000-7dfa4000    \               winhttp
ELF    7dfa4000-7e002000    Deferred        dbghelp<elf>
  \-PE    7dfb0000-7e002000    \               dbghelp
ELF    7e002000-7e028000    Deferred        mpr<elf>
  \-PE    7e010000-7e028000    \               mpr
ELF    7e028000-7e097000    Deferred        wininet<elf>
  \-PE    7e030000-7e097000    \               wininet
ELF    7e097000-7e0ab000    Deferred        psapi<elf>
  \-PE    7e0a0000-7e0ab000    \               psapi
ELF    7e0d9000-7e10d000    Deferred        uxtheme<elf>
  \-PE    7e0e0000-7e10d000    \               uxtheme
ELF    7e10d000-7e113000    Deferred        libxfixes.so.3
ELF    7e113000-7e11e000    Deferred        libxcursor.so.1
ELF    7e11e000-7e123000    Deferred        libcom_err.so.2
ELF    7e123000-7e12a000    Deferred        libnss_dns.so.2
ELF    7e12a000-7e12e000    Deferred        libnss_mdns4_minimal.so.2
ELF    7e16f000-7e199000    Deferred        libexpat.so.1
ELF    7e199000-7e1cd000    Deferred        libfontconfig.so.1
ELF    7e1cd000-7e1dd000    Deferred        libxi.so.6
ELF    7e1dd000-7e1e1000    Deferred        libxcomposite.so.1
ELF    7e1e1000-7e1ea000    Deferred        libxrandr.so.2
ELF    7e1ea000-7e1f4000    Deferred        libxrender.so.1
ELF    7e1f4000-7e1fa000    Deferred        libxxf86vm.so.1
ELF    7e1fa000-7e1fe000    Deferred        libxinerama.so.1
ELF    7e1fe000-7e220000    Deferred        imm32<elf>
  \-PE    7e200000-7e220000    \               imm32
ELF    7e220000-7e227000    Deferred        libxdmcp.so.6
ELF    7e227000-7e22b000    Deferred        libxau.so.6
ELF    7e22b000-7e24c000    Deferred        libxcb.so.1
ELF    7e24c000-7e252000    Deferred        libuuid.so.1
ELF    7e252000-7e26c000    Deferred        libice.so.6
ELF    7e26c000-7e3a0000    Deferred        libx11.so.6
ELF    7e3a0000-7e3b2000    Deferred        libxext.so.6
ELF    7e3b2000-7e3bb000    Deferred        libsm.so.6
ELF    7e3bb000-7e44f000    Deferred        winex11<elf>
  \-PE    7e3d0000-7e44f000    \               winex11
ELF    7e44f000-7e465000    Deferred        libz.so.1
ELF    7e465000-7e4ff000    Deferred        libfreetype.so.6
ELF    7e4ff000-7e575000    Deferred        rpcrt4<elf>
  \-PE    7e510000-7e575000    \               rpcrt4
ELF    7e575000-7e67d000    Deferred        ole32<elf>
  \-PE    7e590000-7e67d000    \               ole32
ELF    7e67d000-7e76f000    Deferred        oleaut32<elf>
  \-PE    7e690000-7e76f000    \               oleaut32
ELF    7e76f000-7e7d9000    Deferred        shlwapi<elf>
  \-PE    7e780000-7e7d9000    \               shlwapi
ELF    7e7d9000-7e9ec000    Deferred        shell32<elf>
  \-PE    7e7f0000-7e9ec000    \               shell32
ELF    7e9ec000-7ea05000    Deferred        version<elf>
  \-PE    7e9f0000-7ea05000    \               version
ELF    7ea05000-7ea67000    Dwarf           advapi32<elf>
  \-PE    7ea10000-7ea67000    \               advapi32
ELF    7ea67000-7eb24000    Deferred        gdi32<elf>
  \-PE    7ea70000-7eb24000    \               gdi32
ELF    7eb24000-7ec64000    Deferred        user32<elf>
  \-PE    7eb40000-7ec64000    \               user32
ELF    7ec64000-7ed5d000    Deferred        comctl32<elf>
  \-PE    7ec70000-7ed5d000    \               comctl32
ELF    7ed5d000-7ed8f000    Deferred        ws2_32<elf>
  \-PE    7ed60000-7ed8f000    \               ws2_32
ELF    7ed8f000-7ed9c000    Deferred        libnss_files.so.2
ELF    7ed9c000-7eda8000    Deferred        libnss_nis.so.2
ELF    7eda8000-7edc2000    Deferred        libnsl.so.1
ELF    7efd4000-7f000000    Deferred        libm.so.6
ELF    b7422000-b7427000    Deferred        libdl.so.2
ELF    b7427000-b75d1000    Dwarf           libc.so.6
ELF    b75d2000-b75ed000    Dwarf           libpthread.so.0
ELF    b75f5000-b75fe000    Deferred        libnss_compat.so.2
ELF    b75ff000-b7741000    Dwarf           libwine.so.1
ELF    b7743000-b7765000    Deferred        ld-linux.so.2
ELF    b7765000-b7766000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001f    0
    0000001e    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001c    0
    00000019    0
    00000014    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001d    0
    0000001b    0
00000021 explorer.exe
    00000022    0
00000023 (D) C:\Program Files\Steam\Steam.exe
    0000000b    0
    00000046    0
    00000045    0
    00000044    0
    00000043    0
    00000042    0
    00000041    0
    00000040    0
    0000003f    0 <==
    0000003d    0
    0000003c    0
    0000003b    0
    0000003a    0
    00000039    0
    00000038    0
    00000037    0
    00000036    0
    00000035    0
    00000034    0
    00000033    0
    00000032    0
    00000031    0
    00000030    0
    0000002d    0
    0000002a    0
    00000029    0
    00000028    0
    00000024    0
System information:
    Wine build: wine-1.4.1
    Platform: i386
    Host system: Linux
    Host version: 3.8.0-34-generic
```


Anything will help thank you so much

---

### Post by pdcant on 2013-12-06
Wine v1.7.8 was released sometime today to fix this problem caused by a Steam update. It fixed this problem on my Ubuntu amd64 v13.10.

---

### Post by neko4 on 2013-12-15
I am also very new to linux in general.  I installed wine.  Then I installed steam.  Now I get the following error.  Can anybody help to pinpoint what this issue is?

Thanks for your help.

```
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x7bc51b48).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7bc51b48 ESP:06d5b2cc EBP:06d5b3b4 EFLAGS:00210216(  R- --  I   -A-P- )
 EAX:0000000c EBX:7bca6ff4 ECX:00000000 EDX:00000010
 ESI:06d5b408 EDI:00000000
Stack dump:
0x06d5b2cc:  06d5b328 06d5b320 7bc46923 00000038
0x06d5b2dc:  00000000 06d5b320 7bc68453 f774e6a0
0x06d5b2ec:  00000000 3868af94 00000010 001c6f40
0x06d5b2fc:  00110000 00000010 7bc3512f 06d5b418
0x06d5b30c:  00000000 00000374 00000000 00110000
0x06d5b31c:  7bca6ff4 06d5b380 7bc472f3 00000000
000c: sel=0067 base=00000000 limit=00000000 16-bit r-x
Backtrace:
=>0 0x7bc51b48 NtAdjustPrivilegesToken+0xf8() in ntdll (0x06d5b3b4)
  1 0x7ea2fa4b AdjustTokenPrivileges+0x4a() in advapi32 (0x06d5b3e4)
  2 0x3823574e in steamclient (+0x23574d) (0x06d5b430)
  3 0x38236284 in steamclient (+0x236283) (0x06d5b708)
  4 0x381e9739 in steamclient (+0x1e9738) (0x06d5b770)
  5 0x381eb712 in steamclient (+0x1eb711) (0x06d5b7a4)
  6 0x380ef0d9 in steamclient (+0xef0d8) (0x06d5b90c)
  7 0x380efd3c in steamclient (+0xefd3b) (0x06d5cad0)
  8 0x3845e818 in steamclient (+0x45e817) (0x06d5cbe8)
  9 0x3845f140 in steamclient (+0x45f13f) (0x06d5cc38)
  10 0x380efba6 in steamclient (+0xefba5) (0x06d5de00)
  11 0x3849ddc7 in steamclient (+0x49ddc6) (0x06d5e210)
  12 0x3849dfe4 in steamclient (+0x49dfe3) (0x06d5e224)
  13 0x384506d9 in steamclient (+0x4506d8) (0x06d5e448)
  14 0x3841cbf3 in steamclient (+0x41cbf2) (0x06d5e46c)
  15 0x3846249c in steamclient (+0x46249b) (0x06d5e478)
  16 0x38462123 in steamclient (+0x462122) (0x06d5e504)
  17 0x3819af12 in steamclient (+0x19af11) (0x06d5e574)
  18 0x3819b060 in steamclient (+0x19b05f) (0x06d5e588)
  19 0x3f00ca4f in tier0_s (+0xca4e) (0x06d5e5b8)
  20 0x3f00db0c in tier0_s (+0xdb0b) (0x06d5e5dc)
  21 0x3f011b70 in tier0_s (+0x11b6f) (0x06d5ea18)
  22 0x7bc71db0 call_thread_func_wrapper+0xb() in ntdll (0x06d5ea28)
  23 0x7bc7486d call_thread_func+0x7c() in ntdll (0x06d5eaf8)
  24 0x7bc71d8e RtlRaiseException+0x21() in ntdll (0x06d5eb18)
  25 0x7bc7a748 in ntdll (+0x6a747) (0x06d5f368)
  26 0xf75f7d4c start_thread+0xcb() in libpthread.so.0 (0x06d5f468)
0x7bc51b48 NtAdjustPrivilegesToken+0xf8 in ntdll: movl    %edx,0x0(%edi)
Modules:
Module    Address            Debug info    Name (161 modules)
PE      400000-  63d000    Deferred        steam
PE      fd0000- 1087000    Deferred        sdl2
PE     42d0000- 43ea000    Deferred        chromehtml
PE     43f0000- 57cb000    Deferred        libcef
PE     6d60000- 706d000    Deferred        steamservice
PE    10000000-100b4000    Deferred        crashhandler
PE    30000000-302c1000    Deferred        steam
PE    38000000-38881000    Export          steamclient
PE    3a000000-3aaf4000    Deferred        steamui
PE    3f000000-3f0ac000    Export          tier0_s
PE    3f200000-3f2b1000    Deferred        vgui2_s
PE    3f600000-3f64b000    Deferred        vstdlib_s
PE    3f800000-3f82e000    Deferred        filesystem_stdio
PE    4ad00000-4b67f000    Deferred        icudt
PE    60000000-60021000    Deferred        cserhelper
PE    65ec0000-66072000    Deferred        avcodec-53
PE    68b80000-68ba7000    Deferred        avutil-51
PE    6ab00000-6ab33000    Deferred        avformat-53
ELF    7932d000-79343000    Deferred        wbemprox<elf>
  \-PE    79330000-79343000    \               wbemprox
ELF    793cb000-794bd000    Deferred        libasound.so.2
ELF    794bd000-79500000    Deferred        dsound<elf>
  \-PE    794c0000-79500000    \               dsound
ELF    79802000-79817000    Deferred        hid<elf>
  \-PE    79810000-79817000    \               hid
ELF    79836000-7b800000    Deferred        libnvidia-glcore.so.319.32
ELF    7b800000-7ba15000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba15000    \               kernel32
ELF    7ba1d000-7ba49000    Deferred        winealsa<elf>
  \-PE    7ba20000-7ba49000    \               winealsa
ELF    7bc00000-7bcc3000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bcdd000-7bd00000    Deferred        mmdevapi<elf>
  \-PE    7bce0000-7bd00000    \               mmdevapi
ELF    7be03000-7be41000    Deferred        rsaenh<elf>
  \-PE    7be10000-7be41000    \               rsaenh
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7bf04000-7bf21000    Deferred        pdh<elf>
  \-PE    7bf10000-7bf21000    \               pdh
ELF    7bf21000-7bf3b000    Deferred        imagehlp<elf>
  \-PE    7bf30000-7bf3b000    \               imagehlp
ELF    7bf3b000-7bfc8000    Deferred        msvcrt<elf>
  \-PE    7bf50000-7bfc8000    \               msvcrt
ELF    7bfc8000-7c000000    Deferred        usp10<elf>
  \-PE    7bfd0000-7c000000    \               usp10
ELF    7c423000-7c44e000    Deferred        netapi32<elf>
  \-PE    7c430000-7c44e000    \               netapi32
ELF    7c44e000-7c47a000    Deferred        secur32<elf>
  \-PE    7c450000-7c47a000    \               secur32
ELF    7c47a000-7c4fe000    Deferred        urlmon<elf>
  \-PE    7c490000-7c4fe000    \               urlmon
ELF    7c4fe000-7c565000    Deferred        setupapi<elf>
  \-PE    7c510000-7c565000    \               setupapi
PE    7d0d0000-7d0d3000    Deferred        dhcpcsvc
ELF    7d0db000-7d0f3000    Deferred        userenv<elf>
  \-PE    7d0e0000-7d0f3000    \               userenv
ELF    7d0f3000-7d12b000    Deferred        winhttp<elf>
  \-PE    7d100000-7d12b000    \               winhttp
ELF    7d32b000-7d32f000    Deferred        libnvidia-tls.so.319.32
ELF    7d32f000-7d431000    Deferred        libgl.so.1
ELF    7d446000-7d500000    Deferred        opengl32<elf>
  \-PE    7d460000-7d500000    \               opengl32
ELF    7d600000-7d622000    Deferred        iphlpapi<elf>
  \-PE    7d610000-7d622000    \               iphlpapi
ELF    7d622000-7d640000    Deferred        libgcc_s.so.1
ELF    7d640000-7d649000    Deferred        librt.so.1
ELF    7d649000-7d6ce000    Deferred        libgcrypt.so.11
ELF    7d6ce000-7d79d000    Deferred        libkrb5.so.3
ELF    7d79d000-7d861000    Deferred        libgnutls.so.26
ELF    7d901000-7d906000    Deferred        libgpg-error.so.0
ELF    7d906000-7d91e000    Deferred        libresolv.so.2
ELF    7d91e000-7d967000    Deferred        libdbus-1.so.3
ELF    7d967000-7d979000    Deferred        libp11-kit.so.0
ELF    7d979000-7d98b000    Deferred        libtasn1.so.3
ELF    7d98b000-7d994000    Deferred        libkrb5support.so.0
ELF    7d994000-7d9bc000    Deferred        libk5crypto.so.3
ELF    7d9bc000-7da9b000    Deferred        comdlg32<elf>
  \-PE    7d9c0000-7da9b000    \               comdlg32
ELF    7da9b000-7db53000    Deferred        crypt32<elf>
  \-PE    7daa0000-7db53000    \               crypt32
ELF    7db53000-7dc00000    Deferred        winmm<elf>
  \-PE    7db60000-7dc00000    \               winmm
ELF    7dd01000-7dd13000    Deferred        libavahi-client.so.3
ELF    7dd13000-7dd51000    Deferred        libgssapi_krb5.so.2
ELF    7dd51000-7dda4000    Deferred        libcups.so.2
ELF    7dde1000-7dde5000    Deferred        libkeyutils.so.1
ELF    7dde6000-7ddfa000    Deferred        msimg32<elf>
  \-PE    7ddf0000-7ddfa000    \               msimg32
ELF    7ddfa000-7de34000    Deferred        winspool<elf>
  \-PE    7de00000-7de34000    \               winspool
ELF    7de34000-7de5c000    Deferred        msacm32<elf>
  \-PE    7de40000-7de5c000    \               msacm32
ELF    7de5c000-7deba000    Deferred        dbghelp<elf>
  \-PE    7de60000-7deba000    \               dbghelp
ELF    7deba000-7dee0000    Deferred        mpr<elf>
  \-PE    7dec0000-7dee0000    \               mpr
ELF    7dee0000-7df4f000    Deferred        wininet<elf>
  \-PE    7def0000-7df4f000    \               wininet
ELF    7df4f000-7df63000    Deferred        psapi<elf>
  \-PE    7df50000-7df63000    \               psapi
ELF    7e0ad000-7e0e1000    Deferred        uxtheme<elf>
  \-PE    7e0b0000-7e0e1000    \               uxtheme
ELF    7e0e1000-7e0e7000    Deferred        libxfixes.so.3
ELF    7e0e7000-7e0f2000    Deferred        libxcursor.so.1
ELF    7e0f2000-7e0f7000    Deferred        libcom_err.so.2
ELF    7e0f7000-7e105000    Deferred        libavahi-common.so.3
ELF    7e166000-7e190000    Deferred        libexpat.so.1
ELF    7e190000-7e1c4000    Deferred        libfontconfig.so.1
ELF    7e1c4000-7e1d4000    Deferred        libxi.so.6
ELF    7e1d4000-7e1d8000    Deferred        libxcomposite.so.1
ELF    7e1d8000-7e1e1000    Deferred        libxrandr.so.2
ELF    7e1e1000-7e1eb000    Deferred        libxrender.so.1
ELF    7e1eb000-7e1f1000    Deferred        libxxf86vm.so.1
ELF    7e1f1000-7e213000    Deferred        imm32<elf>
  \-PE    7e200000-7e213000    \               imm32
ELF    7e213000-7e21a000    Deferred        libxdmcp.so.6
ELF    7e21a000-7e23b000    Deferred        libxcb.so.1
ELF    7e23b000-7e241000    Deferred        libuuid.so.1
ELF    7e241000-7e25b000    Deferred        libice.so.6
ELF    7e25b000-7e38f000    Deferred        libx11.so.6
ELF    7e38f000-7e3a1000    Deferred        libxext.so.6
ELF    7e3b6000-7e449000    Deferred        winex11<elf>
  \-PE    7e3c0000-7e449000    \               winex11
ELF    7e449000-7e45f000    Deferred        libz.so.1
ELF    7e45f000-7e4f9000    Deferred        libfreetype.so.6
ELF    7e4f9000-7e56e000    Deferred        rpcrt4<elf>
  \-PE    7e500000-7e56e000    \               rpcrt4
ELF    7e56e000-7e676000    Deferred        ole32<elf>
  \-PE    7e580000-7e676000    \               ole32
ELF    7e676000-7e768000    Deferred        oleaut32<elf>
  \-PE    7e690000-7e768000    \               oleaut32
ELF    7e768000-7e7d2000    Deferred        shlwapi<elf>
  \-PE    7e780000-7e7d2000    \               shlwapi
ELF    7e7d2000-7e9e3000    Deferred        shell32<elf>
  \-PE    7e7e0000-7e9e3000    \               shell32
ELF    7e9e3000-7e9fc000    Deferred        version<elf>
  \-PE    7e9f0000-7e9fc000    \               version
ELF    7e9fc000-7ea5c000    Dwarf           advapi32<elf>
  \-PE    7ea10000-7ea5c000    \               advapi32
ELF    7ea5c000-7eb19000    Deferred        gdi32<elf>
  \-PE    7ea70000-7eb19000    \               gdi32
ELF    7eb19000-7ec59000    Deferred        user32<elf>
  \-PE    7eb30000-7ec59000    \               user32
ELF    7ec59000-7ed51000    Deferred        comctl32<elf>
  \-PE    7ec60000-7ed51000    \               comctl32
ELF    7ed51000-7ed83000    Deferred        ws2_32<elf>
  \-PE    7ed60000-7ed83000    \               ws2_32
ELF    7ed83000-7ed90000    Deferred        libnss_files.so.2
ELF    7ed90000-7ed9c000    Deferred        libnss_nis.so.2
ELF    7ed9c000-7edb6000    Deferred        libnsl.so.1
ELF    7edb6000-7edbf000    Deferred        libnss_compat.so.2
ELF    7efbf000-7efeb000    Deferred        libm.so.6
ELF    7efec000-7eff0000    Deferred        libxinerama.so.1
ELF    7eff0000-7eff9000    Deferred        libsm.so.6
ELF    f7441000-f7446000    Deferred        libdl.so.2
ELF    f7446000-f75f0000    Dwarf           libc.so.6
ELF    f75f1000-f760c000    Dwarf           libpthread.so.0
ELF    f760c000-f7610000    Deferred        libxau.so.6
ELF    f7621000-f7763000    Dwarf           libwine.so.1
ELF    f7765000-f7787000    Deferred        ld-linux.so.2
ELF    f7787000-f7788000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000002d    0
    0000001e    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001c    0
    00000019    0
    00000014    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001d    0
    0000001b    0
00000045 explorer.exe
    00000046    0
00000023 (D) C:\Program Files (x86)\Steam\Steam.exe
    0000001f    0
    0000002a    0
    0000002c    0
    0000002b    0
    00000031    0
    0000000b    0
    00000028    0
    00000018    0
    0000000d    0
    00000017    0 <==
    0000002f    0
    00000044    0
    00000021    0
    0000000c    0
    00000022    0
    0000003c    0
    00000039    0
    00000035    0
    0000003d    0
    00000041    0
    0000003f    0
    00000042    0
    0000003e    0
    00000040    0
    00000038    0
    00000009    0
    00000034    0
    00000024    0
00000037 steamerrorreporter.exe
    0000003b    0
    00000036    0
System information:
    Wine build: wine-1.4
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.8.0-29-generic
```

---

