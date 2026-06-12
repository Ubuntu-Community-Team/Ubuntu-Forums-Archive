---
title: "Europa Universalis III"
date: 2008-08-26
forum: Wine
---

### Post by Largaroth on 2008-08-26
i've been trying to get Europa Universalis III to work in Wine 1.0.0 and though the installation works, when I launch the game, nothing seems to happen... Has anybody manages to play Europa Universalis en Ubuntu Hardy Heron ?

When I run ```
$ wine eu3game.exe
```

I get this :

```
err:module:import_dll Library MSVCP60.dll (which is needed by L"C:\\Program_Files\\Paradox_Interactive\\Europa_Universalis_III\\eu3game.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program_Files\\Paradox_Interactive\\Europa_Universalis_III\\eu3game.exe" failed, status c0000135

```

and When I run ```
$ wine eu3.exe
```

I get this :

```
fixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:ole:CoGetContextToken stub
fixme:advapi:CheckTokenMembership (0x138 0x14a050 0x32dce8) stub!

Unhandled Exception: System.TypeInitializationException: The type initializer for 'System.Globalization.TextInfo' threw an exception.
   at System.Globalization.TextInfo.GetNativeTextInfo(Int32 cultureID)
   at System.Globalization.TextInfo.get_InvariantNativeTextInfo()
   at System.String.Compare(String strA, Int32 indexA, String strB, Int32 indexB, Int32 length, StringComparison comparisonType)
   at System.Security.Util.URLString.PreProcessForExtendedPathRemoval(String url, Boolean isFileUrl)
   at System.AppDomainSetup.NormalizePath(String path, Boolean useAppBase)
   at System.AppDomainSetup.SetupDefaultApplicationBase(String imageLocation)
   at System.AppDomain.SetupFusionStore(AppDomainSetup info)
   at System.AppDomain.SetupDomain(Boolean allowRedirects, String path, String configFile)
wine: Unhandled exception 0xe0434f4d at address 0x7b844b20 (thread 0009), starting debugger...
Unhandled exception: 0xe0434f4d in 32-bit code (0x7b844b96).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b844b96 ESP:0032ef54 EBP:0032efb8 EFLAGS:00000202(   - 00      - - I1)
 EAX:7b82eb09 EBX:7b8b3884 ECX:00000000 EDX:0032eff0
 ESI:0032eff0 EDI:e0434f4d
Stack dump:
0x0032ef54:  0032eff0 00000004 2bc9f31d 00861d14
0x0032ef64:  e0434f4d 00000001 00000000 7b844b20
0x0032ef74:  00000001 80131534 0032eff0 00392010
0x0032ef84:  02000036 0032ef9c 79e814da 0032efa8
0x0032ef94:  02000036 00000001 0032f018 79e87ff4
0x0032efa4:  0000012c 003f161c 79f958b8 02d364b4
Backtrace:
=>1 0x7b844b96 in kernel32 (+0x24b96) (0x0032efb8)
  2 0x79f97065 in mscorwks (+0x127065) (0x0032f018)
  3 0x7a0945a4 in mscorwks (+0x2245a4) (0x0032f0dc)
  4 0x02d4356b (0x0032f10c)
  5 0x02d43431 (0x0032f138)
0x7b844b96: movl	0xfffffffc(%ebp),%ebx
Modules:
Module	Address			Debug info	Name (66 modules)
PE	  400000-  420000	Deferred        eu3
PE	5e380000-5e409000	Deferred        diasymreader
PE	78130000-781cb000	Deferred        msvcr80
PE	79000000-79045000	Deferred        mscoree
PE	79060000-790b3000	Deferred        mscorjit
PE	790c0000-794de000	Deferred        mscorlib
PE	79e70000-7a3d1000	Export          mscorwks
ELF	7b800000-7b92d000	Export          kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e4ac000-7e4c0000	Deferred        lz32<elf>
  \-PE	7e4b0000-7e4c0000	\               lz32
ELF	7e4c0000-7e4d9000	Deferred        version<elf>
  \-PE	7e4d0000-7e4d9000	\               version
ELF	7e501000-7e514000	Deferred        libresolv.so.2
ELF	7e522000-7e540000	Deferred        iphlpapi<elf>
  \-PE	7e530000-7e540000	\               iphlpapi
ELF	7e540000-7e5a1000	Deferred        rpcrt4<elf>
  \-PE	7e550000-7e5a1000	\               rpcrt4
ELF	7e5a1000-7e645000	Deferred        ole32<elf>
  \-PE	7e5b0000-7e645000	\               ole32
ELF	7e867000-7e8d1000	Deferred        msvcrt<elf>
  \-PE	7e880000-7e8d1000	\               msvcrt
ELF	7e8d1000-7e8da000	Deferred        libxcursor.so.1
ELF	7e8da000-7e8df000	Deferred        libxfixes.so.3
ELF	7e8df000-7e8e2000	Deferred        libxcomposite.so.1
ELF	7e8e2000-7e8e8000	Deferred        libxrandr.so.2
ELF	7e8e8000-7e8f0000	Deferred        libxrender.so.1
ELF	7e8f0000-7e8f3000	Deferred        libxinerama.so.1
ELF	7e8f3000-7e913000	Deferred        imm32<elf>
  \-PE	7e900000-7e913000	\               imm32
ELF	7e913000-7e918000	Deferred        libxdmcp.so.6
ELF	7e918000-7e930000	Deferred        libxcb.so.1
ELF	7e930000-7e932000	Deferred        libxcb-xlib.so.0
ELF	7e932000-7e935000	Deferred        libxau.so.6
ELF	7e935000-7ea1c000	Deferred        libx11.so.6
ELF	7ea1c000-7ea2a000	Deferred        libxext.so.6
ELF	7ea2a000-7ea2f000	Deferred        libxxf86vm.so.1
ELF	7ea2f000-7ea47000	Deferred        libice.so.6
ELF	7ea47000-7ea4f000	Deferred        libsm.so.6
ELF	7ea5d000-7eaf4000	Deferred        winex11<elf>
  \-PE	7ea70000-7eaf4000	\               winex11
ELF	7eb11000-7eb32000	Deferred        libexpat.so.1
ELF	7eb32000-7eb5c000	Deferred        libfontconfig.so.1
ELF	7eb6a000-7eb7f000	Deferred        libz.so.1
ELF	7eb7f000-7ebef000	Deferred        libfreetype.so.6
ELF	7ebfd000-7ec98000	Deferred        gdi32<elf>
  \-PE	7ec10000-7ec98000	\               gdi32
ELF	7ec98000-7eddf000	Deferred        user32<elf>
  \-PE	7ecb0000-7eddf000	\               user32
ELF	7eddf000-7ee38000	Deferred        shlwapi<elf>
  \-PE	7edf0000-7ee38000	\               shlwapi
ELF	7ee38000-7ee8a000	Deferred        advapi32<elf>
  \-PE	7ee40000-7ee8a000	\               advapi32
ELF	7efaa000-7efb5000	Deferred        libnss_files.so.2
ELF	7efb5000-7efcd000	Deferred        libnsl.so.1
ELF	7efcd000-7eff2000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7cc3000-b7ccc000	Deferred        libnss_compat.so.2
ELF	b7ccd000-b7cd1000	Deferred        libdl.so.2
ELF	b7cd1000-b7e20000	Deferred        libc.so.6
ELF	b7e21000-b7e39000	Deferred        libpthread.so.0
ELF	b7e47000-b7f7d000	Deferred        libwine.so.1
ELF	b7f7f000-b7f9b000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program_Files\Paradox_Interactive\Europa_Universalis_III\eu3.exe
	00000018    2
	00000017    0
	00000009    0 <==
0000000c 
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000019 
	0000001a    0
Backtrace:
=>1 0x7b844b96 in kernel32 (+0x24b96) (0x0032efb8)
  2 0x79f97065 in mscorwks (+0x127065) (0x0032f018)
  3 0x7a0945a4 in mscorwks (+0x2245a4) (0x0032f0dc)
  4 0x02d4356b (0x0032f10c)
  5 0x02d43431 (0x0032f138)
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003ff,(nil),0x0001,0x00000000,0x32ea9c,(nil)): stub
err:eventlog:ReportEventW L".NET Runtime version 2.0.50727.42 - Fatal Execution Engine Error (79F97075) (80131506)"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub

```

---

### Post by Oldsoldier2003 on 2008-08-27
Have you checked the winehq application database to see if there are any workarounds? [http://appdb.winehq.org/](http://appdb.winehq.org/)

I'm also tagging this thread for the unanswered posts team to see if someone there can help.

---

### Post by Largaroth on 2008-08-29
I couldn't find anything to make it work on the Wine HQ site :S

---

