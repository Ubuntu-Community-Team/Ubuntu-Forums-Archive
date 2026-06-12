---
title: "League of Legends crash Radeon 7870"
date: 2015-06-16
forum: Wine
---

### Post by roy27 on 2015-06-16
Crashes when "Launch" button is pressed.
```
Unhandled exception: page fault on read access to 0x0000000c in 32-bit code (0x7c849a74).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7c849a74 ESP:0033e15c EBP:0033e198 EFLAGS:00010202(  R- --  I   - - - )
 EAX:00000000 EBX:7c49d000 ECX:00000000 EDX:00000001
 ESI:00000000 EDI:00000000
Stack dump:
0x0033e15c:  7c44b082 00000000 000000b9 00000000
0x0033e16c:  00000002 f752a420 00000000 0033e1d8
0x0033e17c:  000000b9 00000008 000000b1 7c44b02b
0x0033e18c:  7c49d000 7cc41820 00000000 0033e1d8
0x0033e19c:  7c4298f6 7cc56a70 0000009b 00000000
0x0033e1ac:  00000002 7cc334c0 7c429ae0 00000001
Backtrace:
=>0 0x7c849a74 xcb_glx_query_server_string_string_length+0x4() in libxcb-glx.so.0 (0x0033e198)
  1 0x7c44b082 in libgl.so.1 (+0x3b081) (0x0033e198)
  2 0x7c4298f6 in libgl.so.1 (+0x198f5) (0x0033e1d8)
  3 0x7c425f3d in libgl.so.1 (+0x15f3c) (0x0033e568)
  4 0x7c4267be glXChooseVisual+0x4d() in libgl.so.1 (0x0033e568)
  5 0x7dc215a1 in winex11 (+0x315a0) (0x0033e568)
  6 0x7dc24305 in winex11 (+0x34304) (0x0033e598)
  7 0x7dc12de2 in winex11 (+0x22de1) (0x0033e5b8)
  8 0x7e6fc0bf __wine_get_wgl_driver+0x4e() in gdi32 (0x0033e5d8)
  9 0x7c509cd7 in wined3d (+0x49cd6) (0x0033ea48)
  10 0x7c514db3 in wined3d (+0x54db2) (0x0033ea78)
  11 0x7c5a23d9 wined3d_create+0x68() in wined3d (0x0033eab8)
  12 0x7c8a1a28 in d3d9 (+0x11a27) (0x0033eaf8)
  13 0x7c894dc7 Direct3DCreate9+0x76() in d3d9 (0x0033eb38)
  14 0x1036b918 in adobe air (+0x36b917) (0x0033efb8)
  15 0x101c5cf8 in adobe air (+0x1c5cf7) (0x0033f000)
  16 0x101c6e23 in adobe air (+0x1c6e22) (0x0033f088)
  17 0x101c6f9c in adobe air (+0x1c6f9b) (0x0033f0b4)
  18 0x101c81a2 in adobe air (+0x1c81a1) (0x0033f0d4)
  19 0x101c958f in adobe air (+0x1c958e) (0x0033f134)
  20 0x1006d526 in adobe air (+0x6d525) (0x0033f25c)
0x7c849a74 xcb_glx_query_server_string_string_length+0x4 in libxcb-glx.so.0: movl    0xc(%eax),%eax
Modules:
Module    Address            Debug info    Name (162 modules)
PE      400000-  416000    Deferred        lolclient
PE    10000000-114d1000    Export          adobe air
ELF    7a800000-7a92c000    Deferred        opengl32<elf>
  \-PE    7a820000-7a92c000    \               opengl32
ELF    7b800000-7ba66000    Deferred        kernel32<elf>
  \-PE    7b820000-7ba66000    \               kernel32
ELF    7bc00000-7bce4000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bce4000    \               ntdll
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
ELF    7c410000-7c4a2000    Dwarf           libgl.so.1
ELF    7c4a8000-7c5f9000    Dwarf           wined3d<elf>
  \-PE    7c4c0000-7c5f9000    \               wined3d
ELF    7c808000-7c816000    Deferred        libdrm.so.2
ELF    7c818000-7c81b000    Deferred        libxshmfence.so.1
ELF    7c820000-7c827000    Deferred        libxcb-sync.so.1
ELF    7c828000-7c82c000    Deferred        libxcb-present.so.0
ELF    7c830000-7c834000    Deferred        libxcb-dri3.so.0
ELF    7c838000-7c83e000    Deferred        libxcb-dri2.so.0
ELF    7c840000-7c858000    Dwarf           libxcb-glx.so.0
ELF    7c880000-7c8be000    Dwarf           d3d9<elf>
  \-PE    7c890000-7c8be000    \               d3d9
ELF    7c8c0000-7c8c9000    Deferred        libogg.so.0
ELF    7c8d0000-7c8fc000    Deferred        libvorbis.so.0
ELF    7c900000-7ca78000    Deferred        libvorbisenc.so.2
ELF    7ca78000-7caac000    Deferred        libflac.so.8
ELF    7cab0000-7cab7000    Deferred        libasyncns.so.0
ELF    7cab8000-7cb2a000    Deferred        libsndfile.so.1
ELF    7cb30000-7cc26000    Deferred        libasound.so.2
ELF    7ccf0000-7ccf3000    Deferred        libx11-xcb.so.1
ELF    7ccf8000-7cd02000    Deferred        libwrap.so.0
ELF    7cd08000-7cd77000    Deferred        libpulsecommon-4.0.so
ELF    7cd78000-7cd83000    Deferred        libjson-c.so.2
ELF    7cd88000-7cdd7000    Deferred        libpulse.so.0
ELF    7cdd8000-7cdf1000    Deferred        libglapi.so.0
ELF    7cf08000-7cf39000    Deferred        winealsa<elf>
  \-PE    7cf10000-7cf39000    \               winealsa
ELF    7cf40000-7cf62000    Deferred        mmdevapi<elf>
  \-PE    7cf50000-7cf62000    \               mmdevapi
ELF    7cf68000-7cf7d000    Deferred        schannel<elf>
  \-PE    7cf70000-7cf7d000    \               schannel
ELF    7cf80000-7cfa8000    Deferred        mlang<elf>
  \-PE    7cf90000-7cfa8000    \               mlang
ELF    7d018000-7d02b000    Deferred        psapi<elf>
  \-PE    7d020000-7d02b000    \               psapi
ELF    7d030000-7d097000    Deferred        dbghelp<elf>
  \-PE    7d040000-7d097000    \               dbghelp
ELF    7d098000-7d0ac000    Deferred        libtasn1.so.6
ELF    7d0b0000-7d0e0000    Deferred        p11-kit-trust.so
ELF    7d0e0000-7d0e7000    Deferred        libffi.so.6
ELF    7d0e8000-7d0ed000    Deferred        libgpg-error.so.0
ELF    7d0f0000-7d0f4000    Deferred        libkeyutils.so.1
ELF    7d0f8000-7d143000    Deferred        libdbus-1.so.3
ELF    7d148000-7d184000    Deferred        libp11-kit.so.0
ELF    7d188000-7d20d000    Deferred        libgcrypt.so.11
ELF    7d210000-7d222000    Deferred        libtasn1.so.3
ELF    7d228000-7d234000    Deferred        libkrb5support.so.0
ELF    7d238000-7d268000    Deferred        libk5crypto.so.3
ELF    7d268000-7d326000    Deferred        libkrb5.so.3
ELF    7d328000-7d33a000    Deferred        libavahi-client.so.3
ELF    7d340000-7d34e000    Deferred        libavahi-common.so.3
ELF    7d350000-7d419000    Deferred        libgnutls.so.26
ELF    7d420000-7d465000    Deferred        libgssapi_krb5.so.2
ELF    7d468000-7d4d5000    Deferred        libcups.so.2
ELF    7d4d8000-7d4dc000    Deferred        libxdamage.so.1
ELF    7d4e0000-7d4e7000    Deferred        libasound_module_pcm_pulse.so
ELF    7d4e8000-7d4fb000    Deferred        gnome-keyring-pkcs11.so
ELF    7d500000-7d54d000    Deferred        dsound<elf>
  \-PE    7d510000-7d54d000    \               dsound
ELF    7d550000-7d568000    Deferred        libresolv.so.2
ELF    7d570000-7d58f000    Deferred        dnsapi<elf>
  \-PE    7d580000-7d58f000    \               dnsapi
ELF    7d590000-7d5b6000    Deferred        iphlpapi<elf>
  \-PE    7d5a0000-7d5b6000    \               iphlpapi
ELF    7d5b8000-7d5e7000    Deferred        netapi32<elf>
  \-PE    7d5c0000-7d5e7000    \               netapi32
ELF    7d5e8000-7d61a000    Deferred        secur32<elf>
  \-PE    7d5f0000-7d61a000    \               secur32
ELF    7d620000-7d63c000    Deferred        mscms<elf>
  \-PE    7d630000-7d63c000    \               mscms
ELF    7d640000-7d682000    Deferred        winspool<elf>
  \-PE    7d650000-7d682000    \               winspool
ELF    7d688000-7d775000    Deferred        comdlg32<elf>
  \-PE    7d690000-7d775000    \               comdlg32
ELF    7d778000-7d7d6000    Deferred        oleacc<elf>
  \-PE    7d780000-7d7d6000    \               oleacc
ELF    7d7d8000-7d802000    Deferred        msacm32<elf>
  \-PE    7d7e0000-7d802000    \               msacm32
ELF    7d808000-7d8c0000    Deferred        winmm<elf>
  \-PE    7d810000-7d8c0000    \               winmm
ELF    7d8c0000-7d991000    Deferred        crypt32<elf>
  \-PE    7d8d0000-7d991000    \               crypt32
ELF    7d998000-7d9d0000    Deferred        uxtheme<elf>
  \-PE    7d9a0000-7d9d0000    \               uxtheme
ELF    7d9d0000-7d9d6000    Deferred        libxfixes.so.3
ELF    7d9d8000-7d9e3000    Deferred        libxcursor.so.1
ELF    7d9e8000-7d9f8000    Deferred        libxi.so.6
ELF    7d9f8000-7d9fc000    Deferred        libxcomposite.so.1
ELF    7da00000-7da0b000    Deferred        libxrandr.so.2
ELF    7da10000-7da1b000    Deferred        libxrender.so.1
ELF    7da20000-7da26000    Deferred        libxxf86vm.so.1
ELF    7da28000-7da2c000    Deferred        libxinerama.so.1
ELF    7da30000-7da37000    Deferred        libxdmcp.so.6
ELF    7da38000-7da3c000    Deferred        libxau.so.6
ELF    7da40000-7da62000    Deferred        libxcb.so.1
ELF    7da68000-7db9c000    Deferred        libx11.so.6
ELF    7dba0000-7dbb3000    Deferred        libxext.so.6
ELF    7dbb8000-7dbbd000    Deferred        libcom_err.so.2
ELF    7dbc0000-7dbd3000    Deferred        msimg32<elf>
  \-PE    7dbd0000-7dbd3000    \               msimg32
ELF    7dbe0000-7dc73000    Dwarf           winex11<elf>
  \-PE    7dbf0000-7dc73000    \               winex11
ELF    7dc78000-7dc9c000    Deferred        imm32<elf>
  \-PE    7dc80000-7dc9c000    \               imm32
ELF    7dd90000-7ddb9000    Deferred        libexpat.so.1
ELF    7ddc0000-7ddfb000    Deferred        libfontconfig.so.1
ELF    7de00000-7de28000    Deferred        libpng12.so.0
ELF    7de28000-7dec8000    Deferred        libfreetype.so.6
ELF    7def0000-7df10000    Deferred        cabinet<elf>
  \-PE    7df00000-7df10000    \               cabinet
ELF    7df10000-7e01b000    Deferred        comctl32<elf>
  \-PE    7df20000-7e01b000    \               comctl32
ELF    7e020000-7e059000    Deferred        ws2_32<elf>
  \-PE    7e030000-7e059000    \               ws2_32
ELF    7e060000-7e087000    Deferred        mpr<elf>
  \-PE    7e070000-7e087000    \               mpr
ELF    7e088000-7e0a1000    Deferred        libz.so.1
ELF    7e0a8000-7e125000    Deferred        wininet<elf>
  \-PE    7e0b0000-7e125000    \               wininet
ELF    7e128000-7e26a000    Deferred        oleaut32<elf>
  \-PE    7e140000-7e26a000    \               oleaut32
ELF    7e270000-7e2f6000    Deferred        rpcrt4<elf>
  \-PE    7e280000-7e2f6000    \               rpcrt4
ELF    7e2f8000-7e43a000    Deferred        ole32<elf>
  \-PE    7e310000-7e43a000    \               ole32
ELF    7e440000-7e4e4000    Deferred        urlmon<elf>
  \-PE    7e450000-7e4e4000    \               urlmon
ELF    7e4e8000-7e5e9000    Deferred        msi<elf>
  \-PE    7e4f0000-7e5e9000    \               msi
ELF    7e5f0000-7e669000    Deferred        advapi32<elf>
  \-PE    7e600000-7e669000    \               advapi32
ELF    7e670000-7e789000    Dwarf           gdi32<elf>
  \-PE    7e680000-7e789000    \               gdi32
ELF    7e790000-7e8ed000    Deferred        user32<elf>
  \-PE    7e7a0000-7e8ed000    \               user32
ELF    7e8f0000-7e96b000    Deferred        shlwapi<elf>
  \-PE    7e900000-7e96b000    \               shlwapi
ELF    7e970000-7ebb9000    Deferred        shell32<elf>
  \-PE    7e980000-7ebb9000    \               shell32
ELF    7ebc0000-7ebcd000    Deferred        libnss_files.so.2
ELF    7ebd0000-7ebdc000    Deferred        libnss_nis.so.2
ELF    7ebe0000-7ebf9000    Deferred        libnsl.so.1
ELF    7ec00000-7ec09000    Deferred        libnss_compat.so.2
ELF    7ef80000-7efc6000    Deferred        libm.so.6
ELF    7efc8000-7efd1000    Deferred        librt.so.1
ELF    7efe0000-7eff9000    Deferred        version<elf>
  \-PE    7eff0000-7eff9000    \               version
ELF    f7378000-f737d000    Deferred        libdl.so.2
ELF    f7380000-f752e000    Deferred        libc.so.6
ELF    f7530000-f754c000    Deferred        libpthread.so.0
ELF    f7578000-f772e000    Dwarf           libwine.so.1
ELF    f7730000-f7752000    Deferred        ld-linux.so.2
ELF    f7754000-f7755000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001d    0
    0000001c    0
    00000016    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001b    0
    00000018    0
    00000017    0
    00000013    0
00000019 plugplay.exe
    0000001f    0
    0000001e    0
    0000001a    0
00000020 rads_user_kernel.exe
    00000030    0
    0000002f    0
    0000002e    0
    0000002d    0
    0000002c    0
    0000002a    0
    00000029    0
    00000021    0
00000023 explorer.exe
    00000028    0
    00000027    0
    00000026    0
    00000024    0
00000032 LoLLauncher.exe
    00000038    0
    00000037    0
    00000036    0
    00000035    0
    00000034    0
    00000033    0
0000003a LoLPatcher.exe
    000000a8    0
    000000a7    0
    000000a6    0
    00000081    0
    00000045    0
    00000044    0
    00000043    0
    00000042    0
    00000041    0
    00000040    0
    0000003f    0
    0000003e    0
    0000003d    0
    0000003c    0
    0000003b    0
000000a9 (D) C:\Riot Games\League of Legends\RADS\projects\lol_air_client\releases\0.0.1.148\deploy\LolClient.exe
    000000c3    0
    000000c2    0
    000000c1    0
    000000c0    0
    000000bf    0
    000000be    0
    000000bd    0
    000000bc    0
    000000bb    0
    000000ba    0
    000000b9    0
    000000b8    0
    000000b7    0
    000000b6    0
    000000b5    0
    000000b4    0
    000000b3    0
    000000b2    0
    000000b1    0
    000000b0    0
    000000af    0
    000000ae    0
    000000ad    0
    000000ac    0
    000000ab    0
    000000aa    0 <==
System information:
    Wine build: wine-1.7.44
    Platform: i386
    Host system: Linux
    Host version: 3.16.0-41-generic
```

Right now I am using xorg drivers (open source), they used to work. They used to let me play the game at 30-40 FPS (doesn't matter if the quality of the game was set to the lowest setting or the highest setting), on my Windows 7 (I'm dual booting) I can run League of Legends at 60 FPS on the highest setting. I want to do that on Ubuntu, so I don't have to keep rebooting into Windows. Is it possible? The game looked perfect when it was running, it just had a really low frame rate (there is no way I can win tradeoffs with other players with that low framerate). I tried to install the 7870 drivers, and I did, they first crashed my PC (a couple of times) then I went back and did a recommended installation for Trusty Ubuntu, and they seemed to work alright. I tried launching the game with that driver (Advanced Micro Devices, Inc. [AMD/ATI] Pitcairn XT[Radeon HD 7870 GHz Edition]...they keep making my Ubuntu pop up all sorts of errors so I normally disable them), the client would load and everything, but when you actually load the match, it displays the League of Legends in the middle of the screen forever. That sometimes happened on my Windows too. Here's what supposed to happen: -2)You click the icon to start the game -1) A client loads that lets you press Launch 0) You hit Launch and that old client disappears, and a new client appears that lets you login 0.5)You login and that client now lets you queue for a game 1)You queue for a match and get into a screen in which you pick your player. 2)After the time runs out the client minimizes itself a new window pops up (with a logo). 3)That logo turns into a new screen that fully maximizes itself onto your screen and shows you that each player is loading the game. 5) Once all players have loaded you are allowed to see the game and start playing. .........I can only get to step 2 with the proprietary drivers, and to step -1 with X.org drivers... I just tried to proprietary drivers again, they'e giving me the same error as the X.org driver, stopping at step -1.
Edit: The software I've used is PlayOnLinux, which uses Wine.

---

### Post by roy27 on 2015-06-20
I tried installing more drivers, tweaking most of the available settings in the PlayOnLinux client, deleting certain folders, and I reinstalling the game about five times...none of it worked.

---

