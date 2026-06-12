---
title: "Dragon Naturally Speaking -- msiexec unhandled page fault exception"
date: 2013-01-03
forum: Wine
---

### Post by Kirk Schnable on 2013-01-03
Good afternoon everyone.

I am trying to install Dragon Naturally Speaking 12 on a Ubuntu 12.04 laptop running WINE 1.5.20.

I have installed a number of Winetricks to try to avert this problem, but they have not helped.  dotnet40, msxml3, msxml4, ie7, windowscodecs, and gecko.  (Some of those were suggested by a different bug report I found on Google).

No matter what, the MSI will run, but part way through the installation, I will get an error.

This is my backtrace:
```
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x6840c928).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:6840c928 ESP:0033f860 EBP:0033f8a8 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:68475ff4 ECX:0033f750 EDX:00000000
 ESI:00852580 EDI:008525a4
Stack dump:
0x0033f860:  0013eb08 6846146c 00000016 683fd2a1
0x0033f870:  00000000 00000002 00011000 00000000
0x0033f880:  00000000 00000000 008527b8 007fac68
0x0033f890:  001506bc 00150680 0033f948 68475ff4
0x0033f8a0:  0066c158 00150680 0033f948 683fe5b8
0x0033f8b0:  00150680 00000001 00852580 68475ff4
Backtrace:
=>0 0x6840c928 in msi (+0x5c928) (0x0033f8a8)
  1 0x683fe5b8 in msi (+0x4e5b7) (0x0033f948)
  2 0x683c38e9 in msi (+0x138e8) (0x0033f998)
  3 0x683d5776 in msi (+0x25775) (0x0033f9e8)
  4 0x683d59ef in msi (+0x259ee) (0x0033fa38)
  5 0x6841f4c0 in msi (+0x6f4bf) (0x0033fa78)
  6 0x683c2862 in msi (+0x12861) (0x0033fac8)
  7 0x683c38e9 in msi (+0x138e8) (0x0033fb18)
  8 0x683d5776 in msi (+0x25775) (0x0033fb68)
  9 0x683d59ef in msi (+0x259ee) (0x0033fbb8)
  10 0x6841f4c0 in msi (+0x6f4bf) (0x0033fbf8)
  11 0x683d6056 in msi (+0x26055) (0x0033fc48)
  12 0x684108bd MsiInstallProductW+0x8c() in msi (0x0033fc98)
  13 0x6839caa4 WinMain+0x673() in msiexec (0x0033fd78)
  14 0x6839e3bf main+0xae() in msiexec (0x0033fe08)
  15 0x6839e2fc in msiexec (+0xe2fb) (0x0033fe58)
  16 0x7b85f8ec call_process_entry+0xb() in kernel32 (0x0033fe78)
  17 0x7b860b6f in kernel32 (+0x50b6e) (0x0033feb8)
  18 0x7bc77130 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  19 0x7bc79cad call_thread_func+0x7c() in ntdll (0x0033ffa8)
  20 0x7bc7710e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  21 0x7bc4c82e call_dll_entry_point+0x61d() in ntdll (0x0033ffe8)
0x6840c928: movzwl	0x0(%edx,%eax,1),%ecx
Modules:
Module	Address			Debug info	Name (126 modules)
PE	  460000-  46e000	Deferred        msi3ae7.tmp
PE	  9e0000-  a14000	Deferred        msi8158.tmp
PE	  a20000-  a43000	Deferred        msi855f.tmp
PE	  a50000-  a93000	Deferred        msi8568.tmp
PE	  ac0000-  ac7000	Deferred        msi897d.tmp
PE	  d90000-  f43000	Deferred        msi414e.tmp
PE	10000000-10036000	Deferred        msi3a4e.tmp
ELF	20014000-20052000	Deferred        libgssapi_krb5.so.2
ELF	20052000-20064000	Deferred        libavahi-client.so.3
ELF	20064000-20133000	Deferred        libkrb5.so.3
ELF	20133000-20138000	Deferred        libcom_err.so.2
ELF	20138000-2014a000	Deferred        libtasn1.so.3
ELF	2014a000-20193000	Deferred        libdbus-1.so.3
ELF	20214000-20228000	Deferred        shfolder<elf>
  \-PE	20220000-20228000	\               shfolder
ELF	20228000-20253000	Deferred        netapi32<elf>
  \-PE	20230000-20253000	\               netapi32
ELF	20253000-20277000	Deferred        iphlpapi<elf>
  \-PE	20260000-20277000	\               iphlpapi
ELF	20277000-202a6000	Deferred        secur32<elf>
  \-PE	20280000-202a6000	\               secur32
ELF	20b14000-20b26000	Deferred        libp11-kit.so.0
ELF	21d6d000-21dc0000	Deferred        libcups.so.2
ELF	25089000-250bc000	Deferred        ws2_32<elf>
  \-PE	25090000-250bc000	\               ws2_32
ELF	29ce3000-29cfd000	Deferred        sxs<elf>
  \-PE	29cf0000-29cfd000	\               sxs
ELF	2aa63000-2aa8b000	Deferred        libk5crypto.so.3
ELF	2c11e000-2c122000	Deferred        libkeyutils.so.1
ELF	362dd000-362eb000	Deferred        libavahi-common.so.3
ELF	3d6e9000-3d798000	Deferred        winmm<elf>
  \-PE	3d6f0000-3d798000	\               winmm
ELF	48efc000-48fc0000	Deferred        libgnutls.so.26
ELF	4c164000-4c1c3000	Deferred        dbghelp<elf>
  \-PE	4c170000-4c1c3000	\               dbghelp
ELF	4e730000-4e739000	Deferred        libkrb5support.so.0
ELF	53ee2000-53efa000	Deferred        libresolv.so.2
PE	5dca0000-5dce5000	Deferred        iertutil
ELF	5e608000-5e611000	Deferred        librt.so.1
PE	603b0000-60416000	Deferred        mscoreei
PE	604a0000-604ac000	Deferred        fusion
ELF	605a8000-605ad000	Deferred        libgpg-error.so.0
PE	61410000-61534000	Deferred        urlmon
ELF	63a94000-63ab7000	Deferred        imm32<elf>
  \-PE	63aa0000-63ab7000	\               imm32
ELF	63ca7000-63cab000	Deferred        libnss_mdns4_minimal.so.2
ELF	68000000-68022000	Deferred        ld-linux.so.2
ELF	68022000-68164000	Dwarf           libwine.so.1
ELF	68164000-6817f000	Deferred        libpthread.so.0
ELF	6817f000-68329000	Deferred        libc.so.6
ELF	68329000-6832e000	Deferred        libdl.so.2
ELF	6832e000-6835a000	Deferred        libm.so.6
ELF	6835a000-68363000	Deferred        libnss_compat.so.2
ELF	68363000-6837d000	Deferred        libnsl.so.1
ELF	6837d000-6838a000	Deferred        libnss_files.so.2
ELF	6838a000-683a8000	Dwarf           msiexec<elf>
  \-PE	68390000-683a8000	\               msiexec
ELF	683a8000-68491000	Dwarf           msi<elf>
  \-PE	683b0000-68491000	\               msi
ELF	68491000-68526000	Deferred        msvcrt<elf>
  \-PE	684a0000-68526000	\               msvcrt
ELF	68526000-6863b000	Deferred        ole32<elf>
  \-PE	68540000-6863b000	\               ole32
ELF	6863b000-686a0000	Deferred        advapi32<elf>
  \-PE	68650000-686a0000	\               advapi32
ELF	686a0000-687e7000	Deferred        user32<elf>
  \-PE	686b0000-687e7000	\               user32
ELF	687e7000-688f2000	Deferred        gdi32<elf>
  \-PE	687f0000-688f2000	\               gdi32
ELF	688f2000-6890c000	Deferred        version<elf>
  \-PE	68900000-6890c000	\               version
ELF	6890c000-68a26000	Deferred        oleaut32<elf>
  \-PE	68920000-68a26000	\               oleaut32
ELF	68a26000-68a3c000	Deferred        libz.so.1
ELF	68a3c000-68a62000	Deferred        mpr<elf>
  \-PE	68a40000-68a62000	\               mpr
ELF	68a62000-68c7b000	Deferred        shell32<elf>
  \-PE	68a70000-68c7b000	\               shell32
ELF	68c7b000-68c9b000	Deferred        cabinet<elf>
  \-PE	68c80000-68c9b000	\               cabinet
ELF	68c9b000-68d35000	Deferred        libfreetype.so.6
ELF	68d35000-68dbf000	Deferred        winex11<elf>
  \-PE	68d40000-68dbf000	\               winex11
ELF	68dbf000-68dc8000	Deferred        libsm.so.6
ELF	68dc8000-68efc000	Deferred        libx11.so.6
ELF	68efc000-68f02000	Deferred        libuuid.so.1
ELF	68f02000-68f23000	Deferred        libxcb.so.1
ELF	68f23000-68f27000	Deferred        libxau.so.6
ELF	68f27000-68f2e000	Deferred        libxdmcp.so.6
ELF	68f2e000-68f32000	Deferred        libxinerama.so.1
ELF	68f32000-68f3c000	Deferred        libxrender.so.1
ELF	68f3c000-68f45000	Deferred        libxrandr.so.2
ELF	68f45000-68f49000	Deferred        libxcomposite.so.1
ELF	68f49000-68f59000	Deferred        libxi.so.6
ELF	68f59000-68f5f000	Deferred        libxfixes.so.3
ELF	68f5f000-68f93000	Deferred        uxtheme<elf>
  \-PE	68f70000-68f93000	\               uxtheme
ELF	6936d000-6938b000	Deferred        libgcc_s.so.1
ELF	6b9ef000-6b9f6000	Deferred        libnss_dns.so.2
ELF	6bf38000-6bf55000	Deferred        fusion<elf>
ELF	711fa000-71272000	Deferred        rpcrt4<elf>
  \-PE	71210000-71272000	\               rpcrt4
ELF	71c59000-71c73000	Deferred        libice.so.6
ELF	73149000-731ce000	Deferred        libgcrypt.so.11
ELF	73e00000-73e0c000	Deferred        libnss_nis.so.2
ELF	74470000-74499000	Deferred        msacm32<elf>
  \-PE	74480000-74499000	\               msacm32
ELF	74501000-74575000	Deferred        wininet<elf>
  \-PE	74510000-74575000	\               wininet
ELF	76722000-76728000	Deferred        libxxf86vm.so.1
ELF	76736000-76741000	Deferred        libxcursor.so.1
ELF	77665000-77679000	Deferred        psapi<elf>
  \-PE	77670000-77679000	\               psapi
PE	77f60000-77fd6000	Deferred        shlwapi
ELF	78a36000-78a48000	Deferred        libxext.so.6
PE	79000000-7904a000	Deferred        mscoree
PE	79060000-7911e000	Deferred        msvcr100_clr0400
PE	79140000-797af000	Deferred        clr
ELF	799a8000-799bb000	Deferred        gnome-keyring-pkcs11.so
ELF	7b149000-7b245000	Deferred        comctl32<elf>
  \-PE	7b150000-7b245000	\               comctl32
ELF	7b800000-7ba33000	Dwarf           kernel32<elf>
  \-PE	7b810000-7ba33000	\               kernel32
ELF	7bc00000-7bcca000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcca000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	00000028    0
	00000027    0
	00000020    0
	00000010    0
	0000000f    0
00000014 explorer.exe
	00000015    0
0000001d winedevice.exe
	00000025    0
	00000022    0
	0000001f    0
	0000001e    0
00000023 plugplay.exe
	00000029    0
	00000026    0
	00000024    0
0000002a setup.exe
	0000002b    0
0000002c (D) C:\windows\system32\msiexec.exe
	0000005f    0
	0000005d    0
	0000005b    0
	00000059    0
	00000055    0
	00000053    0
	0000004f    0
	0000004d    0
	0000004b    0
	00000049    0
	00000011    0
	0000001b    0
	00000033    0
	00000009    0
	00000017    0
	00000013    0
	00000016    0
	00000046    0
	00000044    0
	00000042    0
	00000040    0
	0000003e    0
	0000003c    0
	0000003a    0
	00000038    0
	00000036    0
	00000034    0
	00000032    0
	00000031    0
	0000002d    0 <==
System information:
    Wine build: wine-1.5.20
    Platform: i386
    Host system: Linux
    Host version: 3.2.0-35-generic
```

Has anyone ever seen a problem like this before, or have any advice?

Thanks!

---

### Post by Kirk Schnable on 2013-01-06
I think this might be an issue with WINE 1.5.20.  I did get Dragon Naturally Speaking 12 working on Ubuntu, but I had to use WINE 1.4.  

I wrote a how-to, if anyone who stumbles across this thread later has any questions.

[http://binaryimpulse.com/2013/01/installing-dragon-naturally-speaking-12-on-ubuntu-12-04-using-playonlinux/](http://binaryimpulse.com/2013/01/installing-dragon-naturally-speaking-12-on-ubuntu-12-04-using-playonlinux/)

Kirk

---

### Post by grey1beard on 2013-01-15
Kirk,
Thanks for the link to your how to, which I shall be trying shortly.
My own case is one where I'm firstly trying to run my old DNS 5 in ubuntu 12.04.
I ran into serious frozen mouse problems during my attemps to install it in Wine 1.5.21 configured to win xp, and I'm still not clear on how I can get rid of the 'fallout', and clean up the mess, but that's for another thread.

Firstly do you see any obvious reason why your method should not also work for older verions of DNS ?

Secondly, you didn't mention any configuration of Wine inside the Playonlinux. Is this at all necessary, like choosing a version of windows that matches the age of the DNS version ?

Lastly, am I likely to need to download several versions of Wine for a 'trial & error' approach ?

Regards
John

---

### Post by grey1beard on 2013-01-15
Kirk,
I've just visited the pol web page and the pol wiki, and read that the necessary configuration is carried out automatically from their database, so my second question is redundant, possibly my third one, too !!
John

---

### Post by Kirk Schnable on 2013-04-16
> **grey1beard said:**
> Firstly do you see any obvious reason why your method should not also work for older verions of DNS ?
Sorry, I am not a Dragon Naturally Speaking expert by any means, this was just something I had to get working, and I found the hoops I had to jump through to be somewhat frustrating, so I wrote a how-to to spare others the future torment.

If you were able to get older versions working using my how-to, then I encourage you to report your results here!

Kirk

---

