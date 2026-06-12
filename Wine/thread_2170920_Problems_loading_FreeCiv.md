---
title: "Problems loading FreeCiv"
date: 2013-08-28
forum: Wine
---

### Post by heroquestelf on 2013-08-28
I'm running Ubuntu 13.04 on an Acer 3613. I've updated my graphics and sound drivers, and I'm having trouble with Wine. I can only get one or two games to run. Most of the time it errors out on me. This morning I lost my patience. I tried to run a game that I KNEW ran on an older dev of Ubuntu that won't run now, namely FreeCiv. Here is the error code it generated:

> Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb75c2c19).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b75c2c19 ESP:00d6fff0 EBP:00000000 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:b76ea000 ECX:08c0e040 EDX:7cb2c434
 ESI:bfce1c54 EDI:00000000
Stack dump:
0x00d6fff0:  7b8621ca 00000000 00000000 00000000
0x00d70000:  00905a4d 00000003 00000004 0000ffff
0x00d70010:  000000b8 00000000 00000040 00000000
0x00d70020:  00000000 00000000 00000000 00000000
0x00d70030:  00000000 00000000 00000000 000000e8
0x00d70040:  0eba1f0e cd09b400 4c01b821 685421cd
Backtrace:
=>0 0xb75c2c19 wine_call_on_stack+0x1d() in libwine.so.1 (0x00000000)
  1 0xb75c2bf7 wine_switch_to_stack+0x2a() in libwine.so.1 (0xbfce1c78)
  2 0x7bc54ed9 LdrInitializeThunk+0x341() in ntdll (0xbfce1cf8)
  3 0x7b862be7 __wine_kernel_init+0x71b() in kernel32 (0xbfce2b88)
  4 0x7bc5566e __wine_process_init+0x156() in ntdll (0xbfce2bd8)
  5 0xb75c1446 wine_init+0x13d() in libwine.so.1 (0xbfce2c18)
  6 0x7bf011ca main+0x13d() in <wine-loader> (0xbfce3058)
  7 0xb73eb935 __libc_start_main+0xf4() in libc.so.6 (0x00000000)
0xb75c2c19 wine_call_on_stack+0x1d in libwine.so.1: movl    %esi,%esp
Modules:
Module    Address            Debug info    Name (148 modules)
PE      230000-  276000    Deferred        sdl
PE      280000-  35a000    Deferred        iconv
PE      360000-  36b000    Deferred        intl
PE      370000-  3be000    Deferred        libgcrypt
PE      3c0000-  3cd000    Deferred        libgpg-error-0
PE      3d0000-  3eb000    Deferred        libggzcore-9
PE      3f0000-  3fa000    Deferred        libggzmod-4
PE      400000-  b6e000    Deferred        civclient
PE      d70000-  d95000    Export          libexpat
PE    10000000-1005b000    Deferred        sdl_mixer
PE    603c0000-6042a000    Deferred        exchndl
PE    60480000-607df000    Deferred        libgtk-win32-2.0-0
PE    61640000-6165d000    Deferred        libatk-1.0-0
PE    61b80000-61b98000    Deferred        zlib1
PE    62740000-6277b000    Deferred        libgobject-2.0-0
PE    62f80000-62f8f000    Deferred        libggz-2
PE    64040000-6405b000    Deferred        libgdk_pixbuf-2.0-0
PE    64280000-642bd000    Deferred        libpango-1.0-0
PE    672c0000-67382000    Deferred        libglib-2.0-0
PE    67580000-675b6000    Deferred        libpng13
PE    67ac0000-67b2b000    Deferred        libcairo-2
PE    69f80000-69f93000    Deferred        libpangowin32-1.0-0
PE    6b040000-6b0df000    Deferred        libgdk-win32-2.0-0
PE    6c1c0000-6c1cd000    Deferred        libpangocairo-1.0-0
PE    6ca00000-6ca0a000    Deferred        libgmodule-2.0-0
PE    6df00000-6df3a000    Deferred        libggz-gtk-1
ELF    7b800000-7ba44000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba44000    \               kernel32
ELF    7bc00000-7bce4000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bce4000    \               ntdll
ELF    7bf00000-7bf04000    Dwarf           <wine-loader>
ELF    7c975000-7c9e5000    Deferred        dbghelp<elf>
  \-PE    7c980000-7c9e5000    \               dbghelp
ELF    7c9e5000-7ca00000    Deferred        imagehlp<elf>
  \-PE    7c9f0000-7ca00000    \               imagehlp
ELF    7cb01000-7cb15000    Deferred        psapi<elf>
  \-PE    7cb10000-7cb15000    \               psapi
ELF    7cb15000-7cb32000    Deferred        msimtf<elf>
  \-PE    7cb20000-7cb32000    \               msimtf
ELF    7d333000-7d33b000    Deferred        libogg.so.0
ELF    7d33b000-7d367000    Deferred        libvorbis.so.0
ELF    7d367000-7d4df000    Deferred        libvorbisenc.so.2
ELF    7d4df000-7d52f000    Deferred        libflac.so.8
ELF    7d52f000-7d536000    Deferred        libasyncns.so.0
ELF    7d536000-7d5aa000    Deferred        libsndfile.so.1
ELF    7d5aa000-7d5b4000    Deferred        libwrap.so.0
ELF    7d5b4000-7d61f000    Deferred        libpulsecommon-3.0.so
ELF    7d61f000-7d629000    Deferred        libjson.so.0
ELF    7d629000-7d678000    Deferred        libpulse.so.0
ELF    7d678000-7d76a000    Deferred        libasound.so.2
ELF    7d775000-7d77c000    Deferred        libasound_module_pcm_pulse.so
ELF    7d783000-7d7b4000    Deferred        winealsa<elf>
  \-PE    7d790000-7d7b4000    \               winealsa
ELF    7d7b4000-7d8f9000    Deferred        oleaut32<elf>
  \-PE    7d7d0000-7d8f9000    \               oleaut32
ELF    7d8f9000-7d91e000    Deferred        mmdevapi<elf>
  \-PE    7d900000-7d91e000    \               mmdevapi
ELF    7d91e000-7d96b000    Deferred        dsound<elf>
  \-PE    7d920000-7d96b000    \               dsound
ELF    7d96b000-7d974000    Deferred        librt.so.1
ELF    7d974000-7d979000    Deferred        libgpg-error.so.0
ELF    7d979000-7d990000    Deferred        libresolv.so.2
ELF    7d990000-7d994000    Deferred        libkeyutils.so.1
ELF    7d994000-7d9de000    Deferred        libdbus-1.so.3
ELF    7d9de000-7d9f2000    Deferred        libp11-kit.so.0
ELF    7d9f2000-7da04000    Deferred        libtasn1.so.3
ELF    7da04000-7da88000    Deferred        libgcrypt.so.11
ELF    7da88000-7da91000    Deferred        libkrb5support.so.0
ELF    7da91000-7da96000    Deferred        libcom_err.so.2
ELF    7da96000-7dabe000    Deferred        libk5crypto.so.3
ELF    7dabe000-7db8c000    Deferred        libkrb5.so.3
ELF    7db8c000-7db9e000    Deferred        libavahi-client.so.3
ELF    7db9e000-7dbac000    Deferred        libavahi-common.so.3
ELF    7dbac000-7dc71000    Deferred        libgnutls.so.26
ELF    7dc71000-7dcae000    Deferred        libgssapi_krb5.so.2
ELF    7dcae000-7dd0d000    Deferred        libcups.so.2
ELF    7dd13000-7dd26000    Deferred        gnome-keyring-pkcs11.so
ELF    7dd3e000-7dd75000    Deferred        uxtheme<elf>
  \-PE    7dd40000-7dd75000    \               uxtheme
ELF    7dd75000-7dd7c000    Deferred        libxfixes.so.3
ELF    7dd7c000-7dd87000    Deferred        libxcursor.so.1
ELF    7de08000-7de30000    Deferred        libexpat.so.1
ELF    7de30000-7de69000    Deferred        libfontconfig.so.1
ELF    7de69000-7de79000    Deferred        libxi.so.6
ELF    7de79000-7de7d000    Deferred        libxcomposite.so.1
ELF    7de7d000-7de88000    Deferred        libxrandr.so.2
ELF    7de88000-7de92000    Deferred        libxrender.so.1
ELF    7de92000-7de98000    Deferred        libxxf86vm.so.1
ELF    7de98000-7de9f000    Deferred        libxdmcp.so.6
ELF    7de9f000-7dec1000    Deferred        libxcb.so.1
ELF    7dec1000-7dedb000    Deferred        libice.so.6
ELF    7dedb000-7e012000    Deferred        libx11.so.6
ELF    7e012000-7e024000    Deferred        libxext.so.6
ELF    7e024000-7e0d5000    Deferred        winex11<elf>
  \-PE    7e030000-7e0d5000    \               winex11
ELF    7e0d5000-7e0ee000    Deferred        libz.so.1
ELF    7e0ee000-7e189000    Deferred        libfreetype.so.6
ELF    7e1a2000-7e1c7000    Deferred        iphlpapi<elf>
  \-PE    7e1b0000-7e1c7000    \               iphlpapi
ELF    7e1c7000-7e1e3000    Deferred        wsock32<elf>
  \-PE    7e1d0000-7e1e3000    \               wsock32
ELF    7e1e3000-7e224000    Deferred        winspool<elf>
  \-PE    7e1f0000-7e224000    \               winspool
ELF    7e224000-7e312000    Deferred        comdlg32<elf>
  \-PE    7e230000-7e312000    \               comdlg32
ELF    7e312000-7e336000    Deferred        imm32<elf>
  \-PE    7e320000-7e336000    \               imm32
ELF    7e336000-7e36a000    Deferred        ws2_32<elf>
  \-PE    7e340000-7e36a000    \               ws2_32
ELF    7e36a000-7e489000    Deferred        comctl32<elf>
  \-PE    7e370000-7e489000    \               comctl32
ELF    7e489000-7e4ff000    Deferred        shlwapi<elf>
  \-PE    7e4a0000-7e4ff000    \               shlwapi
ELF    7e4ff000-7e73d000    Deferred        shell32<elf>
  \-PE    7e510000-7e73d000    \               shell32
ELF    7e73d000-7e7df000    Deferred        msvcrt<elf>
  \-PE    7e750000-7e7df000    \               msvcrt
ELF    7e7df000-7e80b000    Deferred        msacm32<elf>
  \-PE    7e7e0000-7e80b000    \               msacm32
ELF    7e80b000-7e895000    Deferred        rpcrt4<elf>
  \-PE    7e820000-7e895000    \               rpcrt4
ELF    7e895000-7e9f7000    Deferred        ole32<elf>
  \-PE    7e8b0000-7e9f7000    \               ole32
ELF    7e9f7000-7ea12000    Deferred        version<elf>
  \-PE    7ea00000-7ea12000    \               version
ELF    7ea12000-7ea84000    Deferred        advapi32<elf>
  \-PE    7ea20000-7ea84000    \               advapi32
ELF    7ea84000-7eb65000    Deferred        gdi32<elf>
  \-PE    7ea90000-7eb65000    \               gdi32
ELF    7eb65000-7ecd5000    Deferred        user32<elf>
  \-PE    7eb80000-7ecd5000    \               user32
ELF    7ecd5000-7ed8b000    Deferred        winmm<elf>
  \-PE    7ece0000-7ed8b000    \               winmm
ELF    7ef8b000-7ef98000    Deferred        libnss_files.so.2
ELF    7ef98000-7efa4000    Deferred        libnss_nis.so.2
ELF    7efa4000-7efbd000    Deferred        libnsl.so.1
ELF    7efbd000-7f000000    Deferred        libm.so.6
ELF    b73c3000-b73cc000    Deferred        libnss_compat.so.2
ELF    b73cd000-b73d2000    Deferred        libdl.so.2
ELF    b73d2000-b7585000    Dwarf           libc.so.6
ELF    b7586000-b75a1000    Deferred        libpthread.so.0
ELF    b75a2000-b75a6000    Deferred        libxinerama.so.1
ELF    b75a6000-b75aa000    Deferred        libxau.so.6
ELF    b75aa000-b75b0000    Deferred        libuuid.so.1
ELF    b75b0000-b75b9000    Deferred        libsm.so.6
ELF    b75ba000-b76fe000    Dwarf           libwine.so.1
ELF    b7700000-b7722000    Deferred        ld-linux.so.2
ELF    b7722000-b7723000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Freeciv-2.1.3-gtk2\civclient.exe
    00000036    2
    00000035   15
    00000034    0
    00000033    0
    00000009    0 <==
0000000e services.exe
    00000032    0
    0000001f    0
    00000019    0
    00000018    0
    00000017    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001d    0
    0000001a    0
    00000014    0
    00000013    0
0000001b plugplay.exe
    00000021    0
    0000001e    0
    0000001c    0
00000026 explorer.exe
    00000027    0
System information:
    Wine build: wine-1.4.1
    Platform: i386
    Host system: Linux
    Host version: 3.8.0-29-generic

Anybody got any suggestions?

---

### Post by Beren Camlost on 2013-08-28
FreeCiv is native, in the repositories, and should *not* be run through Wine.

---

