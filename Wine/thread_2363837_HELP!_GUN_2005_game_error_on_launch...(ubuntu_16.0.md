---
title: "HELP! GUN 2005 game error on launch...(ubuntu 16.04 LTS)"
date: 2017-06-15
forum: Wine
---

### Post by soulversion on 2017-06-15
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0052e930).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0052e930 ESP:0033f860 EBP:00000000 EFLAGS:00010202(  R- --  I   - - - )
 EAX:00000000 EBX:00000000 ECX:00000000 EDX:012f6680
 ESI:01329f60 EDI:0033f9a6
Stack dump:
0x0033f860:  0041201e 0139d5a0 012f9d00 0033fe30
0x0033f870:  01329f60 00000080 00000000 00000000
0x0033f880:  00000000 00000000 00000000 00000000
0x0033f890:  013a878c 00000000 00000000 00000000
0x0033f8a0:  00000000 00000000 00000000 00000000
0x0033f8b0:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x0052e930 in gun (+0x12e930) (0x00000000)
0x0052e930: movl    0x0(%ecx),%eax
Modules:
Module    Address            Debug info    Name (158 modules)
PE      400000-  86fac4    Export          gun
PE    18000000-18068000    Deferred        binkw32
ELF    7a800000-7a935000    Deferred        opengl32<elf>
  \-PE    7a820000-7a935000    \               opengl32
ELF    7b400000-7b7e0000    Deferred        kernel32<elf>
  \-PE    7b410000-7b7e0000    \               kernel32
ELF    7baea000-7bc00000    Deferred        libasound.so.2
ELF    7bc00000-7bcf6000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcf6000    \               ntdll
ELF    7bd00000-7bd16000    Deferred        midimap<elf>
  \-PE    7bd10000-7bd16000    \               midimap
ELF    7bd16000-7bd47000    Deferred        winealsa<elf>
  \-PE    7bd20000-7bd47000    \               winealsa
ELF    7bd47000-7bd73000    Deferred        libvorbis.so.0
ELF    7bd73000-7bdff000    Deferred        libvorbisenc.so.2
ELF    7bdff000-7be78000    Deferred        libsndfile.so.1
ELF    7be78000-7bf00000    Deferred        libpulsecommon-8.0.so
ELF    7c000000-7c004000    Deferred        <wine-loader>
ELF    7c00d000-7c06d000    Deferred        libflac.so.8
ELF    7c06d000-7c0c7000    Deferred        libpulse.so.0
ELF    7c0cf000-7c0e8000    Deferred        msacm32<elf>
  \-PE    7c0d0000-7c0e8000    \               msacm32
ELF    7c0e8000-7c111000    Deferred        winepulse<elf>
  \-PE    7c0f0000-7c111000    \               winepulse
ELF    7c111000-7c20c000    Deferred        comctl32<elf>
  \-PE    7c120000-7c20c000    \               comctl32
ELF    7c405000-7c40e000    Deferred        libogg.so.0
ELF    7c40e000-7c415000    Deferred        libasyncns.so.0
ELF    7c415000-7c41f000    Deferred        libwrap.so.0
ELF    7c41f000-7c456000    Deferred        uxtheme<elf>
  \-PE    7c430000-7c456000    \               uxtheme
ELF    7c466000-7c4b1000    Deferred        dinput<elf>
  \-PE    7c470000-7c4b1000    \               dinput
ELF    7c4b1000-7c4cd000    Deferred        dinput8<elf>
  \-PE    7c4c0000-7c4cd000    \               dinput8
ELF    7c5ce000-7c5da000    Deferred        libjson-c.so.2
ELF    7c5da000-7c5fd000    Deferred        mmdevapi<elf>
  \-PE    7c5e0000-7c5fd000    \               mmdevapi
ELF    7c5fd000-7c628000    Deferred        msvfw32<elf>
  \-PE    7c600000-7c628000    \               msvfw32
ELF    7c628000-7c63d000    Deferred        avicap32<elf>
  \-PE    7c630000-7c63d000    \               avicap32
ELF    7c63d000-7c665000    Deferred        devenum<elf>
  \-PE    7c640000-7c665000    \               devenum
ELF    7c995000-7c9cc000    Deferred        libtxc_dxtn.so
ELF    7cacc000-7cad8000    Deferred        libpciaccess.so.0
ELF    7cc4f000-7cc74000    Deferred        libdrm_intel.so.1
ELF    7cc95000-7d3e5000    Deferred        i965_dri.so
ELF    7d3e5000-7d406000    Deferred        libudev.so.1
ELF    7d406000-7d418000    Deferred        libdrm.so.2
ELF    7d418000-7d41e000    Deferred        libxcb-dri2.so.0
ELF    7d41e000-7d439000    Deferred        libxcb-glx.so.0
ELF    7d439000-7d43c000    Deferred        libx11-xcb.so.1
ELF    7d43c000-7d440000    Deferred        libxdamage.so.1
ELF    7d440000-7d45c000    Deferred        libglapi.so.0
ELF    7d45c000-7d464000    Deferred        libxcb-sync.so.1
ELF    7d464000-7d468000    Deferred        libxcb-present.so.0
ELF    7d468000-7d46c000    Deferred        libxcb-dri3.so.0
ELF    7d46c000-7d4dd000    Deferred        libgl.so.1
ELF    7d5dd000-7d5f3000    Deferred        libgpg-error.so.0
ELF    7d5f3000-7d668000    Deferred        libpcre.so.3
ELF    7d668000-7d685000    Deferred        libgcc_s.so.1
ELF    7d685000-7d734000    Deferred        libgcrypt.so.20
ELF    7d734000-7d75a000    Deferred        liblzma.so.5
ELF    7d75a000-7d763000    Deferred        librt.so.1
ELF    7d763000-7d789000    Deferred        libselinux.so.1
ELF    7d789000-7d817000    Deferred        libsystemd.so.0
ELF    7d817000-7d820000    Deferred        libffi.so.6
ELF    7d820000-7d839000    Deferred        libresolv.so.2
ELF    7d839000-7d893000    Deferred        libdbus-1.so.3
ELF    7d893000-7d91f000    Deferred        libgmp.so.10
ELF    7d91f000-7d954000    Deferred        libhogweed.so.4
ELF    7d954000-7d991000    Deferred        libnettle.so.6
ELF    7d991000-7d9f2000    Deferred        libp11-kit.so.0
ELF    7d9f2000-7dac8000    Deferred        libkrb5.so.3
ELF    7dac8000-7dc20000    Deferred        libgnutls.so.30
ELF    7dc83000-7dc86000    Deferred        libxshmfence.so.1
ELF    7dc86000-7dc9b000    Deferred        libtasn1.so.6
ELF    7dc9b000-7dccf000    Deferred        libidn.so.11
ELF    7dccf000-7dcdc000    Deferred        libkrb5support.so.0
ELF    7dcdc000-7dd0d000    Deferred        libk5crypto.so.3
ELF    7dd0d000-7dd21000    Deferred        libavahi-client.so.3
ELF    7dd21000-7dd2f000    Deferred        libavahi-common.so.3
ELF    7dd2f000-7dd81000    Deferred        libgssapi_krb5.so.2
ELF    7dd81000-7de08000    Deferred        libcups.so.2
ELF    7de0a000-7de18000    Deferred        libdrm_radeon.so.1
ELF    7de18000-7de22000    Deferred        libdrm_nouveau.so.2
ELF    7de29000-7de52000    Deferred        dxgi<elf>
  \-PE    7de30000-7de52000    \               dxgi
ELF    7de52000-7de7b000    Deferred        iphlpapi<elf>
  \-PE    7de60000-7de7b000    \               iphlpapi
ELF    7de7b000-7deba000    Deferred        winspool<elf>
  \-PE    7de80000-7deba000    \               winspool
ELF    7deba000-7def2000    Deferred        wbemprox<elf>
  \-PE    7dec0000-7def2000    \               wbemprox
ELF    7def2000-7df67000    Deferred        ddraw<elf>
  \-PE    7df00000-7df67000    \               ddraw
ELF    7dfd4000-7dfdb000    Deferred        libxfixes.so.3
ELF    7dfdb000-7dfe6000    Deferred        libxcursor.so.1
ELF    7dfe6000-7dff9000    Deferred        libxi.so.6
ELF    7dff9000-7dffd000    Deferred        libxcomposite.so.1
ELF    7dffd000-7e00a000    Deferred        libxrandr.so.2
ELF    7e00a000-7e016000    Deferred        libxrender.so.1
ELF    7e016000-7e01d000    Deferred        libxxf86vm.so.1
ELF    7e01d000-7e021000    Deferred        libxinerama.so.1
ELF    7e021000-7e028000    Deferred        libxdmcp.so.6
ELF    7e028000-7e02c000    Deferred        libxau.so.6
ELF    7e02c000-7e052000    Deferred        libxcb.so.1
ELF    7e052000-7e19d000    Deferred        libx11.so.6
ELF    7e19d000-7e1b2000    Deferred        libxext.so.6
ELF    7e1b3000-7e1b8000    Deferred        libkeyutils.so.1
ELF    7e1b8000-7e1bd000    Deferred        libcom_err.so.2
ELF    7e1d3000-7e260000    Deferred        winex11<elf>
  \-PE    7e1e0000-7e260000    \               winex11
ELF    7e260000-7e284000    Deferred        imm32<elf>
  \-PE    7e270000-7e284000    \               imm32
ELF    7e307000-7e331000    Deferred        libexpat.so.1
ELF    7e331000-7e37a000    Deferred        libfontconfig.so.1
ELF    7e37a000-7e3a5000    Deferred        libpng12.so.0
ELF    7e3a5000-7e3c0000    Deferred        libz.so.1
ELF    7e3c0000-7e470000    Deferred        libfreetype.so.6
ELF    7e491000-7e5c1000    Deferred        wined3d<elf>
  \-PE    7e4a0000-7e5c1000    \               wined3d
ELF    7e5c1000-7e600000    Deferred        d3d9<elf>
  \-PE    7e5d0000-7e600000    \               d3d9
ELF    7e600000-7e63a000    Deferred        ws2_32<elf>
  \-PE    7e610000-7e63a000    \               ws2_32
ELF    7e63a000-7e665000    Deferred        msacm32<elf>
  \-PE    7e640000-7e665000    \               msacm32
ELF    7e665000-7e71d000    Deferred        winmm<elf>
  \-PE    7e670000-7e71d000    \               winmm
ELF    7e71d000-7e84f000    Deferred        oleaut32<elf>
  \-PE    7e730000-7e84f000    \               oleaut32
ELF    7e84f000-7e8cf000    Deferred        rpcrt4<elf>
  \-PE    7e860000-7e8cf000    \               rpcrt4
ELF    7e8cf000-7e9ff000    Deferred        gdi32<elf>
  \-PE    7e8e0000-7e9ff000    \               gdi32
ELF    7e9ff000-7eb54000    Deferred        user32<elf>
  \-PE    7ea10000-7eb54000    \               user32
ELF    7eb54000-7ec8d000    Deferred        ole32<elf>
  \-PE    7eb70000-7ec8d000    \               ole32
ELF    7ec8d000-7ecd8000    Deferred        dsound<elf>
  \-PE    7ec90000-7ecd8000    \               dsound
ELF    7ecd8000-7ed4f000    Deferred        advapi32<elf>
  \-PE    7ecf0000-7ed4f000    \               advapi32
ELF    7ed4f000-7ed62000    Deferred        libnss_files.so.2
ELF    7ed62000-7ed6f000    Deferred        libnss_nis.so.2
ELF    7ed6f000-7ed8a000    Deferred        libnsl.so.1
ELF    7ef8a000-7efdf000    Deferred        libm.so.6
ELF    7efe6000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f73b3000-f73b8000    Deferred        libdl.so.2
ELF    f73b8000-f756e000    Deferred        libc.so.6
ELF    f756f000-f758c000    Deferred        libpthread.so.0
ELF    f75a1000-f75ab000    Deferred        libnss_compat.so.2
ELF    f75ad000-f7764000    Dwarf           libwine.so.1
ELF    f7766000-f778b000    Deferred        ld-linux.so.2
ELF    f778d000-f778e000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000020    0
    0000001f    0
    00000017    0
    00000016    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001e    0
    0000001b    0
    0000001a    0
    00000019    0
    00000018    0
    00000013    0
0000001c plugplay.exe
    00000022    0
    00000021    0
    0000001d    0
00000023 explorer.exe
    00000029    0
    00000028    0
    00000027    0
    00000026    0
    00000025    0
    00000024    0
0000002a (D) C:\Program Files\R.G. Mechanics\Gun\Gun.exe
    00000032    2
    00000031   15
    00000030   15
    0000002f    0
    0000002e    0
    0000002d    0
    0000002c    0
    0000002b    0 <==
System information:
    Wine build: wine-2.0.1
    Platform: i386
    Version: Windows XP
    Host system: Linux
    Host version: 4.8.0-54-generic

---

