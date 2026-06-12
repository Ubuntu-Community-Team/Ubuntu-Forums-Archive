---
title: "Counter Strike Source + Gutsy = Problems?"
date: 2007-10-18
forum: Wine
---

### Post by myacademy on 2007-10-18
So I upgraded to Gutsy overnight, and it looks super awesome.
Of course with Compiz integration I decide it would be a good idea to test the waters by trying some of my games out.
Lo-and-behold, the first game I try (CS:S) doesn't work!
It hangs at the "Sending info to server" step, you know, the last one.
Anyway, heres a dump from terminal, its pretty thick and while I'm usually good at deciphering these things, I'm totally lost here:

```
fixme:avifile:AVIFileExit (): stub!
wine: Unhandled page fault on read access to 0x00000024 at address 0xe00b423 (thread 0041), starting debugger...
Unhandled exception: page fault on read access to 0x00000024 in 32-bit code (0x0e00b423).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0e00b423 ESP:0034e5e8 EBP:00000002 EFLAGS:00210212(   - 00      - RIA1)
 EAX:00000020 EBX:00000000 ECX:2393d388 EDX:07ee6a40
 ESI:0e01ea18 EDI:00000090
Stack dump:
0x0034e5e8:  0e01ea18 011e390c 0e00b452 23930002
0x0034e5f8:  0e01ea18 011e390c 0e01ea18 23930006
0x0034e608:  0e00b7d5 23930006 0e01ea18 23930006
0x0034e618:  0e01ea3c 000000c0 0e01ea18 0e0098da
0x0034e628:  23930001 ffffffff 00000000 00000009
0x0034e638:  0034ff08 0034e67c 003d753b 00000003
Backtrace:
=>1 0x0e00b423 in datacache (+0xb423) (0x00000002)
  2 0x00000000 (0x00000000)
0x0e00b423: movl        0x24(%ebx),%eax
Modules:
Module  Address                 Debug info      Name (219 modules)
PE        3d0000-  400000       Deferred        launcher
PE        400000-  41c000       Deferred        hl2
PE       1160000- 1196000       Deferred        tier0
PE       11a0000- 11be000       Deferred        vstdlib
PE       dad0000- db24000       Deferred        filesystem_steam
PE       db30000- db44000       Deferred        inputsystem
PE       ddb0000- deae000       Deferred        datamodel
PE       dfc0000- dffd000       Deferred        dmserializers
PE       e000000- e025000       Export          datacache
PE       e140000- e1f4000       Deferred        materialsystem
PE       e200000- e216000       Deferred        valve_avi
PE       e220000- e2f0000       Deferred        vguimatsurface
PE       e2f0000- e365000       Deferred        vgui2
PE       e370000- e384000       Deferred        steam_api
PE       e5b0000- e5d9000       Deferred        stdshader_dbg
PE       e5e0000- e615000       Deferred        stdshader_dx6
PE       e620000- e62f000       Deferred        unicode
PE       f6c0000- f6f6000       Deferred        soundemittersystem
PE       f700000- f71b000       Deferred        scenefilecache
PE       f720000- f8dc000       Deferred        steamclient
PE       f8e0000- f91f000       Deferred        tier0_s
PE       f920000- f992000       Deferred        vstdlib_s
PE       fac0000- faee000       Deferred        nattypeprobe
PE       faf0000- fd8b000       Deferred        p2pcore
PE       fd90000- feea000       Deferred        p2pvoice
PE      10000000-10031000       Deferred        gameoverlayrenderer
PE      1c840000-1ca23000       Deferred        gameui
PE      1dba0000-1dbb0000       Deferred        vaudio_miles
PE      1dbb0000-1dc14000       Deferred        mss32
PE      1e630000-1e6fb000       Deferred        serverbrowser
PE      1ec40000-1ec67000       Deferred        vaudio_speex
PE      1ec70000-1ec76000       Deferred        xpcom
PE      1ec80000-1ece9000       Deferred        xpcom_core
PE      1ecf0000-1ed17000       Deferred        nspr4
PE      1ed20000-1ed27000       Deferred        plc4
PE      1f9d0000-1f9d6000       Deferred        plds4
PE      1f9e0000-1f9ef000       Deferred        jsd3250
PE      1f9f0000-1fa61000       Deferred        js3250
PE      1fa70000-1faa5000       Deferred        xpc3250
PE      1fab0000-1fad0000       Deferred        ssl3
PE      1ff00000-1ff5b000       Deferred        nss3
PE      1ff60000-1ff9f000       Deferred        softokn3
PE      1ffa0000-1ffa6000       Deferred        xpistub
PE      1ffb0000-1ffe1000       Deferred        freebl3
PE      1fff0000-1fff6000       Deferred        mozctlx
PE      20000000-205ee000       Deferred        engine
PE      21090000-210a1000       Deferred        mozz
PE      210b0000-210c6000       Deferred        gkgfx
PE      210d0000-210ea000       Deferred        smime3
PE      210f0000-210fc000       Deferred        xppref32
PE      21100000-211ad000       Deferred        mss32_s
PE      21f70000-21fae000       Deferred        nssckbi
PE      21fb0000-21fc4000       Deferred        xpcom_compat
PE      21fd0000-21fe3000       Deferred        jsj3250
PE      21ff0000-21fff000       Deferred        caps
PE      22000000-22642000       Deferred        server
PE      23fd0000-23ffe000       Deferred        i18n
PE      24000000-24476000       Deferred        client
PE      25ab0000-25b2d000       Deferred        necko
PE      25b30000-25b4f000       Deferred        embedcomponents
PE      25b50000-25b5c000       Deferred        typeaheadfind
PE      25b60000-25df9000       Deferred        gklayout
PE      25e00000-25e27000       Deferred        imglib2
PE      25e30000-25e4b000       Deferred        rdf
PE      25e50000-25e88000       Deferred        appcomps
PE      25e90000-25ea0000       Deferred        appshell
PE      25ea0000-25eaf000       Deferred        profile
PE      25eb0000-25eb7000       Deferred        xpcom_compat_c
PE      25ec0000-25ec7000       Deferred        sroaming
PE      25ed0000-25ee0000       Deferred        chrome
PE      25ee0000-25f19000       Deferred        gkparser
PE      25f20000-25fde000       Deferred        uconv
PE      25fe0000-25fea000       Deferred        nsprefm
PE      25ff0000-25ffe000       Deferred        webbrwsr
PE      26000000-26138000       Deferred        vphysics
PE      26140000-2616c000       Deferred        docshell
PE      26170000-26195000       Deferred        gkwidget
PE      261a0000-261c4000       Deferred        gkgfxwin
PE      261d0000-261d8000       Deferred        pipboot
PE      261e0000-261ec000       Deferred        oji
PE      261f0000-261fd000       Deferred        jar50
PE      26400000-26439000       Deferred        mssvoice.asi
PE      26f00000-26f2e000       Deferred        mssmp3.asi
PE      2a000000-2a0a8000       Deferred        shaderapidx9
PE      2c000000-2c3e3000       Deferred        studiorender
PE      30000000-30320000       Deferred        steam
PE      60000000-60021000       Deferred        cserhelper
PE      628c0000-628d9000       Deferred        parsifal
ELF     77ca6000-77cf0000       Deferred        dbghelp<elf>
  \-PE  77cb0000-77cf0000       \               dbghelp
ELF     78993000-789e4000       Deferred        libgcrypt.so.11
ELF     789e4000-78a12000       Deferred        libcrypt.so.1
ELF     78a12000-78a82000       Deferred        libgnutls.so.13
ELF     78a82000-78aa7000       Deferred        libk5crypto.so.3
ELF     78aa7000-78b2f000       Deferred        libkrb5.so.3
ELF     78b2f000-78b58000       Deferred        libgssapi_krb5.so.2
ELF     78b58000-78bf9000       Deferred        comdlg32<elf>
  \-PE  78b60000-78bf9000       \               comdlg32
ELF     79db1000-79dfa000       Deferred        dsound<elf>
  \-PE  79dc0000-79dfa000       \               dsound
ELF     7ab1b000-7ab50000       Deferred        libcups.so.2
ELF     7ab50000-7ab85000       Deferred        winspool<elf>
  \-PE  7ab60000-7ab85000       \               winspool
ELF     7ac96000-7acfe000       Deferred        msvcrt<elf>
  \-PE  7acb0000-7acfe000       \               msvcrt
ELF     7b60d000-7b61d000       Deferred        libtasn1.so.3
ELF     7b61d000-7b6a0000       Deferred        mshtml<elf>
  \-PE  7b630000-7b6a0000       \               mshtml
ELF     7b6a0000-7b6dc000       Deferred        urlmon<elf>
  \-PE  7b6b0000-7b6dc000       \               urlmon
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7b92d000-7b931000       Deferred        libgpg-error.so.0
ELF     7b931000-7b933000       Deferred        libkeyutils.so.1
ELF     7b933000-7b93b000       Deferred        libkrb5support.so.0
ELF     7b9bf000-7b9c2000       Deferred        libcom_err.so.2
ELF     7b9f7000-7ba31000       Deferred        shdocvw<elf>
  \-PE  7ba00000-7ba31000       \               shdocvw
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c3c2000-7c3e7000       Deferred        netapi32<elf>
  \-PE  7c3d0000-7c3e7000       \               netapi32
ELF     7c3e7000-7c40e000       Deferred        secur32<elf>
  \-PE  7c3f0000-7c40e000       \               secur32
ELF     7c40e000-7c423000       Deferred        psapi<elf>
  \-PE  7c410000-7c423000       \               psapi
ELF     7ca9a000-7cab1000       Deferred        mcicda<elf>
  \-PE  7caa0000-7cab1000       \               mcicda
ELF     7cbc2000-7cbd6000       Deferred        winejoystick<elf>
  \-PE  7cbd0000-7cbd6000       \               winejoystick
ELF     7cdf8000-7ced9000       Deferred        wined3d<elf>
  \-PE  7ce10000-7ced9000       \               wined3d
ELF     7ced9000-7cf08000       Deferred        d3d9<elf>
  \-PE  7cee0000-7cf08000       \               d3d9
ELF     7cf08000-7cf28000       Deferred        mpr<elf>
  \-PE  7cf10000-7cf28000       \               mpr
ELF     7cf28000-7cf72000       Deferred        wininet<elf>
  \-PE  7cf30000-7cf72000       \               wininet
ELF     7cf72000-7d010000       Deferred        oleaut32<elf>
  \-PE  7cf80000-7d010000       \               oleaut32
ELF     7d010000-7d037000       Deferred        msvfw32<elf>
  \-PE  7d020000-7d037000       \               msvfw32
ELF     7d037000-7d071000       Deferred        avifil32<elf>
  \-PE  7d040000-7d071000       \               avifil32
ELF     7d071000-7d086000       Deferred        midimap<elf>
  \-PE  7d080000-7d086000       \               midimap
ELF     7d086000-7d0ac000       Deferred        msacm32<elf>
  \-PE  7d090000-7d0ac000       \               msacm32
ELF     7d0ac000-7d0c4000       Deferred        msacm32<elf>
  \-PE  7d0b0000-7d0c4000       \               msacm32
ELF     7d0c4000-7d18a000       Deferred        libasound.so.2
ELF     7d199000-7d1cf000       Deferred        winealsa<elf>
  \-PE  7d1a0000-7d1cf000       \               winealsa
ELF     7d1cf000-7d25d000       Deferred        winmm<elf>
  \-PE  7d1e0000-7d25d000       \               winmm
ELF     7d3d3000-7d405000       Deferred        uxtheme<elf>
  \-PE  7d3e0000-7d405000       \               uxtheme
ELF     7d405000-7d419000       Deferred        mswsock<elf>
  \-PE  7d410000-7d419000       \               mswsock
ELF     7d419000-7d42d000       Deferred        lz32<elf>
  \-PE  7d420000-7d42d000       \               lz32
ELF     7d42d000-7d447000       Deferred        version<elf>
  \-PE  7d430000-7d447000       \               version
ELF     7d447000-7d505000       Deferred        comctl32<elf>
  \-PE  7d450000-7d505000       \               comctl32
ELF     7d505000-7d55e000       Deferred        shlwapi<elf>
  \-PE  7d510000-7d55e000       \               shlwapi
ELF     7d55e000-7d661000       Deferred        shell32<elf>
  \-PE  7d570000-7d661000       \               shell32
ELF     7d661000-7d6ba000       Deferred        rpcrt4<elf>
  \-PE  7d670000-7d6ba000       \               rpcrt4
ELF     7d6ba000-7d75b000       Deferred        ole32<elf>
  \-PE  7d6d0000-7d75b000       \               ole32
ELF     7d75b000-7d779000       Deferred        iphlpapi<elf>
  \-PE  7d760000-7d779000       \               iphlpapi
ELF     7d9c2000-7d9d5000       Deferred        libresolv.so.2
ELF     7d9d5000-7da02000       Deferred        ws2_32<elf>
  \-PE  7d9e0000-7da02000       \               ws2_32
ELF     7da02000-7da1c000       Deferred        wsock32<elf>
  \-PE  7da10000-7da1c000       \               wsock32
ELF     7da1c000-7da21000       Deferred        libxfixes.so.3
ELF     7da21000-7da2a000       Deferred        libxcursor.so.1
ELF     7da2a000-7da47000       Deferred        imm32<elf>
  \-PE  7da30000-7da47000       \               imm32
ELF     7da47000-7da4d000       Deferred        libxrandr.so.2
ELF     7da4d000-7da55000       Deferred        libxrender.so.1
ELF     7e012000-7e014000       Deferred        libnvidia-tls.so.1
ELF     7e014000-7e89a000       Deferred        libglcore.so.1
ELF     7e89a000-7e926000       Deferred        libgl.so.1
ELF     7e926000-7e92b000       Deferred        libxdmcp.so.6
ELF     7e92b000-7e92e000       Deferred        libxau.so.6
ELF     7e92e000-7ea1f000       Deferred        libx11.so.6
ELF     7ea1f000-7ea2d000       Deferred        libxext.so.6
ELF     7ea2d000-7ea32000       Deferred        libxxf86vm.so.1
ELF     7ea32000-7ea4a000       Deferred        libice.so.6
ELF     7ea4a000-7ea52000       Deferred        libsm.so.6
ELF     7ea61000-7eaec000       Deferred        winex11<elf>
  \-PE  7ea70000-7eaec000       \               winex11
ELF     7eb71000-7eb91000       Deferred        libexpat.so.1
ELF     7eb91000-7ebbc000       Deferred        libfontconfig.so.1
ELF     7ebcb000-7ebe0000       Deferred        libz.so.1
ELF     7ebe0000-7ec50000       Deferred        libfreetype.so.6
ELF     7ec50000-7ec99000       Deferred        advapi32<elf>
  \-PE  7ec60000-7ec99000       \               advapi32
ELF     7ec99000-7ed34000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed34000       \               gdi32
ELF     7ed34000-7ee72000       Deferred        user32<elf>
  \-PE  7ed50000-7ee72000       \               user32
ELF     7ee72000-7ee7d000       Deferred        libnss_files.so.2
ELF     7ee7d000-7ee95000       Deferred        libnsl.so.1
ELF     7ee95000-7ee9e000       Deferred        libnss_compat.so.2
ELF     7efcc000-7eff1000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cb6000-b7cba000       Deferred        libdl.so.2
ELF     b7cba000-b7e04000       Deferred        libc.so.6
ELF     b7e05000-b7e1d000       Deferred        libpthread.so.0
ELF     b7e2c000-b7f40000       Deferred        libwine.so.1
ELF     b7f42000-b7f5e000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000040 (D) C:\Program Files\Valve\Steam\SteamApps\myusername@lulz.har\counter-strike source\hl2.exe
        00000048    0
        00000028    0
        00000024    0
        0000003d    0
        0000002b    0
        00000029    0
        00000021    0
        00000020   15
        00000047    2
        00000046    0
        00000045    0
        00000043    0
        00000042    2
        00000041    0 <==
0000000a 
        0000000c    0
        0000000b    0
00000008 
        00000044    1
        0000003f    0
        0000003e    0
        0000003c    0
        0000003b    0
        0000003a    1
        00000039    0
        00000038    1
        00000037    0
        00000036    1
        00000035    0
        00000034    1
        00000033    0
        00000032    1
        00000031    0
        00000030    1
        0000002f    0
        0000002e    1
        0000002d    0
        0000002c    1
        0000002a    0
        00000027    0
        00000026    0
        00000025    0
        00000023    0
        00000022    1
        0000001f    0
        0000001e    0
        0000001d    0
        0000001c   15
        0000001b   15
        0000001a    0
        00000019    0
        00000018    0
        00000017    0
        00000016    0
        00000015    1
        00000014    0
        00000013    0
        00000012    0
        00000011    0
        00000010    0
        0000000f    0
        0000000e    0
        0000000d    0
        00000009    0
Killed

```

I noticed the part about 32-bit code, but all is lost after that point.
This is only the tail end of the log, after just about everything else goes off without a hitch.
This worked perfectly before I upgraded to Gutsy, otherwise the title for this would've been something like 'CS:S + Wine = Problems?' rather than what it actually is.
Any help is appreciated!

---

### Post by MofoVideo on 2008-03-16
Im on mint and I get the same problem =\ Anyone have anyideas
its this or im goign to dual boot with winxp

---

### Post by wheredidrealitygo on 2008-03-16
I had the same problem on Gutsy with CS:S. Tried CrossOver, Cedega, and pure Wine, none worked properly.

---

