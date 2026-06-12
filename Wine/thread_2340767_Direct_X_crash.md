---
title: "Direct X crash"
date: 2016-10-21
forum: Wine
---

### Post by ryan19554 on 2016-10-21
Steam attempts to install direct X before launching the game, always ends in DXSetup.exe has encountered a serious problem and needs to close. Here is the log


Unhandled exception: unimplemented function sfc.dll.SRSetRestorePoint called in 32-bit code (0x7b4346cf).
Register dump:
 CS:001b SS:0023 DS:0023 ES:0023 FS:1007 GS:000f
 EIP:7b4346cf ESP:0033f994 EBP:0033fa08 EFLAGS:00000246(   - --  I  Z- -P- )
 EAX:7b418919 EBX:00000000 ECX:0033f9a0 EDX:00000000
 ESI:00000001 EDI:80000100
Stack dump:
0x0033f994:  0033fa28 00000008 00000022 80000100
0x0033f9a4:  00000001 00000000 7b4346cf 00000002
0x0033f9b4:  49d7558c 49d75594 007e1de2 00000022
0x0033f9c4:  49d70000 7ffc0000 7b4641c0 0067181c
0x0033f9d4:  0033fa00 00000000 7b464700 00000000
0x0033f9e4:  00000000 0033fa30 7b464785 0033fa28
0200: sel=1007 base=7ffc0000 limit=00000fff 32-bit rw-
Backtrace:
=>0 0x7b4346cf RaiseException+0xbf() in kernel32 (0x0033fa08)
  1 0x49d7554f __wine_spec_unimplemented_stub+0x3e() in sfc (0x0033fa38)
  2 0x49d75169 __wine_stub_SRSetRestorePoint+0x28() in sfc (0x0033fab4)
  3 0x006773ac in dsetup32 (+0x73ab) (0x0033fab4)
  4 0x0067eab1 in dsetup32 (+0xeab0) (0x0033fcf0)
  5 0x1000500e in dsetup (+0x500d) (0x0033fd10)
  6 0x010050a7 in dxsetup (+0x50a6) (0x0033fd38)
  7 0x0100701c in dxsetup (+0x701b) (0x0033fe60)
  8 0x7b46f4dc call_process_entry+0xb() in kernel32 (0x0033fe78)
  9 0x7b473243 start_process+0x1b2() in kernel32 (0x0033fee8)
  10 0x7bc9d77c call_thread_func_wrapper+0xb() in ntdll (0x0033fef8)
  11 0x7bca0a28 call_thread_func+0x67() in ntdll (0x0033ffa8)
  12 0x7bc9d742 call_thread_entry_point+0x11() in ntdll (0x0033ffc8)
  13 0x7bc5c4eb start_process+0x2a() in ntdll (0x0033ffe8)
  14 0x4000858d wine_call_on_stack+0x1c() in libwine.1.0.dylib (0x00000000)
  15 0x400086b1 wine_switch_to_stack+0x30() in libwine.1.0.dylib (0xfeffef28)
  16 0x7bc5c04a LdrInitializeThunk+0x439() in ntdll (0xfeffeff8)
  17 0x7b46fe47 __wine_kernel_init+0x946() in kernel32 (0xfeffff28)
  18 0x7bc5cd2b __wine_process_init+0x19a() in ntdll (0xfeffff88)
  19 0x929be794 _pthread_body+0x89() in libsystem_pthread.dylib (0xfeffffa8)
  20 0x929be70a _pthread_start+0x9a() in libsystem_pthread.dylib (0xfeffffc8)
  21 0x929bbfa6 thread_start+0x21() in libsystem_pthread.dylib (0xfeffffec)
0x7b4346cf RaiseException+0xbf in kernel32: leal    0xfffffff8(%ebp),%esp
Modules:
Module    Address            Debug info    Name (224 modules)
PE      670000-  7f2000    Export          dsetup32
PE     1000000- 1082000    Export          dxsetup
PE    10000000-1001a000    Export          dsetup
PE    40001000-401bc000    Stabs           libwine.1.0.dylib
ELF    43b00000-43b9d000    Deferred        advapi32<elf>
  \-PE    43b10000-43b84000    \               advapi32
ELF    43b9d000-43cfd000    Deferred        gdi32<elf>
  \-PE    43ba0000-43c8e000    \               gdi32
ELF    43d0a000-43ec2000    Deferred        user32<elf>
  \-PE    43d10000-43e76000    \               user32
ELF    43ec2000-43ee0000    Deferred        version<elf>
  \-PE    43ed0000-43ede000    \               version
PE    43ee0000-43f61000    Deferred        libfreetype.6.dylib
ELF    43f61000-43f8a000    Deferred        imm32<elf>
  \-PE    43f70000-43f85000    \               imm32
ELF    46911000-46a83000    Deferred        comctl32<elf>
  \-PE    46920000-46a57000    \               comctl32
ELF    46a83000-46b51000    Deferred        winemac<elf>
  \-PE    46a90000-46b27000    \               winemac
ELF    46e82000-46ec4000    Deferred        uxtheme<elf>
  \-PE    46e90000-46ebc000    \               uxtheme
ELF    46ec4000-46ef8000    Deferred        msacm32<elf>
  \-PE    46ed0000-46ef3000    \               msacm32
ELF    496d9000-497ad000    Deferred        winmm<elf>
  \-PE    496e0000-4979d000    \               winmm
ELF    497ad000-49959000    Deferred        ole32<elf>
  \-PE    497b0000-49916000    \               ole32
ELF    49959000-49a12000    Deferred        rpcrt4<elf>
  \-PE    49960000-499ef000    \               rpcrt4
ELF    49a12000-49cbf000    Deferred        shell32<elf>
  \-PE    49a20000-49c7d000    \               shell32
ELF    49cbf000-49d64000    Deferred        shlwapi<elf>
  \-PE    49cc0000-49d3e000    \               shlwapi
ELF    49d64000-49d78000    Stabs           sfc<elf>
  \-PE    49d70000-49d77000    \               sfc
ELF    7b400000-7b82d000    Stabs           kernel32<elf>
  \-PE    7b410000-7b7ef000    \               kernel32
ELF    7bc00000-7bd3b000    Stabs           ntdll<elf>
  \-PE    7bc10000-7bcfc000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
PE    90237000-9023a000    Deferred        libsystem_coreservices.dylib
PE    9023a000-9023e000    Deferred        servicemanagement
PE    90242000-9025e000    Deferred        cfopendirectory
PE    90297000-907c6000    Deferred        vimage
PE    907c6000-907cd000    Deferred        ioaccelerator
PE    9148b000-9148c000    Deferred        libopenscriptingutil.dylib
PE    9148c000-91492000    Deferred        tcc
PE    915b3000-916a8000    Deferred        libxml2.2.dylib
PE    916a8000-916d1000    Deferred        iconservices
PE    916d1000-916d4000    Deferred        libquarantine.dylib
PE    916d4000-916f4000    Deferred        generationalstorage
PE    916f5000-91709000    Deferred        libcmph.dylib
PE    91709000-919ad000    Deferred        libmecabra.dylib
PE    91a9e000-91af5000    Deferred        libc++.1.dylib
PE    91b48000-91b88000    Deferred        libglimage.dylib
PE    91de0000-91ecc000    Deferred        libvmisc.dylib
PE    91ecc000-91ed0000    Deferred        libcorevmclient.dylib
PE    92079000-92084000    Deferred        libsystem_notify.dylib
PE    92084000-92085000    Deferred        carbon
PE    92085000-92124000    Deferred        colorsync
PE    92138000-9216a000    Deferred        coreservicesinternal
PE    921d4000-921d7000    Deferred        libsystem_secinit.dylib
PE    921d7000-9224b000    Deferred        ats
PE    92407000-92449000    Deferred        libauto.dylib
PE    92449000-9266c000    Deferred        coreimage
PE    9266c000-9266e000    Deferred        libdiagnosticmessagesclient.dyli
PE    929bb000-929c4000    Stabs           libsystem_pthread.dylib
PE    929c4000-929c6000    Deferred        libsystem.b.dylib
PE    929d2000-929e7000    Deferred        corebluetooth
PE    929e7000-929e8000    Deferred        audiounit
PE    929e8000-929fc000    Deferred        sharing
PE    929fc000-92a60000    Deferred        systemconfiguration
PE    92a60000-92a61000    Deferred        liblaunch.dylib
PE    92a61000-92a6b000    Deferred        libsystem_networkextension.dylib
PE    92a6b000-92b5d000    Deferred        libiconv.2.dylib
PE    92b98000-92ba6000    Deferred        speechrecognitioncore
PE    92ba6000-92bb0000    Deferred        commonauth
PE    92bde000-92bf4000    Deferred        libsystem_coretls.dylib
PE    92bf4000-92fcf000    Deferred        liblapack.dylib
PE    92fcf000-9328b000    Deferred        coredata
PE    9328b000-93f65000    Deferred        appkit
PE    94296000-942c0000    Deferred        libsystem_info.dylib
PE    942c0000-942cd000    Deferred        crashreportersupport
PE    942cd000-942e4000    Deferred        libcompression.dylib
PE    94334000-94337000    Deferred        libcvmspluginsupport.dylib
PE    945ca000-94660000    Deferred        libsystem_c.dylib
PE    94660000-94689000    Deferred        libxpc.dylib
PE    947ac000-947bc000    Deferred        libxar.1.dylib
PE    947bc000-9485d000    Deferred        qd
PE    94865000-948af000    Deferred        sharedfilelist
PE    948af000-948d3000    Deferred        libc++abi.dylib
PE    948f6000-94902000    Deferred        libcommoncrypto.dylib
PE    94902000-94a7c000    Deferred        audiotoolbox
PE    94a7f000-94a80000    Deferred        accelerate
PE    94a80000-94ba7000    Deferred        libsqlite3.dylib
PE    94bca000-94bcb000    Deferred        libkeymgr.dylib
PE    94c86000-94ce2000    Deferred        printcore
PE    94ce2000-94ce9000    Deferred        libunwind.dylib
PE    95453000-955d9000    Deferred        uifoundation
PE    955d9000-9595d000    Deferred        foundation
PE    9595d000-9596b000    Deferred        speechsynthesis
PE    9596b000-95971000    Deferred        print
PE    96239000-9637c000    Deferred        libvdsp.dylib
PE    963ac000-963b0000    Deferred        help
PE    96995000-96999000    Deferred        libdyld.dylib
PE    9699c000-96c2c000    Deferred        cfnetwork
PE    96c2c000-96c30000    Deferred        libcorefscache.dylib
PE    96c33000-96c3d000    Deferred        diskarbitration
PE    96c74000-96c77000    Deferred        libradiance.dylib
PE    96d9f000-96de3000    Deferred        metal
PE    96de3000-96e07000    Deferred        libjpeg.dylib
PE    96e3b000-96e3c000    Deferred        libmetal_timestamp.dylib
PE    96eb8000-9700a000    Deferred        coreui
PE    9700d000-97065000    Deferred        hiservices
PE    97065000-97247000    Deferred        quartzcore
PE    97247000-97249000    Deferred        libremovefile.dylib
PE    97249000-972b0000    Deferred        libsystem_network.dylib
PE    972c3000-972cf000    Deferred        netauth
PE    972d0000-9732d000    Deferred        libtiff.dylib
PE    97331000-9739d000    Deferred        corewifi
PE    9739d000-973f3000    Deferred        htmlrendering
PE    973f5000-973fb000    Deferred        libcompiler_rt.dylib
PE    973fb000-9740a000    Deferred        opengl
PE    9740a000-97418000    Deferred        libbz2.1.0.dylib
PE    97989000-97ba8000    Deferred        libicucore.a.dylib
PE    97ba8000-97be8000    Deferred        navigationservices
PE    97be8000-97bef000    Deferred        speechrecognition
PE    97bef000-97bf6000    Deferred        libsystem_platform.dylib
PE    97f09000-97f0a000    Deferred        libunc.dylib
PE    97f20000-97fc2000    Deferred        ink
PE    97fc2000-97fc5000    Deferred        libsystem_configuration.dylib
PE    97fc5000-97fc6000    Deferred        applicationservices
PE    97fc6000-97fc7000    Deferred        coreservices
PE    97fc7000-97fd2000    Deferred        carbonsound
PE    97fd2000-98001000    Deferred        libarchive.2.dylib
PE    98001000-98004000    Deferred        securityhi
PE    98004000-98041000    Deferred        remoteviewservices
PE    98041000-9808a000    Deferred        libfontregistry.dylib
PE    9808a000-98094000    Deferred        libcopyfile.dylib
PE    980a6000-980aa000    Deferred        libpam.2.dylib
PE    980aa000-98472000    Deferred        hitoolbox
PE    98472000-98475000    Deferred        loginsupport
PE    98475000-98872000    Deferred        coregraphics
PE    9888a000-98893000    Deferred        fsevents
PE    988c2000-98917000    Deferred        coreaudio
PE    98917000-9898e000    Deferred        securityfoundation
PE    98be2000-98c37000    Deferred        symbolication
PE    98c64000-98fc0000    Deferred        libobjc.a.dylib
PE    98fc0000-98fc6000    Deferred        libmacho.dylib
PE    98fc6000-9925e000    Deferred        security
PE    997ad000-997ca000    Deferred        openscripting
PE    997ca000-9985c000    Deferred        coresymbolication
PE    99870000-9988f000    Deferred        libresolv.9.dylib
PE    9a976000-9aa9c000    Deferred        coretext
PE    9aa9c000-9ab04000    Deferred        libcorecrypto.dylib
PE    9abb1000-9ac08000    Deferred        libcups.2.dylib
PE    9ac08000-9ac2f000    Deferred        multitouchsupport
PE    9ac2f000-9ac89000    Deferred        ae
PE    9acb0000-9acf4000    Deferred        libglu.dylib
PE    9acf4000-9ad02000    Deferred        opendirectory
PE    9ad63000-9ad68000    Deferred        libcache.dylib
PE    9ad68000-9ad83000    Deferred        liblzma.5.dylib
PE    9ad90000-9adc4000    Deferred        libsystem_m.dylib
PE    9adc4000-9ade5000    Deferred        libsystem_kernel.dylib
PE    9adf0000-9b223000    Deferred        facecore
PE    9b223000-9b257000    Deferred        gss
PE    9b27e000-9b28d000    Deferred        libz.1.dylib
PE    9b28d000-9b461000    Deferred        imageio
PE    9b461000-9b493000    Deferred        dictionaryservices
PE    9b4c7000-9b4d3000    Deferred        libchinesetokenizer.dylib
PE    9b4d3000-9b4d8000    Deferred        iosurface
PE    9b4d8000-9b96c000    Deferred        corefoundation
PE    9b96c000-9ba14000    Deferred        metadata
PE    9ba14000-9ba93000    Deferred        iokit
PE    9ba93000-9bb98000    Deferred        libjp2.dylib
PE    9bb98000-9bbb2000    Deferred        libsystem_malloc.dylib
PE    9bbb2000-9bbb3000    Deferred        libenergytrace.dylib
PE    9bbef000-9bc30000    Deferred        applejpeg
PE    9bc30000-9bc67000    Deferred        corevideo
PE    9bc67000-9bc80000    Deferred        libsparseblas.dylib
PE    9bd77000-9bd7c000    Deferred        libgif.dylib
PE    9bd7c000-9bdf7000    Deferred        heimdal
PE    9bdf7000-9c0f3000    Deferred        carboncore
PE    9c0f3000-9c167000    Deferred        datadetectorscore
PE    9c167000-9c1da000    Deferred        corewlan
PE    9c1da000-9c1f4000    Deferred        libsystem_asl.dylib
PE    9c1f4000-9c2f5000    Deferred        libfontparser.dylib
PE    9c2f5000-9c2fe000    Deferred        netfs
PE    9c2fe000-9c2ff000    Deferred        libsystem_blocks.dylib
PE    9c2ff000-9c363000    Deferred        osservices
PE    9c363000-9c36c000    Deferred        libsystem_dnssd.dylib
PE    9c4f6000-9c503000    Deferred        libkxld.dylib
PE    9ce08000-9cec3000    Deferred        backup
PE    9cec3000-9cf13000    Deferred        opencl
PE    9cf13000-9cfbf000    Deferred        languagemodeling
PE    9cfbf000-9cfc9000    Deferred        libgfxshared.dylib
PE    9cfc9000-9d123000    Deferred        libblas.dylib
PE    9d123000-9d1d7000    Deferred        iobluetooth
PE    9d1d7000-9d2d6000    Deferred        launchservices
PE    9d2d6000-9d2db000    Deferred        libheimdal-asn1.dylib
PE    9d38b000-9d3a5000    Deferred        kerberos
PE    9d3a5000-9d3b6000    Deferred        libgl.dylib
PE    9d3b6000-9d3ba000    Deferred        libextension.dylib
PE    9d3c2000-9d3d4000    Deferred        libbsm.0.dylib
PE    9d3d4000-9d44a000    Deferred        searchkit
PE    9d44a000-9d468000    Deferred        libcrfsuite.dylib
PE    9d4c5000-9d4dd000    Deferred        libmarisa.dylib
PE    9d4dd000-9d4e2000    Deferred        commonpanels
PE    9d69f000-9d6a3000    Deferred        libsystem_sandbox.dylib
PE    9d6a3000-9d6ce000    Deferred        libxslt.1.dylib
PE    9d6ce000-9d908000    Deferred        libfosl_dynamic.dylib
PE    9d976000-9d99d000    Deferred        libpng.dylib
PE    9e33f000-9e340000    Deferred        veclib
PE    9e7c9000-9e7da000    Deferred        langanalysis
PE    9e8c6000-9e8dd000    Deferred        liblinearalgebra.dylib
PE    9e8dd000-9e901000    Deferred        apple80211
PE    9e905000-9e917000    Deferred        libsystem_trace.dylib
PE    9e917000-9ea31000    Deferred        desktopservicespriv
PE    9ea31000-9ea6f000    Deferred        debugsymbols
PE    9ea6f000-9ea76000    Deferred        imagecapture
PE    9ea79000-9eaa4000    Deferred        libdispatch.dylib
PE    9eaa8000-9eaac000    Deferred        libscreenreader.dylib
PE    9eaac000-9eaae000    Deferred        liblangid.dylib
PE    9eaae000-9eb43000    Deferred        performanceanalysis
Threads:
process  tid      prio (all id:s are in hex)
00000008 Steam.exe
    00000056    0
    00000051    0
    00000050    0
    0000004d    0
    0000004c    0
    0000004a    0
    00000049    0
    00000048    0
    0000000d    0
    0000000b    0
    00000047    0
    00000045    1
    00000042    0
    00000040    0
    0000003f    0
    0000003d    0
    0000002b    0
    0000002a    0
    00000029    0
    00000026    0
    00000009    0
0000000e services.exe
    0000001e    0
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
    00000025    0
    00000024    0
    00000023    0
    00000022    0
00000027 steamwebhelper.exe
    0000004b    0
    0000003e    0
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
    0000002f    0
    0000002e    0
    0000002d    0
    0000002c    0
    00000028    0
00000030 SteamService.exe
    00000031    0
00000046 wineconsole.exe
    00000041    0
0000004f (D) Z:\Applications\steamapps\common\Sid Meier's Civilization VI\_CommonRedist\DirectX\Jun2010\DXSETUP.exe
    0000004e    0 <==
System information:
    Wine build: wine-1.9.7
    Platform: i386 (WOW64)
    Version: Windows XP
    Host system: Darwin
    Host version: 15.0.0

---

