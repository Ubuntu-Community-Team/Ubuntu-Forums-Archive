---
title: "Bloodline Champions"
date: 2012-01-22
forum: Wine
---

### Post by God of the Meeps on 2012-01-22
I was recently successful in getting the BLC installer to run its course. However, when I get to the loader, it returns an error and spits out the following:

```
fixme:actctx:parse_manifest_buffer root element is L"asmv1:assembly", not <assembly>
fixme:sync:CreateMemoryResourceNotification (0) stub
err:ole:CoGetContextToken apartment not initialised
fixme:win:EnumDisplayDevicesW ((null),0,0x32ca24,0x00000000), stub!
fixme:ole:OLEPictureImpl_QueryInterface () : asking for un supported interface {c3fcc19e-a970-11d2-8b5a-00a0c9b7c9c4}
fixme:ole:OLEPictureImpl_QueryInterface () : asking for un supported interface {b196b283-bab4-101a-b69c-00aa00341d07}
fixme:ole:OLEPictureImpl_QueryInterface () : asking for un supported interface {00000003-0000-0000-c000-000000000046}
fixme:ole:OLEPictureImpl_QueryInterface () : asking for un supported interface {00000144-0000-0000-c000-000000000046}
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:richedit:ME_HandleMessage EM_SETTARGETDEVICE doesn't use non-NULL target devices
fixme:richedit:ME_HandleMessage EM_GETLANGOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_GETLANGOPTIONS: stub
fixme:richedit:ME_HandleMessage EM_SETLANGOPTIONS: stub
fixme:x11drv:sync_window_opacity LWA_COLORKEY not supported
fixme:imm:ImmDisableIME (-1): stub
fixme:thread:NtQueryInformationThread Cannot get kerneltime or usertime of other threads
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime 2.0 Error Reporting"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003e8,(nil),0x0008,0x00000110,0x3009b09c,0x5dc630): stub
err:eventlog:ReportEventW L"bloodlinechampionsloader.exe"
err:eventlog:ReportEventW L"1.1.0.23"
err:eventlog:ReportEventW L"4d2cb2fb"
err:eventlog:ReportEventW L"kernel32.dll"
err:eventlog:ReportEventW L"5.1.2600.2180"
err:eventlog:ReportEventW L"00000000"
err:eventlog:ReportEventW L"0"
err:eventlog:ReportEventW L"000213f9"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
err:ole:CoUninitialize Mismatched CoUninitialize
err:ole:CoUninitialize Mismatched CoUninitialize

Unhandled Exception: System.TypeInitializationException: The type initializer for 'System.Net.Sockets.SocketAsyncEventArgs' threw an exception. ---> System.Configuration.ConfigurationErrorsException: Configuration system failed to initialize ---> System.Configuration.ConfigurationErrorsException: Unrecognized configuration section system.serviceModel. (C:\windows\Microsoft.NET\Framework\v2.0.50727\Config\machine.config line 147)
   at System.Configuration.ConfigurationSchemaErrors.ThrowIfErrors(Boolean ignoreLocal)
   at System.Configuration.BaseConfigurationRecord.ThrowIfParseErrors(ConfigurationSchemaErrors schemaErrors)
   at System.Configuration.BaseConfigurationRecord.ThrowIfInitErrors()
   at System.Configuration.ClientConfigurationSystem.EnsureInit(String configKey)
   --- End of inner exception stack trace ---
   at System.Configuration.ConfigurationManager.PrepareConfigSystem()
   at System.Configuration.ConfigurationManager.GetSection(String sectionName)
   at System.Configuration.PrivilegedConfigurationManager.GetSection(String sectionName)
   at System.Net.Configuration.WebRequestModulesSectionInternal.GetSection()
   at System.Net.WebRequest.get_PrefixList()
   at System.Net.WebRequest.Create(Uri requestUri, Boolean useUriBase)
   at System.Net.WebRequest.Create(Uri requestUri)
   at System.Net.WebClient.GetWebRequest(Uri address)
   at System.Net.WebClient.DownloadDataInternal(Uri address, WebRequest& request)
   --- End of inner exception stack trace ---
   at System.Net.Sockets.SocketAsyncEventArgs.Finalize()
wine: Unhandled exception 0xe0434f4d at address 0x684713f9 (thread 006f), starting debugger...
Unhandled exception: 0xe0434f4d in 32-bit code (0x684713f9).
fixme:dbghelp_dwarf:compute_location Only supporting one reg (ebp/22 -> -2)
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:684713f9 ESP:02c4dff0 EBP:02c4e0b4 EFLAGS:00200203(   - --  I   - - -C)
 EAX:6845cef1 EBX:684daff4 ECX:80131534 EDX:02c4e014
 ESI:e0434f4d EDI:001489d0
Stack dump:
0x02c4dff0:  02c4e08c 00000004 02c4e004 e0434f4d
0x02c4e000:  00000001 00000000 684713f9 00000001
0x02c4e010:  80131534 02c4e08c 00392010 02000038
0x02c4e020:  02c4e030 79e80024 02c4e038 02000038
0x02c4e030:  02c4e03c 79e80687 003f0714 02c4e04c
0x02c4e040:  79eda76f 030f11e4 0000012f 02c4e05c
Backtrace:
=>0 0x684713f9 RaiseException+0x59(code=0x1, flags=0x1, nbargs=<is not available>, args=0x29f237f2) [/home/ethereal/wine-1.3.25/dlls/kernel32/except.c:84] in kernel32 (0x02c4e0b4)
  1 0xe0434f4d (0x02c4e0b4)
  2 0x7a097ad1 in mscorwks (+0x227ad0) (0x02c4e0cc)
  3 0x7a097b43 in mscorwks (+0x227b42) (0x02c4e0f4)
  4 0x7a097b74 in mscorwks (+0x227b73) (0x02c4e120)
  5 0x7a097b82 in mscorwks (+0x227b81) (0x02c4e130)
  6 0x79fb9225 in mscorwks (+0x149224) (0x02c4e620)
  7 0x79e81043 in mscorwks (+0x11042) (0x02c4e670)
  8 0x79e81363 in mscorwks (+0x11362) (0x02c4e6c0)
  9 0x0078a1be (0x02c4e6d8)
  10 0x79f8df9a in mscorwks (+0x11df99) (0x02c4e75c)
  11 0x79f8e05b in mscorwks (+0x11e05a) (0x02c4e77c)
  12 0x79f8df09 in mscorwks (+0x11df08) (0x02c4e790)
  13 0x79f95cbc in mscorwks (+0x125cbb) (0x02c4e7e0)
  14 0x79f95d17 in mscorwks (+0x125d16) (0x02c4e868)
  15 0x79f97083 in mscorwks (+0x127082) (0x02c4e880)
  16 0x79e9845f in mscorwks (+0x2845e) (0x02c4e894)
  17 0x79e983fb in mscorwks (+0x283fa) (0x02c4e928)
  18 0x79e98321 in mscorwks (+0x28320) (0x02c4e964)
  19 0x79eef6cc in mscorwks (+0x7f6cb) (0x02c4e98c)
  20 0x79eef6dd in mscorwks (+0x7f6dc) (0x02c4e99c)
  21 0x79f3c63c in mscorwks (+0xcc63b) (0x02c4e9d4)
  22 0x79f92015 in mscorwks (+0x122014) (0x02c4ea78)
  23 0x68372728 call_thread_func+0xb() in ntdll (0x02c4ea88)
  24 0x683761eb call_thread_entry_point+0x6a(entry=0x79f91fcf, arg=0x1491a0) [/home/ethereal/wine-1.3.25/dlls/ntdll/signal_i386.c:2499] in ntdll (0x001491a0)
  25 0x6837b7cc start_thread+0xdb(info=0x7ffd0fb8) [/home/ethereal/wine-1.3.25/dlls/ntdll/thread.c:404] in ntdll (0x001491a0)
  26 0x6816ad31 start_thread+0xd0() in libpthread.so.0 (0x02c4f498)
0x684713f9 RaiseException+0x59 [/home/ethereal/wine-1.3.25/dlls/kernel32/except.c:84] in kernel32: subl	$4,%esp
Unable to access file '/home/ethereal/wine-1.3.25/dlls/kernel32/except.c'
Modules:
Module	Address			Debug info	Name (94 modules)
PE	  400000-  67a000	Deferred        bloodlinechampionsloader
PE	 4090000- 40ac000	Deferred        microsoft.xna.framework.game
ELF	20000000-2009b000	Deferred        msvcrt<elf>
  \-PE	20010000-2009b000	\               msvcrt
ELF	2009b000-200b5000	Deferred        version<elf>
  \-PE	200a0000-200b5000	\               version
ELF	200b5000-20169000	Deferred        winex11<elf>
  \-PE	200c0000-20169000	\               winex11
ELF	20169000-2016f000	Deferred        libuuid.so.1
ELF	2016f000-20173000	Deferred        libxau.so.6
ELF	20173000-2017a000	Deferred        libxdmcp.so.6
ELF	2017a000-2017e000	Deferred        libxinerama.so.1
ELF	2017e000-2018e000	Deferred        libxi.so.6
ELF	2018e000-20194000	Deferred        libxfixes.so.3
ELF	20194000-202c2000	Deferred        ole32<elf>
  \-PE	201b0000-202c2000	\               ole32
ELF	202c2000-20341000	Deferred        rpcrt4<elf>
  \-PE	202d0000-20341000	\               rpcrt4
ELF	20341000-20378000	Deferred        uxtheme<elf>
  \-PE	20350000-20378000	\               uxtheme
ELF	20378000-20433000	Deferred        crypt32<elf>
  \-PE	20380000-20433000	\               crypt32
ELF	20433000-20546000	Deferred        oleaut32<elf>
  \-PE	20450000-20546000	\               oleaut32
ELF	20546000-2057a000	Deferred        ws2_32<elf>
  \-PE	20550000-2057a000	\               ws2_32
ELF	26393000-263b1000	Deferred        libgcc_s.so.1
ELF	293b1000-293b5000	Deferred        libxcomposite.so.1
ELF	2d198000-2d249000	Deferred        gdi32<elf>
  \-PE	2d1a0000-2d249000	\               gdi32
ELF	2f8bb000-2fa0b000	Deferred        user32<elf>
  \-PE	2f8d0000-2fa0b000	\               user32
ELF	39260000-392f7000	Deferred        libfreetype.so.6
ELF	3b48c000-3b497000	Deferred        libxrender.so.1
ELF	3c7c8000-3c7e2000	Deferred        libice.so.6
ELF	404a4000-404b7000	Deferred        libxext.so.6
ELF	42303000-4236c000	Deferred        advapi32<elf>
  \-PE	42310000-4236c000	\               advapi32
ELF	44013000-44037000	Deferred        imm32<elf>
  \-PE	44020000-44037000	\               imm32
PE	4ec50000-4edf6000	Deferred        gdiplus
ELF	4f25a000-4f279000	Deferred        libxcb.so.1
ELF	500bc000-501f2000	Deferred        libx11.so.6
ELF	55e01000-55e0a000	Deferred        libxrandr.so.2
ELF	5b99e000-5b9d3000	Deferred        libfontconfig.so.1
ELF	5caed000-5caf6000	Deferred        libsm.so.6
PE	5e3a0000-5e42d000	Deferred        diasymreader
ELF	5eb90000-5ebba000	Deferred        libexpat.so.1
ELF	5f95f000-5fa60000	Deferred        comctl32<elf>
  \-PE	5f970000-5fa60000	\               comctl32
PE	60000000-60008000	Deferred        accessibility
PE	60340000-60348000	Deferred        culture
PE	60610000-60616000	Deferred        fusion
ELF	61a4f000-61c6a000	Deferred        shell32<elf>
  \-PE	61a60000-61c6a000	\               shell32
PE	637a0000-63998000	Deferred        system.xml
PE	641f0000-6420e000	Deferred        shfusion
PE	64220000-64238000	Deferred        shfusres
PE	64890000-648fc000	Deferred        system.configuration
ELF	659dd000-65a3a000	Deferred        riched20<elf>
  \-PE	659f0000-65a3a000	\               riched20
PE	65ce0000-65db0000	Deferred        system.web.services
ELF	66be6000-66c28000	Deferred        rsaenh<elf>
  \-PE	66bf0000-66c28000	\               rsaenh
ELF	68000000-68020000	Deferred        ld-linux.so.2
ELF	68020000-68164000	Dwarf           libwine.so.1
ELF	68164000-6817f000	Dwarf           libpthread.so.0
ELF	6817f000-682fb000	Dwarf           libc.so.6
ELF	682fb000-68300000	Deferred        libdl.so.2
ELF	68300000-683d1000	Dwarf           ntdll<elf>
  \-PE	68310000-683d1000	\               ntdll
ELF	683d1000-683fb000	Deferred        libm.so.6
ELF	683fb000-68405000	Deferred        libnss_compat.so.2
ELF	68405000-6841e000	Deferred        libnsl.so.1
ELF	6841e000-6842a000	Deferred        libnss_nis.so.2
ELF	6842a000-68437000	Deferred        libnss_files.so.2
ELF	68437000-685ef000	Dwarf           kernel32<elf>
  \-PE	68450000-685ef000	\               kernel32
ELF	685ef000-6860e000	Deferred        libtinfo.so.5
PE	6c1d0000-6c276000	Deferred        system.core
ELF	6c338000-6c343000	Deferred        libxcursor.so.1
PE	77f60000-77fd6000	Deferred        shlwapi
PE	78130000-781cb000	Deferred        msvcr80
PE	79000000-79046000	Deferred        mscoree
PE	79060000-790bb000	Deferred        mscorjit
PE	790c0000-79518000	Deferred        mscorlib
PE	79e70000-7a400000	Export          mscorwks
PE	7a440000-7a744000	Deferred        system
PE	7ade0000-7ae7c000	Deferred        system.drawing
PE	7afd0000-7b49e000	Deferred        system.windows.forms
ELF	7ba9f000-7bac1000	Deferred        libncurses.so.5
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c425000-7c42b000	Deferred        libxxf86vm.so.1
ELF	7cb24000-7cb39000	Deferred        libz.so.1
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000004f    0
	00000024    0
	0000001e    0
	00000010    0
	0000000f    0
0000001b winedevice.exe
	00000020    0
	0000001f    0
	0000001d    0
	0000001c    0
00000021 plugplay.exe
	00000025    0
	00000023    0
	00000022    0
0000002a explorer.exe
	0000002d    0
00000070 iexplore.exe
	00000018    0
	00000026    0
	00000079    0
	0000007c    0
00000076 svchost.exe
	0000008d    0
	00000097    0
	00000095    0
	0000004a    0
	0000008c    0
	0000007d    0
000000a8 (D) C:\Program Files\Stunlock Studios\Bloodline Champions\Binary\BloodlineChampionsLoader.exe
	00000012    0
	00000078    0
	0000008e    0
	0000006f    2 <==
	00000049    0
	00000074    0
Backtrace:
=>0 0x684713f9 RaiseException+0x59(code=0x1, flags=0x1, nbargs=<is not available>, args=0x29f237f2) [/home/ethereal/wine-1.3.25/dlls/kernel32/except.c:84] in kernel32 (0x02c4e0b4)
  1 0xe0434f4d (0x02c4e0b4)
  2 0x7a097ad1 in mscorwks (+0x227ad0) (0x02c4e0cc)
  3 0x7a097b43 in mscorwks (+0x227b42) (0x02c4e0f4)
  4 0x7a097b74 in mscorwks (+0x227b73) (0x02c4e120)
  5 0x7a097b82 in mscorwks (+0x227b81) (0x02c4e130)
  6 0x79fb9225 in mscorwks (+0x149224) (0x02c4e620)
  7 0x79e81043 in mscorwks (+0x11042) (0x02c4e670)
  8 0x79e81363 in mscorwks (+0x11362) (0x02c4e6c0)
  9 0x0078a1be (0x02c4e6d8)
  10 0x79f8df9a in mscorwks (+0x11df99) (0x02c4e75c)
  11 0x79f8e05b in mscorwks (+0x11e05a) (0x02c4e77c)
  12 0x79f8df09 in mscorwks (+0x11df08) (0x02c4e790)
  13 0x79f95cbc in mscorwks (+0x125cbb) (0x02c4e7e0)
  14 0x79f95d17 in mscorwks (+0x125d16) (0x02c4e868)
  15 0x79f97083 in mscorwks (+0x127082) (0x02c4e880)
  16 0x79e9845f in mscorwks (+0x2845e) (0x02c4e894)
  17 0x79e983fb in mscorwks (+0x283fa) (0x02c4e928)
  18 0x79e98321 in mscorwks (+0x28320) (0x02c4e964)
  19 0x79eef6cc in mscorwks (+0x7f6cb) (0x02c4e98c)
  20 0x79eef6dd in mscorwks (+0x7f6dc) (0x02c4e99c)
  21 0x79f3c63c in mscorwks (+0xcc63b) (0x02c4e9d4)
  22 0x79f92015 in mscorwks (+0x122014) (0x02c4ea78)
  23 0x68372728 call_thread_func+0xb() in ntdll (0x02c4ea88)
  24 0x683761eb call_thread_entry_point+0x6a(entry=0x79f91fcf, arg=0x1491a0) [/home/ethereal/wine-1.3.25/dlls/ntdll/signal_i386.c:2499] in ntdll (0x001491a0)
  25 0x6837b7cc start_thread+0xdb(info=0x7ffd0fb8) [/home/ethereal/wine-1.3.25/dlls/ntdll/thread.c:404] in ntdll (0x001491a0)
  26 0x6816ad31 start_thread+0xd0() in libpthread.so.0 (0x02c4f498)
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003ff,(nil),0x0001,0x00000000,0x2c4db40,(nil)): stub
err:eventlog:ReportEventW L".NET Runtime version 2.0.50727.3053 - Fatal Execution Engine Error (79EDA92C) (80131506)"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub

```

---

