---
title: "Adobe pluign for ies4linux"
date: 2008-08-27
forum: Wine
---

### Post by Cadmus on 2008-08-27
Now, I know ies4linux isn't oficially supported, but I'm sure someone else here must have had the same problem.

I've got ies4linux installed and happy. However attempting to install Adobe 5.05 using ```
WINEPREFIX=/home/user/.ies4linux/ie6/ wine adobe505enu.exe
``` causes it to crash quite hard (I'll be back later to add the full error message) but it works fine if I don't use the wineprefix.

Failing that is there a later version of Adobe that works and how do I stop the installer from complaining about having the wrong version of Windows? Is it something I change in the main wine preferences or is there a file in ies4linux I need to tweak?

---

### Post by Cadmus on 2008-08-27
As promised here's the full message

```
err:service:RPC_Init RpcServerUseProtseq failed with error 1703
err:wineboot:start_services_process Unexpected termination of services.exe - exit code 1703
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PROCESSOR_PERFORMANCE_INFORMATION
err:module:DelayLoadFailureHook failed to delay load rpcrt4.dll.NdrClientInitializeNew
wine: Call from 0x7b844e40 to unimplemented function rpcrt4.dll.NdrClientInitializeNew, aborting
err:module:DelayLoadFailureHook failed to delay load rpcrt4.dll.I_RpcExceptionFilter
wine: Call from 0x7b844e40 to unimplemented function rpcrt4.dll.I_RpcExceptionFilter, aborting
wine: Unimplemented function rpcrt4.dll.I_RpcExceptionFilter called at address 0x7b844e40 (thread 0014), starting debugger...
Unhandled exception: unimplemented function rpcrt4.dll.I_RpcExceptionFilter called in 32-bit code (0x7b844eb6).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b844eb6 ESP:0033e3e4 EBP:0033e448 EFLAGS:00200202(   - 00      - - I1)
 EAX:7b82ec99 EBX:7b8b4b88 ECX:00000000 EDX:7ec8b1af
 ESI:7ec8b1af EDI:7ec8b1a4
Stack dump:
0x0033e3e4:  0033e474 00000008 7b8ad3d4 0000000a
0x0033e3f4:  80000100 00000001 00000000 7b844e40
0x0033e404:  00000002 7ec8b1a4 7ec8b1af 00000001
0x0033e414:  7b9397f0 7b8ad3d4 7b8ad319 0033e460
0x0033e424:  7ffd8c00 7ffd8bf8 0033e438 00000000
0x0033e434:  000b000a 00160014 0033e460 7b8b4b88
Backtrace:
=>1 0x7b844eb6 in kernel32 (+0x24eb6) (0x0033e448)
  2 0x7b86617b DelayLoadFailureHook+0x5b() in kernel32 (0x0033e488)
  3 0x7ec7da85 in advapi32 (+0x2da85) (0x0033e4a8)
  4 0x7ec55978 in advapi32 (+0x5978) (0x0033e4c8)
  5 0x7ec7460a in advapi32 (+0x2460a) (0x0033e4f8)
  6 0x7bc649d5 call_exception_handler+0x29() in ntdll (0x0033e528)
  7 0x7bc649a7 EXC_CallHandler+0x1b() in ntdll (0x0033e548)
  8 0x7bc3b41e in ntdll (+0x2b41e) (0x0033e5c8)
  9 0x7bc3b539 __regs_RtlRaiseException+0x29() in ntdll (0x0033e638)
  10 0x7bc77fb3 in ntdll (+0x67fb3) (0x0033e994)
  11 0x7bc3ac56 RtlRaiseException+0x6() in ntdll (0x0033ea0c)
  12 0x7b86617b DelayLoadFailureHook+0x5b() in kernel32 (0x0033ea4c)
  13 0x7ec7da85 in advapi32 (+0x2da85) (0x0033ea6c)
  14 0x7ec55978 in advapi32 (+0x5978) (0x0033ebbc)
  15 0x7ec7775c OpenSCManagerW+0xbc() in advapi32 (0x0033ecac)
  16 0x7ec787cc OpenSCManagerA+0x15c() in advapi32 (0x0033ecdc)
  17 0x00447c5f in _ins5576._mp (+0x47c5f) (0x0033ecf4)
  18 0x00446cf1 in _ins5576._mp (+0x46cf1) (0x0033ed04)
  19 0x0044e57b in _ins5576._mp (+0x4e57b) (0x0033ee20)
  20 0x0044d920 in _ins5576._mp (+0x4d920) (0x0033ef48)
  21 0x0043cbf6 in _ins5576._mp (+0x3cbf6) (0x0033fd88)
  22 0x0040fff8 in _ins5576._mp (+0xfff8) (0x0033fdc0)
  23 0x00410b29 in _ins5576._mp (+0x10b29) (0x0033fdd4)
  24 0x00416912 in _ins5576._mp (+0x16912) (0x0033fdec)
  25 0x00416bff in _ins5576._mp (+0x16bff) (0x0033fe04)
  26 0x00410e60 in _ins5576._mp (+0x10e60) (0x0033fe44)
  27 0x004113ad in _ins5576._mp (+0x113ad) (0x0033fe7c)
  28 0x00476b77 in _ins5576._mp (+0x76b77) (0x0033ff08)
  29 0x7b877937 in kernel32 (+0x57937) (0x0033ffe8)
0x7b844eb6: movl	0xfffffffc(%ebp),%ebx
Modules:
Module	Address			Debug info	Name (90 modules)
PE	  340000-  344000	Deferred        121c
PE	  350000-  360000	Deferred        _wutl951
PE	  3a0000-  3c3000	Deferred        121b
PE	  400000-  48d000	Export          _ins5576._mp
PE	10000000-10014000	Deferred        zdatai51
PE	65f00000-65fc2000	Deferred        ole32
PE	70bd0000-70c35000	Deferred        shlwapi
PE	78000000-78044000	Deferred        msvcrt
ELF	7b800000-7b93c000	Export          kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca6000	Export          ntdll<elf>
  \-PE	7bc10000-7bca6000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e1a1000-7e1b5000	Deferred        midimap<elf>
  \-PE	7e1b0000-7e1b5000	\               midimap
ELF	7e1b5000-7e1db000	Deferred        msacm32<elf>
  \-PE	7e1c0000-7e1db000	\               msacm32
ELF	7e1db000-7e1f2000	Deferred        msacm32<elf>
  \-PE	7e1e0000-7e1f2000	\               msacm32
ELF	7e1f2000-7e2b5000	Deferred        libasound.so.2
ELF	7e2b5000-7e2ea000	Deferred        winealsa<elf>
  \-PE	7e2c0000-7e2ea000	\               winealsa
ELF	7e33f000-7e372000	Deferred        uxtheme<elf>
  \-PE	7e350000-7e372000	\               uxtheme
ELF	7e372000-7e376000	Deferred        libgpg-error.so.0
ELF	7e376000-7e3c3000	Deferred        libgcrypt.so.11
ELF	7e3c3000-7e3d3000	Deferred        libtasn1.so.3
ELF	7e3d3000-7e3e6000	Deferred        libresolv.so.2
ELF	7e3e6000-7e3e9000	Deferred        libkeyutils.so.1
ELF	7e3e9000-7e3f1000	Deferred        libkrb5support.so.0
ELF	7e3f1000-7e423000	Deferred        libcrypt.so.1
ELF	7e423000-7e499000	Deferred        libgnutls.so.13
ELF	7e499000-7e49c000	Deferred        libcom_err.so.2
ELF	7e49c000-7e4bf000	Deferred        libk5crypto.so.3
ELF	7e4bf000-7e54c000	Deferred        libkrb5.so.3
ELF	7e54c000-7e575000	Deferred        libgssapi_krb5.so.2
ELF	7e575000-7e5a8000	Deferred        libcups.so.2
ELF	7e5a8000-7e5b1000	Deferred        libxcursor.so.1
ELF	7e5b1000-7e5b6000	Deferred        libxfixes.so.3
ELF	7e5b6000-7e5b9000	Deferred        libxcomposite.so.1
ELF	7e5b9000-7e5bf000	Deferred        libxrandr.so.2
ELF	7e5bf000-7e5c7000	Deferred        libxrender.so.1
ELF	7e5c7000-7e5cc000	Deferred        libxxf86vm.so.1
ELF	7e5cc000-7e5cf000	Deferred        libxinerama.so.1
ELF	7e5cf000-7e5ef000	Deferred        imm32<elf>
  \-PE	7e5e0000-7e5ef000	\               imm32
ELF	7e5ef000-7e5f4000	Deferred        libxdmcp.so.6
ELF	7e5f4000-7e60c000	Deferred        libxcb.so.1
ELF	7e60c000-7e60f000	Deferred        libxau.so.6
ELF	7e60f000-7e6f6000	Deferred        libx11.so.6
ELF	7e6f6000-7e704000	Deferred        libxext.so.6
ELF	7e704000-7e71c000	Deferred        libice.so.6
ELF	7e71c000-7e724000	Deferred        libsm.so.6
ELF	7e72e000-7e7c6000	Deferred        winex11<elf>
  \-PE	7e740000-7e7c6000	\               winex11
ELF	7e7de000-7e7ff000	Deferred        libexpat.so.1
ELF	7e7ff000-7e829000	Deferred        libfontconfig.so.1
ELF	7e833000-7e848000	Deferred        libz.so.1
ELF	7e848000-7e8b8000	Deferred        libfreetype.so.6
ELF	7e8b8000-7e8ba000	Deferred        libxcb-xlib.so.0
ELF	7e8c2000-7e954000	Deferred        winmm<elf>
  \-PE	7e8d0000-7e954000	\               winmm
ELF	7e954000-7e968000	Deferred        lz32<elf>
  \-PE	7e960000-7e968000	\               lz32
ELF	7e968000-7e981000	Deferred        version<elf>
  \-PE	7e970000-7e981000	\               version
ELF	7e981000-7ea41000	Deferred        comctl32<elf>
  \-PE	7e990000-7ea41000	\               comctl32
ELF	7ea41000-7eb5a000	Deferred        shell32<elf>
  \-PE	7ea50000-7eb5a000	\               shell32
ELF	7eb5a000-7ec05000	Deferred        comdlg32<elf>
  \-PE	7eb60000-7ec05000	\               comdlg32
ELF	7ec05000-7ec3a000	Deferred        winspool<elf>
  \-PE	7ec10000-7ec3a000	\               winspool
ELF	7ec3a000-7ec8c000	Export          advapi32<elf>
  \-PE	7ec50000-7ec8c000	\               advapi32
ELF	7ec8c000-7ed2a000	Deferred        gdi32<elf>
  \-PE	7eca0000-7ed2a000	\               gdi32
ELF	7ed2a000-7ee71000	Deferred        user32<elf>
  \-PE	7ed40000-7ee71000	\               user32
ELF	7ee71000-7ee7c000	Deferred        libnss_files.so.2
ELF	7ee7c000-7ee86000	Deferred        libnss_nis.so.2
ELF	7ee86000-7ee9e000	Deferred        libnsl.so.1
ELF	7ee9e000-7eea7000	Deferred        libnss_compat.so.2
ELF	7efd1000-7eff6000	Deferred        libm.so.6
ELF	b7d27000-b7d2b000	Deferred        libdl.so.2
ELF	b7d2b000-b7e7a000	Deferred        libc.so.6
ELF	b7e7b000-b7e93000	Deferred        libpthread.so.0
ELF	b7e9d000-b7fd3000	Deferred        libwine.so.1
ELF	b7fd5000-b7ff1000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000e 
	0000000f    0
00000011 
	00000012    0
00000013 (D) C:\windows\temp\_ISTMP6.DIR\_INS5576._MP
	00000014    0 <==
Backtrace:
=>1 0x7b844eb6 in kernel32 (+0x24eb6) (0x0033e448)
  2 0x7b86617b DelayLoadFailureHook+0x5b() in kernel32 (0x0033e488)
  3 0x7ec7da85 in advapi32 (+0x2da85) (0x0033e4a8)
  4 0x7ec55978 in advapi32 (+0x5978) (0x0033e4c8)
  5 0x7ec7460a in advapi32 (+0x2460a) (0x0033e4f8)
  6 0x7bc649d5 call_exception_handler+0x29() in ntdll (0x0033e528)
  7 0x7bc649a7 EXC_CallHandler+0x1b() in ntdll (0x0033e548)
  8 0x7bc3b41e in ntdll (+0x2b41e) (0x0033e5c8)
  9 0x7bc3b539 __regs_RtlRaiseException+0x29() in ntdll (0x0033e638)
  10 0x7bc77fb3 in ntdll (+0x67fb3) (0x0033e994)
  11 0x7bc3ac56 RtlRaiseException+0x6() in ntdll (0x0033ea0c)
  12 0x7b86617b DelayLoadFailureHook+0x5b() in kernel32 (0x0033ea4c)
  13 0x7ec7da85 in advapi32 (+0x2da85) (0x0033ea6c)
  14 0x7ec55978 in advapi32 (+0x5978) (0x0033ebbc)
  15 0x7ec7775c OpenSCManagerW+0xbc() in advapi32 (0x0033ecac)
  16 0x7ec787cc OpenSCManagerA+0x15c() in advapi32 (0x0033ecdc)
  17 0x00447c5f in _ins5576._mp (+0x47c5f) (0x0033ecf4)
  18 0x00446cf1 in _ins5576._mp (+0x46cf1) (0x0033ed04)
  19 0x0044e57b in _ins5576._mp (+0x4e57b) (0x0033ee20)
  20 0x0044d920 in _ins5576._mp (+0x4d920) (0x0033ef48)
  21 0x0043cbf6 in _ins5576._mp (+0x3cbf6) (0x0033fd88)
  22 0x0040fff8 in _ins5576._mp (+0xfff8) (0x0033fdc0)
  23 0x00410b29 in _ins5576._mp (+0x10b29) (0x0033fdd4)
  24 0x00416912 in _ins5576._mp (+0x16912) (0x0033fdec)
  25 0x00416bff in _ins5576._mp (+0x16bff) (0x0033fe04)
  26 0x00410e60 in _ins5576._mp (+0x10e60) (0x0033fe44)
  27 0x004113ad in _ins5576._mp (+0x113ad) (0x0033fe7c)
  28 0x00476b77 in _ins5576._mp (+0x76b77) (0x0033ff08)
  29 0x7b877937 in kernel32 (+0x57937) (0x0033ffe8)

```

---

