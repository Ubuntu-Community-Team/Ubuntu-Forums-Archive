---
title: "&quot;The program [x].exe has experienced a serious problem&quot; while installing a game."
date: 2012-07-14
forum: Wine
---

### Post by SerFaren on 2012-07-14
I tried installing this game (Dragon Age: Origins) through Wine and through PlayOnLinux, however I get the same error.

I'm unsure of the problem here:
"[filename].exe has experienced a serious problem and needs to be closed"
I clicked "Show Details" and this came up:

```
Unhandled exception: page fault on read access to 0x21b1951c in 32-bit code (0x203aa757).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:203aa757 ESP:00b5e470 EBP:00b5e4c8 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:00142260 EBX:203c2ff4 ECX:00000000 EDX:21b19500
 ESI:0000133f EDI:00000000
Stack dump:
0x00b5e470:  00142260 0000133f 00000000 00000032
0x00b5e480:  7e32a750 00000000 7d1c9264 6816bd19
0x00b5e490:  00000008 00b5e804 00000008 00142260
0x00b5e4a0:  00000008 00000000 21b19500 00000000
0x00b5e4b0:  4e1c20cf 00000000 203aa64b 4fb63ff4
0x00b5e4c0:  7d18c990 203aa640 246fc420 4fad4c55
Backtrace:
=>0 0x203aa757 in winegstreamer (+0xa757) (0x00b5e4c8)
  1 0x4fad4c55 in libgstreamer-0.10.so.0 (+0x54c54) (0x246fc420)
  2 0x4fadafa6 gst_pad_pull_range+0x115() in libgstreamer-0.10.so.0 (0x00b5e8b8)
  3 0x4fac2c74 in libgstreamer-0.10.so.0 (+0x42c73) (0x246fc420)
  4 0x4fad4c55 in libgstreamer-0.10.so.0 (+0x54c54) (0x246fc420)
  5 0x4fadafa6 gst_pad_pull_range+0x115() in libgstreamer-0.10.so.0 (0x00b5e8b8)
  6 0x2662fa9f in libgstcoreelements.so (+0x33a9e) (0x246fc420)
  7 0x4fad4c55 in libgstreamer-0.10.so.0 (+0x54c54) (0x246fc420)
  8 0x4fadafa6 gst_pad_pull_range+0x115() in libgstreamer-0.10.so.0 (0x00b5e8b8)
  9 0x4e1afb97 in libgstasf.so (+0x6b96) (0x00000032)
  10 0x4e1b995b in libgstasf.so (+0x1095a) (0x00000000)
  11 0x4fb03ee0 in libgstreamer-0.10.so.0 (+0x83edf) (0x7d1c4920)
  12 0x4fb05188 in libgstreamer-0.10.so.0 (+0x85187) (0x00000001)
  13 0x24670a27 in libglib-2.0.so.0 (+0x6ca26) (0x00000001)
  14 0x2466e5f4 in libglib-2.0.so.0 (+0x6a5f3) (0x246fc420)
  15 0x203a4f57 in winegstreamer (+0x4f56) (0x00b5ea48)
  16 0x7bc71da0 call_thread_func_wrapper+0xb() in ntdll (0x00b5ea58)
  17 0x7bc7485d call_thread_func+0x7c() in ntdll (0x00b5eb28)
  18 0x7bc71d7e RtlRaiseException+0x21() in ntdll (0x00b5eb48)
  19 0x7bc7a738 in ntdll (+0x6a737) (0x00b5f398)
  20 0x68168d31 start_thread+0xd0() in libpthread.so.0 (0x00b5f498)
0x203aa757: call	*0x1c(%edx)
Modules:
Module	Address			Debug info	Name (173 modules)
PE	  400000-  533000	Deferred        autorun
ELF	20000000-2001d000	Deferred        msxml<elf>
  \-PE	20010000-2001d000	\               msxml
ELF	2001d000-2016a000	Deferred        libxml2.so.2
ELF	2016a000-201a6000	Deferred        libxslt.so.1
ELF	201a6000-201ca000	Deferred        devenum<elf>
  \-PE	201b0000-201ca000	\               devenum
ELF	201ca000-201df000	Deferred        avicap32<elf>
  \-PE	201d0000-201df000	\               avicap32
ELF	201df000-202d0000	Deferred        libasound.so.2
ELF	202d0000-2031e000	Deferred        libpulse.so.0
ELF	2031e000-2038f000	Deferred        libsndfile.so.1
ELF	2038f000-203c5000	Dwarf           winegstreamer<elf>
  \-PE	203a0000-203c5000	\               winegstreamer
ELF	203c5000-203d2000	Deferred        libgstapp-0.10.so.0
ELF	203d2000-20421000	Deferred        libgobject-2.0.so.0
ELF	20421000-20428000	Deferred        libffi.so.6
ELF	20428000-20467000	Deferred        libpcre.so.3
ELF	20467000-20474000	Deferred        libgstvideo-0.10.so.0
ELF	20474000-2048a000	Deferred        libgsttypefindfunctions.so
ELF	2048a000-204a2000	Deferred        libgstrtsp-0.10.so.0
ELF	204a2000-204c8000	Deferred        libgstaudio-0.10.so.0
ELF	204c8000-204cd000	Deferred        utf-16.so
ELF	204cd000-204de000	Deferred        libbz2.so.1.0
ELF	204de000-20522000	Deferred        libtheoraenc.so.1
ELF	2056f000-2058f000	Deferred        libgstpbutils-0.10.so.0
ELF	2058f000-206d5000	Deferred        libgio-2.0.so.0
ELF	206d5000-207da000	Deferred        libavformat.so.53
ELF	207da000-2133f000	Deferred        libavcodec.so.53
ELF	21b7c000-21cf4000	Deferred        libvorbisenc.so.2
ELF	23b0c000-23b65000	Deferred        libgstbase-0.10.so.0
ELF	23df8000-23e11000	Deferred        msacm32<elf>
  \-PE	23e00000-23e11000	\               msacm32
ELF	24604000-246fd000	Dwarf           libglib-2.0.so.0
ELF	249ab000-249ba000	Deferred        libgstriff-0.10.so.0
ELF	265fc000-26643000	Dwarf           libgstcoreelements.so
ELF	27570000-27591000	Deferred        libavutil.so.51
ELF	275f4000-27642000	Deferred        libflac.so.8
ELF	27a5e000-27a70000	Deferred        libgstinterfaces-0.10.so.0
ELF	27dba000-27dc1000	Deferred        libasyncns.so.0
ELF	29620000-29641000	Deferred        libspeex.so.1
ELF	2c9e3000-2c9f1000	Deferred        libgsm.so.1
ELF	2f07c000-2f0b6000	Deferred        libgstffmpeg.so
ELF	33a8f000-33af4000	Deferred        libpulsecommon-1.0.so
ELF	34704000-34709000	Deferred        libgmodule-2.0.so.0
ELF	35932000-3595d000	Deferred        libgsttag-0.10.so.0
ELF	35b8c000-35b94000	Deferred        libjson.so.0
ELF	3903d000-39060000	Deferred        mmdevapi<elf>
  \-PE	39040000-39060000	\               mmdevapi
ELF	3e08e000-3e0a8000	Deferred        libtheoradec.so.1
ELF	45946000-4594e000	Deferred        libogg.so.0
ELF	465f5000-465fb000	Deferred        libgthread-2.0.so.0
ELF	473ba000-473d2000	Deferred        libgstrtp-0.10.so.0
ELF	488c8000-488d1000	Deferred        libgstsdp-0.10.so.0
ELF	4b2cb000-4b379000	Deferred        libschroedinger-1.0.so.0
ELF	4e1a9000-4e1c8000	Dwarf           libgstasf.so
ELF	4e936000-4e961000	Deferred        libvorbis.so.0
ELF	4fa80000-4fb66000	Dwarf           libgstreamer-0.10.so.0
ELF	503e1000-5046e000	Deferred        liborc-0.4.so.0
ELF	550cc000-550f6000	Deferred        libva.so.1
ELF	5a8e7000-5a92b000	Deferred        dsound<elf>
  \-PE	5a8f0000-5a92b000	\               dsound
ELF	631be000-631da000	Deferred        libgstdecodebin2.so
ELF	63c5d000-63c73000	Deferred        midimap<elf>
  \-PE	63c60000-63c73000	\               midimap
ELF	644db000-644f8000	Deferred        mciqtz32<elf>
  \-PE	644e0000-644f8000	\               mciqtz32
ELF	65a71000-65a78000	Deferred        libasound_module_pcm_pulse.so
ELF	664f9000-66525000	Deferred        winealsa<elf>
  \-PE	66500000-66525000	\               winealsa
ELF	68000000-68020000	Deferred        ld-linux.so.2
ELF	68020000-68162000	Dwarf           libwine.so.1
ELF	68162000-6817d000	Dwarf           libpthread.so.0
ELF	6817d000-682f9000	Dwarf           libc.so.6
ELF	682f9000-682fe000	Deferred        libdl.so.2
ELF	682fe000-68308000	Deferred        libnss_compat.so.2
ELF	68308000-68321000	Deferred        libnsl.so.1
ELF	68321000-6832d000	Deferred        libnss_nis.so.2
ELF	6832d000-6833a000	Deferred        libnss_files.so.2
ELF	6833a000-683b0000	Deferred        rpcrt4<elf>
  \-PE	68350000-683b0000	\               rpcrt4
ELF	683b0000-68411000	Deferred        advapi32<elf>
  \-PE	683c0000-68411000	\               advapi32
ELF	68411000-68480000	Deferred        wininet<elf>
  \-PE	68420000-68480000	\               wininet
ELF	68480000-68495000	Deferred        libz.so.1
ELF	68495000-684bb000	Deferred        mpr<elf>
  \-PE	684a0000-684bb000	\               mpr
ELF	684bb000-685fb000	Deferred        user32<elf>
  \-PE	684d0000-685fb000	\               user32
ELF	685fb000-686b8000	Deferred        gdi32<elf>
  \-PE	68610000-686b8000	\               gdi32
ELF	686b8000-686d1000	Deferred        version<elf>
  \-PE	686c0000-686d1000	\               version
ELF	686d1000-6873b000	Deferred        shlwapi<elf>
  \-PE	686e0000-6873b000	\               shlwapi
ELF	6873b000-68833000	Deferred        comctl32<elf>
  \-PE	68740000-68833000	\               comctl32
ELF	68833000-68847000	Deferred        msimg32<elf>
  \-PE	68840000-68847000	\               msimg32
ELF	68847000-68926000	Deferred        comdlg32<elf>
  \-PE	68850000-68926000	\               comdlg32
ELF	68926000-68960000	Deferred        winspool<elf>
  \-PE	68930000-68960000	\               winspool
ELF	68960000-68a68000	Deferred        ole32<elf>
  \-PE	68980000-68a68000	\               ole32
ELF	68a68000-68b5b000	Deferred        oleaut32<elf>
  \-PE	68a80000-68b5b000	\               oleaut32
ELF	68b5b000-68b8d000	Deferred        ws2_32<elf>
  \-PE	68b60000-68b8d000	\               ws2_32
ELF	68b8d000-68c3a000	Deferred        winmm<elf>
  \-PE	68b90000-68c3a000	\               winmm
ELF	68c3a000-68c62000	Deferred        msacm32<elf>
  \-PE	68c40000-68c62000	\               msacm32
ELF	68c62000-68cf9000	Deferred        libfreetype.so.6
ELF	68cf9000-68d8c000	Deferred        winex11<elf>
  \-PE	68d00000-68d8c000	\               winex11
ELF	68d8c000-68d9f000	Deferred        libxext.so.6
ELF	68d9f000-68ed5000	Deferred        libx11.so.6
ELF	68ed5000-68eef000	Deferred        libice.so.6
ELF	68eef000-68ef5000	Deferred        libuuid.so.1
ELF	68ef5000-68f14000	Deferred        libxcb.so.1
ELF	68f14000-68f18000	Deferred        libxau.so.6
ELF	68f18000-68f1f000	Deferred        libxdmcp.so.6
ELF	68f1f000-68f23000	Deferred        libxinerama.so.1
ELF	68f23000-68f29000	Deferred        libxxf86vm.so.1
ELF	68f29000-68f34000	Deferred        libxrender.so.1
ELF	68f34000-68f38000	Deferred        libxcomposite.so.1
ELF	68f38000-68f48000	Deferred        libxi.so.6
ELF	68f48000-68f7d000	Deferred        libfontconfig.so.1
ELF	68f7d000-68fa7000	Deferred        libexpat.so.1
ELF	68fa7000-68fb2000	Deferred        libxcursor.so.1
ELF	68fb2000-68fe6000	Deferred        uxtheme<elf>
  \-PE	68fc0000-68fe6000	\               uxtheme
ELF	68fe6000-69038000	Deferred        libcups.so.2
ELF	69038000-69076000	Deferred        libgssapi_krb5.so.2
ELF	69076000-69126000	Deferred        libgnutls.so.26
ELF	69126000-69139000	Deferred        libavahi-client.so.3
ELF	69139000-69202000	Deferred        libkrb5.so.3
ELF	69202000-6922b000	Deferred        libk5crypto.so.3
ELF	6922b000-6922f000	Deferred        libcom_err.so.2
ELF	6922f000-69238000	Deferred        libkrb5support.so.0
ELF	69238000-6924a000	Deferred        libtasn1.so.3
ELF	6924a000-692cf000	Deferred        libgcrypt.so.11
ELF	692cf000-69318000	Deferred        libdbus-1.so.3
ELF	69318000-6931c000	Deferred        libkeyutils.so.1
ELF	6931c000-69321000	Deferred        libgpg-error.so.0
ELF	69321000-6932a000	Deferred        librt.so.1
ELF	696de000-696e4000	Deferred        libxfixes.so.3
ELF	6b8b2000-6b8bb000	Deferred        libxrandr.so.2
ELF	6d362000-6d3f8000	Deferred        msxml3<elf>
  \-PE	6d370000-6d3f8000	\               msxml3
ELF	6f882000-6f8a0000	Deferred        libselinux.so.1
ELF	7294d000-72b5d000	Deferred        shell32<elf>
  \-PE	72960000-72b5d000	\               shell32
ELF	74dc2000-74e5c000	Deferred        libvpx.so.0
ELF	7522a000-75248000	Deferred        libgcc_s.so.1
ELF	75e1e000-75e2c000	Deferred        libavahi-common.so.3
ELF	7776b000-77782000	Deferred        libresolv.so.2
ELF	77d2c000-77d56000	Deferred        libm.so.6
ELF	77fc4000-78049000	Deferred        urlmon<elf>
  \-PE	77fd0000-78049000	\               urlmon
ELF	786dc000-786e6000	Deferred        libwrap.so.0
ELF	7ab52000-7ab5b000	Deferred        libsm.so.6
ELF	7af71000-7af93000	Deferred        imm32<elf>
  \-PE	7af80000-7af93000	\               imm32
ELF	7b096000-7b0ce000	Deferred        oledlg<elf>
  \-PE	7b0a0000-7b0ce000	\               oledlg
ELF	7b800000-7ba16000	Deferred        kernel32<elf>
  \-PE	7b810000-7ba16000	\               kernel32
ELF	7bc00000-7bcc3000	Dwarf           ntdll<elf>
  \-PE	7bc10000-7bcc3000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) E:\autorun.exe
	00000028   15
	00000027    0
	00000026    0 <==
	00000024    0
	00000023    0
	00000009    0
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
00000021 explorer.exe
	00000022    0
System information:
    Wine build: wine-1.4
    Platform: i386
    Host system: Linux
    Host version: 3.0.0-12-generic

```
Does anyone have the solution to this problem?

---

### Post by oldos2er on 2012-07-14
Moved to Wine.

---

