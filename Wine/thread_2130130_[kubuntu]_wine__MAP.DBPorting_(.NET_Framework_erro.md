---
title: "[kubuntu] wine : MAP.DBPorting (.NET Framework error message )"
date: 2013-03-28
forum: Wine
---

### Post by edoo82 on 2013-03-28
Hello,

First of all thanks for your help.

I'm trying to install a windows application (MonAlbumPhoto.exe) which uses .NET Framework (.NF) 2.0 
(it is said in its website) But I didn't know this the first time I tried installing it).

So I tried using wine and it asked me to install mono, I did but still it didn't work.
So I installed .NF directly typing on the terminal:

[COLOR=#000000][FONT=monospace]$ wget [http://winetricks.googlecode.com/svn/trunk/src/winetricks](http://winetricks.googlecode.com/svn/trunk/src/winetricks)
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]$ bash winetricks dotnet20sp2

[/FONT][/COLOR] Now when I execute the .exe file ($wine file.exe) at the end I get the message:
"MAP.DBPorting has found a problem and must be closed".

Some ideas? Thanks for your help.




=============================================================

From the terminal:
morgane@Horus:~$ wine monAlbumPhoto.exe
fixme: Process:SetProcessShutdownParameters (00000380, 00000000): partial stub.
fixme:win: DisableProcessWindowsGhosting : stub
fixme:msg:ChangeWindowMessageFilter c046 00000001
fixme:msg:ChangeWindowMessageFilter c046 00000001
fixme:msg:ChangeWindowMessageFilter c046 00000001
err:richedit:ReadStyleSheet skipping optional destination
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\monAlbumPhoto" 1 4 (nil) (nil) 0x19ae68 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data\\albumphoto" 1 4 (nil) (nil) 0x19ae68 (nil)
fixme:ieframe:taskbar_list_SetProgressValue iface 0x19a558, hwnd 0x1008a, ullCompleted 0, ullTotal 77a9e5b stub!
fixme:sfc:SfcIsFileProtected ((nil), L"C:\\Program Files\\monAlbumPhoto\\unins000.exe") stub
fixme:advapi: DecryptFileA "C:\\users\\morgane\\Temp\\IXP000.TMP\\" 00000000
fixme:advapi: DecryptFileA "C:\\users\\morgane\\Temp\\IXP001.TMP\\" 00000000
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:sxs:cache_QueryAssemblyInfo 0x2031c0, 0x00000002, L"Microsoft.VC80.ATL,type=\"win32\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f978
fixme:sxs:cache_QueryAssemblyInfo 0x2031c0, 0x00000002, L"Microsoft.VC80.CRT,type=\"win32\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f978
fixme:sxs:cache_QueryAssemblyInfo 0x2031c0, 0x00000002, L"Microsoft.VC80.MFC,type=\"win32\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f978
fixme:sxs:cache_QueryAssemblyInfo 0x2031c0, 0x00000002, L"Microsoft.VC80.MFCLOC,type=\"win32\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f978
fixme:sxs:cache_QueryAssemblyInfo 0x2031c0, 0x00000002, L"Microsoft.VC80.OpenMP,type=\"win32\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f978
fixme:sxs:cache_QueryAssemblyInfo 0x2031c0, 0x00000002, L"policy.8.0.Microsoft.VC80.ATL,type=\"win32-policy\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f978
fixme:sxs:cache_QueryAssemblyInfo 0x2031c0, 0x00000002, L"policy.8.0.Microsoft.VC80.CRT,type=\"win32-policy\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f978
fixme:sxs:cache_QueryAssemblyInfo 0x2031c0, 0x00000002, L"policy.8.0.Microsoft.VC80.MFC,type=\"win32-policy\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f978
fixme:sxs:cache_QueryAssemblyInfo 0x2031c0, 0x00000002, L"policy.8.0.Microsoft.VC80.MFCLOC,type=\"win32-policy\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f978
fixme:sxs:cache_QueryAssemblyInfo 0x2031c0, 0x00000002, L"policy.8.0.Microsoft.VC80.OpenMP,type=\"win32-policy\",version=\"8.0.50727.762\",publicKeyToken=\"1fc8b3b9a1e18e3b\",processorArchitecture=\"x86\"", 0x33f978
fixme:msi:ITERATE_RemoveExistingProducts remove L"0"
fixme:ieframe:taskbar_list_SetProgressState iface 0x18bf78, hwnd 0x1008a, flags 0 stub!
fixme:clusapi:GetNodeClusterState ((null),0x33f808) stub!
fixme:advapi: DecryptFileA "c:\\85256443cee8719fa42f67a50fd1\\" 00000000
fixme:setupapi: PSetupGetGlobalFlags stub
fixme:clusapi:GetNodeClusterState ((null),0x33ec04) stub!
fixme:advapi: DecryptFileA "c:\\e995db094d7aaf21b623\\" 00000000
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:wincodecs:JpegDecoder_Frame_GetResolution (0x14663c,0x74dfa8,0x74dfa0): stub
fixme:wincodecs:JpegDecoder_Frame_GetResolution (0x1a004c,0x74dfa8,0x74dfa0): stub
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\monAlbumPhoto\\TempFolder_6.3.3.3\\monAlbumPhoto.exe" 1 4 (nil) (nil) 0x19d018 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data\\albumphoto\\ref\\AppConfigDB.dat" 1 4 (nil) (nil) 0x19d018 (nil)
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\Software\\Microsoft\\Windows NT\\CurrentVersion\\Fonts" 4 4 (nil) (nil) 0x18bf60 (nil)
fixme:advapi:SetNamedSecurityInfoW L"CURRENT_USER\\Software\\monAlbumPhoto" 4 4 (nil) (nil) 0x18bf60 (nil)
fixme:advapi:SetNamedSecurityInfoW L"CURRENT_USER\\Software\\monAlbumPhoto" 4 4 (nil) (nil) 0x18bf60 (nil)
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\AppCompatFlags\\Layers" 4 4 (nil) (nil) 0x18bf60 (nil)
err: ole:CoGetContextToken apartment not initialised
fixme:shell:URL_ParseUrl failed to parse L"PresentationFramework"
Could not parse file "/home/morgane/.local/share/applications/Paint.desktop": Invalid key name: Path[$e]
fixme:imm:ImmDisableIME (-1): stub
fixme:thread:NtQueryInformationThread Cannot get kerneltime or usertime of other threads
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:thread:NtQueryInformationThread info class 9 not supported yet
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime 2.0 Error Reporting"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003e8,(nil),0x0008,0x000000f8,0x3009b09c,0x5dc5d0): stub
err:eventlog:ReportEventW L"map.dbporting.exe"
err:eventlog:ReportEventW L"6.3.3.3"
err:eventlog:ReportEventW L"511ce58d"
err:eventlog:ReportEventW L"kernel32.dll"
err:eventlog:ReportEventW L"5.1.2600.2180"
err:eventlog:ReportEventW L"00000000"
err:eventlog:ReportEventW L"0"
err:eventlog:ReportEventW L"00029d82"
fixme:advapi: DeregisterEventSource (0xcafe4242) stub
err: ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
err: ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
err: ole:CoUninitialize Mismatched CoUninitialize
err ole:CoUninitialize Mismatched CoUninitialize


Unhandled Exception: fixme:shell:URL_ParseUrl failed to parse L"mscorlib.resources"
fixme:shell:URL_ParseUrl failed to parse L"mscorlib.resources"
System.IO.FileNotFoundException: Could not load file or assembly 'PresentationFramework, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies. Exception from HRESULT: 0x80070002
File name: 'PresentationFramework, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35'


WRN: Assembly binding logging is turned OFF.
To enable assembly bind failure logging, set the registry value [HKLM\Software\Microsoft\Fusion!EnableLog] (DWORD) to 1.
Note: There is some performance penalty associated with assembly bind failure logging.
To turn this feature off, remove the registry value [HKLM\Software\Microsoft\Fusion!EnableLog].


wine: Unhandled exception 0xe0434f4d at address 0x7b839d82 (thread 0031), starting debugger...
morgane@Horus:~$ Unhandled exception: 0xe0434f4d in 32-bit code (0x7b839d82).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b839d82 ESP:0033fd18 EBP:0033fd7c EFLAGS:00000283(   - --  I S - - -C)
 EAX:7b826255 EBX:7b895000 ECX:80070002 EDX:0033fd3c
 ESI:e0434f4d EDI:00146088
Stack dump:
0x0033fd18:  0033fdb4 00000004 0033fd2c e0434f4d
0x0033fd28:  00000001 00000000 7b839d82 00000001
0x0033fd38:  80070002 0033fdb4 790c1000 02000038
0x0033fd48:  0033fd58 79e80024 0033fd60 02000038
0x0033fd58:  0033fd64 79e80687 79330ba0 0033fd74
0x0033fd68:  79eda76f 793171fc 7b839d3a e0434f4d
Backtrace:
=>0 0x7b839d82 in kernel32 (+0x29d82) (0x0033fd7c)
  1 0x79eda91c in mscorwks (+0x6a91b) (0x0033fddc)
  2 0x79f39e44 in mscorwks (+0xc9e43) (0x0033fe14)
  3 0x7a0057ac in mscorwks (+0x1957ab) (0x0033fe60)
  4 0x79007c24 in mscoree (+0x7c23) (0x0033fe70)
  5 0x7b859ddc call_process_entry+0xb() in kernel32 (0x0033fe88)
  6 0x7b85b04f in kernel32 (+0x4b04e) (0x0033fec8)
  7 0x7bc71d90 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  8 0x7bc7486d call_thread_func+0x7c() in ntdll (0x0033ffa8)
  9 0x7bc71d6e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  10 0x7bc49f4e call_dll_entry_point+0x61d() in ntdll (0x0033ffe8)
0x7b839d82: subl        $4,%esp
Modules:
Module  Address                 Debug info      Name (67 modules)
PE        400000-  416000       Deferred        map.dbporting
PE      78130000-781cb000       Deferred        msvcr80
PE      79000000-79046000       Export          mscoree
PE      790c0000-79bb7000       Deferred        mscorlib.ni
PE      79e70000-7a400000       Export          mscorwks
ELF     7b800000-7ba29000       Dwarf           kernel32<elf>
  \-PE  7b810000-7ba29000       \               kernel32
ELF     7bc00000-7bcc3000       Dwarf           ntdll<elf>
  \-PE  7bc10000-7bcc3000       \               ntdll
ELF     7bf00000-7bf04000       Deferred        <wine-loader>
ELF     7e0a1000-7e0d5000       Deferred        uxtheme<elf>
  \-PE  7e0b0000-7e0d5000       \               uxtheme
ELF     7e0d5000-7e1ce000       Deferred        comctl32<elf>
  \-PE  7e0e0000-7e1ce000       \               comctl32
ELF     7e1ce000-7e3e1000       Deferred        shell32<elf>
  \-PE  7e1e0000-7e3e1000       \               shell32
ELF     7e40f000-7e485000       Deferred        rpcrt4<elf>
  \-PE  7e420000-7e485000       \               rpcrt4
ELF     7e485000-7e58c000       Deferred        ole32<elf>
  \-PE  7e4a0000-7e58c000       \               ole32
ELF     7e58c000-7e619000       Deferred        msvcrt<elf>
  \-PE  7e5a0000-7e619000       \               msvcrt
ELF     7e619000-7e620000       Deferred        libxfixes.so.3
ELF     7e620000-7e62b000       Deferred        libxcursor.so.1
ELF     7e6be000-7e6e6000       Deferred        libexpat.so.1
ELF     7e6e6000-7e71e000       Deferred        libfontconfig.so.1
ELF     7e71e000-7e72e000       Deferred        libxi.so.6
ELF     7e72e000-7e739000       Deferred        libxrandr.so.2
ELF     7e739000-7e743000       Deferred        libxrender.so.1
ELF     7e743000-7e749000       Deferred        libxxf86vm.so.1
ELF     7e749000-7e74d000       Deferred        libxinerama.so.1
ELF     7e74d000-7e76f000       Deferred        imm32<elf>
  \-PE  7e750000-7e76f000       \               imm32
ELF     7e76f000-7e791000       Deferred        libxcb.so.1
ELF     7e791000-7e7ab000       Deferred        libice.so.6
ELF     7e7ab000-7e8e1000       Deferred        libx11.so.6
ELF     7e8e1000-7e8f3000       Deferred        libxext.so.6
ELF     7e8f3000-7e8fc000       Deferred        libsm.so.6
ELF     7e915000-7e9a9000       Deferred        winex11<elf>
  \-PE  7e920000-7e9a9000       \               winex11
ELF     7e9a9000-7e9c2000       Deferred        libz.so.1
ELF     7e9c2000-7ea5c000       Deferred        libfreetype.so.6
ELF     7ea6a000-7ea6e000       Deferred        libxcomposite.so.1
ELF     7ea6e000-7ea75000       Deferred        libxdmcp.so.6
ELF     7ea75000-7eb32000       Deferred        gdi32<elf>
  \-PE  7ea80000-7eb32000       \               gdi32
ELF     7eb32000-7ec72000       Deferred        user32<elf>
  \-PE  7eb40000-7ec72000       \               user32
ELF     7ec72000-7ecdc000       Deferred        shlwapi<elf>
  \-PE  7ec80000-7ecdc000       \               shlwapi
ELF     7ecdc000-7ed3e000       Deferred        advapi32<elf>
  \-PE  7ecf0000-7ed3e000       \               advapi32
ELF     7ed3e000-7ed58000       Deferred        libnsl.so.1
ELF     7ed58000-7ed61000       Deferred        libnss_compat.so.2
ELF     7ed61000-7ed7a000       Deferred        version<elf>
  \-PE  7ed70000-7ed7a000       \               version
ELF     7efbb000-7efe7000       Deferred        libm.so.6
ELF     7efe7000-7eff4000       Deferred        libnss_files.so.2
ELF     7eff4000-7f000000       Deferred        libnss_nis.so.2
ELF     b73d1000-b73d5000       Deferred        libxau.so.6
ELF     b73d5000-b73db000       Deferred        libuuid.so.1
ELF     b73dc000-b73e1000       Deferred        libdl.so.2
ELF     b73e1000-b758b000       Deferred        libc.so.6
ELF     b758c000-b75a7000       Deferred        libpthread.so.0
ELF     b75c0000-b7702000       Dwarf           libwine.so.1
ELF     b7704000-b7726000       Deferred        ld-linux.so.2
ELF     b7726000-b7727000       Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
        00000028    0
        00000027    0
        00000020    0
        00000017    0
        00000010    0
        0000000f    0
00000012 mscorsvw.exe
        0000001c    0
        0000001b    0
        00000016    0
        00000013    0
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
00000033 (D) C:\Program Files\monAlbumPhoto\ref\MAP.DBPorting.exe
        0000002c    2
        0000002d    0
        00000031    0 <==

---

