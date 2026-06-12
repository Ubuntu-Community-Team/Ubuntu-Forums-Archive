---
title: "Dota 2 ubuntu wine"
date: 2012-12-18
forum: Wine
---

### Post by thelavajatan on 2012-12-18
please how can i install dota 2 using wine on steam i have downloaded and when i press play nothing happens please help me am dead :( TY

---

### Post by Lila7714 on 2012-12-24
Hello. I have been running Dota 2 flawlessly with wine 1.5.20. Everything you'll need to know can be found at 'http://appdb.winehq.org/objectManager.php?sClass=version&iId=24458' however there are a few things I advise. I had a problem with wine tricks installing steam so I just downloaded from the steam website and installed. If your Steam client ran and you saw no text run with '-no-dwrite' arg. Also, running full screen doesn't work the greatest with gnome shell so run in a different x session using this 'https://wiki.archlinux.org/index.php/Running_program_in_separate_X_display'. Lastly make sure you have all the proper 32 bit libraries if running 64bit.

---

### Post by LaRainette on 2013-01-04
Hi Lila7714,

Could you elaborate on the appropriate 32 bits librairies to install ?
I've installed wine 1.5.20 from the winehq wbesite and steam and dota 2.

Dota 2 launches and the game runs very smoothly but it crashes every 3-5 minutes with the same error message every time.
What librairies do I need to install ?


Here is the error :
```
 Unhandled exception: page fault on write access to 0x00000140 in 32-bit code (0x0f994e92).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0f994e92 ESP:16cee320 EBP:16cee4ec EFLAGS:00210286(  R- --  I S - -P- )
 EAX:16cee330 EBX:0fa2eb34 ECX:00000034 EDX:00000033
 ESI:00000000 EDI:00000000
Stack dump:
0x16cee320:  0f9950a2 00000000 00000000 00000000
0x16cee330:  00000006 ffffffff ffffffff 00000007
0x16cee340:  00000008 0000000d 0000000e 0000000f
0x16cee350:  00000010 00000011 00000012 00000013
0x16cee360:  00000014 00000015 00000016 ffffffff
0x16cee370:  ffffffff ffffffff ffffffff ffffffff
000c: sel=0067 base=00000000 limit=00000000 32-bit --x
Backtrace:
=>0 0x0f994e92 in stdshader_dx9 (+0x64e92) (0x16cee4ec)
  1 0x0f9abf08 in stdshader_dx9 (+0x7bf07) (0x16cee534)
  2 0x0a765484 in materialsystem (+0x45483) (0x16cee58c)
  3 0x0a7278c5 in materialsystem (+0x78c4) (0x16cee5b4)
  4 0x0d205317 in shaderapidx9 (+0x15316) (0x16cee608)
  5 0x0d1f7d98 in shaderapidx9 (+0x7d97) (0x16cee698)
  6 0x0d1faaa8 in shaderapidx9 (+0xaaa7) (0x16cee7a4)
  7 0x0d1fab12 in shaderapidx9 (+0xab11) (0x16cee7b8)
  8 0x0d1fc5fe in shaderapidx9 (+0xc5fd) (0x16cee804)
  9 0x0d1fd6cc in shaderapidx9 (+0xd6cb) (0x16cee82c)
  10 0x0a7534e5 in materialsystem (+0x334e4) (0x16cee844)
  11 0x0a74c712 in materialsystem (+0x2c711) (0x16cee864)
  12 0x0a748fd8 in materialsystem (+0x28fd7) (0x16cee8a8)
  13 0x0a7386e1 in materialsystem (+0x186e0) (0x16cee8e0)
  14 0x018eb274 in vstdlib (+0xb273) (0x16cee918)
  15 0x018eb547 in vstdlib (+0xb546) (0x16cee948)
  16 0x018ebc7d in vstdlib (+0xbc7c) (0x16cee9e8)
  17 0x01884e33 in tier0 (+0x14e32) (0x16ceea18)
  18 0x7bc77130 call_thread_func_wrapper+0xb() in ntdll (0x16ceea28)
  19 0x7bc79cad call_thread_func+0x7c() in ntdll (0x16ceeaf8)
  20 0x7bc7710e RtlRaiseException+0x21() in ntdll (0x16ceeb18)
  21 0x7bc7fe58 in ntdll (+0x6fe57) (0x16cef368)
  22 0xf7606d4c start_thread+0xcb() in libpthread.so.0 (0x16cef468)
0x0f994e92: movl    %ecx,0x10c(%eax)
Modules:
Module    Address            Debug info    Name (195 modules)
PE      400000-  441000    Deferred        dota
PE     1830000- 186c000    Deferred        launcher
PE     1870000- 18d1000    Export          tier0
PE     18e0000- 1968000    Export          vstdlib
PE     9750000- 97c2000    Deferred        filesystem_stdio
PE     99d0000- a294000    Deferred        engine
PE     a620000- a6ef000    Deferred        networksystem
PE     a6f0000- a718000    Deferred        inputsystem
PE     a720000- a87d000    Export          materialsystem
PE     b8b0000- be47000    Deferred        datacache
PE     be50000- c2b7000    Deferred        studiorender
PE     c2c0000- c2f4000    Deferred        soundemittersystem
PE     c300000- c42f000    Deferred        vphysics
PE     c430000- c4f1000    Deferred        vscript
PE     c500000- c52c000    Deferred        valve_avi
PE     c530000- c6ea000    Deferred        vguimatsurface
PE     c6f0000- c774000    Deferred        vgui2
PE     c780000- cfdc000    Deferred        scaleformui_4
PE     cfe0000- d1df000    Deferred        d3dx9_43
PE     d1f0000- d321000    Export          shaderapidx9
PE     d330000- d361000    Deferred        localize
PE     f590000- f642000    Deferred        crashhandler
PE     f780000- f794000    Deferred        xinput1_3
PE     f8f0000- f92a000    Deferred        stdshader_dbg
PE     f930000- fa4e000    Export          stdshader_dx9
PE    10000000-10098000    Deferred        gameoverlayrenderer
PE    13af0000-15d14000    Deferred        client
PE    16ad0000-16ae8000    Deferred        scenefilecache
PE    18000000-18033000    Deferred        binkw32
PE    21580000-21596000    Deferred        vaudio_miles
PE    215a0000-21639000    Deferred        mss32
PE    21750000-21757000    Deferred        mssds3d.flt
PE    21760000-21766000    Deferred        mssdolby.flt
PE    22300000-22311000    Deferred        msseax.flt
PE    23000000-23007000    Deferred        msssrs.flt
PE    24100000-24112000    Deferred        mssdsp.flt
PE    26400000-2642a000    Deferred        mssvoice.asi
PE    26f00000-26f21000    Deferred        mssmp3.asi
PE    2b940000-2ba2e000    Deferred        chromehtml
PE    2ba30000-2cdbe000    Deferred        libcef
PE    38000000-386d2000    Deferred        steamclient
PE    3b400000-3b41e000    Deferred        steam_api
PE    3f000000-3f0a8000    Deferred        tier0_s
PE    3f600000-3f646000    Deferred        vstdlib_s
PE    48150000-4817d000    Deferred        vaudio_celt
PE    4ad00000-4b67f000    Deferred        icudt
ELF    7b800000-7ba33000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba33000    \               kernel32
ELF    7bc00000-7bcca000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcca000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7e3b8000-7e3bf000    Deferred        libxfixes.so.3
ELF    7e3c0000-7e3cb000    Deferred        libxcursor.so.1
ELF    7e3d0000-7e3e0000    Deferred        libxi.so.6
ELF    7e3e0000-7e3e4000    Deferred        libxcomposite.so.1
ELF    7e3e8000-7e3f3000    Deferred        libxrandr.so.2
ELF    7e3f8000-7e402000    Deferred        libxrender.so.1
ELF    7e408000-7e40e000    Deferred        libxxf86vm.so.1
ELF    7e410000-7e414000    Deferred        libxinerama.so.1
ELF    7e418000-7e41f000    Deferred        libxdmcp.so.6
ELF    7e420000-7e442000    Deferred        libxcb.so.1
ELF    7e448000-7e44e000    Deferred        libuuid.so.1
ELF    7e450000-7e46a000    Deferred        libice.so.6
ELF    7e470000-7e5a6000    Deferred        libx11.so.6
ELF    7e5a8000-7e5ba000    Deferred        libxext.so.6
ELF    7e5c0000-7e5c9000    Deferred        libsm.so.6
ELF    7e5d0000-7e65a000    Deferred        winex11<elf>
  \-PE    7e5e0000-7e65a000    \               winex11
ELF    7e660000-7e679000    Deferred        libz.so.1
ELF    7e680000-7e71a000    Deferred        libfreetype.so.6
ELF    7e748000-7e7c0000    Deferred        rpcrt4<elf>
  \-PE    7e750000-7e7c0000    \               rpcrt4
ELF    7e7c0000-7e8d5000    Deferred        ole32<elf>
  \-PE    7e7e0000-7e8d5000    \               ole32
ELF    7e8d8000-7e8fb000    Deferred        imm32<elf>
  \-PE    7e8e0000-7e8fb000    \               imm32
ELF    7e928000-7e98d000    Deferred        advapi32<elf>
  \-PE    7e930000-7e98d000    \               advapi32
ELF    7e990000-7ea9b000    Deferred        gdi32<elf>
  \-PE    7e9a0000-7ea9b000    \               gdi32
ELF    7eaa0000-7ebe7000    Deferred        user32<elf>
  \-PE    7eab0000-7ebe7000    \               user32
ELF    7ebe8000-7ebf5000    Deferred        libnss_files.so.2
ELF    7ebf8000-7ec04000    Deferred        libnss_nis.so.2
ELF    7ec08000-7ec22000    Deferred        libnsl.so.1
ELF    7ec28000-7ec31000    Deferred        libnss_compat.so.2
ELF    7efa8000-7efd4000    Deferred        libm.so.6
ELF    7efd8000-7efdc000    Deferred        libxau.so.6
ELF    7efe0000-7effa000    Deferred        version<elf>
  \-PE    7eff0000-7effa000    \               version
ELF    e6860000-e68f2000    Deferred        urlmon<elf>
  \-PE    e6870000-e68f2000    \               urlmon
ELF    e68f8000-e69da000    Deferred        comdlg32<elf>
  \-PE    e6900000-e69da000    \               comdlg32
ELF    ec200000-ec214000    Deferred        msimg32<elf>
  \-PE    ec210000-ec214000    \               msimg32
ELF    ec218000-ec256000    Deferred        usp10<elf>
  \-PE    ec220000-ec256000    \               usp10
ELF    ec258000-ec276000    Deferred        libgcc_s.so.1
ELF    ec278000-ec2b0000    Deferred        winhttp<elf>
  \-PE    ec280000-ec2b0000    \               winhttp
ELF    f1728000-f173f000    Deferred        libresolv.so.2
ELF    f1740000-f176c000    Deferred        libvorbis.so.0
ELF    f1770000-f18e8000    Deferred        libvorbisenc.so.2
ELF    f18e8000-f1938000    Deferred        libflac.so.8
ELF    f1938000-f19ac000    Deferred        libsndfile.so.1
ELF    f19b0000-f19ba000    Deferred        libwrap.so.0
ELF    f19c0000-f1a0a000    Deferred        libdbus-1.so.3
ELF    f1a10000-f1a74000    Deferred        libpulsecommon-2.1.so
ELF    f1a78000-f1a82000    Deferred        libjson.so.0
ELF    f1a88000-f1ad6000    Deferred        libpulse.so.0
ELF    f1b00000-f1b26000    Deferred        winepulse<elf>
  \-PE    f1b10000-f1b26000    \               winepulse
ELF    f1b28000-f1b49000    Deferred        mmdevapi<elf>
  \-PE    f1b30000-f1b49000    \               mmdevapi
ELF    f3c30000-f3c54000    Deferred        dxgi<elf>
  \-PE    f3c40000-f3c54000    \               dxgi
ELF    f3c58000-f3c80000    Deferred        wbemprox<elf>
  \-PE    f3c60000-f3c80000    \               wbemprox
ELF    f3c80000-f3cbe000    Deferred        winspool<elf>
  \-PE    f3c90000-f3cbe000    \               winspool
ELF    f3cc0000-f3d29000    Deferred        setupapi<elf>
  \-PE    f3cd0000-f3d29000    \               setupapi
ELF    f3d30000-f3db4000    Deferred        libgcrypt.so.11
ELF    f3db8000-f3dca000    Deferred        libtasn1.so.3
ELF    f3dd0000-f3e94000    Deferred        libgnutls.so.26
ELF    f3ea0000-f3ea7000    Deferred        libnss_dns.so.2
ELF    f3ea8000-f3ebe000    Deferred        winejoystick<elf>
  \-PE    f3eb0000-f3ebe000    \               winejoystick
ELF    f3ec0000-f3eeb000    Deferred        netapi32<elf>
  \-PE    f3ed0000-f3eeb000    \               netapi32
ELF    f3ef0000-f3f1f000    Deferred        secur32<elf>
  \-PE    f3f00000-f3f1f000    \               secur32
ELF    f4788000-f47a0000    Deferred        userenv<elf>
  \-PE    f4790000-f47a0000    \               userenv
ELF    f4800000-f4809000    Deferred        librt.so.1
ELF    f48b8000-f48c0000    Deferred        libogg.so.0
ELF    f48c0000-f48c5000    Deferred        libgpg-error.so.0
ELF    f48c8000-f48dc000    Deferred        libp11-kit.so.0
ELF    f48e0000-f48fe000    Deferred        pdh<elf>
  \-PE    f48f0000-f48fe000    \               pdh
ELF    f4900000-f491a000    Deferred        imagehlp<elf>
  \-PE    f4910000-f491a000    \               imagehlp
ELF    f4920000-f49dd000    Deferred        crypt32<elf>
  \-PE    f4930000-f49dd000    \               crypt32
ELF    f4a80000-f6785000    Deferred        libnvidia-glcore.so.304.51
ELF    f6788000-f6864000    Deferred        libgl.so.1
ELF    f6868000-f686f000    Deferred        libasyncns.so.0
ELF    f6890000-f6925000    Deferred        msvcrt<elf>
  \-PE    f68a0000-f6925000    \               msvcrt
ELF    f6928000-f69ff000    Deferred        opengl32<elf>
  \-PE    f6940000-f69ff000    \               opengl32
ELF    f6a00000-f6b32000    Deferred        wined3d<elf>
  \-PE    f6a10000-f6b32000    \               wined3d
ELF    f6b38000-f6c52000    Deferred        oleaut32<elf>
  \-PE    f6b50000-f6c52000    \               oleaut32
ELF    f6cb8000-f6cbc000    Deferred        libnvidia-tls.so.304.51
ELF    f6cc0000-f6d05000    Deferred        dsound<elf>
  \-PE    f6cd0000-f6d05000    \               dsound
ELF    f6d08000-f6d40000    Deferred        d3d9<elf>
  \-PE    f6d10000-f6d40000    \               d3d9
ELF    f6d40000-f6d6b000    Deferred        msvfw32<elf>
  \-PE    f6d50000-f6d6b000    \               msvfw32
ELF    f6d70000-f6db2000    Deferred        avifil32<elf>
  \-PE    f6d80000-f6db2000    \               avifil32
ELF    f6db8000-f6dde000    Deferred        mpr<elf>
  \-PE    f6dc0000-f6dde000    \               mpr
ELF    f6de0000-f6e54000    Deferred        wininet<elf>
  \-PE    f6df0000-f6e54000    \               wininet
ELF    f6f20000-f6f34000    Deferred        psapi<elf>
  \-PE    f6f30000-f6f34000    \               psapi
ELF    f6f38000-f6f6c000    Deferred        uxtheme<elf>
  \-PE    f6f40000-f6f6c000    \               uxtheme
ELF    f6f70000-f6f99000    Deferred        msacm32<elf>
  \-PE    f6f80000-f6f99000    \               msacm32
ELF    f6fa0000-f704f000    Deferred        winmm<elf>
  \-PE    f6fb0000-f704f000    \               winmm
ELF    f7050000-f7074000    Deferred        iphlpapi<elf>
  \-PE    f7060000-f7074000    \               iphlpapi
ELF    f7078000-f70ab000    Deferred        ws2_32<elf>
  \-PE    f7080000-f70ab000    \               ws2_32
ELF    f70b0000-f71ac000    Deferred        comctl32<elf>
  \-PE    f70c0000-f71ac000    \               comctl32
ELF    f71b0000-f721f000    Deferred        shlwapi<elf>
  \-PE    f71c0000-f721f000    \               shlwapi
ELF    f7220000-f7439000    Deferred        shell32<elf>
  \-PE    f7230000-f7439000    \               shell32
ELF    f7448000-f744d000    Deferred        libdl.so.2
ELF    f7450000-f75fa000    Dwarf           libc.so.6
ELF    f7600000-f761b000    Dwarf           libpthread.so.0
ELF    f7620000-f763b000    Deferred        wsock32<elf>
  \-PE    f7630000-f763b000    \               wsock32
ELF    f7648000-f778a000    Dwarf           libwine.so.1
ELF    f7790000-f77b2000    Deferred        ld-linux.so.2
ELF    f77b6000-f77b7000    Deferred        [vdso].so
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
00000096 explorer.exe
    00000097    0
00000066 Steam.exe
    0000004b    1
    0000004e    0
    00000090    0
    00000079    0
    0000005a    0
    0000006d    0
    0000006c    0
    00000069    0
    00000018    1
    00000042    1
    00000067    0
    0000006f    0
    00000045    0
    0000006a    0
    0000006b    0
    00000056    0
    00000057    0
    00000089    0
    0000008a    0
    0000008d    0
    00000083    0
    00000082    0
    00000080    0
    0000007c    0
    0000007b    0
    00000078    0
    00000074    0
    00000072    0
    0000005f    0
    0000005e   15
    0000005d    0
    0000005c    0
    0000005b    0
    00000059    0
    00000058    0
    0000007f    0
    0000007e    0
    0000007d    0
    0000007a    0
    00000071    0
    00000070    0
    00000073    0
    0000008e    0
    00000084    0
    0000008b    0
    00000085    0
    00000088    0
    00000086    0
    00000087    0
    00000081    0
    0000008c    0
    00000061    0
    00000062    0
    00000065    0
00000030 (D) C:\Program Files (x86)\Steam\SteamApps\common\dota 2 beta\dota.exe
    0000003d   15
    00000053    0
    00000038    0
    00000009    0
    0000000d    0
    0000003b    0
    0000003c    0
    0000004c    0
    0000002b    0
    00000027    0
    0000003a    0
    00000068    0
    00000021    0
    00000095    0
    0000000c    0
    00000024    0
    00000041    0
    00000037    2
    00000036    2
    00000032   15
    0000002e    0
    0000003e    0 <==
    00000025    0
    00000031    0
    00000040    0
    0000003f   15
    00000023    0
    0000002d    0
    00000035    0
    0000002f    0
    00000034    0
    00000033    0
00000043 GameOverlayUI.exe
    00000044    0
    00000076    0
    00000077   15
    00000060    0
    00000026    0
    00000093    0
    0000004f    0
    00000028    0
    0000002c    0
    00000029    0
    00000051    0
    00000050    0
    00000052    0
    00000055    0
    00000049    0
    0000004d    0
    00000054    0
    00000091    0
System information:
    Wine build: wine-1.5.20
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.5.0-19-generic
```

---

### Post by Lila7714 on 2013-01-04
Well currently the only 64bit system I have is running Archlinux(T'is what I am running the dota 2 on) my Ubuntu is 32 so I'm not entirely sure about package names but last time I checked there was ia32-libs.

Also, if you aren't, use the proprietary nvidia drivers.

PS. J'aime le nom:p

---

### Post by saurabhs on 2013-04-15
Hi, 
I am using playonlinux with version 1.5.26. It runs steam fine and  when i launch Dota2 it goes starting for first time use, installing  directx. Then it goes to dota2 loading screen. Then it crashes saying  Engine Error. Playonlinux log file  

Creating D3D9 device with D3DCREATE_MULTITHREADED 
CDOTAGCClientSystem::CDOTAGCClientSystem user session not yet created 
CClientSteamContext logged on = 1 
ConVarRef rr_debugresponses doesn't point to an existing ConVar 
Could not get IReplayDirector interface from library server.dllGame.dll loaded for "Dota 2" 

I am swtiching to uBuntu from windows and in windows dota2 works  fine expect there is a audiodg memory leak issue of which no current  hotfix is able to fix for my system.  

Regards 
Saurabh

---

