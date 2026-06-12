---
title: "Let's get Alien Isolation running in Ubuntu"
date: 2014-10-08
forum: Wine
---

### Post by ZICODIAN on 2014-10-08
Ok, so Alien Isolation looks very nifty and we should try to get it running in Ubuntu.

Here's where I'm at: I'm running Ubuntu 14.04 64 bit. I've got the Steam Windows client installed and running successfully using Wine version 1.7.22 via PlayOnLinux. I've got Alien Isolation installed successfully simply using the Steam client.

Now, when I launch the game from the Steam client, I am presented with a black screen featuring a movable stylised mouse pointer. This is very promising. At this point, unhappily, an error is encountered and the game must be closed.

[IMG]http://i.imgur.com/dgJv3tH.png[/IMG]

Here's the error report:

```

Unhandled exception: unimplemented function d3d11.dll.D3D11CreateDeviceAndSwapChain called in 32-bit code (0x7b83deb9).Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b83deb9 ESP:0033fa84 EBP:0033faf8 EFLAGS:00000287(   - --  I S - -P-C)
 EAX:7b8283e5 EBX:7b8a7604 ECX:7e6501c4 EDX:0033faa4
 ESI:00000002 EDI:80000100
Stack dump:
0x0033fa84:  0033fb28 00000008 0033fb48 80000100
0x0033fa94:  00000001 00000000 7b83deb9 00000002
0x0033faa4:  7e6501c4 7e650237 100a4658 8841824c
0x0033fab4:  0033facc 00a737a0 0033fb48 0033faec
0x0033fac4:  00000020 00000000 0033fb74 00a1f504
0x0033fad4:  0033fb48 0033faec 00000020 0033fcec
Backtrace:
=>0 0x7b83deb9 in kernel32 (+0x2deb9) (0x0033faf8)
  1 0x7e650168 in d3d11 (+0x10167) (0x0033fb38)
  2 0x7e64f7b9 in d3d11 (+0xf7b8) (0x0033fcd0)
  3 0x00a247f4 in ai (+0x6247f3) (0x0033fcd0)
  4 0x00a1144d in ai (+0x61144c) (0x0033fd80)
  5 0x007d9882 in ai (+0x3d9881) (0x0033fe60)
  6 0x7b86249c call_process_entry+0xb() in kernel32 (0x0033fe78)
  7 0x7b865ffb in kernel32 (+0x55ffa) (0x0033feb8)
  8 0x7bc7da40 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  9 0x7bc7dc9d call_thread_func+0x7c() in ntdll (0x0033ffa8)
  10 0x7bc7da1e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  11 0x7bc53dee in ntdll (+0x43ded) (0x0033ffe8)
0x7b83deb9: movl	0xfffffff0(%ebp),%ecx
Modules:
Module	Address			Debug info	Name (153 modules)
PE	  340000-  356000	Deferred        xinput1_3
PE	  400000- 237c000	Export          ai
PE	10000000-1010f000	Deferred        gameoverlayrenderer
PE	26a30000-26b01000	Deferred        steam
PE	30000000-302c1000	Deferred        steam2
PE	38000000-3890d000	Deferred        steamclient
PE	3b400000-3b41e000	Deferred        steam_api
PE	3f000000-3f0b0000	Deferred        tier0_s
PE	3f600000-3f652000	Deferred        vstdlib_s
PE	60000000-60021000	Deferred        cserhelper
ELF	7b800000-7ba4d000	Dwarf           kernel32<elf>
  \-PE	7b810000-7ba4d000	\               kernel32
ELF	7bc00000-7bcd0000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcd0000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7d5cd000-7d5d3000	Deferred        libxfixes.so.3
ELF	7d5d3000-7d5de000	Deferred        libxcursor.so.1
ELF	7d5de000-7d5ef000	Deferred        libxi.so.6
ELF	7d5ef000-7d5f3000	Deferred        libxcomposite.so.1
ELF	7d5f3000-7d5fe000	Deferred        libxrandr.so.2
ELF	7d5fe000-7d609000	Deferred        libxrender.so.1
ELF	7d609000-7d60f000	Deferred        libxxf86vm.so.1
ELF	7d60f000-7d613000	Deferred        libxinerama.so.1
ELF	7d613000-7d61a000	Deferred        libxdmcp.so.6
ELF	7d61a000-7d61e000	Deferred        libxau.so.6
ELF	7d61e000-7d640000	Deferred        libxcb.so.1
ELF	7d640000-7d774000	Deferred        libx11.so.6
ELF	7d774000-7d787000	Deferred        libxext.so.6
ELF	7d7b5000-7d840000	Deferred        winex11<elf>
  \-PE	7d7c0000-7d840000	\               winex11
ELF	7d966000-7d98f000	Deferred        libexpat.so.1
ELF	7d98f000-7d9ca000	Deferred        libfontconfig.so.1
ELF	7d9ca000-7d9f2000	Deferred        libpng12.so.0
ELF	7d9f2000-7da92000	Deferred        libfreetype.so.6
ELF	7dac0000-7dac7000	Deferred        libffi.so.6
ELF	7dac7000-7daf8000	Deferred        libcrypt.so.1
ELF	7daf8000-7dbb5000	Deferred        libsqlite3.so.0
ELF	7dbb5000-7dbfc000	Deferred        libhx509.so.5
ELF	7dbfc000-7dc0b000	Deferred        libheimbase.so.1
ELF	7dc0b000-7dc34000	Deferred        libwind.so.0
ELF	7dc34000-7dc39000	Deferred        libgpg-error.so.0
ELF	7dc39000-7dc75000	Deferred        libp11-kit.so.0
ELF	7dc75000-7dc87000	Deferred        libtasn1.so.3
ELF	7dc87000-7dc9d000	Deferred        libroken.so.18
ELF	7dc9d000-7dcd2000	Deferred        libhcrypto.so.4
ELF	7dcd2000-7dd78000	Deferred        libasn1.so.8
ELF	7dd78000-7ddfe000	Deferred        libkrb5.so.26
ELF	7ddfe000-7de07000	Deferred        libheimntlm.so.0
ELF	7de07000-7de8e000	Deferred        libgcrypt.so.11
ELF	7de8e000-7df57000	Deferred        libgnutls.so.26
ELF	7df57000-7df93000	Deferred        libgssapi.so.3
ELF	7df93000-7dfae000	Deferred        libsasl2.so.2
ELF	7dfae000-7dfbd000	Deferred        liblber-2.4.so.2
ELF	7dfbd000-7e00f000	Deferred        libldap_r-2.4.so.2
ELF	7e01b000-7e03d000	Deferred        imm32<elf>
  \-PE	7e020000-7e03d000	\               imm32
ELF	7e03d000-7e09c000	Deferred        wldap32<elf>
  \-PE	7e050000-7e09c000	\               wldap32
ELF	7e09c000-7e0c4000	Deferred        msacm32<elf>
  \-PE	7e0a0000-7e0c4000	\               msacm32
ELF	7e0c4000-7e177000	Deferred        winmm<elf>
  \-PE	7e0d0000-7e177000	\               winmm
ELF	7e177000-7e28f000	Deferred        ole32<elf>
  \-PE	7e190000-7e28f000	\               ole32
ELF	7e28f000-7e374000	Deferred        opengl32<elf>
  \-PE	7e2b0000-7e374000	\               opengl32
ELF	7e374000-7e4a6000	Deferred        wined3d<elf>
  \-PE	7e380000-7e4a6000	\               wined3d
ELF	7e4a6000-7e4ca000	Deferred        dxgi<elf>
  \-PE	7e4b0000-7e4ca000	\               dxgi
ELF	7e4ca000-7e544000	Deferred        rpcrt4<elf>
  \-PE	7e4e0000-7e544000	\               rpcrt4
ELF	7e544000-7e5ae000	Deferred        setupapi<elf>
  \-PE	7e550000-7e5ae000	\               setupapi
ELF	7e5ae000-7e5c7000	Deferred        libz.so.1
ELF	7e5c7000-7e625000	Deferred        dbghelp<elf>
  \-PE	7e5d0000-7e625000	\               dbghelp
ELF	7e625000-7e63d000	Deferred        libresolv.so.2
ELF	7e63e000-7e652000	Dwarf           d3d11<elf>
  \-PE	7e640000-7e652000	\               d3d11
ELF	7e652000-7e66b000	Deferred        imagehlp<elf>
  \-PE	7e660000-7e66b000	\               imagehlp
ELF	7e66b000-7e68f000	Deferred        iphlpapi<elf>
  \-PE	7e670000-7e68f000	\               iphlpapi
ELF	7e68f000-7e6a9000	Deferred        wsock32<elf>
  \-PE	7e690000-7e6a9000	\               wsock32
ELF	7e6a9000-7e6db000	Deferred        ws2_32<elf>
  \-PE	7e6b0000-7e6db000	\               ws2_32
ELF	7e6db000-7e7e9000	Deferred        gdi32<elf>
  \-PE	7e6f0000-7e7e9000	\               gdi32
ELF	7e7e9000-7e931000	Deferred        user32<elf>
  \-PE	7e800000-7e931000	\               user32
ELF	7e931000-7e9a1000	Deferred        shlwapi<elf>
  \-PE	7e940000-7e9a1000	\               shlwapi
ELF	7e9a1000-7ebc0000	Deferred        shell32<elf>
  \-PE	7e9b0000-7ebc0000	\               shell32
ELF	7ebc0000-7ec27000	Deferred        advapi32<elf>
  \-PE	7ebd0000-7ec27000	\               advapi32
ELF	7ec27000-7ec34000	Deferred        libnss_files.so.2
ELF	7ec34000-7ec40000	Deferred        libnss_nis.so.2
ELF	7ec40000-7ec59000	Deferred        libnsl.so.1
ELF	7ec59000-7ec62000	Deferred        libnss_compat.so.2
ELF	7ec64000-7ec77000	Deferred        psapi<elf>
  \-PE	7ec70000-7ec77000	\               psapi
ELF	7ec77000-7ec90000	Deferred        version<elf>
  \-PE	7ec80000-7ec90000	\               version
ELF	f624b000-f625f000	Deferred        hid<elf>
  \-PE	f6250000-f625f000	\               hid
ELF	f6291000-f62c8000	Deferred        libtxc_dxtn.so
ELF	f6310000-f631b000	Deferred        libpciaccess.so.0
ELF	f640f000-f641e000	Deferred        libdrm_radeon.so.1
ELF	f641e000-f6426000	Deferred        libdrm_nouveau.so.2
ELF	f6426000-f6448000	Deferred        libdrm_intel.so.1
ELF	f6448000-f69bb000	Deferred        i965_dri.so
ELF	f69bb000-f6a06000	Deferred        libdbus-1.so.3
ELF	f6a06000-f6a10000	Deferred        libnih-dbus.so.1
ELF	f6a10000-f6a29000	Deferred        libnih.so.1
ELF	f6a29000-f6a47000	Deferred        libcgmanager.so.0
ELF	f6a47000-f6a5a000	Deferred        libudev.so.1
ELF	f6a5a000-f6a67000	Deferred        libdrm.so.2
ELF	f6a67000-f6a6a000	Deferred        libxshmfence.so.1
ELF	f6a6a000-f6a82000	Deferred        libxcb-glx.so.0
ELF	f6a82000-f6ae2000	Deferred        libgl.so.1
ELF	f6ae2000-f6b00000	Deferred        libgcc_s.so.1
ELF	f6c02000-f6c09000	Deferred        libxcb-sync.so.1
ELF	f6c09000-f6c0d000	Deferred        libxcb-present.so.0
ELF	f6c0d000-f6c11000	Deferred        libxcb-dri3.so.0
ELF	f6c11000-f6c17000	Deferred        libxcb-dri2.so.0
ELF	f6c17000-f6c1b000	Deferred        libxdamage.so.1
ELF	f6c49000-f6c5d000	Deferred        libtasn1.so.6
ELF	f6c5d000-f6c60000	Deferred        libx11-xcb.so.1
ELF	f6c60000-f6c78000	Deferred        libglapi.so.0
ELF	f6c78000-f6c8b000	Deferred        gnome-keyring-pkcs11.so
ELF	f6c8b000-f6cbb000	Deferred        p11-kit-trust.so
ELF	f6cbb000-f6ce7000	Deferred        netapi32<elf>
  \-PE	f6cc0000-f6ce7000	\               netapi32
ELF	f6ce7000-f6d15000	Deferred        secur32<elf>
  \-PE	f6cf0000-f6d15000	\               secur32
ELF	f6d15000-f6e2c000	Deferred        oleaut32<elf>
  \-PE	f6d30000-f6e2c000	\               oleaut32
ELF	f6e2c000-f6ef0000	Deferred        crypt32<elf>
  \-PE	f6e40000-f6ef0000	\               crypt32
ELF	f6f06000-f6fa5000	Deferred        msvcrt<elf>
  \-PE	f6f20000-f6fa5000	\               msvcrt
ELF	f72f0000-f72f5000	Deferred        libcom_err.so.2
ELF	f72f7000-f733d000	Deferred        libm.so.6
ELF	f733d000-f7342000	Deferred        libdl.so.2
ELF	f7342000-f74f2000	Deferred        libc.so.6
ELF	f74f2000-f750e000	Deferred        libpthread.so.0
ELF	f7534000-f753d000	Deferred        librt.so.1
ELF	f753d000-f76f1000	Dwarf           libwine.so.1
ELF	f76f3000-f7715000	Deferred        ld-linux.so.2
ELF	f7715000-f7716000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	00000096    0
	0000001c    0
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
00000020 explorer.exe
	00000021    0
00000026 Steam.exe
	0000007c    0
	00000097    0
	00000093    0
	00000076    0
	00000016    0
	00000028    0
	00000066    0
	00000065    0
	00000064    0
	00000063    0
	00000062    0
	00000061    0
	00000022    0
	00000024    0
	00000023    0
	0000000b    0
	0000000d    0
	0000000c    0
	00000047    0
	00000046    0
	00000044    0
	00000043    0
	00000042    0
	0000002c    0
	0000002b    0
	00000027    0
0000002d steamwebhelper.exe
	0000008b    0
	00000088    0
	00000068    0
	0000004a    0
	00000045    0
	00000041    0
	00000040    0
	0000003f    0
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
	0000002f    0
	0000002e    0
00000025 steamwebhelper.exe
	0000005f    0
	00000054    0
	00000053    0
	00000052    0
	00000051    0
	00000050    0
	0000004f    0
	0000004e    0
	0000004d    0
	0000004c    0
	0000004b    0
	00000009    0
00000048 steamwebhelper.exe
	00000060    0
	0000005e    0
	0000005d    0
	0000005c    0
	0000005b    0
	0000005a    0
	00000059    0
	00000058    0
	00000057    0
	00000056    0
	00000055    0
	00000049    0
00000029 steamwebhelper.exe
	00000075    0
	00000074    0
	00000073    0
	00000072    0
	00000071    0
	00000070    0
	0000006f    0
	0000006e    0
	0000006d    0
	0000006c    0
	0000002a    0
00000079 steamwebhelper.exe
	0000009b    0
	0000001d    0
	0000007e    0
	0000006b    0
	00000069    0
	00000077    0
	00000089    0
	00000084    0
	00000085    0
	0000006a    0
	0000007b    0
	0000008e    0
000000ae (D) C:\Program Files\Steam\SteamApps\common\Alien Isolation\AI.exe
	000000b8    0
	000000b5   -1
	000000b4   -1
	000000b3   -1
	000000b2   -1
	000000b1    0
	000000b0   -1
	000000af    0 <==
System information:
    Wine build: wine-1.7.22
    Platform: i386
    Host system: Linux
Screenshot from 2014-10-08 22:35:52    Host version: 3.13.0-36-generic

```

A quick search suggests ([https://forums.eveonline.com/default.aspx?g=posts&m=2359669#post2359669](https://forums.eveonline.com/default.aspx?g=posts&m=2359669#post2359669)) that this may be a problem with DirectX 11. In the configuration for Steam in PlayOnLinux, I selected and installed d3dx11. On attempting to run the game again, I observe the same behaviour and error report. A next step could be to disable DirectX 11 and attempt running again, though I'm not sure how to do this.

What should I try next?

---

### Post by Mark_Pedersen-Cook on 2014-10-09
well to force steam to try and run the current program as DX9, you have to add the command under properaties -dxlevel 90 for dx9. ill have a look at other alternative commands

EDIT: as far as i can see there is 0 support for dx9 as you can see that the minimum req for running the game in terms of graphics card, is has to be a dx11 enabled card else it simply wont function

EDIT 2: after looking at your code, id recommend you try getting it over to 64bit DX11 instead of the 32bit, as it might be hanging up due to starvation of resources for the game to run

EDIT 3: also looking at the eve online forum, remember. eve online has DX9 available as graphics settings, and the post is over 2 years old, but disabling the dx11 function is done by 

winecfg -> Libraries -> [New override for library: ] d3d11 -> Add -> Edit... -> Disable

EDIT 4: also, your log dosent say witch direct x 11 version your using, try running winetricks in terminal, click ok at select the default wineprefix, click install windows dll or components, and try to install all direct x versions you can get. + all dotnet3.5-4.5 and Visual Basic+VisualC++ to try and get the most possible components of windows core programming for games to work

---

