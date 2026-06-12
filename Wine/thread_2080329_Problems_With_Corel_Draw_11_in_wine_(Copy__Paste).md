---
title: "Problems With Corel Draw 11 in wine (Copy / Paste)"
date: 2012-11-03
forum: Wine
---

### Post by grig4all on 2012-11-03
I have instaled with succes Corel Draw 11 in Wiine - Ubuntu 12.04 and it works almos fine with a little problem i cant copy objects in it i get an error: and it is closing.
Same one can help me, pls?
> Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000000 ESP:0033e2b0 EBP:31e4dff4 EFLAGS:00210206(  R- --  I   - -P- )
 EAX:00000000 EBX:00000000 ECX:00000000 EDX:00000000
 ESI:0033e2c4 EDI:058e8e48
Stack dump:
0x0033e2b0:  09d3a590 31e325dd 31e4dff4 31e4dff4
0x0033e2c0:  00163d28 0033e464 31e33d73 00000002
0x0033e2d0:  00000000 00000001 09d7400c 09d76250
0x0033e2e0:  0033e320 201335bb 09d3a590 00000400
0x0033e2f0:  00000000 31ebdb10 22dca290 0033e314
0x0033e300:  00500041 00000053 00000000 00000000
Backtrace:
=>0 0x00000000 (0x31e4dff4)
  1 0x00000000 (0x0003bf18)
0x00000000: -- no code accessible --
Modules:
Module	Address			Debug info	Name (231 modules)
PE	  340000-  364000	Deferred        fn3api
PE	  400000-  411000	Deferred        coreldrw
PE	  780000-  7ec000	Deferred        iuiintl
PE	  900000-  948000	Deferred        kodakcms
PE	 4470000- 4501000	Deferred        dao350
PE	 4f10000- 4f21000	Deferred        threeptcurvetool110
PE	10000000-10020000	Deferred        cdrcrv110
ELF	20000000-200bd000	Deferred        gdi32<elf>
  \-PE	20010000-200bd000	\               gdi32
ELF	200bd000-201c5000	Deferred        ole32<elf>
  \-PE	200d0000-201c5000	\               ole32
ELF	201c5000-2023a000	Deferred        rpcrt4<elf>
  \-PE	201d0000-2023a000	\               rpcrt4
ELF	2023a000-20262000	Deferred        msacm32<elf>
  \-PE	20240000-20262000	\               msacm32
ELF	20262000-20284000	Deferred        imm32<elf>
  \-PE	20270000-20284000	\               imm32
ELF	20284000-20376000	Deferred        oleaut32<elf>
  \-PE	202a0000-20376000	\               oleaut32
ELF	20376000-20455000	Deferred        comdlg32<elf>
  \-PE	20380000-20455000	\               comdlg32
ELF	20455000-20477000	Deferred        msvcirt<elf>
  \-PE	20460000-20477000	\               msvcirt
ELF	20477000-20480000	Deferred        libsm.so.6
ELF	20480000-20486000	Deferred        libuuid.so.1
ELF	20486000-2048a000	Deferred        libxau.so.6
ELF	2048a000-2048e000	Deferred        libxinerama.so.1
ELF	2048e000-204c2000	Deferred        libfontconfig.so.1
ELF	204c2000-204c8000	Deferred        libxfixes.so.3
ELF	204c8000-2051b000	Deferred        libcups.so.2
ELF	2051b000-2052d000	Deferred        libavahi-client.so.3
ELF	2052d000-205fc000	Deferred        libkrb5.so.3
ELF	205fc000-20681000	Deferred        libgcrypt.so.11
ELF	20681000-20685000	Deferred        libkeyutils.so.1
ELF	20685000-2069d000	Deferred        libresolv.so.2
ELF	2069d000-206d5000	Deferred        usp10<elf>
  \-PE	206a0000-206d5000	\               usp10
ELF	206d5000-206fe000	Deferred        msvcrt40<elf>
  \-PE	206e0000-206fe000	\               msvcrt40
ELF	206fe000-2071f000	Deferred        localspl<elf>
  \-PE	20700000-2071f000	\               localspl
ELF	2071f000-2073d000	Deferred        libgcc_s.so.1
PE	209c0000-2138c000	Deferred        coreldrw110
PE	214e0000-21d22000	Deferred        drawintl
PE	22ac0000-22ee5000	Deferred        cdrcore110
ELF	234fa000-23534000	Deferred        winspool<elf>
  \-PE	23500000-23534000	\               winspool
PE	23830000-23ac6000	Deferred        cdrprnintl110
PE	23af0000-23ced000	Deferred        cdrprn110
PE	23d50000-23f23000	Deferred        cdrtra110
PE	24150000-242af000	Deferred        cdrrip110
PE	244d0000-24619000	Deferred        drwbasetoolcore110
PE	24680000-247c3000	Deferred        cdrtxt110
PE	24ab0000-24bb4000	Deferred        crlfrmwk110
PE	24d30000-24e04000	Deferred        crlfom110
PE	24f60000-25025000	Deferred        crlcui110
PE	25120000-251c7000	Deferred        drwextrudetool110
PE	25200000-252a5000	Deferred        crlctl110
PE	252e0000-25388000	Deferred        crlutl110
PE	25510000-25595000	Deferred        crlfomui110
PE	25720000-257a1000	Deferred        crlcuiintl110
PE	257d0000-25851000	Deferred        cdrtxtui110
PE	25870000-258f0000	Deferred        crliui110
PE	25920000-2599e000	Deferred        crlfx110
PE	25cb0000-25d1c000	Deferred        crlcmnres110
PE	25dd0000-25e32000	Deferred        drwfilltool110
PE	25ec0000-25f20000	Deferred        crlclr110
PE	25fb0000-26005000	Deferred        drwblendtool110
PE	26090000-260e2000	Deferred        cdrflt110
PE	26160000-261af000	Deferred        crlrcvy110
PE	26380000-263c9000	Deferred        cdrfnt110
PE	26500000-26544000	Deferred        drwcontourtool110
PE	265c0000-26602000	Deferred        drwartisticmediatool110
PE	266d0000-2670d000	Deferred        drwenvpersptool110
PE	26770000-267a9000	Deferred        drwtransparencytool110
PE	267c0000-267f8000	Deferred        crllshape110
PE	26900000-26933000	Deferred        drwdropshadowtool110
PE	26950000-26984000	Deferred        drwzoompantool110
PE	26a40000-26a72000	Deferred        drwdimensiontool110
PE	26b00000-26b30000	Deferred        crlfxcontrols110
PE	26bc0000-26bec000	Deferred        cdrsty110
PE	26c00000-26c2c000	Deferred        drwdistortiontool110
PE	26c40000-26c6a000	Deferred        drwerasertool110
PE	26cc0000-26ce8000	Deferred        drwbezierfreehandtoolcore110
PE	26d00000-26d28000	Deferred        cdrpdfui110
PE	26d80000-26da7000	Deferred        drwpicktool110
PE	26e00000-26e27000	Deferred        crlfrmwkintl110
PE	26e40000-26e67000	Deferred        crlfxintl
PE	26e80000-26ea6000	Deferred        drwliveshapetool110
ELF	26ef3000-26efc000	Deferred        libxrandr.so.2
PE	26fa0000-26fc4000	Deferred        drwpolygontool110
PE	27000000-27022000	Deferred        cdrcpr110
PE	27030000-27052000	Deferred        cdrpdfintl110
PE	27060000-27081000	Deferred        drwrectangletool110
PE	270c0000-270e1000	Deferred        crlweb110
PE	27150000-27171000	Deferred        smudgetool110
PE	271a0000-271c0000	Deferred        symboltool110
PE	27230000-2724f000	Deferred        drwroughentool110
PE	27290000-272af000	Deferred        drwmeshfilltool110
PE	272c0000-272de000	Deferred        drwellipsetool110
PE	272f0000-2730e000	Deferred        crlutlintl110
PE	27320000-2733e000	Deferred        drwfilltoolcore110
PE	27380000-2739d000	Deferred        drwspiraltool110
PE	273b0000-273cc000	Deferred        drweyedroppertool110
PE	27410000-2742c000	Deferred        drwoutlinetool110
PE	27440000-2745b000	Deferred        drwconnectortool110
PE	27470000-2748a000	Deferred        drwnodeedittool110
PE	274a0000-274ba000	Deferred        drwartisticmediatoolcore110
PE	274d0000-274ea000	Deferred        threeptellipsetool110
PE	27500000-2751a000	Deferred        crlinet
PE	27530000-27547000	Deferred        drwblendtoolcore110
PE	27550000-27567000	Deferred        drwnodeedittoolcore110
PE	27590000-275a7000	Deferred        drwfhtransformtool110
PE	275d0000-275e6000	Deferred        crlrcvyintl110
PE	27610000-27624000	Deferred        drwgraphpapertool110
PE	27630000-27643000	Deferred        drwknifetool110
PE	27670000-27683000	Deferred        drwbrushtoolcore110
PE	27690000-276a3000	Deferred        cdrtxtintl110
PE	276b0000-276c2000	Deferred        threeptrecttool110
PE	276f0000-27701000	Deferred        drwfreehandtool110
PE	27730000-27742000	Deferred        pentool110
PE	27770000-27782000	Deferred        cdrpdfcmp110
PE	277d0000-277e1000	Deferred        polylinetool110
PE	27860000-2786e000	Deferred        crli18n110
PE	278c0000-278cd000	Deferred        cdrautosense110
PE	278e0000-278ec000	Deferred        drwbeziertool110
PE	27900000-2790d000	Deferred        drwpicktoolcore110
PE	27940000-2794c000	Deferred        drwconnectortoolcore110
PE	27950000-2795c000	Deferred        crlppd110
PE	27970000-2797b000	Deferred        drwtexttool110
PE	27980000-2798b000	Deferred        drwtransparencytoolcore110
PE	279b0000-279ba000	Deferred        drwpolygontoolcore110
PE	279c0000-279ca000	Deferred        drwoutlinetoolcore110
PE	279d0000-279da000	Deferred        cdrfntintl110
PE	279f0000-279fa000	Deferred        crlctlintl110
PE	27a00000-27a0a000	Deferred        drwdimensiontoolcore110
PE	27a30000-27a39000	Deferred        drwmeshfilltoolcore110
PE	27a60000-27a69000	Deferred        crltwain110
PE	27a70000-27a78000	Deferred        drwspiraltoolcore110
PE	27aa0000-27aa8000	Deferred        drweyedroppertoolcore110
PE	27ab0000-27ab8000	Deferred        drwzoompantoolcore110
PE	27ac0000-27ac8000	Deferred        crlclrintl110
PE	27ad0000-27ad7000	Deferred        drwknifetoolcore110
PE	27ae0000-27ae7000	Deferred        drwgraphpapertoolcore110
PE	27af0000-27af7000	Deferred        drwrectangletoolcore110
PE	27b00000-27b07000	Deferred        polylinetoolcore110
PE	27b10000-27b17000	Deferred        drwliveshapetoolcore110
PE	27b20000-27b27000	Deferred        drwerasertoolcore110
PE	27b30000-27b37000	Deferred        drwellipsetoolcore110
PE	27b40000-27b47000	Deferred        threepttoolcore110
PE	27b80000-27b86000	Deferred        componentintl
PE	27bc0000-27bc4000	Deferred        crlfxcontrolsintl
ELF	2f0f0000-2f106000	Deferred        libz.so.1
ELF	2f297000-2f29e000	Deferred        libxdmcp.so.6
ELF	31e12000-31ebf000	Deferred        winmm<elf>
  \-PE	31e20000-31ebf000	\               winmm
ELF	33362000-333cc000	Deferred        shlwapi<elf>
  \-PE	33370000-333cc000	\               shlwapi
ELF	33504000-3351d000	Deferred        version<elf>
  \-PE	33510000-3351d000	\               version
ELF	33572000-33598000	Deferred        mpr<elf>
  \-PE	33580000-33598000	\               mpr
ELF	33776000-337ae000	Deferred        oledlg<elf>
  \-PE	33780000-337ae000	\               oledlg
ELF	33ff6000-34136000	Deferred        user32<elf>
  \-PE	34010000-34136000	\               user32
PE	36a00000-36ac7000	Deferred        wt9_1li
ELF	3745e000-3747a000	Deferred        msimtf<elf>
  \-PE	37460000-3747a000	\               msimtf
ELF	37484000-374a6000	Deferred        iphlpapi<elf>
  \-PE	37490000-374a6000	\               iphlpapi
ELF	399ec000-39bfd000	Deferred        shell32<elf>
  \-PE	39a00000-39bfd000	\               shell32
ELF	3dbe7000-3dbfa000	Deferred        gnome-keyring-pkcs11.so
ELF	3ed50000-3ed6b000	Deferred        spoolss<elf>
  \-PE	3ed60000-3ed6b000	\               spoolss
ELF	3fb1e000-3fb24000	Deferred        libxxf86vm.so.1
ELF	409c8000-40a28000	Deferred        advapi32<elf>
  \-PE	409d0000-40a28000	\               advapi32
ELF	40df8000-40e06000	Deferred        libavahi-common.so.3
ELF	41472000-41477000	Deferred        libgpg-error.so.0
ELF	441ab000-441df000	Deferred        uxtheme<elf>
  \-PE	441b0000-441df000	\               uxtheme
ELF	44e53000-44e58000	Deferred        libcom_err.so.2
ELF	4564b000-456d8000	Deferred        msvcrt<elf>
  \-PE	45660000-456d8000	\               msvcrt
ELF	4c3d6000-4c3da000	Deferred        libxcomposite.so.1
ELF	4eb5b000-4ebee000	Deferred        winex11<elf>
  \-PE	4eb70000-4ebee000	\               winex11
ELF	53886000-5389a000	Deferred        olepro32<elf>
  \-PE	53890000-5389a000	\               olepro32
ELF	5620b000-562cf000	Deferred        libgnutls.so.26
ELF	5731c000-57325000	Deferred        libkrb5support.so.0
ELF	5b65e000-5b670000	Deferred        libp11-kit.so.0
ELF	5c944000-5c96e000	Deferred        libexpat.so.1
PE	5f400000-5f4f2000	Deferred        mfc42
ELF	65f9e000-65fb9000	Deferred        wsock32<elf>
  \-PE	65fa0000-65fb9000	\               wsock32
ELF	66958000-66962000	Deferred        libxrender.so.1
ELF	67f7f000-67fb1000	Deferred        ws2_32<elf>
  \-PE	67f90000-67fb1000	\               ws2_32
ELF	68000000-68022000	Deferred        ld-linux.so.2
ELF	68022000-68164000	Dwarf           libwine.so.1
ELF	68164000-6817f000	Deferred        libpthread.so.0
ELF	6817f000-68329000	Deferred        libc.so.6
ELF	68329000-6832e000	Deferred        libdl.so.2
ELF	6832e000-6835a000	Deferred        libm.so.6
ELF	6835a000-68374000	Deferred        libnsl.so.1
ELF	68374000-68380000	Deferred        libnss_nis.so.2
ELF	68380000-6838d000	Deferred        libnss_files.so.2
ELF	695cf000-69669000	Deferred        libfreetype.so.6
ELF	69f17000-69f27000	Deferred        libxi.so.6
ELF	6a3d0000-6a3ea000	Deferred        libice.so.6
ELF	6bd7d000-6bd9e000	Deferred        libxcb.so.1
ELF	6bf44000-6bf4d000	Deferred        librt.so.1
ELF	70093000-7009c000	Deferred        libnss_compat.so.2
ELF	71e9a000-71eac000	Deferred        libxext.so.6
ELF	763e0000-7641e000	Deferred        libgssapi_krb5.so.2
ELF	772bd000-772c8000	Deferred        libxcursor.so.1
PE	780c0000-78121000	Deferred        msvcp60
ELF	78d52000-78d64000	Deferred        libtasn1.so.3
ELF	78e96000-78fca000	Deferred        libx11.so.6
ELF	79af5000-79b1d000	Deferred        libk5crypto.so.3
ELF	7b567000-7b5b0000	Deferred        libdbus-1.so.3
ELF	7b800000-7ba15000	Deferred        kernel32<elf>
  \-PE	7b810000-7ba15000	\               kernel32
ELF	7bc00000-7bcc3000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcc3000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7bf61000-7c059000	Deferred        comctl32<elf>
  \-PE	7bf70000-7c059000	\               comctl32
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	00000065    0
	000000cc    0
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
00000023 Dreamweaver.exe
	00000027    0
	00000026    0
	00000025    0
	00000024    0
000000c9 svchost.exe
	000000da    0
	000000d2    0
	000000d0    0
	000000cf    0
	000000cb    0
	000000ca    0
000000de rpcss.exe
	0000002d    0
	000000b9    0
	000000ba    0
	000000b5    0
	000000b4    0
	000000df    0
000000be (D) C:\Program Files\Corel\Corel Graphics 11\Programs\CorelDrw.exe
	00000036    0
	00000035    0
	00000034    0
	00000033    0
	00000032    0
	00000031    0
	000000c0    0
	000000dd    0
	000000c8    0
	000000ce    0
	000000c7    0
	0000004e    0
	000000bf    0
	000000d5    0
	000000d6    0
	000000d8    0
	000000d7    0
	00000064    0
	00000063    0
	00000062    0
	00000061    0
	00000060    0
	0000005f    0
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
	00000054    0
	00000053    0
	00000052    0
	00000051    0
	00000050    0
	000000cd    0
	000000d9    0
	000000d3    0
	000000d4    0
	000000d1    0
	000000c5    0
	0000001f    0
	000000b6    0
	00000030    0
	0000002e    0
	000000b7    0
	000000b2    0
	000000b1    0
	000000b0    0
	000000af    0
	000000ae    0
	000000ad    0
	000000ac    0
	000000ab    0
	000000aa    0
	000000a9    0
	000000a8    0
	000000a7    0
	000000a6    0
	000000a5    0
	000000a4    0
	000000a3    0
	000000a2    0
	000000a1    0
	000000a0    0
	0000009f    0
	0000009e    0
	0000009d    0
	0000009c    0
	0000009b    0
	0000009a    0
	00000099    0
	00000098    0
	00000097    0
	00000096    0
	00000095    0
	00000094    0
	00000093    0
	00000092    0
	00000091    0
	00000090    0
	0000008f    0
	0000008e    0
	0000008d    0
	0000008c    0
	0000008b    0
	0000008a    0
	00000089    0
	00000088    0
	00000087    0
	00000086    0
	00000085    0
	00000084    0
	00000083    0
	00000082    0
	00000081    0
	00000080    0
	0000007f    0
	0000007e    0
	0000007d    0
	0000007c    0
	0000007b    0
	0000007a    0
	00000079    0
	00000078    0
	00000077    0
	00000076    0
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
	0000006b    0
	0000002a    0
	000000b8    0
	000000c2    0
	00000066    0
	00000067    0
	0000004f    0
	000000c3    0
	000000db    0
	0000004c    0
	0000004b    0
	0000004a    0
	00000049    0
	00000048    0
	0000002f    0
	0000002b    0
	00000028    0
	00000017    0
	00000029    0
	00000069    0
	000000bc    0
	000000b3    0 <==
System information:
    Wine build: wine-1.4
    Platform: i386
    Host system: Linux
    Host version: 3.2.0-32-generic-pae


---

### Post by cipx2 on 2013-02-14
Same here using wine 1.5 on ubuntu 12.10.
Corel Draw 11 crashes as soon as you try to copy an object to clipboard.

Any clues please?

---

