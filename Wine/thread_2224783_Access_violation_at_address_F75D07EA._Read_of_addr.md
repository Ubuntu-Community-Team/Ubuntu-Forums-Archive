---
title: "Access violation at address F75D07EA. Read of address FFFFFFFF"
date: 2014-05-18
forum: Wine
---

### Post by keratos2 on 2014-05-18
As per subject title.

Getting this error on a few  32bit windows apps I've installed using 64bit wine and 32bit wine running on 64bit host Ubuntu. Tried installing via wine and PlayOnLinux

Wine 1.4.1, PlayOnLinux 4.2.1; ubuntu 13.10; nvidia with proprietary drivers; 8GM RAM; i7 quad core

I am getting an error (output in xterm when running wine) each time I tried to install:
**p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/p11-kit-trust.so: /usr/lib/i386-linux-gnu/pkcs11/p11-kit-trust.so: cannot open shared object file: No such file or directory**

Not sure if this is anything to do with it?

note sure why my signature isnt displaying; it is turned on and populated with system details;

Wine debug output:
```
Unhandled exception: page fault on read access to 0xffffffff in 32-bit code (0xf75477ea).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:f75477ea ESP:0032682c EBP:00000003 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000006 EBX:f75c2000 ECX:7eda522c EDX:00000000
 ESI:7df25ed6 EDI:7df4e21c
Stack dump:
0x0032682c:  00000004 f740c6c0 00000000 00000000
0x0032683c:  6f686174 0000616d 00000025 0000003c
0x0032684c:  0000005b 0000006e 00000077 0000007c
0x0032685c:  7d5d34b4 00000000 00000000 f75c2000
0x0032686c:  f75c2440 00000000 00000100 f748bd08
0x0032687c:  7d5d34b4 00000000 00000000 00000000
000c: sel=0067 base=00000000 limit=00000000 32-bit --x
Backtrace:
=>0 0xf75477ea in libc.so.6 (+0x1357ea) (0x00000003)
  1 0x7defde20 in libfreetype.so.6 (+0x62e1f) (0x00000003)
  2 0x7defe34a in libfreetype.so.6 (+0x63349) (0x7d9707d8)
  3 0x7deac864 FT_Render_Glyph_Internal+0xb3() in libfreetype.so.6 (0x7d9707d8)
  4 0x7deac8fd FT_Render_Glyph+0x3c() in libfreetype.so.6 (0x00326d94)
  5 0x7eb041dc in gdi32 (+0x741db) (0x00326d94)
  6 0x7eb06bd5 in gdi32 (+0x76bd4) (0x00326dd4)
  7 0x7eaef475 GetGlyphOutlineW+0x10c() in gdi32 (0x00326e34)
  8 0x7de656fc in winex11 (+0x756fb) (0x00327094)
  9 0x7de66386 in winex11 (+0x76385) (0x00327144)
  10 0x7eaee0eb ExtTextOutW+0x16e6() in gdi32 (0x00327374)
  11 0x7ec16799 DrawTextExW+0x79f() in user32 (0x00327ca4)
  12 0x7ec16db1 DrawTextW+0x80() in user32 (0x00327cf4)
  13 0x7e36f082 in comctl32 (+0x3f081) (0x003280a4)
  14 0x7e36f6c4 in comctl32 (+0x3f6c3) (0x00328134)
  15 0x7e370535 in comctl32 (+0x40534) (0x003282a4)
  16 0x7e37c11b in comctl32 (+0x4c11a) (0x00328324)
  17 0x7e37c1f9 in comctl32 (+0x4c1f8) (0x00328364)
  18 0x7e37e9a2 in comctl32 (+0x4e9a1) (0x003283d4)
  19 0x7ec30912 WINPROC_wrapper+0x19() in user32 (0x00328404)
  20 0x7ec30a66 WINPROC_wrapper+0x16d() in user32 (0x00328444)
  21 0x7ec31e20 in user32 (+0xb1e1f) (0x00328934)
  22 0x7ec332c9 CallWindowProcA+0x11f() in user32 (0x00328974)
  23 0x00543c6c in dreamset (+0x143c6b) (0x00328994)
  24 0x00543e05 in dreamset (+0x143e04) (0x003289b0)
  25 0x0054718c in dreamset (+0x14718b) (0x00328a24)
  26 0x0054721b in dreamset (+0x14721a) (0x00328a44)
  27 0x7ec30912 WINPROC_wrapper+0x19() in user32 (0x00328a74)
  28 0x7ec30a66 WINPROC_wrapper+0x16d() in user32 (0x00328ab4)
  29 0x7ec3314b in user32 (+0xb314a) (0x00328b04)
  30 0x7ebf3109 DispatchMessageA+0x19a() in user32 (0x00328c14)
  31 0x0054dcff in dreamset (+0x14dcfe) (0x00328c4c)
  32 0x005432b9 in dreamset (+0x1432b8) (0x00328c98)
  33 0x0043172a in dreamset (+0x31729) (0x0032fd9c)
  34 0x00669f7c in dreamset (+0x269f7b) (0x0032fdb0)
  35 0x0064ef1f in dreamset (+0x24ef1e) (0x0032fe40)
  36 0x7b861d48 call_process_entry+0xb() in kernel32 (0x0032fe58)
  37 0x7b861e8d call_process_entry+0x150() in kernel32 (0x0032fea8)
  38 0x7bc7edfc call_thread_func_wrapper+0xb() in ntdll (0x0032feb8)
  39 0x7bc7ee4b call_thread_func+0x44() in ntdll (0x0032ff98)
  40 0x7bc7edda in ntdll (+0x6edd9) (0x0032ffb8)
  41 0x7bc545bf in ntdll (+0x445be) (0x0032ffe8)
  42 0xf7600b5d wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  43 0xf7600b3b wine_switch_to_stack+0x2a() in libwine.so.1 (0xfff74498)
  44 0x7bc54901 LdrInitializeThunk+0x341() in ntdll (0xfff74518)
  45 0x7b862766 __wine_kernel_init+0x719() in kernel32 (0xfff753a8)
  46 0x7bc5507b __wine_process_init+0x156() in ntdll (0xfff753f8)
  47 0xf75ff3ce wine_init+0x140() in libwine.so.1 (0xfff75438)
  48 0x7bf011c6 main+0x13d() in <wine-loader> (0xfff75878)
  49 0xf742b905 __libc_start_main+0xf4() in libc.so.6 (0x00000000)
0xf75477ea: movq	0x10(%esp),%mm1
Modules:
Module	Address			Debug info	Name (116 modules)
PE	  400000-  7e7000	Export          dreamset
ELF	7b800000-7ba43000	Dwarf           kernel32<elf>
  \-PE	7b810000-7ba43000	\               kernel32
ELF	7bc00000-7bce3000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bce3000	\               ntdll
ELF	7bf00000-7bf04000	Dwarf           <wine-loader>
ELF	7d2b6000-7d2d3000	Deferred        libgcc_s.so.1
ELF	7d2d3000-7d300000	Deferred        msvfw32<elf>
  \-PE	7d2e0000-7d300000	\               msvfw32
ELF	7d426000-7d466000	Deferred        usp10<elf>
  \-PE	7d430000-7d466000	\               usp10
ELF	7d466000-7d4cd000	Deferred        riched20<elf>
  \-PE	7d470000-7d4cd000	\               riched20
ELF	7d54a000-7d55e000	Deferred        riched32<elf>
  \-PE	7d550000-7d55e000	\               riched32
ELF	7d5a2000-7d5b8000	Deferred        dwmapi<elf>
  \-PE	7d5b0000-7d5b8000	\               dwmapi
ELF	7d6b8000-7d6c1000	Deferred        librt.so.1
ELF	7d6c1000-7d6c6000	Deferred        libgpg-error.so.0
ELF	7d6c6000-7d6dd000	Deferred        libresolv.so.2
ELF	7d6dd000-7d728000	Deferred        libdbus-1.so.3
ELF	7d728000-7d747000	Deferred        libp11-kit.so.0
ELF	7d747000-7d7cb000	Deferred        libgcrypt.so.11
ELF	7d7cb000-7d89a000	Deferred        libkrb5.so.3
ELF	7d89a000-7d960000	Deferred        libgnutls.so.26
ELF	7d9c5000-7d9c9000	Deferred        libkeyutils.so.1
ELF	7d9c9000-7d9db000	Deferred        libtasn1.so.3
ELF	7d9db000-7d9e4000	Deferred        libkrb5support.so.0
ELF	7d9e4000-7da0c000	Deferred        libk5crypto.so.3
ELF	7da0c000-7da1e000	Deferred        libavahi-client.so.3
ELF	7da1e000-7da5b000	Deferred        libgssapi_krb5.so.2
ELF	7da5b000-7dac7000	Deferred        libcups.so.2
ELF	7daca000-7dadd000	Deferred        gnome-keyring-pkcs11.so
ELF	7db0b000-7db42000	Deferred        uxtheme<elf>
  \-PE	7db10000-7db42000	\               uxtheme
ELF	7db42000-7db48000	Deferred        libxfixes.so.3
ELF	7db48000-7db53000	Deferred        libxcursor.so.1
ELF	7db54000-7db59000	Deferred        libcom_err.so.2
ELF	7db59000-7db67000	Deferred        libavahi-common.so.3
ELF	7dbb5000-7dbde000	Deferred        libexpat.so.1
ELF	7dbde000-7dc18000	Deferred        libfontconfig.so.1
ELF	7dc18000-7dc29000	Deferred        libxi.so.6
ELF	7dc29000-7dc2d000	Deferred        libxcomposite.so.1
ELF	7dc2d000-7dc38000	Deferred        libxrandr.so.2
ELF	7dc38000-7dc43000	Deferred        libxrender.so.1
ELF	7dc43000-7dc49000	Deferred        libxxf86vm.so.1
ELF	7dc49000-7dc4d000	Deferred        libxinerama.so.1
ELF	7dc4d000-7dc54000	Deferred        libxdmcp.so.6
ELF	7dc54000-7dc58000	Deferred        libxau.so.6
ELF	7dc58000-7dc79000	Deferred        libxcb.so.1
ELF	7dc79000-7dc7f000	Deferred        libuuid.so.1
ELF	7dc7f000-7dc99000	Deferred        libice.so.6
ELF	7dc99000-7ddce000	Deferred        libx11.so.6
ELF	7ddce000-7dde1000	Deferred        libxext.so.6
ELF	7dde1000-7ddea000	Deferred        libsm.so.6
ELF	7ddea000-7de9b000	Dwarf           winex11<elf>
  \-PE	7ddf0000-7de9b000	\               winex11
ELF	7de9b000-7df51000	Dwarf           libfreetype.so.6
ELF	7df51000-7df73000	Deferred        libtinfo.so.5
ELF	7df73000-7df98000	Deferred        libncurses.so.5
ELF	7df98000-7dfbc000	Deferred        imm32<elf>
  \-PE	7dfa0000-7dfbc000	\               imm32
ELF	7dfbc000-7dfe5000	Deferred        mpr<elf>
  \-PE	7dfc0000-7dfe5000	\               mpr
ELF	7dfe5000-7dfff000	Deferred        libz.so.1
ELF	7e015000-7e08f000	Deferred        wininet<elf>
  \-PE	7e020000-7e08f000	\               wininet
ELF	7e08f000-7e0af000	Deferred        oleacc<elf>
  \-PE	7e090000-7e0af000	\               oleacc
ELF	7e0af000-7e133000	Deferred        gdiplus<elf>
  \-PE	7e0c0000-7e133000	\               gdiplus
ELF	7e133000-7e166000	Deferred        ws2_32<elf>
  \-PE	7e140000-7e166000	\               ws2_32
ELF	7e166000-7e19f000	Deferred        oledlg<elf>
  \-PE	7e170000-7e19f000	\               oledlg
ELF	7e19f000-7e2e3000	Deferred        oleaut32<elf>
  \-PE	7e1c0000-7e2e3000	\               oleaut32
ELF	7e2e3000-7e324000	Deferred        winspool<elf>
  \-PE	7e2f0000-7e324000	\               winspool
ELF	7e324000-7e443000	Dwarf           comctl32<elf>
  \-PE	7e330000-7e443000	\               comctl32
ELF	7e443000-7e4b9000	Deferred        shlwapi<elf>
  \-PE	7e450000-7e4b9000	\               shlwapi
ELF	7e4b9000-7e6f7000	Deferred        shell32<elf>
  \-PE	7e4d0000-7e6f7000	\               shell32
ELF	7e6f7000-7e7e4000	Deferred        comdlg32<elf>
  \-PE	7e700000-7e7e4000	\               comdlg32
ELF	7e7e4000-7e811000	Deferred        msacm32<elf>
  \-PE	7e7f0000-7e811000	\               msacm32
ELF	7e811000-7e89a000	Deferred        rpcrt4<elf>
  \-PE	7e820000-7e89a000	\               rpcrt4
ELF	7e89a000-7e9fb000	Deferred        ole32<elf>
  \-PE	7e8b0000-7e9fb000	\               ole32
ELF	7e9fb000-7ea16000	Deferred        version<elf>
  \-PE	7ea00000-7ea16000	\               version
ELF	7ea16000-7ea87000	Deferred        advapi32<elf>
  \-PE	7ea20000-7ea87000	\               advapi32
ELF	7ea87000-7eb66000	Dwarf           gdi32<elf>
  \-PE	7ea90000-7eb66000	\               gdi32
ELF	7eb66000-7ecd5000	Dwarf           user32<elf>
  \-PE	7eb80000-7ecd5000	\               user32
ELF	7ecd5000-7ed8b000	Deferred        winmm<elf>
  \-PE	7ece0000-7ed8b000	\               winmm
ELF	7ef8b000-7ef98000	Deferred        libnss_files.so.2
ELF	7ef98000-7efa4000	Deferred        libnss_nis.so.2
ELF	7efa4000-7efbd000	Deferred        libnsl.so.1
ELF	7efbd000-7f000000	Deferred        libm.so.6
ELF	f7403000-f740c000	Deferred        libnss_compat.so.2
ELF	f740d000-f7412000	Deferred        libdl.so.2
ELF	f7412000-f75c6000	Dwarf           libc.so.6
ELF	f75c7000-f75e2000	Deferred        libpthread.so.0
ELF	f75e4000-f75f8000	Deferred        msimg32<elf>
  \-PE	f75f0000-f75f8000	\               msimg32
ELF	f75f8000-f773c000	Dwarf           libwine.so.1
ELF	f773e000-f7760000	Deferred        ld-linux.so.2
ELF	f7760000-f7761000	Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\daz\Downloads\dreamset236\Dreamset.exe
	00000024    0
	00000023    0
	00000009    0 <==
0000000e services.exe
	0000001f    0
	0000001e    0
	00000019    0
	00000017    0
	00000015    0
	00000010    0
	0000000f    0
00000012 winedevice.exe
	0000001c    0
	00000018    0
	00000014    0
	00000013    0
0000001a plugplay.exe
	00000020    0
	0000001d    0
	0000001b    0
00000021 explorer.exe
	00000022    0
System information:
    Wine build: wine-1.4.1
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.11.0-20-generic



```

---

