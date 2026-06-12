---
title: "Amazon Unboxed Player"
date: 2008-07-10
forum: Wine
---

### Post by kevin11951 on 2008-07-10
help? :confused:

```
ksoviero@ksoviero-laptop:~$ wine 'C:\Program Files\Amazon\Amazon Unbox Video\ADVWindowsClientApp.exe'
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:advapi:CheckTokenMembership (0x154 0x190070 0x32dce8) stub!

Unhandled Exception: System.TypeInitializationException: The type initializer for 'System.Globalization.TextInfo' threw an exception.
   at System.Globalization.TextInfo.GetNativeTextInfo(Int32 cultureID)
   at System.Globalization.TextInfo.get_InvariantNativeTextInfo()
   at System.String.Compare(String strA, Int32 indexA, String strB, Int32 indexB, Int32 length, StringComparison comparisonType)
   at System.Security.Util.URLString.PreProcessForExtendedPathRemoval(String url, Boolean isFileUrl)
   at System.AppDomainSetup.NormalizePath(String path, Boolean useAppBase)
   at System.AppDomainSetup.SetupDefaultApplicationBase(String imageLocation)
   at System.AppDomain.SetupFusionStore(AppDomainSetup info)
   at System.AppDomain.SetupDomain(Boolean allowRedirects, String path, String configFile)
wine: Unhandled exception 0xe0434f4d at address 0x7b844e00 (thread 0020), starting debugger...
Unhandled exception: 0xe0434f4d in 32-bit code (0x7b844e76).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b844e76 ESP:0032ef54 EBP:0032efb8 EFLAGS:00000212(   - 00      - -IA1)
 EAX:7b82eba9 EBX:7b8b3884 ECX:00000000 EDX:0032eff0
 ESI:0032eff0 EDI:e0434f4d
Stack dump:
0x0032ef54:  0032eff0 00000004 8b22974f 00931d50
0x0032ef64:  e0434f4d 00000001 00000000 7b844e00
0x0032ef74:  00000001 80131534 0032eff0 00392010
0x0032ef84:  02000036 0032ef9c 79e814da 0032efa8
0x0032ef94:  02000036 00000001 0032f018 79e87ff4
0x0032efa4:  0000012c 003f161c 79f958b8 02f164b4
Backtrace:
=>1 0x7b844e76 in kernel32 (+0x24e76) (0x0032efb8)
  2 0x79f97065 in mscorwks (+0x127065) (0x0032f018)
  3 0x7a0945a4 in mscorwks (+0x2245a4) (0x0032f0dc)
  4 0x02f2355b (0x0032f10c)
  5 0x02f23421 (0x0032f138)
0x7b844e76: movl	0xfffffffc(%ebp),%ebx
Modules:
Module	Address			Debug info	Name (79 modules)
PE	  400000-  4f0000	Deferred        advwindowsclientapp
PE	5e380000-5e409000	Deferred        diasymreader
PE	64020000-64033000	Deferred        mscorsec
PE	78130000-781cb000	Deferred        msvcr80
PE	79000000-79045000	Deferred        mscoree
PE	79060000-790b3000	Deferred        mscorjit
PE	790c0000-794de000	Deferred        mscorlib
PE	79e70000-7a3d1000	Export          mscorwks
ELF	7b800000-7b930000	Export          kernel32<elf>
  \-PE	7b820000-7b930000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e2cb000-7e2df000	Deferred        lz32<elf>
  \-PE	7e2d0000-7e2df000	\               lz32
ELF	7e2df000-7e2f8000	Deferred        version<elf>
  \-PE	7e2e0000-7e2f8000	\               version
ELF	7e30b000-7e31e000	Deferred        libresolv.so.2
ELF	7e334000-7e352000	Deferred        iphlpapi<elf>
  \-PE	7e340000-7e352000	\               iphlpapi
ELF	7e352000-7e3b4000	Deferred        rpcrt4<elf>
  \-PE	7e360000-7e3b4000	\               rpcrt4
ELF	7e3b4000-7e458000	Deferred        ole32<elf>
  \-PE	7e3c0000-7e458000	\               ole32
ELF	7e458000-7e493000	Deferred        rsaenh<elf>
  \-PE	7e460000-7e493000	\               rsaenh
ELF	7e493000-7e4aa000	Deferred        imagehlp<elf>
  \-PE	7e4a0000-7e4aa000	\               imagehlp
ELF	7e4aa000-7e4dd000	Deferred        uxtheme<elf>
  \-PE	7e4b0000-7e4dd000	\               uxtheme
ELF	7e4dd000-7e59c000	Deferred        comctl32<elf>
  \-PE	7e4f0000-7e59c000	\               comctl32
ELF	7e59c000-7e604000	Deferred        crypt32<elf>
  \-PE	7e5b0000-7e604000	\               crypt32
ELF	7e604000-7e62d000	Deferred        wintrust<elf>
  \-PE	7e610000-7e62d000	\               wintrust
ELF	7e84f000-7e8b9000	Deferred        msvcrt<elf>
  \-PE	7e860000-7e8b9000	\               msvcrt
ELF	7e8b9000-7e8c2000	Deferred        libxcursor.so.1
ELF	7e8c2000-7e8c7000	Deferred        libxfixes.so.3
ELF	7e8c7000-7e8ca000	Deferred        libxcomposite.so.1
ELF	7e8ca000-7e8d0000	Deferred        libxrandr.so.2
ELF	7e8d0000-7e8d8000	Deferred        libxrender.so.1
ELF	7e8d8000-7e8db000	Deferred        libxinerama.so.1
ELF	7e8db000-7e8fb000	Deferred        imm32<elf>
  \-PE	7e8e0000-7e8fb000	\               imm32
ELF	7e8fb000-7e900000	Deferred        libxdmcp.so.6
ELF	7e900000-7e918000	Deferred        libxcb.so.1
ELF	7e918000-7e91b000	Deferred        libxau.so.6
ELF	7e91b000-7ea02000	Deferred        libx11.so.6
ELF	7ea02000-7ea10000	Deferred        libxext.so.6
ELF	7ea10000-7ea15000	Deferred        libxxf86vm.so.1
ELF	7ea16000-7ea29000	Deferred        softpub<elf>
  \-PE	7ea20000-7ea29000	\               softpub
ELF	7ea2b000-7eac2000	Deferred        winex11<elf>
  \-PE	7ea40000-7eac2000	\               winex11
ELF	7eaf9000-7eb1a000	Deferred        libexpat.so.1
ELF	7eb1a000-7eb44000	Deferred        libfontconfig.so.1
ELF	7eb44000-7eb59000	Deferred        libz.so.1
ELF	7eb59000-7ebc9000	Deferred        libfreetype.so.6
ELF	7ebc9000-7ebcb000	Deferred        libxcb-xlib.so.0
ELF	7ebdf000-7ec7d000	Deferred        gdi32<elf>
  \-PE	7ebf0000-7ec7d000	\               gdi32
ELF	7ec7d000-7edc4000	Deferred        user32<elf>
  \-PE	7eca0000-7edc4000	\               user32
ELF	7edc4000-7ee1d000	Deferred        shlwapi<elf>
  \-PE	7edd0000-7ee1d000	\               shlwapi
ELF	7ee1d000-7ee6f000	Deferred        advapi32<elf>
  \-PE	7ee30000-7ee6f000	\               advapi32
ELF	7ef8f000-7ef9a000	Deferred        libnss_files.so.2
ELF	7ef9a000-7efa4000	Deferred        libnss_nis.so.2
ELF	7efa4000-7efbc000	Deferred        libnsl.so.1
ELF	7efbc000-7efc5000	Deferred        libnss_compat.so.2
ELF	7efc5000-7efea000	Deferred        libm.so.6
ELF	f7cd1000-f7cd5000	Deferred        libdl.so.2
ELF	f7cd5000-f7e24000	Deferred        libc.so.6
ELF	f7e25000-f7e3d000	Deferred        libpthread.so.0
ELF	f7e53000-f7f89000	Deferred        libwine.so.1
ELF	f7f8b000-f7faa000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
	0000000b    0
0000000c 
	0000000e    0
	0000000d    0
0000001f (D) C:\Program Files\Amazon\Amazon Unbox Video\ADVWindowsClientApp.exe
	00000022    2
	00000021    0
	00000020    0 <==
00000023 
	00000024    0
Backtrace:
=>1 0x7b844e76 in kernel32 (+0x24e76) (0x0032efb8)
  2 0x79f97065 in mscorwks (+0x127065) (0x0032f018)
  3 0x7a0945a4 in mscorwks (+0x2245a4) (0x0032f0dc)
  4 0x02f2355b (0x0032f10c)
  5 0x02f23421 (0x0032f138)
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003ff,(nil),0x0001,0x00000000,0x32ea9c,(nil)): stub
err:eventlog:ReportEventW L".NET Runtime version 2.0.50727.42 - Fatal Execution Engine Error (79F97075) (80131506)"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
ksoviero@ksoviero-laptop:~$ 


```

---

