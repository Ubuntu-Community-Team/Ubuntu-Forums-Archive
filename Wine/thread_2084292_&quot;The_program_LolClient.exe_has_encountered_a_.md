---
title: "&quot;The program LolClient.exe has encountered a serious problem and needs to close.&quot;"
date: 2012-11-15
forum: Wine
---

### Post by kupokupo on 2012-11-15
Hey guys, I had a lot of trouble with wine in general, but I fixed them. This is the only problem I can't get over.

I recently downloaded league of legends through wine using this guide mostly: [http://na.leagueoflegends.com/board/showthread.php?t=1946188](http://na.leagueoflegends.com/board/showthread.php?t=1946188)

I downloaded everything to my knowledge and followed it (though it was hard running the .exe file as it was using Pando Media Booster). I installed the patch and all and I started it up, got to login screen, and logged in. Then, I encountered this error:

> The program LolClient.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience.

This can be caused by a problem in the program or a deficiency in Wine. You may want to check out the Application Database for tips about running this application.

When I clicked on 'Show details', this is what I got:

> Unhandled exception: page fault on read access to 0xffffffff in 32-bit code (0x7d77781a).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7d77781a ESP:1394d958 EBP:7d7b0fb8 EFLAGS:00010212(  R- --  I   -A- - )
 EAX:1394d9b4 EBX:7d7cfff4 ECX:7d7b0fb8 EDX:1394d9a4
 ESI:1394d9b4 EDI:0000000a
Stack dump:
0x1394d958:  1394d9a4 1394d9b4 7d778bcd 7d7b0fb8
0x1394d968:  e5ced75f 7d778d29 7d7cfff4 1394d9a4
0x1394d978:  1394d9b4 7d7cfff4 7d779224 1394d9b4
0x1394d988:  1394d9a4 7d7b0fb8 2b706380 48681ad1
0x1394d998:  5a99f84c 48c7f4d0 513e9698 e66fd24e
0x1394d9a8:  00000060 1394dad0 7d7a61f8 ebeae9e8
Backtrace:
=>0 0x7d77781a in libgcrypt.so.11 (+0x2981a) (0x7d7b0fb8)
  1 0x7d778bcd in libgcrypt.so.11 (+0x2abcc) (0x7d7b0fb8)
  2 0x7d779224 in libgcrypt.so.11 (+0x2b223) (0x7d7b0fb8)
  3 0x7d778d7f in libgcrypt.so.11 (+0x2ad7e) (0x00000000)
  4 0x7d75d3f7 in libgcrypt.so.11 (+0xf3f6) (0x7d98b584)
  5 0x7d7537c4 gcry_cipher_setkey+0x43() in libgcrypt.so.11 (0x7d98b584)
  6 0x7d96659b in libgnutls.so.26 (+0x9e59a) (0x7d98b584)
  7 0x7d8e8859 in libgnutls.so.26 (+0x20858) (0x7d98b584)
  8 0x7d8f3c58 in libgnutls.so.26 (+0x2bc57) (0x7c1022b0)
  9 0x7d8f4211 in libgnutls.so.26 (+0x2c210) (0x00000010)
  10 0x7d8f4957 in libgnutls.so.26 (+0x2c956) (0x7c101914)
  11 0x7d8dd14d in libgnutls.so.26 (+0x1514c) (0x1394de9c)
  12 0x7d8e0550 in libgnutls.so.26 (+0x1854f) (0x1394de9c)
  13 0x7d8e1f6d gnutls_handshake+0x5c() in libgnutls.so.26 (0x1394de9c)
  14 0x7dbfc233 in secur32 (+0xc232) (0x1394de9c)
  15 0x7dbf9e44 in secur32 (+0x9e43) (0x1394df4c)
  16 0x7dbfabae in secur32 (+0xabad) (0x1394dfbc)
  17 0x7dc01a3d InitializeSecurityContextA+0x18c() in secur32 (0x1394e03c)
  18 0x702470b3 in wininet (+0x470b2) (0x1394e09c)
  19 0x70247339 in wininet (+0x47338) (0x1394e0bc)
  20 0x7020df87 in wininet (+0xdf86) (0x1394e0e0)
  21 0x70247b3f in wininet (+0x47b3e) (0x1394e120)
  22 0x70247c99 in wininet (+0x47c98) (0x1394e140)
  23 0x7020df87 in wininet (+0xdf86) (0x1394e1a0)
  24 0x70247fb0 in wininet (+0x47faf) (0x1394e1c0)
0x7d77781a: movq	0x0(%esi),%mm1
Modules:
Module	Address			Debug info	Name (150 modules)
PE	  400000-  428000	Deferred        lolclient
PE	10000000-10e50000	Deferred        adobe air
PE	70200000-70294000	Export          wininet
PE	702b0000-70328000	Deferred        urlmon
PE	70440000-704cf000	Deferred        mlang
PE	70bd0000-70c34000	Deferred        shlwapi
ELF	7b800000-7ba29000	Deferred        kernel32<elf>
  \-PE	7b810000-7ba29000	\               kernel32
ELF	7bc00000-7bcc3000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcc3000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c5cd000-7c600000	Deferred        wintrust<elf>
  \-PE	7c5d0000-7c600000	\               wintrust
ELF	7c721000-7c73c000	Deferred        rasapi32<elf>
  \-PE	7c730000-7c73c000	\               rasapi32
ELF	7c73c000-7c757000	Deferred        wsock32<elf>
  \-PE	7c740000-7c757000	\               wsock32
ELF	7c7a8000-7c7c6000	Deferred        libgcc_s.so.1
ELF	7cfda000-7d152000	Deferred        libvorbisenc.so.2
ELF	7d152000-7d1a2000	Deferred        libflac.so.8
ELF	7d1a2000-7d216000	Deferred        libsndfile.so.1
ELF	7d216000-7d220000	Deferred        libwrap.so.0
ELF	7d220000-7d284000	Deferred        libpulsecommon-2.1.so
ELF	7d284000-7d376000	Deferred        libasound.so.2
ELF	7d47e000-7d486000	Deferred        libogg.so.0
ELF	7d486000-7d4b2000	Deferred        libvorbis.so.0
ELF	7d4b2000-7d500000	Deferred        libpulse.so.0
ELF	7d60b000-7d612000	Deferred        libasyncns.so.0
ELF	7d612000-7d61c000	Deferred        libjson.so.0
ELF	7d61c000-7d648000	Deferred        winealsa<elf>
  \-PE	7d620000-7d648000	\               winealsa
ELF	7d648000-7d66b000	Deferred        mmdevapi<elf>
  \-PE	7d650000-7d66b000	\               mmdevapi
ELF	7d66b000-7d680000	Deferred        schannel<elf>
  \-PE	7d670000-7d680000	\               schannel
ELF	7d680000-7d694000	Deferred        psapi<elf>
  \-PE	7d690000-7d694000	\               psapi
ELF	7d694000-7d6f2000	Deferred        dbghelp<elf>
  \-PE	7d6a0000-7d6f2000	\               dbghelp
ELF	7d6f2000-7d6fb000	Deferred        librt.so.1
ELF	7d6fb000-7d700000	Deferred        libgpg-error.so.0
ELF	7d700000-7d704000	Deferred        libkeyutils.so.1
ELF	7d704000-7d74e000	Deferred        libdbus-1.so.3
ELF	7d74e000-7d7d2000	Dwarf           libgcrypt.so.11
ELF	7d7d2000-7d7fa000	Deferred        libk5crypto.so.3
ELF	7d7fa000-7d8c8000	Deferred        libkrb5.so.3
ELF	7d8c8000-7d98c000	Dwarf           libgnutls.so.26
ELF	7da24000-7da2b000	Deferred        libnss_dns.so.2
ELF	7da2b000-7da2f000	Deferred        libnss_mdns4_minimal.so.2
ELF	7da2f000-7da36000	Deferred        libasound_module_pcm_pulse.so
ELF	7da36000-7da4a000	Deferred        libp11-kit.so.0
ELF	7da4a000-7da5c000	Deferred        libtasn1.so.3
ELF	7da5c000-7da65000	Deferred        libkrb5support.so.0
ELF	7da65000-7da6a000	Deferred        libcom_err.so.2
ELF	7da6a000-7da7c000	Deferred        libavahi-client.so.3
ELF	7da7c000-7dab9000	Deferred        libgssapi_krb5.so.2
ELF	7dab9000-7db18000	Deferred        libcups.so.2
ELF	7db18000-7db2f000	Deferred        libresolv.so.2
ELF	7db2f000-7db4e000	Deferred        dnsapi<elf>
  \-PE	7db30000-7db4e000	\               dnsapi
ELF	7db4e000-7db92000	Deferred        dsound<elf>
  \-PE	7db50000-7db92000	\               dsound
ELF	7db92000-7dbb4000	Deferred        iphlpapi<elf>
  \-PE	7dba0000-7dbb4000	\               iphlpapi
ELF	7dbb4000-7dbdf000	Deferred        netapi32<elf>
  \-PE	7dbc0000-7dbdf000	\               netapi32
ELF	7dbdf000-7dc0b000	Dwarf           secur32<elf>
  \-PE	7dbf0000-7dc0b000	\               secur32
ELF	7dc0b000-7dc45000	Deferred        liblcms.so.1
ELF	7dc45000-7dc58000	Deferred        gnome-keyring-pkcs11.so
ELF	7dc58000-7dc77000	Deferred        mscms<elf>
  \-PE	7dc60000-7dc77000	\               mscms
ELF	7dc77000-7dcb1000	Deferred        winspool<elf>
  \-PE	7dc80000-7dcb1000	\               winspool
ELF	7dcb1000-7dd90000	Deferred        comdlg32<elf>
  \-PE	7dcc0000-7dd90000	\               comdlg32
ELF	7dd90000-7dda4000	Deferred        msimg32<elf>
  \-PE	7dda0000-7dda4000	\               msimg32
ELF	7dda4000-7ddc4000	Deferred        oleacc<elf>
  \-PE	7ddb0000-7ddc4000	\               oleacc
ELF	7ddc4000-7ddec000	Deferred        msacm32<elf>
  \-PE	7ddd0000-7ddec000	\               msacm32
ELF	7ddec000-7de99000	Deferred        winmm<elf>
  \-PE	7ddf0000-7de99000	\               winmm
ELF	7de99000-7decb000	Deferred        ws2_32<elf>
  \-PE	7dea0000-7decb000	\               ws2_32
ELF	7def9000-7df2d000	Deferred        uxtheme<elf>
  \-PE	7df00000-7df2d000	\               uxtheme
ELF	7df2d000-7df34000	Deferred        libxfixes.so.3
ELF	7df34000-7df3f000	Deferred        libxcursor.so.1
ELF	7df42000-7df50000	Deferred        libavahi-common.so.3
ELF	7dfaa000-7dfd2000	Deferred        libexpat.so.1
ELF	7dfd2000-7e00a000	Deferred        libfontconfig.so.1
ELF	7e00a000-7e01a000	Deferred        libxi.so.6
ELF	7e01a000-7e025000	Deferred        libxrandr.so.2
ELF	7e025000-7e047000	Deferred        imm32<elf>
  \-PE	7e030000-7e047000	\               imm32
ELF	7e047000-7e069000	Deferred        libxcb.so.1
ELF	7e069000-7e06f000	Deferred        libuuid.so.1
ELF	7e06f000-7e089000	Deferred        libice.so.6
ELF	7e089000-7e1bf000	Deferred        libx11.so.6
ELF	7e1bf000-7e1d1000	Deferred        libxext.so.6
ELF	7e1d1000-7e1da000	Deferred        libsm.so.6
ELF	7e1e3000-7e1ed000	Deferred        libxrender.so.1
ELF	7e1ed000-7e281000	Deferred        winex11<elf>
  \-PE	7e200000-7e281000	\               winex11
ELF	7e281000-7e31b000	Deferred        libfreetype.so.6
ELF	7e31b000-7e334000	Deferred        libz.so.1
ELF	7e339000-7e33d000	Deferred        libxcomposite.so.1
ELF	7e33d000-7e343000	Deferred        libxxf86vm.so.1
ELF	7e343000-7e347000	Deferred        libxinerama.so.1
ELF	7e347000-7e367000	Deferred        cabinet<elf>
  \-PE	7e350000-7e367000	\               cabinet
ELF	7e367000-7e459000	Deferred        oleaut32<elf>
  \-PE	7e380000-7e459000	\               oleaut32
ELF	7e459000-7e513000	Deferred        crypt32<elf>
  \-PE	7e460000-7e513000	\               crypt32
ELF	7e513000-7e589000	Deferred        rpcrt4<elf>
  \-PE	7e520000-7e589000	\               rpcrt4
ELF	7e589000-7e690000	Deferred        ole32<elf>
  \-PE	7e5a0000-7e690000	\               ole32
ELF	7e690000-7e774000	Deferred        msi<elf>
  \-PE	7e6a0000-7e774000	\               msi
ELF	7e774000-7e86d000	Deferred        comctl32<elf>
  \-PE	7e780000-7e86d000	\               comctl32
ELF	7e86d000-7ea80000	Deferred        shell32<elf>
  \-PE	7e880000-7ea80000	\               shell32
ELF	7ea80000-7eb0d000	Deferred        msvcrt<elf>
  \-PE	7ea90000-7eb0d000	\               msvcrt
ELF	7eb0d000-7eb26000	Deferred        version<elf>
  \-PE	7eb10000-7eb26000	\               version
ELF	7eb26000-7eb88000	Deferred        advapi32<elf>
  \-PE	7eb30000-7eb88000	\               advapi32
ELF	7eb88000-7ec45000	Deferred        gdi32<elf>
  \-PE	7eb90000-7ec45000	\               gdi32
ELF	7ec45000-7ed85000	Deferred        user32<elf>
  \-PE	7ec60000-7ed85000	\               user32
ELF	7ed85000-7ed92000	Deferred        libnss_files.so.2
ELF	7ed92000-7ed9e000	Deferred        libnss_nis.so.2
ELF	7ed9e000-7edb8000	Deferred        libnsl.so.1
ELF	7edb8000-7edc1000	Deferred        libnss_compat.so.2
ELF	7efc1000-7efed000	Deferred        libm.so.6
ELF	b748b000-b7490000	Deferred        libdl.so.2
ELF	b7490000-b763a000	Deferred        libc.so.6
ELF	b763b000-b7656000	Deferred        libpthread.so.0
ELF	b7656000-b765d000	Deferred        libxdmcp.so.6
ELF	b765d000-b7661000	Deferred        libxau.so.6
ELF	b7669000-b77ab000	Dwarf           libwine.so.1
ELF	b77ad000-b77cf000	Deferred        ld-linux.so.2
ELF	b77cf000-b77d0000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	00000038    0
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
00000048 PMB.exe
	00000063    0
	0000005e    0
	0000002d    0
	00000026    0
	0000002a    0
	0000003a    0
	00000041    0
	00000027    0
	0000003d    0
	0000003e    0
	0000003b    0
	0000003c    0
	00000059    0
	0000005a    0
	00000060    0
	00000058    0
	00000052    0
	00000057    0
00000061 rads_user_kernel.exe
	0000000d    0
	00000033    0
	00000031    0
	00000042    0
	00000018    0
	00000036    0
	0000002e    0
	00000066    0
	00000030    0
00000055 LoLLauncher.exe
	00000044    0
	00000053    0
	00000028    0
	0000001f    0
	00000037    0
	00000062    0
	00000047    0
	00000034    0
00000045 (D) C:\Program Files\Riot Games\League of Legends\RADS\projects\lol_air_client\releases\0.0.0.223\deploy\LolClient.exe
	00000056    0 <==
	00000049    2
	00000024    0
	00000065    0
	00000046    0
	00000054    0
	0000002b    0
	0000004e    0
	00000040    0
	00000032    0
	00000035    0
	0000005d    0
	0000005f    0
	0000004c    0
System information:
    Wine build: wine-1.4.1
    Platform: i386
    Host system: Linux
    Host version: 3.5.0-18-generic

This has been extremely frustrating for me, and this seems like it's the last step (hopefully) in getting it to run out of many. Any and all help will be GREATLY appreciated! Thanks!

---

