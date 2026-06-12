---
title: "Cinema 4D error."
date: 2013-11-07
forum: Wine
---

### Post by vonvic on 2013-11-07
Whenever I launch Cinema 4D, it gives  me this error

```

Unhandled exception: 0xc06d007e in 32-bit code (0x7b83a9fe).Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b83a9fe ESP:0033f854 EBP:0033f8c8 EFLAGS:00000287(   - --  I S - -P-C)
 EAX:7b8268b5 EBX:7b8b5000 ECX:0033f900 EDX:0033f878
 ESI:c06d007e EDI:00000011
Stack dump:
0x0033f854:  0033f8f0 00000004 0033f880 c06d007e
0x0033f864:  00000000 00000000 7b83a9fe 00000001
0x0033f874:  0033f900 0033f8a8 7b858161 7ffd8c00
0x0033f884:  00000000 00000000 02045000 02045014
0x0033f894:  7b85812c 0033f8c0 7b8b5000 0119ce2c
0x0033f8a4:  00000011 0033f8d8 7b8581cd 0000000b
000c: sel=0067 base=00000000 limit=00000000 32-bit --x
Backtrace:
=>0 0x7b83a9fe in kernel32 (+0x2a9fe) (0x0033f8c8)
  1 0x0102f18f in cinema 4d (+0xc2f18e) (0x0033f948)
  2 0x0105fb1f in cinema 4d (+0xc5fb1e) (0x0033fd78)
  3 0x010ed452 in cinema 4d (+0xced451) (0x0033fe60)
  4 0x7b85e51c call_process_entry+0xb() in kernel32 (0x0033fe78)
  5 0x7b85f5a3 in kernel32 (+0x4f5a2) (0x0033feb8)
  6 0x7bc78910 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  7 0x7bc7b89d call_thread_func+0x7c() in ntdll (0x0033ffa8)
  8 0x7bc788ee RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  9 0x7bc4e4fe call_dll_entry_point+0x7ed() in ntdll (0x0033ffe8)
  10 0xf75c44ed wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  11 0xf75c45ab wine_switch_to_stack+0x2a() in libwine.so.1 (0xff976f08)
  12 0x7bc53dc2 LdrInitializeThunk+0x3a1() in ntdll (0xff976f68)
  13 0x7b865b3d __wine_kernel_init+0xa0c() in kernel32 (0xff978088)
  14 0x7bc54383 __wine_process_init+0x192() in ntdll (0xff978118)
  15 0xf75c1c50 wine_init+0x30f() in libwine.so.1 (0xff978178)
  16 0x7bf00fdc main+0xfb() in <wine-loader> (0xff9785c8)
  17 0xf73e7905 __libc_start_main+0xf4() in libc.so.6 (0x00000000)
0x7b83a9fe: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (108 modules)
PE	  400000- 1e25000	Export          cinema 4d
ELF	7b800000-7ba5b000	Dwarf           kernel32<elf>
  \-PE	7b810000-7ba5b000	\               kernel32
ELF	7bc00000-7bcda000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcda000	\               ntdll
ELF	7bf00000-7bf04000	Dwarf           <wine-loader>
ELF	7d5ca000-7d5d3000	Deferred        librt.so.1
ELF	7d5d3000-7d5d8000	Deferred        libgpg-error.so.0
ELF	7d5d8000-7d5ef000	Deferred        libresolv.so.2
ELF	7d5ef000-7d5f3000	Deferred        libkeyutils.so.1
ELF	7d5f3000-7d63e000	Deferred        libdbus-1.so.3
ELF	7d63e000-7d65d000	Deferred        libp11-kit.so.0
ELF	7d65d000-7d66f000	Deferred        libtasn1.so.3
ELF	7d66f000-7d6f3000	Deferred        libgcrypt.so.11
ELF	7d6f3000-7d6fc000	Deferred        libkrb5support.so.0
ELF	7d6fc000-7d724000	Deferred        libk5crypto.so.3
ELF	7d724000-7d7f3000	Deferred        libkrb5.so.3
ELF	7d7f3000-7d805000	Deferred        libavahi-client.so.3
ELF	7d805000-7d8cb000	Deferred        libgnutls.so.26
ELF	7d8cb000-7d908000	Deferred        libgssapi_krb5.so.2
ELF	7d908000-7d974000	Deferred        libcups.so.2
ELF	7d98c000-7d9c2000	Deferred        uxtheme<elf>
  \-PE	7d990000-7d9c2000	\               uxtheme
ELF	7d9c2000-7d9c8000	Deferred        libxfixes.so.3
ELF	7d9c8000-7d9d3000	Deferred        libxcursor.so.1
ELF	7d9d3000-7d9e4000	Deferred        libxi.so.6
ELF	7d9e4000-7d9e8000	Deferred        libxcomposite.so.1
ELF	7d9e8000-7d9f3000	Deferred        libxrandr.so.2
ELF	7d9f3000-7d9fe000	Deferred        libxrender.so.1
ELF	7d9fe000-7da04000	Deferred        libxxf86vm.so.1
ELF	7da04000-7da08000	Deferred        libxinerama.so.1
ELF	7da08000-7da0f000	Deferred        libxdmcp.so.6
ELF	7da0f000-7da13000	Deferred        libxau.so.6
ELF	7da13000-7da34000	Deferred        libxcb.so.1
ELF	7da34000-7da3a000	Deferred        libuuid.so.1
ELF	7da3a000-7da54000	Deferred        libice.so.6
ELF	7da54000-7db89000	Deferred        libx11.so.6
ELF	7db89000-7db9c000	Deferred        libxext.so.6
ELF	7db9c000-7dba5000	Deferred        libsm.so.6
ELF	7dba8000-7dbad000	Deferred        libcom_err.so.2
ELF	7dbad000-7dbbb000	Deferred        libavahi-common.so.3
ELF	7dbbd000-7dc4e000	Deferred        winex11<elf>
  \-PE	7dbd0000-7dc4e000	\               winex11
ELF	7dcd2000-7dcfb000	Deferred        libexpat.so.1
ELF	7dcfb000-7dd35000	Deferred        libfontconfig.so.1
ELF	7dd35000-7ddd4000	Deferred        libfreetype.so.6
ELF	7ddd4000-7de5e000	Deferred        gdiplus<elf>
  \-PE	7dde0000-7de5e000	\               gdiplus
ELF	7de5e000-7dea0000	Deferred        usp10<elf>
  \-PE	7de60000-7dea0000	\               usp10
ELF	7dea0000-7deba000	Deferred        libz.so.1
ELF	7ded2000-7df3a000	Deferred        dbghelp<elf>
  \-PE	7dee0000-7df3a000	\               dbghelp
ELF	7df3a000-7df54000	Deferred        imagehlp<elf>
  \-PE	7df40000-7df54000	\               imagehlp
ELF	7df54000-7df7a000	Deferred        iphlpapi<elf>
  \-PE	7df60000-7df7a000	\               iphlpapi
ELF	7df7a000-7e0af000	Deferred        oleaut32<elf>
  \-PE	7df90000-7e0af000	\               oleaut32
ELF	7e0af000-7e0ef000	Deferred        winspool<elf>
  \-PE	7e0c0000-7e0ef000	\               winspool
ELF	7e0ef000-7e169000	Deferred        shlwapi<elf>
  \-PE	7e100000-7e169000	\               shlwapi
ELF	7e169000-7e39c000	Deferred        shell32<elf>
  \-PE	7e180000-7e39c000	\               shell32
ELF	7e39c000-7e487000	Deferred        comdlg32<elf>
  \-PE	7e3a0000-7e487000	\               comdlg32
ELF	7e487000-7e4f8000	Deferred        setupapi<elf>
  \-PE	7e490000-7e4f8000	\               setupapi
ELF	7e4f8000-7e52e000	Deferred        ws2_32<elf>
  \-PE	7e500000-7e52e000	\               ws2_32
ELF	7e52e000-7e62b000	Deferred        opengl32<elf>
  \-PE	7e550000-7e62b000	\               opengl32
ELF	7e62b000-7e672000	Deferred        avifil32<elf>
  \-PE	7e630000-7e672000	\               avifil32
ELF	7e672000-7e779000	Deferred        comctl32<elf>
  \-PE	7e680000-7e779000	\               comctl32
ELF	7e779000-7e7a5000	Deferred        msvfw32<elf>
  \-PE	7e780000-7e7a5000	\               msvfw32
ELF	7e7a5000-7e7d0000	Deferred        msacm32<elf>
  \-PE	7e7b0000-7e7d0000	\               msacm32
ELF	7e7d0000-7e852000	Deferred        rpcrt4<elf>
  \-PE	7e7e0000-7e852000	\               rpcrt4
ELF	7e852000-7e98f000	Deferred        ole32<elf>
  \-PE	7e870000-7e98f000	\               ole32
ELF	7e98f000-7e9a9000	Deferred        version<elf>
  \-PE	7e990000-7e9a9000	\               version
ELF	7e9a9000-7ea1b000	Deferred        advapi32<elf>
  \-PE	7e9c0000-7ea1b000	\               advapi32
ELF	7ea1b000-7eb39000	Deferred        gdi32<elf>
  \-PE	7ea30000-7eb39000	\               gdi32
ELF	7eb39000-7ec93000	Deferred        user32<elf>
  \-PE	7eb50000-7ec93000	\               user32
ELF	7ec93000-7ed4d000	Deferred        winmm<elf>
  \-PE	7eca0000-7ed4d000	\               winmm
ELF	7ed4d000-7ed66000	Deferred        libnsl.so.1
ELF	7ed6a000-7ed7e000	Deferred        psapi<elf>
  \-PE	7ed70000-7ed7e000	\               psapi
ELF	7efbd000-7f000000	Deferred        libm.so.6
ELF	f73c0000-f73cd000	Deferred        libnss_files.so.2
ELF	f73ce000-f7582000	Dwarf           libc.so.6
ELF	f7582000-f7587000	Deferred        libdl.so.2
ELF	f7588000-f75a3000	Deferred        libpthread.so.0
ELF	f75a5000-f75b1000	Deferred        libnss_nis.so.2
ELF	f75b1000-f75ba000	Deferred        libnss_compat.so.2
ELF	f75bb000-f7770000	Dwarf           libwine.so.1
ELF	f7772000-f7794000	Deferred        ld-linux.so.2
ELF	f7794000-f7795000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	00000033    0
	00000032    0
	0000002b    0
	00000025    0
	00000017    0
	00000010    0
	0000000f    0
00000012 AppleMobileDeviceService.exe
	00000024    0
	00000022    0
	00000021    0
	0000001e    0
	0000001a    0
	00000016    0
	00000013    0
00000014 explorer.exe
	00000023    0
	00000015    0
0000001f mDNSResponder.exe
	00000028    0
	00000027    0
	00000020    0
00000029 winedevice.exe
	00000031    0
	0000002e    0
	0000002d    0
	0000002a    0
0000002f plugplay.exe
	00000035    0
	00000034    0
	00000030    0
00000036 (D) L:\home\vonvic\Desktop\CINEMA 4D.exe
	00000037    0 <==
0000003a CINEMA 4D 64 Bit.exe
	0000003b    0
0000003c winedbg.exe
	0000003d    0
System information:
    Wine build: wine-1.6
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.11.0-12-generic



```

I have Xubuntu 64-bit installed.  It worked before but I don't know why it's not working now.

---

