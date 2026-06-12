---
title: "Dragon Naturally Speaking Error"
date: 2008-07-06
forum: Wine
---

### Post by domi84 on 2008-07-06
I use Ubuntu 8.04 and I have install Dragon Naturally Speaking 9 Preferred with Wine 1.0. Dragon work good, but when I try to correct a word evil dictated by clicking on "Fix text" -> "write letter" I have this error:
[http://img241.imageshack.us/img241/7986/schermatadragonnaturallwp9.png](http://img241.imageshack.us/img241/7986/schermatadragonnaturallwp9.png)
(Sorry, I'm Italian)
and application **freezes**.
I have also prepared a video
[http://it.youtube.com/watch?v=uWA0rxJKUEw](http://it.youtube.com/watch?v=uWA0rxJKUEw)

With Wine 9.95 This is the output of terminal:
```

mimmo@mimmo-laptop:~$ wine /home/mimmo/.wine/drive_c/Programmi/Nuance/NaturallySpeaking9/Program/natspeak.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:reg:RegSetKeySecurity :(0x6c,4,0x7f5a8e00): stub
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
wine: Call from 0x7b844360 to unimplemented function oleacc.dll.GetRoleTextA, aborting
fixme:wininet:InternetGetConnectedState always returning LAN connection.
err:module:import_dll Library REGAPI.dll (which is needed by L"C:\\Programmi\\Nuance\\NaturallySpeaking9\\Program\\wfapi.dll") not found
err:module:import_dll Library WINSTA.dll (which is needed by L"C:\\Programmi\\Nuance\\NaturallySpeaking9\\Program\\wfapi.dll") not found
err:ole:CoGetClassObject class {edb0e980-90bd-11d4-8599-0008c7d3b6f8} not registered
err:ole:CoGetClassObject no class object {edb0e980-90bd-11d4-8599-0008c7d3b6f8} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x7b4caedc,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10062 0x00000000
fixme:shell:SHAppBarMessage msg=0, data={cb=36, hwnd=0x10068, callback=bd0, edge=1, rc=(262272,32)-(2068625260,4304218), lparam=1}: stub
fixme:shell:SHAppBarMessage msg=2, data={cb=36, hwnd=0x10068, callback=41c2a0, edge=1, rc=(0,0)-(1280,28), lparam=7b4cb634}: stub
fixme:shell:SHAppBarMessage msg=3, data={cb=36, hwnd=0x10068, callback=41c2a0, edge=1, rc=(637,383)-(637,411), lparam=7b4cb634}: stub
fixme:shell:SHAppBarMessage msg=9, data={cb=36, hwnd=0x10068, callback=7, edge=2076391295, rc=(2081854344,6238488)-(2068622444,2081854371), lparam=7c21ff50}: stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:htmlhelp:HtmlHelpW HH case HH_CLOSE_ALL not handled.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:msxml:bsc_QueryInterface interface {6d5140c1-7436-11ce-8034-00aa006009fa} not implemented
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msxml:bsc_QueryInterface interface {79eac9e4-baf9-11ce-8c82-00aa004ba90b} not implemented
fixme:msxml:DllCanUnloadNow
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:advapi:SetEntriesInAclA 2 0x7dc40330 (nil) 0x7dc403c4
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:shell:SHAppBarMessage msg=2, data={cb=36, hwnd=0x10068, callback=7c1520e1, edge=1, rc=(0,0)-(1280,28), lparam=ffffffec}: stub
fixme:keyboard:UnregisterHotKey (0x1008e,1): stub
fixme:keyboard:RegisterHotKey (0x1008e,1,0x00000000,106): stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:shell:SHAppBarMessage msg=6, data={cb=36, hwnd=0x10068, callback=7b4cac44, edge=2082505772, rc=(-1,2139548416)-(2081853346,2139548416), lparam=7f870548}: stub
fixme:shell:SHAppBarMessage msg=6, data={cb=36, hwnd=0x10068, callback=7b4cac44, edge=2082505772, rc=(-1,2139548416)-(2081853346,2139548416), lparam=7f870548}: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common ECO_AUTOWORDSELECTION not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOHSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOVSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_NOHIDESEL not implemented yet!
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common ECO_AUTOWORDSELECTION not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOHSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOVSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_NOHIDESEL not implemented yet!
fixme:shell:SHAppBarMessage msg=6, data={cb=36, hwnd=0x10068, callback=7b4cac44, edge=2082505772, rc=(-1,2139548416)-(2081853346,2139548416), lparam=7f870548}: stub
fixme:richedit:IRichEditOle_fnSetHostNames stub 0x7cb131e0 Dragon NaturallySpeaking Documento
fixme:richedit:IRichEditOle_fnGetObject stub 0x7cb131e0
wine: Unhandled page fault on read access to 0x4786a2e8 at address 0x7ecf707d (thread 0009), starting debugger...
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:wave:widRecorder Recovering from XRUN!
Unhandled exception: page fault on read access to 0x4786a2e8 in 32-bit code (0x7ecf707d).
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
EIP:7ecf707d ESP:7f22efc0 EBP:7f22efe8 EFLAGS:00010206( - 00 - RIP1)
EAX:4786a2e8 EBX:7ed1ecec ECX:7ed26c04 EDX:7ed19de0
ESI:7f0ff590 EDI:7f0dd060
Stack dump:
0x7f22efc0: 0000c7bc 0000ffff 00000068 0000005c
0x7f22efd0: 00000380 00000254 7ed19de0 7ed1ecec
0x7f22efe0: 7f0ff590 7f6313c8 7f22f018 7ecce51c
0x7f22eff0: 0000c7bc 0000ffff 00000000 00000000
0x7f22f000: 7f7292a0 7b8b2888 7ecce0db 7ed1ecec
0x7f22f010: 7f0ff590 7f6313c8 7f22f058 7eccf543
Backtrace:
=>1 0x7ecf707d DeleteObject+0x13d() in gdi32 (0x7f22efe8)
2 0x7ecce51c SetDCState+0x44c() in gdi32 (0x7f22f018)
3 0x7eccf543 RestoreDC+0x193() in gdi32 (0x7f22f058)
4 0x7edd6476 GetDCEx+0x236() in user32 (0x7f22f0b8)
5 0x7edd6961 GetDC+0x31() in user32 (0x7f22f0d8)
6 0x7ed9c1fe in user32 (+0x4c1fe) (0x7f22f148)
7 0x7ed9e3b5 in user32 (+0x4e3b5) (0x7f22f1a8)
8 0x7ed9e9b8 in user32 (+0x4e9b8) (0x7f22f3a8)
9 0x7eda2f81 in user32 (+0x52f81) (0x7f22f458)
10 0x7eda4f42 EditWndProcA+0x22() in user32 (0x7f22f468)
11 0x7edfe69a WINPROC_wrapper+0x1a() in user32 (0x7f22f498)
12 0x7edfed7e WINPROC_wrapper+0x6fe() in user32 (0x7f22f4d8)
13 0x7ee04151 in user32 (+0xb4151) (0x7f22f518)
14 0x7edc6f86 DispatchMessageA+0x96() in user32 (0x7f22f558)
0x7ecf707d DeleteObject+0x13d in gdi32: movl 0x0(%eax),%eax
Modules:
Module Address Debug info Name (166 modules)
PE 400000- 859000 Deferred natspeak
PE 10000000-1001c000 Deferred srpump
PE 20000000-20010000 Deferred dd10scrp
PE 21000000-2101a000 Deferred dd10trob
PE 22000000-2218e000 Deferred dd10shrd
PE 24000000-24370000 Deferred dd10rita
PE 25000000-250c1000 Deferred dd10srvr
PE 26340000-263da000 Deferred ipworks6
PE 29000000-29022000 Deferred dd10gldt
PE 2a000000-2a039000 Deferred dd10midl
PE 2b000000-2b02d000 Deferred dd10hook
PE 2b200000-2b21b000 Deferred dd10edit
PE 30000000-304d1000 Deferred mrec
PE 36000000-3615c000 Deferred server
PE 38000000-380d1000 Deferred tokenizer
PE 39800000-399b2000 Deferred gdiplus
PE 40100000-40131000 Deferred dd10axa
PE 41300000-41310000 Deferred chartp
PE 41400000-41412000 Deferred mobile
PE 41500000-41510000 Deferred wavconvert
PE 42000000-4200e000 Deferred wav
PE 42100000-4217d000 Deferred speechtools
PE 42500000-42534000 Deferred winclass
PE 46000000-4602b000 Deferred dd10slme
PE 50200000-502ea000 Deferred dnstk10
PE 52000000-5201c000 Deferred vcmigrat
PE 60600000-60689000 Deferred dgnmycmds
PE 63850000-6387b000 Deferred vcmshl
PE 68000000-68018000 Deferred dgnmycmds_ita
ELF 78149000-78160000 Deferred spoolss
\-PE 78150000-78160000 \ spoolss
ELF 78717000-78730000 Deferred localspl
\-PE 78720000-78730000 \ localspl
ELF 7a7ae000-7a7d0000 Deferred hhctrl
\-PE 7a7b0000-7a7d0000 \ hhctrl
ELF 7b800000-7b92c000 Deferred kernel32
\-PE 7b820000-7b92c000 \ kernel32
ELF 7bc00000-7bca5000 Deferred ntdll
\-PE 7bc10000-7bca5000 \ ntdll
ELF 7bf00000-7bf03000 Deferred
PE 7c140000-7c243000 Deferred mfc71
PE 7c2b0000-7c33f000 Deferred stlport_vc745
PE 7c340000-7c396000 Deferred msvcr71
PE 7c3a0000-7c41b000 Deferred msvcp71
ELF 7c45c000-7c470000 Deferred wtsapi32
\-PE 7c460000-7c470000 \ wtsapi32
ELF 7c470000-7c496000 Deferred netapi32
\-PE 7c480000-7c496000 \ netapi32
ELF 7c496000-7c4aa000 Deferred oleacc
\-PE 7c4a0000-7c4aa000 \ oleacc
ELF 7cc22000-7cc6b000 Deferred riched20
\-PE 7cc30000-7cc6b000 \ riched20
ELF 7cc6b000-7cc7e000 Deferred riched32
\-PE 7cc70000-7cc7e000 \ riched32
ELF 7dd3e000-7dd52000 Deferred icmp
\-PE 7dd40000-7dd52000 \ icmp
ELF 7dd52000-7dd72000 Deferred cabinet
\-PE 7dd60000-7dd72000 \ cabinet
ELF 7dd72000-7dd93000 Deferred mpr
\-PE 7dd80000-7dd93000 \ mpr
ELF 7dd93000-7dde1000 Deferred wininet
\-PE 7dda0000-7dde1000 \ wininet
ELF 7dde1000-7de20000 Deferred urlmon
\-PE 7ddf0000-7de20000 \ urlmon
ELF 7de20000-7dec7000 Deferred msi
\-PE 7de30000-7dec7000 \ msi
ELF 7dec7000-7deda000 Deferred shfolder
\-PE 7ded0000-7deda000 \ shfolder
ELF 7deda000-7deee000 Deferred lz32
\-PE 7dee0000-7deee000 \ lz32
ELF 7deee000-7df07000 Deferred version
\-PE 7def0000-7df07000 \ version
ELF 7df07000-7df26000 Deferred imm32
\-PE 7df10000-7df26000 \ imm32
ELF 7df26000-7df3a000 Deferred midimap
\-PE 7df30000-7df3a000 \ midimap
ELF 7df3a000-7df60000 Deferred msacm32
\-PE 7df40000-7df60000 \ msacm32
ELF 7df60000-7df77000 Deferred msacm32
\-PE 7df70000-7df77000 \ msacm32
ELF 7df77000-7e03a000 Deferred libasound.so.2
ELF 7e03a000-7e070000 Deferred winealsa
\-PE 7e040000-7e070000 \ winealsa
ELF 7e070000-7e0fe000 Deferred winmm
\-PE 7e080000-7e0fe000 \ winmm
ELF 7e0fe000-7e114000 Deferred snmpapi
\-PE 7e100000-7e114000 \ snmpapi
ELF 7e12d000-7e159000 Deferred ws2_32
\-PE 7e130000-7e159000 \ ws2_32
ELF 7e159000-7e1c2000 Deferred msvcrt
\-PE 7e170000-7e1c2000 \ msvcrt
ELF 7e1c2000-7e264000 Deferred oleaut32
\-PE 7e1d0000-7e264000 \ oleaut32
ELF 7e264000-7e268000 Deferred libgpg-error.so.0
ELF 7e268000-7e2b5000 Deferred libgcrypt.so.11
ELF 7e2b5000-7e2c5000 Deferred libtasn1.so.3
ELF 7e2c5000-7e2c8000 Deferred libkeyutils.so.1
ELF 7e2c8000-7e2d0000 Deferred libkrb5support.so.0
ELF 7e2d0000-7e302000 Deferred libcrypt.so.1
ELF 7e302000-7e378000 Deferred libgnutls.so.13
ELF 7e378000-7e39b000 Deferred libk5crypto.so.3
ELF 7e39b000-7e428000 Deferred libkrb5.so.3
ELF 7e428000-7e451000 Deferred libgssapi_krb5.so.2
ELF 7e451000-7e484000 Deferred libcups.so.2
ELF 7e4a8000-7e4bb000 Deferred libresolv.so.2
ELF 7e4bc000-7e4c7000 Deferred libgcc_s.so.1
ELF 7e4cc000-7e4ea000 Deferred iphlpapi
\-PE 7e4d0000-7e4ea000 \ iphlpapi
ELF 7e4ea000-7e54a000 Deferred rpcrt4
\-PE 7e500000-7e54a000 \ rpcrt4
ELF 7e54a000-7e5ee000 Deferred ole32
\-PE 7e560000-7e5ee000 \ ole32
ELF 7e613000-7e649000 Deferred winspool
\-PE 7e620000-7e649000 \ winspool
ELF 7e649000-7e6a2000 Deferred shlwapi
\-PE 7e660000-7e6a2000 \ shlwapi
ELF 7e6a2000-7e7ac000 Deferred shell32
\-PE 7e6b0000-7e7ac000 \ shell32
ELF 7e7ac000-7e855000 Deferred comdlg32
\-PE 7e7b0000-7e855000 \ comdlg32
ELF 7e855000-7e887000 Deferred uxtheme
\-PE 7e860000-7e887000 \ uxtheme
ELF 7e887000-7e946000 Deferred comctl32
\-PE 7e890000-7e946000 \ comctl32
ELF 7e946000-7e94f000 Deferred libxcursor.so.1
ELF 7e94f000-7e954000 Deferred libxfixes.so.3
ELF 7e954000-7e957000 Deferred libxcomposite.so.1
ELF 7e957000-7e95d000 Deferred libxrandr.so.2
ELF 7e95d000-7e965000 Deferred libxrender.so.1
ELF 7e965000-7e968000 Deferred libxinerama.so.1
ELF 7e968000-7e96d000 Deferred libxdmcp.so.6
ELF 7e96d000-7e985000 Deferred libxcb.so.1
ELF 7e985000-7e987000 Deferred libxcb-xlib.so.0
ELF 7e987000-7e98a000 Deferred libxau.so.6
ELF 7e98a000-7ea71000 Deferred libx11.so.6
ELF 7ea71000-7ea7f000 Deferred libxext.so.6
ELF 7ea7f000-7ea84000 Deferred libxxf86vm.so.1
ELF 7ea84000-7ea9c000 Deferred libice.so.6
ELF 7ea9c000-7eaa4000 Deferred libsm.so.6
ELF 7eab0000-7eab3000 Deferred libcom_err.so.2
ELF 7eab5000-7eb46000 Deferred winex11
\-PE 7eac0000-7eb46000 \ winex11
ELF 7eb59000-7eb7a000 Deferred libexpat.so.1
ELF 7eb7a000-7eba4000 Deferred libfontconfig.so.1
ELF 7ebb5000-7ebca000 Deferred libz.so.1
ELF 7ebca000-7ec3a000 Deferred libfreetype.so.6
ELF 7ec4b000-7ec9c000 Deferred advapi32
\-PE 7ec60000-7ec9c000 \ advapi32
ELF 7ec9c000-7ed37000 Export gdi32
\-PE 7ecb0000-7ed37000 \ gdi32
ELF 7ed37000-7ee7d000 Export user32
\-PE 7ed50000-7ee7d000 \ user32
ELF 7ef9d000-7efa8000 Deferred libnss_files.so.2
ELF 7efa8000-7efb2000 Deferred libnss_nis.so.2
ELF 7efb2000-7efca000 Deferred libnsl.so.1
ELF 7efca000-7efef000 Deferred libm.so.6
ELF 7eff7000-7f000000 Deferred libnss_compat.so.2
PE 7fb90000-7fbb4000 Deferred sx96v32
PE 7fee0000-7fef0000 Deferred lhsp01
PE 7fef0000-7ff1f000 Deferred lhcom02w
PE 7ff20000-7ff39000 Deferred pipeline
ELF b7ca1000-b7ca5000 Deferred libdl.so.2
ELF b7ca5000-b7df4000 Deferred libc.so.6
ELF b7df5000-b7e0d000 Deferred libpthread.so.0
ELF b7e1e000-b7f33000 Deferred libwine.so.1
ELF b7f35000-b7f51000 Deferred ld-linux.so.2
Threads:
process tid prio (all id:s are in hex)
00000008 (D) C:\Programmi\Nuance\NaturallySpeaking9\Program\natspeak.exe
0000000f 0
00000047 15
00000046 -1
00000045 0
00000044 -1
00000043 0
00000042 -1
00000041 0
00000040 0
0000003e 0
0000003d 0
0000003c 0
0000003b 0
0000003a 0
00000039 0
00000038 0
00000037 0
00000036 0
00000035 0
00000034 0
00000033 0
00000032 0
00000031 0
00000030 0
0000002f 0
0000002e 0
0000002d 0
0000001f 0
00000009 0 1 0x7ecf707d DeleteObject+0x13d() in gdi32 (0x7f22efe8)
2 0x7ecce51c SetDCState+0x44c() in gdi32 (0x7f22f018)
3 0x7eccf543 RestoreDC+0x193() in gdi32 (0x7f22f058)
4 0x7edd6476 GetDCEx+0x236() in user32 (0x7f22f0b8)
5 0x7edd6961 GetDC+0x31() in user32 (0x7f22f0d8)
6 0x7ed9c1fe in user32 (+0x4c1fe) (0x7f22f148)
7 0x7ed9e3b5 in user32 (+0x4e3b5) (0x7f22f1a8)
8 0x7ed9e9b8 in user32 (+0x4e9b8) (0x7f22f3a8)
9 0x7eda2f81 in user32 (+0x52f81) (0x7f22f458)
10 0x7eda4f42 EditWndProcA+0x22() in user32 (0x7f22f468)
11 0x7edfe69a WINPROC_wrapper+0x1a() in user32 (0x7f22f498)
12 0x7edfed7e WINPROC_wrapper+0x6fe() in user32 (0x7f22f4d8)
13 0x7ee04151 in user32 (+0xb4151) (0x7f22f518)
14 0x7edc6f86 DispatchMessageA+0x96() in user32 (0x7f22f558)
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
fixme:winmm:MMDRV_Exit Closing while ll-driver open
err:syslevel:_CheckNotSysLevel Holding lock 0x7ed26c00 level 3
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7ee43520, level 2): Holding 0x7ed26c00, level 3. Expect deadlock!
mimmo@mimmo-laptop:~$

```
Can you help me?

---

### Post by domi84 on 2008-07-07
:popcorn:

---

### Post by whitworth on 2009-02-02
Get winetricks from kegel.com/wine/winetricks, install dcom98 using:

sh winetricks dcom98

and then try it again.  This fixed the problem for me.

---

### Post by alex.rayu on 2009-02-03
Sounds cool. "Dragon Naturally Speaking Error". Naturally, we speak errors.

---

### Post by jack_spratt on 2010-01-18
That worked for me too - thanks very much!

I just used winetricks as instructed.

---

