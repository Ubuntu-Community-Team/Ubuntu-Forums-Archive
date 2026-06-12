---
title: "[kubuntu] Hidden: Source: Crash after &quot;Sending Client Info&quot;"
date: 2013-06-12
forum: Wine
---

### Post by Tike on 2013-06-12
Hello, I recently installed kubuntu because I was sick of Windows.
I kept all my games including Hidden: Source. But when I try to go ingame it crashes after "Sending client info.." with this log:

Unhandled exception: page fault on read access to 0x00000024 in 32-bit code (0x0d3bb423).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0d3bb423 ESP:0033e550 EBP:00000002 EFLAGS:00210206(  R- --  I   - -P- )
 EAX:00000650 EBX:00000000 ECX:16d1c780 EDX:0724b1c0
 ESI:0d3cea18 EDI:00000090
Stack dump:
0x0033e550:  0d3cea18 005514b4 0d3bb452 16d10065
0x0033e560:  0d3cea18 005514b4 0d3cea18 16d10067
0x0033e570:  0d3bb7d5 16d10067 0d3cea18 16d10067
0x0033e580:  0d3cea3c 00000690 0d3cea18 0d3b98da
0x0033e590:  16d10001 ffffffff 00000000 00000009
0x0033e5a0:  0033fe70 0033e5e4 1000753b 00000003
Backtrace:
=>0 0x0d3bb423 in datacache (+0xb423) (0x00000002)
0x0d3bb423: movl	0x24(%ebx),%eax
Modules:
Module	Address			Debug info	Name (206 modules)
PE	  340000-  376000	Deferred        tier0
PE	  380000-  39e000	Deferred        vstdlib
PE	  3a0000-  3f4000	Deferred        filesystem_steam
PE	  400000-  41c000	Deferred        hl2
PE	 ce40000- ce55000	Deferred        inputsystem
PE	 d160000- d25e000	Deferred        datamodel
PE	 d370000- d3ad000	Deferred        dmserializers
PE	 d3b0000- d3d5000	Export          datacache
PE	 d4f0000- d5a5000	Deferred        materialsystem
PE	 d5b0000- d5c6000	Deferred        valve_avi
PE	 d5d0000- d6a0000	Deferred        vguimatsurface
PE	 d6a0000- d715000	Deferred        vgui2
PE	 d720000- d734000	Deferred        steam_api
PE	 d970000- d999000	Deferred        stdshader_dbg
PE	 d9a0000- d9d5000	Deferred        stdshader_dx6
PE	 d9e0000- da08000	Deferred        stdshader_dx7
PE	 da10000- da53000	Deferred        stdshader_dx8
PE	 da60000- da6f000	Deferred        unicode
PE	 dc80000- dcd1000	Deferred        stdshader_dx9
PE	 dde0000- de01000	Deferred        game_shader_generic
PE	 df40000- df76000	Deferred        soundemittersystem
PE	10000000-10030000	Deferred        launcher
PE	12760000-12947000	Deferred        gameui
PE	13f00000-13f10000	Deferred        vaudio_miles
PE	14eb0000-14f7b000	Deferred        serverbrowser
PE	20000000-205ef000	Deferred        engine
PE	21100000-21164000	Deferred        mss32
PE	22000000-22481000	Deferred        server
PE	24000000-2437e000	Deferred        client
PE	26000000-26138000	Deferred        vphysics
PE	26400000-26439000	Deferred        mssvoice.asi
PE	26f00000-26f2e000	Deferred        mssmp3.asi
PE	2a000000-2a0a8000	Deferred        shaderapidx9
PE	2c000000-2c3e3000	Deferred        studiorender
PE	30000000-302c4000	Deferred        steam
PE	38000000-38740000	Deferred        steamclient
ELF	38dd5000-38e62000	Deferred        msvcrt<elf>
  \-PE	38df0000-38e62000	\               msvcrt
PE	3f000000-3f0a8000	Deferred        tier0_s
PE	3f600000-3f648000	Deferred        vstdlib_s
PE	40850000-40902000	Deferred        crashhandler
PE	60000000-60021000	Deferred        cserhelper
PE	628c0000-628d9000	Deferred        parsifal
ELF	64517000-64555000	Deferred        rsaenh<elf>
  \-PE	64520000-64555000	\               rsaenh
ELF	64d56000-64ece000	Deferred        libvorbisenc.so.2
ELF	64ece000-64f1c000	Deferred        libflac.so.8
ELF	64f1c000-64f8e000	Deferred        libsndfile.so.1
ELF	64f8e000-65080000	Deferred        libasound.so.2
ELF	65080000-650e3000	Deferred        ieframe<elf>
  \-PE	65090000-650e3000	\               ieframe
ELF	7a4a9000-7b800000	Deferred        libllvm-3.0.so.1
ELF	7b800000-7ba15000	Deferred        kernel32<elf>
  \-PE	7b810000-7ba15000	\               kernel32
ELF	7ba22000-7ba4d000	Deferred        libvorbis.so.0
ELF	7ba4d000-7bab2000	Deferred        libpulsecommon-1.1.so
ELF	7bab2000-7bb00000	Deferred        libpulse.so.0
ELF	7bc00000-7bcc3000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcc3000	\               ntdll
ELF	7bcd4000-7bd00000	Deferred        winealsa<elf>
  \-PE	7bce0000-7bd00000	\               winealsa
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7bf0a000-7bf12000	Deferred        libogg.so.0
ELF	7bf12000-7bf19000	Deferred        libasyncns.so.0
ELF	7bf19000-7bf23000	Deferred        libwrap.so.0
ELF	7bf23000-7bf46000	Deferred        mmdevapi<elf>
  \-PE	7bf30000-7bf46000	\               mmdevapi
ELF	7bf46000-7bfca000	Deferred        urlmon<elf>
  \-PE	7bf50000-7bfca000	\               urlmon
ELF	7c2ed000-7c305000	Deferred        libresolv.so.2
ELF	7c305000-7c34e000	Deferred        libdbus-1.so.3
ELF	7c34e000-7c360000	Deferred        libp11-kit.so.0
ELF	7c360000-7c3e5000	Deferred        libgcrypt.so.11
ELF	7c3e5000-7c3f7000	Deferred        libtasn1.so.3
ELF	7c3f7000-7c400000	Deferred        libkrb5support.so.0
ELF	7c403000-7c40b000	Deferred        libjson.so.0
ELF	7c40b000-7c433000	Deferred        libk5crypto.so.3
ELF	7c433000-7c502000	Deferred        libkrb5.so.3
ELF	7c502000-7c514000	Deferred        libavahi-client.so.3
ELF	7c514000-7c5d8000	Deferred        libgnutls.so.26
ELF	7c5d8000-7c616000	Deferred        libgssapi_krb5.so.2
ELF	7c616000-7c669000	Deferred        libcups.so.2
ELF	7c669000-7c694000	Deferred        netapi32<elf>
  \-PE	7c670000-7c694000	\               netapi32
ELF	7c694000-7c6c0000	Deferred        secur32<elf>
  \-PE	7c6a0000-7c6c0000	\               secur32
ELF	7c6c0000-7c6dd000	Deferred        pdh<elf>
  \-PE	7c6d0000-7c6dd000	\               pdh
ELF	7c6dd000-7c717000	Deferred        winspool<elf>
  \-PE	7c6e0000-7c717000	\               winspool
ELF	7c717000-7c77e000	Deferred        setupapi<elf>
  \-PE	7c720000-7c77e000	\               setupapi
ELF	7c77e000-7c798000	Deferred        imagehlp<elf>
  \-PE	7c780000-7c798000	\               imagehlp
ELF	7c798000-7c850000	Deferred        crypt32<elf>
  \-PE	7c7a0000-7c850000	\               crypt32
ELF	7c850000-7c893000	Deferred        dsound<elf>
  \-PE	7c860000-7c893000	\               dsound
ELF	7c89e000-7c8a5000	Deferred        libnss_dns.so.2
ELF	7c8a5000-7c8ac000	Deferred        libasound_module_pcm_pulse.so
ELF	7c8ac000-7c8c2000	Deferred        wbemprox<elf>
  \-PE	7c8b0000-7c8c2000	\               wbemprox
ELF	7cec8000-7d287000	Deferred        libgallium.so
ELF	7d287000-7d501000	Deferred        libdricore.so
ELF	7d501000-7d8d1000	Deferred        nouveau_dri.so
ELF	7d984000-7d988000	Deferred        libnss_mdns4_minimal.so.2
ELF	7d98a000-7daa7000	Deferred        libglsl.so
ELF	7daa7000-7db00000	Deferred        libgl.so.1
ELF	7dc00000-7dc05000	Deferred        libgpg-error.so.0
ELF	7dc05000-7dc0a000	Deferred        libcom_err.so.2
ELF	7dc0a000-7dc11000	Deferred        libffi.so.6
ELF	7dc11000-7dc18000	Deferred        libdrm_nouveau.so.1
ELF	7dc18000-7dc25000	Deferred        libdrm.so.2
ELF	7dc25000-7dc3d000	Deferred        libxcb-glx.so.0
ELF	7dc3d000-7dc53000	Deferred        libglapi.so.0
ELF	7dc53000-7dc69000	Deferred        winejoystick<elf>
  \-PE	7dc60000-7dc69000	\               winejoystick
ELF	7dc69000-7dc7d000	Deferred        psapi<elf>
  \-PE	7dc70000-7dc7d000	\               psapi
ELF	7dc7d000-7dcdb000	Deferred        dbghelp<elf>
  \-PE	7dc80000-7dcdb000	\               dbghelp
ELF	7dcdb000-7dcf9000	Deferred        libgcc_s.so.1
ELF	7dcf9000-7dcfd000	Deferred        libkeyutils.so.1
ELF	7dcfd000-7dd0b000	Deferred        libavahi-common.so.3
ELF	7dd0c000-7de40000	Deferred        wined3d<elf>
  \-PE	7dd20000-7de40000	\               wined3d
ELF	7de40000-7de79000	Deferred        d3d9<elf>
  \-PE	7de50000-7de79000	\               d3d9
ELF	7de79000-7de9f000	Deferred        mpr<elf>
  \-PE	7de80000-7de9f000	\               mpr
ELF	7de9f000-7df0e000	Deferred        wininet<elf>
  \-PE	7deb0000-7df0e000	\               wininet
ELF	7df0e000-7e000000	Deferred        oleaut32<elf>
  \-PE	7df20000-7e000000	\               oleaut32
ELF	7e000000-7e02b000	Deferred        msvfw32<elf>
  \-PE	7e010000-7e02b000	\               msvfw32
ELF	7e02b000-7e06c000	Deferred        avifil32<elf>
  \-PE	7e030000-7e06c000	\               avifil32
ELF	7e06c000-7e094000	Deferred        msacm32<elf>
  \-PE	7e070000-7e094000	\               msacm32
ELF	7e094000-7e141000	Deferred        winmm<elf>
  \-PE	7e0a0000-7e141000	\               winmm
ELF	7e16f000-7e1a3000	Deferred        uxtheme<elf>
  \-PE	7e180000-7e1a3000	\               uxtheme
ELF	7e1a3000-7e29b000	Deferred        comctl32<elf>
  \-PE	7e1b0000-7e29b000	\               comctl32
ELF	7e29b000-7e305000	Deferred        shlwapi<elf>
  \-PE	7e2b0000-7e305000	\               shlwapi
ELF	7e305000-7e516000	Deferred        shell32<elf>
  \-PE	7e310000-7e516000	\               shell32
ELF	7e516000-7e58b000	Deferred        rpcrt4<elf>
  \-PE	7e520000-7e58b000	\               rpcrt4
ELF	7e58b000-7e693000	Deferred        ole32<elf>
  \-PE	7e5a0000-7e693000	\               ole32
ELF	7e693000-7e6b5000	Deferred        iphlpapi<elf>
  \-PE	7e6a0000-7e6b5000	\               iphlpapi
ELF	7e6b5000-7e6e7000	Deferred        ws2_32<elf>
  \-PE	7e6c0000-7e6e7000	\               ws2_32
ELF	7e6e7000-7e702000	Deferred        wsock32<elf>
  \-PE	7e6f0000-7e702000	\               wsock32
ELF	7e702000-7e708000	Deferred        libxfixes.so.3
ELF	7e708000-7e713000	Deferred        libxcursor.so.1
ELF	7e714000-7e71d000	Deferred        librt.so.1
ELF	7e71d000-7e720000	Deferred        libx11-xcb.so.1
ELF	7e720000-7e724000	Deferred        libxdamage.so.1
ELF	7e789000-7e7b3000	Deferred        libexpat.so.1
ELF	7e7b3000-7e7e7000	Deferred        libfontconfig.so.1
ELF	7e7e7000-7e7f7000	Deferred        libxi.so.6
ELF	7e7f7000-7e7fb000	Deferred        libxcomposite.so.1
ELF	7e7fb000-7e804000	Deferred        libxrandr.so.2
ELF	7e804000-7e80e000	Deferred        libxrender.so.1
ELF	7e80e000-7e814000	Deferred        libxxf86vm.so.1
ELF	7e814000-7e818000	Deferred        libxinerama.so.1
ELF	7e818000-7e83a000	Deferred        imm32<elf>
  \-PE	7e820000-7e83a000	\               imm32
ELF	7e83a000-7e841000	Deferred        libxdmcp.so.6
ELF	7e841000-7e862000	Deferred        libxcb.so.1
ELF	7e862000-7e87c000	Deferred        libice.so.6
ELF	7e87c000-7e9b0000	Deferred        libx11.so.6
ELF	7e9b0000-7e9c2000	Deferred        libxext.so.6
ELF	7e9d5000-7ea68000	Deferred        winex11<elf>
  \-PE	7e9e0000-7ea68000	\               winex11
ELF	7ea68000-7ea7e000	Deferred        libz.so.1
ELF	7ea7e000-7eb18000	Deferred        libfreetype.so.6
ELF	7eb18000-7eb31000	Deferred        version<elf>
  \-PE	7eb20000-7eb31000	\               version
ELF	7eb31000-7eb91000	Deferred        advapi32<elf>
  \-PE	7eb40000-7eb91000	\               advapi32
ELF	7eb91000-7ec4e000	Deferred        gdi32<elf>
  \-PE	7eba0000-7ec4e000	\               gdi32
ELF	7ec4e000-7ed8e000	Deferred        user32<elf>
  \-PE	7ec60000-7ed8e000	\               user32
ELF	7ed8e000-7ed9b000	Deferred        libnss_files.so.2
ELF	7ed9b000-7eda7000	Deferred        libnss_nis.so.2
ELF	7eda7000-7edc1000	Deferred        libnsl.so.1
ELF	7efc1000-7efed000	Deferred        libm.so.6
ELF	7efed000-7eff1000	Deferred        libxau.so.6
ELF	7eff1000-7eff7000	Deferred        libuuid.so.1
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7461000-b7466000	Deferred        libdl.so.2
ELF	b7466000-b760f000	Deferred        libc.so.6
ELF	b7610000-b762b000	Deferred        libpthread.so.0
ELF	b762e000-b7637000	Deferred        libsm.so.6
ELF	b763e000-b7780000	Dwarf           libwine.so.1
ELF	b7782000-b77a4000	Deferred        ld-linux.so.2
ELF	b77a4000-b77a5000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	00000062    0
	00000085    0
	0000001d    0
	00000015    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001b    0
	00000018    0
	00000014    0
	00000013    0
00000019 plugplay.exe
	00000020    0
	0000001c    0
	0000001a    0
00000021 explorer.exe
	00000022    0
00000023 Steam.exe
	0000007a    1
	00000095    1
	00000082    0
	00000054    0
	00000090    1
	00000075    0
	00000080    1
	0000001e    1
	0000006c    1
	00000069    1
	00000064    1
	00000074    0
	00000053    0
	00000066    0
	00000067    0
	0000005f    0
	00000057    0
	00000052    0
	00000051    0
	0000004c    0
	0000004b    0
	00000049    0
	00000048    0
	0000000b    0
	00000009    0
	0000003f    0
	00000025    0
	00000026    0
	00000027    0
	0000002e    0
	0000002c    0
	0000002b    0
	0000000d    0
	00000047    0
	00000046    0
	00000045    0
	00000044    0
	00000043    0
	00000042    0
	00000041    0
	00000040    0
	0000003e    0
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
00000055 (D) D:\Program Files\Steam\SteamApps\tikeluis\source sdk base\hl2.exe
	00000086    0
	00000068    0
	0000007b    0
	0000007d   15
	00000093    0
	00000077    0
	0000006e    2
	00000070    0
	00000089    0
	0000006b    2
	00000087    0 <==
0000007e SteamService.exe
	00000065    0
	0000007f    0
	00000071    0
	00000081    0
System information:
    Wine build: wine-1.4
    Platform: i386
    Host system: Linux
    Host version: 3.2.0-45-generic-pae

Excuse me, I couldn't find a spoiler tag. Does anybody have a solution for this? My suspect is pulseaudio.

Tike

---

### Post by Tike on 2013-06-14
Bump.

---

