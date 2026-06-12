---
title: "How to Find What I Need to Install a Windows Program Using Wine"
date: 2014-08-04
forum: Wine
---

### Post by ajepson5229 on 2014-08-04
Hey everyone, I just recently hooked up a logitech K750 Solar Keyboard to my Computer, and I want to get the Solar App program from logitech so I can check its battery.
The Program can be found here: ([http://www.logitech.com/en-us/support/k750-keyboard?section=downloads&bit=&osid=23&prevOSID=](http://www.logitech.com/en-us/support/k750-keyboard?section=downloads&bit=&osid=23&prevOSID=))

Anyway, I tried to simply run the install to see if I already had everything I needed, but that didn't exactly work properly, and I got the following result when I ran it in terminal:

```
fixme:msg:ChangeWindowMessageFilter c057 00000001
fixme:msg:ChangeWindowMessageFilter 4a 00000001
fixme:msg:ChangeWindowMessageFilter c04c 00000001
fixme:wincodecs:PngDecoder_Block_GetCount stub
fixme:ieframe:PersistStreamInit_InitNew (0x19e900)
fixme:ieframe:navigate_url Unsupported args (Flags {VT_I4: 0}; TargetFrameName {VT_BSTR: (null)})
fixme:dwmapi:DwmIsCompositionEnabled 0x6b238dcc
fixme:iphlpapi:NotifyAddrChange (Handle 0x136e8b0, overlapped 0x136e8bc): stub
fixme:ntdll:server_ioctl_file Unsupported ioctl 9800012c (device=9800 access=0 func=4b method=0)
fixme:winsock:server_ioctl_sock Unsupported ioctl 9800012c (device=9800 access=0 func=4b method=0)
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (_WSAIOW(IOC_VENDOR, 300))
fixme:ntdll:server_ioctl_file Unsupported ioctl 9800012c (device=9800 access=0 func=4b method=0)
fixme:winsock:server_ioctl_sock Unsupported ioctl 9800012c (device=9800 access=0 func=4b method=0)
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (_WSAIOW(IOC_VENDOR, 300))
fixme:imm:ImmReleaseContext (0x100b6, 0x1ac660): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33b024,0x00000000), stub!
fixme:ole:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ieframe:BrowserService_GetTravelLog 0x19f2d0 0x33bc38
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 84 of CGID_ShellDocView
fixme:ieframe:ClOleCommandTarget_QueryStatus (0x19e9b8)->((null) 1 0x33bc30 (nil))
fixme:ieframe:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 37 of CGID_ShellDocView
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 84 of CGID_ShellDocView
fixme:ieframe:ClientSite_GetContainer (0x19e9b8)->(0x33bc1c)
fixme:mshtml:nsChannel_GetContentDisposition (0x1c5c20)->(0x33b360)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0x1c5c20)->(0x33ab80)
fixme:ieframe:ClientSite_GetContainer (0x19e9b8)->(0x33cc8c)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ieframe:DocHostUIHandler_GetDropTarget (0x19e9b8)
fixme:dwmapi:DwmGetCompositionTimingInfo ((nil) 0x33e878)
fixme:advapi:RegisterTraceGuidsW (0x6aee5270, 0x1572e38, {509962e0-406b-46f4-99ba-5a009f8d2225}, 3, 0x1579380, (null), (null), 0x1572e68): stub
fixme:jscript:JScriptProperty_SetProperty Unimplemented property 70000001
fixme:jscript:JScriptProperty_SetProperty Unimplemented property 70000002
err:mshtml:ensure_nsevent_handler GetBody failed: 00000000
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 69 of CGID_Explorer
fixme:ieframe:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 69 of CGID_Explorer
fixme:mshtml:nsChannel_GetContentDispositionHeader (0x2ad7258)->(0x33d604)
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:mshtml:nsChannel_GetContentDispositionHeader (0x2ad7610)->(0x33d604)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0x2ae8b28)->(0x33d604)
err:mshtml:on_stop_nsrequest RemoveRequest failed: 80004005
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x1a03b0)->(0x139a40)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 103 of CGID_ShellDocView
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 2315 of group {de4ba900-59ca-11cf-9592-444553540000}
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 28
wine: Unhandled page fault on read access to 0x00000000 at address 0x4b9745 (thread 0025), starting debugger...

```

And the following detailed error from the program:

```
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x004b9745).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:004b9745 ESP:0033d7c8 EBP:0033d87c EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:00000000 ECX:0033d850 EDX:80004002
 ESI:0033d808 EDI:0033d7bc
Stack dump:
0x0033d7c8:  00000000 ffffffff 2ff88077 00000000
0x0033d7d8:  006e2318 00000000 02b40000 02d0fec8
0x0033d7e8:  02d07570 02d07570 02d07570 006e2318
0x0033d7f8:  00000003 00000000 00000000 00000000
0x0033d808:  00000000 00000000 00000000 00000000
0x0033d818:  0033d868 00000000 00000002 001a0488
000c: sel=0067 base=00000000 limit=00000000 32-bit r-x
Backtrace:
=>0 0x004b9745 in msetup (+0xb9745) (0x0033d87c)
  1 0x004b97dc in msetup (+0xb97db) (0x0033d894)
  2 0x004c3893 in msetup (+0xc3892) (0x0033d8f8)
  3 0x0043d15c in msetup (+0x3d15b) (0x0033d944)
  4 0x004c36f1 in msetup (+0xc36f0) (0x0033d9cc)
  5 0x004c3d58 in msetup (+0xc3d57) (0x0033da14)
  6 0x0044e38f in msetup (+0x4e38e) (0x0033da3c)
  7 0x00461c0b in msetup (+0x61c0a) (0x0033daf4)
  8 0x0045c6c3 in msetup (+0x5c6c2) (0x0033db60)
  9 0x004499eb in msetup (+0x499ea) (0x0033db8c)
  10 0x0044fa65 in msetup (+0x4fa64) (0x0033dbcc)
  11 0x00451e5c in msetup (+0x51e5b) (0x0033dc38)
  12 0x7d3c0bb2 in ieframe (+0x10bb1) (0x0033dc88)
  13 0x7d3d6bee in ieframe (+0x26bed) (0x0033dd18)
  14 0x7cc65b2c in mshtml (+0x95b2b) (0x0033dd88)
  15 0x6a5c318e in xul (+0x98318d) (0x0033de88)
  16 0x6a5c36a9 in xul (+0x9836a8) (0x0033dee8)
  17 0x6a5c6322 in xul (+0x986321) (0x0033df48)
  18 0x6a355e38 in xul (+0x715e37) (0x0033e018)
  19 0x6a2a3052 in xul (+0x663051) (0x0033e0a8)
  20 0x69d90413 in xul (+0x150412) (0x0033e2f8)
  21 0x69d962f0 in xul (+0x1562ef) (0x0033e3b8)
  22 0x69e145e5 in xul (+0x1d45e4) (0x0033e408)
  23 0x69e14357 in xul (+0x1d4356) (0x0033e478)
  24 0x69e13c1e in xul (+0x1d3c1d) (0x0033e4c8)
  25 0x69e13090 in xul (+0x1d308f) (0x0033e518)
  26 0x69e2712a in xul (+0x1e7129) (0x0033e5f8)
  27 0x69daf8d4 in xul (+0x16f8d3) (0x0033e628)
  28 0x6a51abab in xul (+0x8dabaa) (0x0033e698)
  29 0x69cab80f in xul (+0x6b80e) (0x0033e6d8)
  30 0x6afedd67 in xul (+0x13add66) (0x0033e738)
  31 0x6afe92f0 in xul (+0x13a92ef) (0x0033e818)
  32 0x6afec152 in xul (+0x13ac151) (0x0033e858)
  33 0x69c634e4 in xul (+0x234e3) (0x0033e878)
  34 0x6afe5d4d in xul (+0x13a5d4c) (0x0033e8d8)
  35 0x7ebcc626 in user32 (+0x9c625) (0x0033e928)
  36 0x7ebced83 in user32 (+0x9ed82) (0x0033e978)
  37 0x7eb8f7d5 DispatchMessageW+0xb4() in user32 (0x0033ea78)
  38 0x69d80b99 in xul (+0x140b98) (0x0033eb08)
  39 0x6a0e6961 in xul (+0x4a6960) (0x0033eb38)
  40 0x6a0e644f in xul (+0x4a644e) (0x0033eb78)
  41 0x6afe5011 in xul (+0x13a5010) (0x0033ebd8)
  42 0x69cab80f in xul (+0x6b80e) (0x0033ec18)
  43 0x6a0e65a2 in xul (+0x4a65a1) (0x0033ec48)
  44 0x69d80a60 in xul (+0x140a5f) (0x0033ec68)
  45 0x7ebcbeea WINPROC_wrapper+0x19() in user32 (0x0033ec98)
  46 0x7ebcc626 in user32 (+0x9c625) (0x0033ece8)
  47 0x7ebceffb CallWindowProcW+0x5a() in user32 (0x0033ed30)
  48 0x0043f3c0 in msetup (+0x3f3bf) (0x0033eda8)
  49 0x7ebcbeea WINPROC_wrapper+0x19() in user32 (0x0033edd8)
  50 0x7ebcc626 in user32 (+0x9c625) (0x0033ee28)
  51 0x7ebced83 in user32 (+0x9ed82) (0x0033ee78)
  52 0x7eb8f7d5 DispatchMessageW+0xb4() in user32 (0x0033ef78)
  53 0x0044599c in msetup (+0x4599b) (0x7eba18e0)
  54 0xfff0e483 (0x04244c8d)
0x004b9745: movl    0x0(%eax),%eax
Modules:
Module    Address            Debug info    Name (163 modules)
PE      340000-  378000    Deferred        expr_dll
PE      400000-  5a6000    Export          msetup
PE      9f0000-  a26000    Deferred        nspr4
PE      a30000-  a57000    Deferred        smime3
PE    10000000-1000f000    Deferred        setupdll
PE    61700000-6179a000    Deferred        mozsqlite3
PE    61e40000-61e4c000    Deferred        mozalloc
PE    622c0000-622cd000    Deferred        plds4
PE    64f00000-653cf000    Deferred        gkmedias
PE    65fc0000-6605d000    Deferred        mozglue
PE    66840000-66873000    Deferred        ssl3
PE    67400000-674ea000    Deferred        nss3
PE    69300000-69321000    Deferred        nssutil3
PE    69c40000-6b82b000    Export          xul
PE    6ce40000-6ce4d000    Deferred        plc4
PE    70180000-705d3000    Deferred        mozjs
ELF    7ac00000-7ac61000    Deferred        riched20<elf>
  \-PE    7ac10000-7ac61000    \               riched20
ELF    7b800000-7ba5f000    Deferred        kernel32<elf>
  \-PE    7b810000-7ba5f000    \               kernel32
ELF    7bc00000-7bce4000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bce4000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c666000-7c700000    Deferred        jscript<elf>
  \-PE    7c670000-7c700000    \               jscript
ELF    7c817000-7c82c000    Deferred        t2embed<elf>
  \-PE    7c820000-7c82c000    \               t2embed
ELF    7c92c000-7c942000    Deferred        dwmapi<elf>
  \-PE    7c930000-7c942000    \               dwmapi
ELF    7c942000-7c95b000    Deferred        userenv<elf>
  \-PE    7c950000-7c95b000    \               userenv
ELF    7c95b000-7c98e000    Deferred        secur32<elf>
  \-PE    7c960000-7c98e000    \               secur32
ELF    7c98e000-7c9a3000    Deferred        rasdlg<elf>
  \-PE    7c990000-7c9a3000    \               rasdlg
ELF    7c9a3000-7c9be000    Deferred        rasapi32<elf>
  \-PE    7c9b0000-7c9be000    \               rasapi32
ELF    7c9be000-7c9ed000    Deferred        netapi32<elf>
  \-PE    7c9c0000-7c9ed000    \               netapi32
ELF    7c9ed000-7ca13000    Deferred        iphlpapi<elf>
  \-PE    7c9f0000-7ca13000    \               iphlpapi
ELF    7ca13000-7ca2f000    Deferred        wsock32<elf>
  \-PE    7ca20000-7ca2f000    \               wsock32
ELF    7ca2f000-7ca5a000    Deferred        msacm32<elf>
  \-PE    7ca30000-7ca5a000    \               msacm32
ELF    7ca5a000-7cb13000    Deferred        winmm<elf>
  \-PE    7ca60000-7cb13000    \               winmm
ELF    7cb13000-7cbc1000    Deferred        msvcrt<elf>
  \-PE    7cb30000-7cbc1000    \               msvcrt
ELF    7cbc1000-7cd11000    Dwarf           mshtml<elf>
  \-PE    7cbd0000-7cd11000    \               mshtml
ELF    7d3a7000-7d41a000    Dwarf           ieframe<elf>
  \-PE    7d3b0000-7d41a000    \               ieframe
ELF    7d41a000-7d4d9000    Deferred        windowscodecs<elf>
  \-PE    7d430000-7d4d9000    \               windowscodecs
ELF    7d4e6000-7d503000    Deferred        libgcc_s.so.1
ELF    7d51f000-7d563000    Deferred        usp10<elf>
  \-PE    7d530000-7d563000    \               usp10
ELF    7d563000-7d588000    Deferred        imm32<elf>
  \-PE    7d570000-7d588000    \               imm32
ELF    7d588000-7d5b8000    Deferred        p11-kit-trust.so
ELF    7d5b8000-7d5c1000    Deferred        librt.so.1
ELF    7d5c1000-7d5c8000    Deferred        libffi.so.6
ELF    7d5c8000-7d5cd000    Deferred        libgpg-error.so.0
ELF    7d5cd000-7d5e5000    Deferred        libresolv.so.2
ELF    7d5e5000-7d630000    Deferred        libdbus-1.so.3
ELF    7d630000-7d66c000    Deferred        libp11-kit.so.0
ELF    7d66c000-7d680000    Deferred        libtasn1.so.6
ELF    7d680000-7d706000    Deferred        libgcrypt.so.11
ELF    7d706000-7d712000    Deferred        libkrb5support.so.0
ELF    7d712000-7d742000    Deferred        libk5crypto.so.3
ELF    7d742000-7d800000    Deferred        libkrb5.so.3
ELF    7d800000-7d812000    Deferred        libavahi-client.so.3
ELF    7d812000-7d8d8000    Deferred        libgnutls.so.26
ELF    7d8d8000-7d91d000    Deferred        libgssapi_krb5.so.2
ELF    7d91d000-7d98a000    Deferred        libcups.so.2
ELF    7d993000-7d9a6000    Deferred        gnome-keyring-pkcs11.so
ELF    7d9a6000-7d9ac000    Deferred        libxfixes.so.3
ELF    7d9ac000-7d9b7000    Deferred        libxcursor.so.1
ELF    7d9b7000-7d9c8000    Deferred        libxi.so.6
ELF    7d9c8000-7d9cc000    Deferred        libxcomposite.so.1
ELF    7d9cc000-7d9d7000    Deferred        libxrandr.so.2
ELF    7d9d7000-7d9e2000    Deferred        libxrender.so.1
ELF    7d9e2000-7d9e8000    Deferred        libxxf86vm.so.1
ELF    7d9e8000-7d9ec000    Deferred        libxinerama.so.1
ELF    7d9ec000-7d9f3000    Deferred        libxdmcp.so.6
ELF    7d9f3000-7d9f7000    Deferred        libxau.so.6
ELF    7d9f7000-7da19000    Deferred        libxcb.so.1
ELF    7da19000-7db4d000    Deferred        libx11.so.6
ELF    7db4d000-7db60000    Deferred        libxext.so.6
ELF    7db63000-7db67000    Deferred        libkeyutils.so.1
ELF    7db67000-7db6c000    Deferred        libcom_err.so.2
ELF    7db6c000-7db7a000    Deferred        libavahi-common.so.3
ELF    7db7c000-7dc0f000    Deferred        winex11<elf>
  \-PE    7db90000-7dc0f000    \               winex11
ELF    7dc8d000-7dcb6000    Deferred        libexpat.so.1
ELF    7dcb6000-7dcf1000    Deferred        libfontconfig.so.1
ELF    7dcf1000-7dd19000    Deferred        libpng12.so.0
ELF    7dd19000-7ddb9000    Deferred        libfreetype.so.6
ELF    7ddd5000-7de0d000    Deferred        ws2_32<elf>
  \-PE    7dde0000-7de0d000    \               ws2_32
ELF    7de0d000-7de47000    Deferred        oledlg<elf>
  \-PE    7de10000-7de47000    \               oledlg
ELF    7de47000-7de8a000    Deferred        winspool<elf>
  \-PE    7de50000-7de8a000    \               winspool
ELF    7de8a000-7df75000    Deferred        comdlg32<elf>
  \-PE    7de90000-7df75000    \               comdlg32
ELF    7df75000-7df89000    Deferred        msimg32<elf>
  \-PE    7df80000-7df89000    \               msimg32
ELF    7df89000-7dfa1000    Deferred        wtsapi32<elf>
  \-PE    7df90000-7dfa1000    \               wtsapi32
ELF    7dfa1000-7e011000    Deferred        setupapi<elf>
  \-PE    7dfb0000-7e011000    \               setupapi
ELF    7e011000-7e079000    Deferred        dbghelp<elf>
  \-PE    7e020000-7e079000    \               dbghelp
ELF    7e079000-7e0b0000    Deferred        uxtheme<elf>
  \-PE    7e080000-7e0b0000    \               uxtheme
ELF    7e0b0000-7e0d1000    Deferred        cabinet<elf>
  \-PE    7e0c0000-7e0d1000    \               cabinet
ELF    7e0d1000-7e1da000    Deferred        comctl32<elf>
  \-PE    7e0e0000-7e1da000    \               comctl32
ELF    7e1da000-7e202000    Deferred        mpr<elf>
  \-PE    7e1e0000-7e202000    \               mpr
ELF    7e202000-7e21c000    Deferred        libz.so.1
ELF    7e224000-7e238000    Deferred        psapi<elf>
  \-PE    7e230000-7e238000    \               psapi
ELF    7e238000-7e2b5000    Deferred        wininet<elf>
  \-PE    7e240000-7e2b5000    \               wininet
ELF    7e2b5000-7e4ea000    Deferred        shell32<elf>
  \-PE    7e2c0000-7e4ea000    \               shell32
ELF    7e4ea000-7e58d000    Deferred        urlmon<elf>
  \-PE    7e500000-7e58d000    \               urlmon
ELF    7e58d000-7e68a000    Deferred        msi<elf>
  \-PE    7e5a0000-7e68a000    \               msi
ELF    7e68a000-7e70e000    Deferred        rpcrt4<elf>
  \-PE    7e6a0000-7e70e000    \               rpcrt4
ELF    7e70e000-7e850000    Deferred        ole32<elf>
  \-PE    7e720000-7e850000    \               ole32
ELF    7e850000-7e985000    Deferred        oleaut32<elf>
  \-PE    7e870000-7e985000    \               oleaut32
ELF    7e985000-7e9f8000    Deferred        advapi32<elf>
  \-PE    7e990000-7e9f8000    \               advapi32
ELF    7e9f8000-7eb17000    Deferred        gdi32<elf>
  \-PE    7ea00000-7eb17000    \               gdi32
ELF    7eb17000-7ec72000    Dwarf           user32<elf>
  \-PE    7eb30000-7ec72000    \               user32
ELF    7ec72000-7ecec000    Deferred        shlwapi<elf>
  \-PE    7ec80000-7ecec000    \               shlwapi
ELF    7ecec000-7ed78000    Deferred        gdiplus<elf>
  \-PE    7ed00000-7ed78000    \               gdiplus
ELF    7ed78000-7ed85000    Deferred        libnss_files.so.2
ELF    7ed85000-7ed9e000    Deferred        libnsl.so.1
ELF    7ef9e000-7efe4000    Deferred        libm.so.6
ELF    7efe6000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f73d1000-f73dd000    Deferred        libnss_nis.so.2
ELF    f73de000-f73e3000    Deferred        libdl.so.2
ELF    f73e3000-f7592000    Deferred        libc.so.6
ELF    f7593000-f75af000    Deferred        libpthread.so.0
ELF    f75c1000-f75ca000    Deferred        libnss_compat.so.2
ELF    f75cb000-f7781000    Dwarf           libwine.so.1
ELF    f7783000-f77a5000    Deferred        ld-linux.so.2
ELF    f77a5000-f77a6000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001d    0
    0000001c    0
    00000016    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001b    0
    00000018    0
    00000017    0
    00000013    0
00000019 plugplay.exe
    0000001f    0
    0000001e    0
    0000001a    0
00000020 explorer.exe
    00000021    0
00000022 SolarApp_1103_x64.exe
    00000023    0
00000024 Setup.exe
    00000028    0
    00000025    0
00000026 (D) C:\users\aiden\Temp\Logitech\SolarApp_1\MSetup.exe
    00000046    0
    00000043    0
    00000042    0
    00000041    0
    00000040    0
    0000003f   -1
    0000003e    0
    0000003d    0
    0000003c   -1
    0000003b    0
    0000003a    0
    00000039    0
    00000038    0
    00000037    0
    00000036    0
    00000035    0
    00000027    0 <==
0000002b rpcss.exe
    00000034    0
    00000033    0
    00000032    0
    00000031    0
    00000030    0
    0000002f    0
    0000002d    0
    0000002c    0
System information:
    Wine build: wine-1.7.22
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.13.0-32-generic

```
I'm obviously missing some dependencies, and I was wondering if anyone might be able to find out what they are.

Wine and OS Stats:
Ubuntu 14.04 64 bit Version
Wine 1.7.22
Wine set to Windows 8

Thanks!

---

### Post by Mark Phelps on 2014-08-05
From the output you posted, it looks like their app is using IE components to render the window -- and that's bad news since only very old IE versions will work in Wine.

---

### Post by andyfied on 2014-08-08
If it helps, I have one of those too and honestly I've never had the battery run low (I dual boot and sometimes check the power level on Win7). The panel charges even in a room with a single low energy bulb at the light source, though I suppose it might be taking some from my monitor too.

---

