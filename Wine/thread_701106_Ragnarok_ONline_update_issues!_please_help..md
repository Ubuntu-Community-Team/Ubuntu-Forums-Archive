---
title: "Ragnarok ONline update issues! please help."
date: 2008-02-19
forum: Wine
---

### Post by Dwiman89 on 2008-02-19
So I just installed Ragnarok. Im having issues updating it. When I run the updater The window goes grey(im guessing a crash) Can someone please help we with this.
I found out how to run the updater in Termninal to get some output and this is what I get;
```
derrick@hamebone:~/.wine/drive_c/Program_Files/Gravity/RO$ wine Ragnarok.exe
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
fixme:shdocvw:PersistStreamInit_InitNew (0x135190)
err:ole:ITypeInfo_fnInvoke did not find member id -518, flags 0x4!
err:ole:ITypeInfo_fnInvoke did not find member id -517, flags 0x4!
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x135190)->(0)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x34e850:3; TargetFrameName 0x34e840:8)
fixme:system:SetProcessDPIAware stub!
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:iphlpapi:NotifyAddrChange (Handle 0x7c8c99c8, overlapped 0x7c8c99ac): stub
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x135228)->((null) 1 0x34dfcc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x135228)->((null) 25 2 0x34dff4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x135228)->((null) 26 2 0x34dff4 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x135228)->(0x34e040)
fixme:shdocvw:ClOleCommandTarget_Exec (0x135228)->({000214d1-0000-0000-c000-000000000046} 37 0 0x34e154 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x1596d0)->(L"" L"" 0 0x34e0d0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x135228)->((null) 29 2 0x34d7d4 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x135228)
fixme:shdocvw:ClientSite_GetContainer (0x135228)->(0x34eeb0)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x135228)->(0xb7df6734)
fixme:shdocvw:ClOleCommandTarget_Exec (0x135228)->((null) 25 2 0x34edc4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x135228)->((null) 26 2 0x34edc4 (nil))
wine: Unhandled page fault on write access to 0x20146537 at address 0x15ba2f (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x20146537 in 32-bit code (0x0015ba2f).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0015ba2f ESP:0034d8d4 EBP:0034d8f0 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00135228 EBX:7cf6787c ECX:00000000 EDX:00000000
 ESI:01146800 EDI:01146800
Stack dump:
0x0034d8d4:  7cf4f1ae 00135228 01146800 00010028
0x0034d8e4:  7cf6787c 00000700 00000700 0034d920
0x0034d8f4:  7cf5744a 00135228 01146800 0034ea5c
0x0034d904:  5f401996 7e81a588 0034da5c 7e801e6f
0x0034d914:  7edbf244 0001002e 00000700 0034d950
0x0034d924:  7ed9a652 0001002e 00000700 00000000
Backtrace:
=>1 0x0015ba2f (0x0034d8f0)
  2 0x7cf5744a in shdocvw (+0x1744a) (0x0034d920)
  3 0x7ed9a652 WINPROC_wrapper+0x1a() in user32 (0x0034d950)
  4 0x7ed9a986 WINPROC_wrapper+0x34e() in user32 (0x0034d990)
  5 0x7ed9bf27 in user32 (+0xabf27) (0x0034f2f0)
  6 0x7ed9ffa9 in user32 (+0xaffa9) (0x0034f330)
  7 0x7ed6d2e4 DispatchMessageA+0xb2() in user32 (0x0034f370)
  8 0x5f401328 in mfc42 (+0x1328) (0x0041f7fc)
  9 0x00000700 (0x0001002e)
  10 0x00000000 (0x00000000)
0x0015ba2f: addl        %esp,0x0(%ebp)
Modules:
Module  Address                 Debug info      Name (159 modules)
PE        350000-  357000       Deferred        plc4
PE        400000-  424000       Deferred        ragnarok
PE        540000-  5a9000       Deferred        xpcom_core
PE        5b0000-  5d7000       Deferred        nspr4
PE        5e0000-  5e6000       Deferred        plds4
PE        5f0000-  5ff000       Deferred        jsd3250
PE        600000-  606000       Deferred        xpistub
PE        7f0000-  861000       Deferred        js3250
PE        870000-  8a5000       Deferred        xpc3250
PE        8b0000-  8e1000       Deferred        freebl3
PE        8f0000-  92f000       Deferred        softokn3
PE        930000-  94a000       Deferred        smime3
PE        950000-  9ab000       Deferred        nss3
PE        9b0000-  9c1000       Deferred        mozz
PE        9d0000-  9e4000       Deferred        xpcom_compat
PE        9f0000-  a2e000       Deferred        nssckbi
PE        a30000-  a50000       Deferred        ssl3
PE        a50000-  a66000       Deferred        gkgfx
PE        a70000-  a76000       Deferred        mozctlx
PE        a80000-  a93000       Deferred        jsj3250
PE        aa0000-  b1d000       Deferred        necko
PE        b20000-  b2c000       Deferred        xppref32
PE        b30000-  b5e000       Deferred        i18n
PE        b60000-  b7f000       Deferred        embedcomponents
PE        b80000-  b8f000       Deferred        caps
PE        b90000-  b9c000       Deferred        typeaheadfind
PE        ba0000-  e39000       Deferred        gklayout
PE        e40000-  e67000       Deferred        imglib2
PE        e70000-  e8b000       Deferred        rdf
PE        e90000-  ec8000       Deferred        appcomps
PE        ed0000-  ee0000       Deferred        appshell
PE        ee0000-  eef000       Deferred        profile
PE        ef0000-  ef7000       Deferred        xpcom_compat_c
PE        f00000-  f07000       Deferred        sroaming
PE        f10000-  f20000       Deferred        chrome
PE        f20000-  f59000       Deferred        gkparser
PE        f60000- 101e000       Deferred        uconv
PE       1020000- 104c000       Deferred        docshell
PE       1160000- 116a000       Deferred        nsprefm
PE       1170000- 117e000       Deferred        webbrwsr
PE       1180000- 11a5000       Deferred        gkwidget
PE       11b0000- 11d4000       Deferred        gkgfxwin
PE       11e0000- 11e8000       Deferred        pipboot
PE       11f0000- 11fc000       Deferred        oji
PE       1200000- 120d000       Deferred        jar50
PE       1210000- 1219000       Deferred        cookie
PE      10000000-10006000       Deferred        xpcom
PE      5f400000-5f4f2000       Export          mfc42
PE      780c0000-78121000       Deferred        msvcp60
ELF     7b800000-7b925000       Deferred        kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7c192000-7c19d000       Deferred        libgcc_s.so.1
ELF     7c4d0000-7c521000       Deferred        libgcrypt.so.11
ELF     7c521000-7c525000       Deferred        libgpg-error.so.0
ELF     7c525000-7c535000       Deferred        libtasn1.so.3
ELF     7c535000-7c53d000       Deferred        libkrb5support.so.0
ELF     7c53d000-7c56b000       Deferred        libcrypt.so.1
ELF     7c56b000-7c5db000       Deferred        libgnutls.so.13
ELF     7c5db000-7c600000       Deferred        libk5crypto.so.3
ELF     7c600000-7c688000       Deferred        libkrb5.so.3
ELF     7c688000-7c6b1000       Deferred        libgssapi_krb5.so.2
ELF     7c6b1000-7c6e6000       Deferred        libcups.so.2
ELF     7c6e6000-7c785000       Deferred        comdlg32<elf>
  \-PE  7c6f0000-7c785000       \               comdlg32
ELF     7c785000-7c7ba000       Deferred        winspool<elf>
  \-PE  7c790000-7c7ba000       \               winspool
ELF     7caed000-7cb01000       Deferred        midimap<elf>
  \-PE  7caf0000-7cb01000       \               midimap
ELF     7cb01000-7cb27000       Deferred        msacm32<elf>
  \-PE  7cb10000-7cb27000       \               msacm32
ELF     7cb27000-7cb3e000       Deferred        msacm32<elf>
  \-PE  7cb30000-7cb3e000       \               msacm32
ELF     7cb3e000-7cb79000       Deferred        wineoss<elf>
  \-PE  7cb40000-7cb79000       \               wineoss
ELF     7cb79000-7cb8d000       Deferred        lz32<elf>
  \-PE  7cb80000-7cb8d000       \               lz32
ELF     7cb8d000-7cba6000       Deferred        version<elf>
  \-PE  7cb90000-7cba6000       \               version
ELF     7cba6000-7cc32000       Deferred        winmm<elf>
  \-PE  7cbb0000-7cc32000       \               winmm
ELF     7cc32000-7cc5d000       Deferred        ws2_32<elf>
  \-PE  7cc40000-7cc5d000       \               ws2_32
ELF     7cc5d000-7cc76000       Deferred        wsock32<elf>
  \-PE  7cc60000-7cc76000       \               wsock32
ELF     7cc76000-7cd01000       Deferred        mshtml<elf>
  \-PE  7cc80000-7cd01000       \               mshtml
ELF     7cd01000-7cd3e000       Deferred        urlmon<elf>
  \-PE  7cd10000-7cd3e000       \               urlmon
ELF     7cd3e000-7cd44000       Deferred        libnss_dns.so.2
ELF     7ce99000-7cf39000       Deferred        oleaut32<elf>
  \-PE  7ceb0000-7cf39000       \               oleaut32
ELF     7cf39000-7cf73000       Export          shdocvw<elf>
  \-PE  7cf40000-7cf73000       \               shdocvw
ELF     7d0ee000-7d101000       Deferred        libresolv.so.2
ELF     7d101000-7d104000       Deferred        libcom_err.so.2
ELF     7d110000-7d12e000       Deferred        iphlpapi<elf>
  \-PE  7d120000-7d12e000       \               iphlpapi
ELF     7d12e000-7d18c000       Deferred        rpcrt4<elf>
  \-PE  7d140000-7d18c000       \               rpcrt4
ELF     7d18c000-7d22b000       Deferred        ole32<elf>
  \-PE  7d1a0000-7d22b000       \               ole32
ELF     7d516000-7d548000       Deferred        uxtheme<elf>
  \-PE  7d520000-7d548000       \               uxtheme
ELF     7d548000-7d551000       Deferred        libxcursor.so.1
ELF     7d551000-7d56e000       Deferred        imm32<elf>
  \-PE  7d560000-7d56e000       \               imm32
ELF     7d56e000-7d573000       Deferred        libxfixes.so.3
ELF     7d573000-7d576000       Deferred        libxcomposite.so.1
ELF     7d576000-7d57e000       Deferred        libxrender.so.1
ELF     7d588000-7d58a000       Deferred        libkeyutils.so.1
ELF     7d58a000-7d58d000       Deferred        libnss_mdns4_minimal.so.2
ELF     7dc28000-7dc2a000       Deferred        libnvidia-tls.so.1
ELF     7dc2a000-7e5c2000       Deferred        libglcore.so.1
ELF     7e5c2000-7e658000       Deferred        libgl.so.1
ELF     7e658000-7e65d000       Deferred        libxdmcp.so.6
ELF     7e65d000-7e660000       Deferred        libxau.so.6
ELF     7e660000-7e751000       Deferred        libx11.so.6
ELF     7e751000-7e75f000       Deferred        libxext.so.6
ELF     7e75f000-7e764000       Deferred        libxxf86vm.so.1
ELF     7e764000-7e77c000       Deferred        libice.so.6
ELF     7e77c000-7e784000       Deferred        libsm.so.6
ELF     7e786000-7e78c000       Deferred        libxrandr.so.2
ELF     7e793000-7e822000       Deferred        winex11<elf>
  \-PE  7e7a0000-7e822000       \               winex11
ELF     7e88f000-7e8af000       Deferred        libexpat.so.1
ELF     7e8af000-7e8da000       Deferred        libfontconfig.so.1
ELF     7e8e9000-7e8fe000       Deferred        libz.so.1
ELF     7e8fe000-7e96e000       Deferred        libfreetype.so.6
ELF     7e97d000-7e9e2000       Deferred        msvcrt<elf>
  \-PE  7e990000-7e9e2000       \               msvcrt
ELF     7e9e2000-7eaa1000       Deferred        comctl32<elf>
  \-PE  7e9f0000-7eaa1000       \               comctl32
ELF     7eaa1000-7eba5000       Deferred        shell32<elf>
  \-PE  7eab0000-7eba5000       \               shell32
ELF     7eba5000-7ebfc000       Deferred        shlwapi<elf>
  \-PE  7ebb0000-7ebfc000       \               shlwapi
ELF     7ebfc000-7ec46000       Deferred        advapi32<elf>
  \-PE  7ec10000-7ec46000       \               advapi32
ELF     7ec46000-7ecdd000       Deferred        gdi32<elf>
  \-PE  7ec60000-7ecdd000       \               gdi32
ELF     7ecdd000-7ee14000       Export          user32<elf>
  \-PE  7ecf0000-7ee14000       \               user32
ELF     7ee14000-7ee35000       Deferred        mpr<elf>
  \-PE  7ee20000-7ee35000       \               mpr
ELF     7ee35000-7ee80000       Deferred        wininet<elf>
  \-PE  7ee40000-7ee80000       \               wininet
ELF     7ef9f000-7efaa000       Deferred        libnss_files.so.2
ELF     7efaa000-7efb4000       Deferred        libnss_nis.so.2
ELF     7efb4000-7efcc000       Deferred        libnsl.so.1
ELF     7efcc000-7eff1000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7c61000-b7c65000       Deferred        libdl.so.2
ELF     b7c65000-b7daf000       Deferred        libc.so.6
ELF     b7daf000-b7dc7000       Deferred        libpthread.so.0
ELF     b7dd6000-b7eea000       Deferred        libwine.so.1
ELF     b7eec000-b7f08000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program_Files\Gravity\RO\Ragnarok.exe
        00000019    0
        00000017    0
        00000016    0
        00000015    0
        00000014    0
        00000013    0
        00000009    0 <==
0000000a 
        0000000b    0
00000010 
        00000012    0
        00000011    0
Backtrace:
=>1 0x0015ba2f (0x0034d8f0)
  2 0x7cf5744a in shdocvw (+0x1744a) (0x0034d920)
  3 0x7ed9a652 WINPROC_wrapper+0x1a() in user32 (0x0034d950)
  4 0x7ed9a986 WINPROC_wrapper+0x34e() in user32 (0x0034d990)
  5 0x7ed9bf27 in user32 (+0xabf27) (0x0034f2f0)
  6 0x7ed9ffa9 in user32 (+0xaffa9) (0x0034f330)
  7 0x7ed6d2e4 DispatchMessageA+0xb2() in user32 (0x0034f370)
  8 0x5f401328 in mfc42 (+0x1328) (0x0041f7fc)
  9 0x00000700 (0x0001002e)
  10 0x00000000 (0x00000000)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x135190)
```

I tried following the wiki here, but I couldn't get a connection to the proxy;
[http://wiki.jswindle.com/index.php/Ragnarok_Online]("http://wiki.jswindle.com/index.php/Ragnarok_Online")

Because I couldn't get a connection to the proxy in the directions, I downloaded from here;
[http://hosted.filefront.com/MerrikFiles]("http://hosted.filefront.com/MerrikFiles")

Im using the NehanRO client. It is private as far as I know, so I don't think there is  an issue with GAMEGUARD. Let me know if I can provide any more information.

Please help... :(

---

### Post by ethanubutnumaker on 2008-02-19
Im having the same frikken issues. can someone help? lets get the gears rolling!

---

### Post by Dwiman89 on 2008-02-21
PLEASE HELP.... :confused:

---

### Post by Dwiman89 on 2008-02-21
bump

---

