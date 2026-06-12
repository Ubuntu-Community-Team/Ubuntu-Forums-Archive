---
title: "wine, mono, and ddfixGUI.exe"
date: 2008-10-16
forum: Wine
---

### Post by Griffin Bain on 2008-10-16
I am trying to run a patch called ddfixGUI.exe for my thief 2 game. at first when i tried running it the terminal said that I need a windows version of mono to run it. i researched mono and workarounds in wine and have found very little. It appears that so few people have the problem and is so sporadic that really there is no answer. I went into the repositorys and got what appeared to be the mono/windows type utilities I would need. now I get this message, any help would be great:

[email]nate@nate-desktop:~/.wine[/email]/drive_c/Program Files/Thief2$ taskset -c 1 wine ddfixGUI.exefixme:virtual:NtAllocateVirtualMemory MEM_WRITE_WATCH type not supported
fixme:advapi:CheckTokenMembership (0x134 0x140ae0 0x32dce8) stub!

Unhandled Exception: System.TypeInitializationException: The type initializer for 'System.Globalization.TextInfo' threw an exception.
   at System.Globalization.TextInfo.GetNativeTextInfo(Int32 cultureID)
   at System.Globalization.TextInfo.get_InvariantNativeTextInfo()
   at System.String.Compare(String strA, Int32 indexA, String strB, Int32 indexB, Int32 length, StringComparison comparisonType)
   at System.Security.Util.URLString.PreProcessForExtendedPathRemoval(String url, Boolean isFileUrl)
   at System.AppDomainSetup.NormalizePath(String path, Boolean useAppBase)
   at System.AppDomainSetup.SetupDefaultApplicationBase(String imageLocation)
   at System.AppDomain.SetupFusionStore(AppDomainSetup info)
   at System.AppDomain.SetupDomain(Boolean allowRedirects, String path, String configFile)
wine: Unhandled exception 0xe0434f4d at address 0x7b844fb0 (thread 0009), starting debugger...
Unhandled exception: 0xe0434f4d in 32-bit code (0x7b845026).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b845026 ESP:0032ef54 EBP:0032efb8 EFLAGS:00200202(   - 00      - - I1)
 EAX:7b82edfd EBX:7b8b4f68 ECX:00000000 EDX:0032eff0
 ESI:0032eff0 EDI:e0434f4d
Stack dump:
0x0032ef54:  0032eff0 00000004 23d7de5e 00851d00
0x0032ef64:  e0434f4d 00000001 00000000 7b844fb0
0x0032ef74:  00000001 80131534 0032eff0 00392010
0x0032ef84:  02000036 0032ef9c 79e814da 0032efa8
0x0032ef94:  02000036 00000001 0032f018 79e87ff4
0x0032efa4:  0000012c 003f161c 79f958b8 02d264b4
Backtrace:
=>1 0x7b845026 in kernel32 (+0x25026) (0x0032efb8)
  2 0x79f97065 in mscorwks (+0x127065) (0x0032f018)
  3 0x7a0945a4 in mscorwks (+0x2245a4) (0x0032f0dc)
  4 0x02d3365b (0x0032f10c)
  5 0x02d33521 (0x0032f138)
0x7b845026: movl	0xfffffffc(%ebp),%ebx
Modules:
Module	Address			Debug info	Name (66 modules)
PE	  400000-  40e000	Deferred        ddfixgui
PE	5e380000-5e409000	Deferred        diasymreader
PE	78130000-781cb000	Deferred        msvcr80
PE	79000000-79045000	Deferred        mscoree
PE	79060000-790b3000	Deferred        mscorjit
PE	790c0000-794de000	Deferred        mscorlib
PE	79e70000-7a3d1000	Export          mscorwks
ELF	7b800000-7b93c000	Export          kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca6000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca6000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e41e000-7e432000	Deferred        lz32<elf>
  \-PE	7e420000-7e432000	\               lz32
ELF	7e432000-7e44b000	Deferred        version<elf>
  \-PE	7e440000-7e44b000	\               version
ELF	7e473000-7e486000	Deferred        libresolv.so.2
ELF	7e495000-7e4b4000	Deferred        iphlpapi<elf>
  \-PE	7e4a0000-7e4b4000	\               iphlpapi
ELF	7e4b4000-7e519000	Deferred        rpcrt4<elf>
  \-PE	7e4c0000-7e519000	\               rpcrt4
ELF	7e519000-7e622000	Deferred        ole32<elf>
  \-PE	7e530000-7e622000	\               ole32
ELF	7e844000-7e8ae000	Deferred        msvcrt<elf>
  \-PE	7e850000-7e8ae000	\               msvcrt
ELF	7e8ae000-7e8b7000	Deferred        libxcursor.so.1
ELF	7e8b7000-7e8bc000	Deferred        libxfixes.so.3
ELF	7e8bc000-7e8bf000	Deferred        libxcomposite.so.1
ELF	7e8bf000-7e8c5000	Deferred        libxrandr.so.2
ELF	7e8c5000-7e8cd000	Deferred        libxrender.so.1
ELF	7e8cd000-7e8d2000	Deferred        libxxf86vm.so.1
ELF	7e8d2000-7e8f2000	Deferred        imm32<elf>
  \-PE	7e8e0000-7e8f2000	\               imm32
ELF	7e8f2000-7e8f7000	Deferred        libxdmcp.so.6
ELF	7e8f7000-7e90f000	Deferred        libxcb.so.1
ELF	7e90f000-7e9f6000	Deferred        libx11.so.6
ELF	7e9f6000-7ea04000	Deferred        libxext.so.6
ELF	7ea04000-7ea1c000	Deferred        libice.so.6
ELF	7ea1c000-7ea24000	Deferred        libsm.so.6
ELF	7ea33000-7eacb000	Deferred        winex11<elf>
  \-PE	7ea40000-7eacb000	\               winex11
ELF	7eb09000-7eb2a000	Deferred        libexpat.so.1
ELF	7eb2a000-7eb54000	Deferred        libfontconfig.so.1
ELF	7eb55000-7eb58000	Deferred        libxinerama.so.1
ELF	7eb58000-7eb5b000	Deferred        libxau.so.6
ELF	7eb63000-7eb78000	Deferred        libz.so.1
ELF	7eb78000-7ebe5000	Deferred        libfreetype.so.6
ELF	7ebe5000-7ebe7000	Deferred        libxcb-xlib.so.0
ELF	7ebf4000-7ec92000	Deferred        gdi32<elf>
  \-PE	7ec00000-7ec92000	\               gdi32
ELF	7ec92000-7eddb000	Deferred        user32<elf>
  \-PE	7ecb0000-7eddb000	\               user32
ELF	7eddb000-7ee35000	Deferred        shlwapi<elf>
  \-PE	7edf0000-7ee35000	\               shlwapi
ELF	7ee35000-7ee89000	Deferred        advapi32<elf>
  \-PE	7ee40000-7ee89000	\               advapi32
ELF	7efa9000-7efb4000	Deferred        libnss_files.so.2
ELF	7efb4000-7efcc000	Deferred        libnsl.so.1
ELF	7efcc000-7eff1000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7c53000-b7c5c000	Deferred        libnss_compat.so.2
ELF	b7c5d000-b7c61000	Deferred        libdl.so.2
ELF	b7c61000-b7db0000	Deferred        libc.so.6
ELF	b7db1000-b7dc9000	Deferred        libpthread.so.0
ELF	b7dd8000-b7f0e000	Deferred        libwine.so.1
ELF	b7f10000-b7f2c000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Thief2\ddfixGUI.exe
	0000001d    2
	0000001c    0
	00000009    0 <==
0000000c 
	0000001a    0
	00000019    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	0000001b    0
	00000018    0
	00000017    0
0000001e 
	0000001f    0
Backtrace:
=>1 0x7b845026 in kernel32 (+0x25026) (0x0032efb8)
  2 0x79f97065 in mscorwks (+0x127065) (0x0032f018)
  3 0x7a0945a4 in mscorwks (+0x2245a4) (0x0032f0dc)
  4 0x02d3365b (0x0032f10c)
  5 0x02d33521 (0x0032f138)
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003ff,(nil),0x0001,0x00000000,0x32ea9c,(nil)): stub
err:eventlog:ReportEventW L".NET Runtime version 2.0.50727.42 - Fatal Execution Engine Error (79F97075) (80131506)"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
[email]nate@nate-desktop:~/.wine[/email]/drive_c/Program Files/Thief2$

---

### Post by YokoZar on 2008-10-16
That's a crash.


How did you install Mono into Wine?  What repositories are you referring to?

---

### Post by Griffin Bain on 2008-10-17
i didn't install mono into wine, i just tried installing mono period hoping that wine would think it was reading what it needed to read to open a GUI.exe. I used the synaptic package manager and the add/remove utlities to install what appeared to be some mono utilities and librarys. i have ubuntu 8.04.

---

### Post by YokoZar on 2008-10-17
> **Griffin Bain said:**
> i didn't install mono into wine, i just tried installing mono period hoping that wine would think it was reading what it needed to read to open a GUI.exe. I used the synaptic package manager and the add/remove utlities to install what appeared to be some mono utilities and librarys. i have ubuntu 8.04.
Ahh ok.  Wine can't use the system Mono, it needs the Windows version of Mono to give .NET to Windows programs (or you could install the Microsoft .NET).

The way to do this is with a program called Winetricks (which hasn't yet been updated to support Mono 2.0, though it does do the MS .NET all right)

---

### Post by Griffin Bain on 2008-10-18
ok, i got wine tricks installed. i then used it to install the .netframework 2.0 and also set it to run wine in windows 2000 mode (another thread said to do this . . . ). I then went back to the terminal to try to run ddfixGUI.exe and this is what I got:

nate@nate-desktop:~$ cd ~/.wine/drive_c/Program\ Files/Thief2
[email]nate@nate-desktop:~/.wine[/email]/drive_c/Program Files/Thief2$ wine ddfixGUI.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\Microsoft.NET\\Framework\\v2.0.50727\\mscorsvw.exe" failed, status c0000142
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"

---

