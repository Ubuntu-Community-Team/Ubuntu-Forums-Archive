---
title: "powersim studio 7, output from terminal"
date: 2008-04-29
forum: Wine
---

### Post by studo77 on 2008-04-29
Ok, this is a rare program. But would like to run it on linux if at all possible.

Wine is sort of new to me, although i have Oblivion running, and some other programs, that ran without tweaking.

Does it ring a bell in anyones head, it does not in mine, so i do not know what to try. I have changed windows versions and virtual desktop, but get the same result.

Install went flawless. But when running the program, all the menus gets drawn, and then closes, one by one. Which leads me to something like a dll or config-something. 

Trying to run from terminal i get this output:
```
wine PsStudio.exe
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
err:ole:CoGetClassObject class {b543d78d-d140-11d2-b9a8-00104b138c8c} not registered
err:ole:CoGetClassObject no class object {b543d78d-d140-11d2-b9a8-00104b138c8c} could be created for context 0x1
fixme:shdocvw:PersistStreamInit_InitNew (0x1dfec8)
fixme:shdocvw:WebBrowser_QueryInterface (0x1dfec8)->({3af24292-0c96-11ce-a0cf-00aa00600ab8} 0x1dfc1c) interface not supported
fixme:shdocvw:OleObject_Advise (0x1dfec8)->(0x1dfbfc, 0x1dfc48)
fixme:shdocvw:ViewObject_SetAdvise (0x1dfec8)->(1 00000000 0x1dfbfc)
fixme:shdocvw:ViewObject_Draw (0x1dfec8)->(1 -1 (nil) (nil) (nil) 0x368 0x1dfc60 0x1dfc60 (nil) 00000000)
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer
fixme:iphlpapi:NotifyAddrChange (Handle 0x79ddca08, overlapped 0x79ddc9ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x344ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1dff64)->((null) 1 0x153c0e8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1dff64)->((null) 25 2 0x153c0fc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1dff64)->((null) 26 2 0x153c0fc (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1dff64)->(0x153c138)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1dff64)->({000214d1-0000-0000-c000-000000000046} 37 0 0x153c1fc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1dff64)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x153c28c)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:nsChannel_GetOwner default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1dfec8)->(0)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x153e8f8:3; TargetFrameName (nil):-1)
preloader: Warning: failed to reserve range 00000000-00010000
fixme:storage:StgCreateDocfile Transacted mode not implemented.
fixme:storage:StorageImpl_Commit (0x3580b50 0): stub
fixme:shdocvw:PersistStreamInit_InitNew (0x3592088)
fixme:shdocvw:WebBrowser_QueryInterface (0x3592088)->({3af24292-0c96-11ce-a0cf-00aa00600ab8} 0x3591fe4) interface not supported
fixme:shdocvw:OleObject_Advise (0x3592088)->(0x3591fc4, 0x3592010)
fixme:shdocvw:ViewObject_SetAdvise (0x3592088)->(1 00000000 0x3591fc4)
fixme:shdocvw:ViewObject_Draw (0x3592088)->(1 -1 (nil) (nil) (nil) 0x368 0x3592028 0x3592028 (nil) 00000000)
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x3592124)->((null) 1 0x153c8f0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x3592124)->((null) 25 2 0x153c904 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x3592124)->((null) 26 2 0x153c904 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x3592124)->(0x153c940)
fixme:shdocvw:ClOleCommandTarget_Exec (0x3592124)->({000214d1-0000-0000-c000-000000000046} 37 0 0x153ca04 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x3592124)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x153ca94)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:nsChannel_GetOwner default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x3592088)->(0)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x153f100:3; TargetFrameName (nil):-1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1dff64)->((null) 29 2 0x153f9b0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1dff64)
fixme:shdocvw:ClOleCommandTarget_Exec (0x3592124)->((null) 29 2 0x153f9b0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x3592124)
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shdocvw:ClientSite_GetContainer (0x1dff64)->(0x153f83c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1dff64)->(0xf7e7f7c9)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1dff64)->((null) 25 2 0x153f770 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1dff64)->((null) 26 2 0x153f770 (nil))
fixme:mshtml:HTMLDocument_QueryInterface (0x1e1aa0)->({d30c1661-cdaf-11d0-8a3e-00c04fc9e26e} 0x153f46c) interface not supported
wine: Unhandled page fault on read access to 0x6804fa26 at address 0x153a68 (thread 0009), starting debugger...
preloader: Warning: failed to reserve range 00000000-00010000
Unhandled exception: page fault on read access to 0x6804fa26 in 32-bit code (0x00153a68).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00153a68 ESP:0153f2d8 EBP:0153f304 EFLAGS:00010212(   - 00      - RIA1)
 EAX:00153a68 EBX:7ed7570c ECX:00000000 EDX:00153a68
 ESI:0153fbbc EDI:000100d8
Stack dump:
0x0153f2d8:  7ed529ca 000100d8 00000046 00000000
0x0153f2e8:  0153fbbc 7ed529ca 7ed7570c 0153f304
0x0153f2f8:  7ed7570c 0153fbbc 000100d8 0153f344
0x0153f308:  7ed54808 00153a68 000100d8 00000046
0x0153f318:  00000000 0153fbbc 7ece2320 00010034
0x0153f328:  00000047 00000000 0153fbfc 7ed547ab
Backtrace:
=>1 0x00153a68 (0x0153f304)
  2 0x7ed54808 in user32 (+0xb4808) (0x0153f344)
  3 0x7ed588f5 in user32 (+0xb88f5) (0x0153f814)
  4 0x7ed59220 in user32 (+0xb9220) (0x0153f854)
  5 0x7ece0077 DefDlgProcW+0x87() in user32 (0x0153f884)
  6 0x7ed529ca WINPROC_wrapper+0x1a() in user32 (0x0153f8b4)
  7 0x7ed530ae WINPROC_wrapper+0x6fe() in user32 (0x0153f8f4)
  8 0x7ed59431 in user32 (+0xb9431) (0x0153f934)
  9 0x7ed1b2fa in user32 (+0x7b2fa) (0x0153f9a4)
  10 0x7ed1e5ad in user32 (+0x7e5ad) (0x0153fa04)
  11 0x7ed1ea1a SendMessageW+0x4a() in user32 (0x0153fa44)
  12 0x7ed4f171 in user32 (+0xaf171) (0x0153fb74)
  13 0x7ed4e88e SetWindowPos+0x9e() in user32 (0x0153fbe4)
  14 0x7ed485eb DestroyWindow+0x2cb() in user32 (0x0153fc24)
  15 0x7ed485a7 DestroyWindow+0x287() in user32 (0x0153fc64)
  16 0x0044a6ce in psstudio (+0x4a6ce) (0x0153fc8c)
  17 0x004a0323 in psstudio (+0xa0323) (0x0153fde0)
  18 0x005c0ac9 in psstudio (+0x1c0ac9) (0x0153ff08)
  19 0x7b876447 in kernel32 (+0x56447) (0x0153ffe8)
0x00153a68: movb	0x5804fa26,%al
Modules:
Module	Address			Debug info	Name (178 modules)
PE	  400000-  83a000	Export          psstudio
PE	 2560000- 2567000	Deferred        plc4
PE	 28c0000- 2929000	Deferred        xpcom_core
PE	 2930000- 2957000	Deferred        nspr4
PE	 2960000- 2966000	Deferred        plds4
PE	 2b90000- 2b9f000	Deferred        jsd3250
PE	 2ba0000- 2c11000	Deferred        js3250
PE	 2c20000- 2c55000	Deferred        xpc3250
PE	 2c60000- 2c74000	Deferred        xpcom_compat
PE	 2c80000- 2c9a000	Deferred        smime3
PE	 2ca0000- 2cfb000	Deferred        nss3
PE	 2d00000- 2d3f000	Deferred        softokn3
PE	 2d40000- 2d7e000	Deferred        nssckbi
PE	 2d80000- 2d93000	Deferred        jsj3250
PE	 2da0000- 2da6000	Deferred        xpistub
PE	 2db0000- 2de1000	Deferred        freebl3
PE	 2df0000- 2e01000	Deferred        mozz
PE	 2e10000- 2e16000	Deferred        mozctlx
PE	 2e20000- 2e36000	Deferred        gkgfx
PE	 2e40000- 2e60000	Deferred        ssl3
PE	 2e60000- 2edd000	Deferred        necko
PE	 2ee0000- 2eec000	Deferred        xppref32
PE	 2ef0000- 2f1e000	Deferred        i18n
PE	 2f20000- 2f3f000	Deferred        embedcomponents
PE	 2f40000- 2f4f000	Deferred        caps
PE	 2f50000- 2f5c000	Deferred        typeaheadfind
PE	 2f60000- 31f9000	Deferred        gklayout
PE	 3200000- 3227000	Deferred        imglib2
PE	 3230000- 324b000	Deferred        rdf
PE	 3250000- 3288000	Deferred        appcomps
PE	 3290000- 32a0000	Deferred        appshell
PE	 32a0000- 32af000	Deferred        profile
PE	 32b0000- 32b7000	Deferred        xpcom_compat_c
PE	 32c0000- 32c7000	Deferred        sroaming
PE	 32d0000- 32e0000	Deferred        chrome
PE	 32e0000- 3319000	Deferred        gkparser
PE	 3320000- 33de000	Deferred        uconv
PE	 33e0000- 340c000	Deferred        docshell
PE	 3410000- 341a000	Deferred        nsprefm
PE	 3420000- 342e000	Deferred        webbrwsr
PE	 3430000- 3455000	Deferred        gkwidget
PE	 3460000- 3484000	Deferred        gkgfxwin
PE	 3490000- 3498000	Deferred        pipboot
PE	 34a0000- 34ac000	Deferred        oji
PE	 35c0000- 35cd000	Deferred        jar50
PE	 35d0000- 35d7000	Deferred        txmgr
PE	 35e0000- 35fa000	Deferred        mork
PE	10000000-10006000	Deferred        xpcom
PE	28100000-2810f000	Deferred        pserror
PE	28120000-28152000	Deferred        psundomg
PE	281a0000-281db000	Deferred        psressrv
PE	286e0000-286fd000	Deferred        psstdpnt
PE	28720000-2873e000	Deferred        psxppnt
PE	28800000-28829000	Deferred        pswrpmgr
PE	30000000-30370000	Deferred        psengine
PE	30800000-30b35000	Deferred        psengppg
PE	30c00000-30c2c000	Deferred        psstdigt
PE	30c80000-30d50000	Deferred        psfstd
PE	31400000-31671000	Deferred        psafd
PE	31b50000-31de5000	Deferred        psctrls
PE	32f00000-32f36000	Deferred        xpsstudi
PE	5d310000-5d367000	Deferred        keyhelp
ELF	7b800000-7b92c000	Export          kernel32<elf>
  \-PE	7b820000-7b92c000	\               kernel32
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7cc51000-7cc68000	Deferred        spoolss<elf>
  \-PE	7cc60000-7cc68000	\               spoolss
ELF	7cc68000-7cc81000	Deferred        localspl<elf>
  \-PE	7cc70000-7cc81000	\               localspl
ELF	7ccd6000-7ccec000	Deferred        msimtf<elf>
  \-PE	7cce0000-7ccec000	\               msimtf
ELF	7ccec000-7cd12000	Deferred        msacm32<elf>
  \-PE	7ccf0000-7cd12000	\               msacm32
ELF	7cd12000-7cd29000	Deferred        msacm32<elf>
  \-PE	7cd20000-7cd29000	\               msacm32
ELF	7cd29000-7cdec000	Deferred        libasound.so.2
ELF	7cded000-7ce01000	Deferred        midimap<elf>
  \-PE	7cdf0000-7ce01000	\               midimap
ELF	7ce01000-7ce37000	Deferred        winealsa<elf>
  \-PE	7ce10000-7ce37000	\               winealsa
ELF	7ce37000-7cea0000	Deferred        msvcrt<elf>
  \-PE	7ce50000-7cea0000	\               msvcrt
ELF	7cea0000-7cf2e000	Deferred        winmm<elf>
  \-PE	7ceb0000-7cf2e000	\               winmm
ELF	7cf2e000-7cf48000	Deferred        wsock32<elf>
  \-PE	7cf30000-7cf48000	\               wsock32
ELF	7cf48000-7cfde000	Deferred        mshtml<elf>
  \-PE	7cf50000-7cfde000	\               mshtml
ELF	7cfde000-7d019000	Deferred        shdocvw<elf>
  \-PE	7cff0000-7d019000	\               shdocvw
ELF	7d019000-7d03a000	Deferred        mpr<elf>
  \-PE	7d020000-7d03a000	\               mpr
ELF	7d03a000-7d088000	Deferred        wininet<elf>
  \-PE	7d040000-7d088000	\               wininet
ELF	7d088000-7d0c7000	Deferred        urlmon<elf>
  \-PE	7d090000-7d0c7000	\               urlmon
ELF	7d36a000-7d3b3000	Deferred        riched20<elf>
  \-PE	7d370000-7d3b3000	\               riched20
ELF	7e0c4000-7e0c8000	Deferred        libgpg-error.so.0
ELF	7e0c8000-7e115000	Deferred        libgcrypt.so.11
ELF	7e115000-7e125000	Deferred        libtasn1.so.3
ELF	7e125000-7e12d000	Deferred        libkrb5support.so.0
ELF	7e12d000-7e15f000	Deferred        libcrypt.so.1
ELF	7e15f000-7e1d4000	Deferred        libgnutls.so.13
ELF	7e1d4000-7e1f7000	Deferred        libk5crypto.so.3
ELF	7e1f7000-7e284000	Deferred        libkrb5.so.3
ELF	7e284000-7e2ad000	Deferred        libgssapi_krb5.so.2
ELF	7e2ad000-7e2e0000	Deferred        libcups.so.2
ELF	7e319000-7e34b000	Deferred        uxtheme<elf>
  \-PE	7e320000-7e34b000	\               uxtheme
ELF	7e370000-7e379000	Deferred        libxcursor.so.1
ELF	7e379000-7e37e000	Deferred        libxfixes.so.3
ELF	7e37e000-7e381000	Deferred        libxcomposite.so.1
ELF	7e381000-7e387000	Deferred        libxrandr.so.2
ELF	7e387000-7e38f000	Deferred        libxrender.so.1
ELF	7e38f000-7e392000	Deferred        libxinerama.so.1
ELF	7e392000-7e3b0000	Deferred        imm32<elf>
  \-PE	7e3a0000-7e3b0000	\               imm32
ELF	7e3b0000-7e3b5000	Deferred        libxdmcp.so.6
ELF	7e3b5000-7e3cd000	Deferred        libxcb.so.1
ELF	7e3cd000-7e3cf000	Deferred        libxcb-xlib.so.0
ELF	7e3cf000-7e4b6000	Deferred        libx11.so.6
ELF	7e4b6000-7e4c4000	Deferred        libxext.so.6
ELF	7e4c4000-7e4c9000	Deferred        libxxf86vm.so.1
ELF	7e4cc000-7e4cf000	Deferred        libkeyutils.so.1
ELF	7e4d9000-7e4dc000	Deferred        libcom_err.so.2
ELF	7e4de000-7e574000	Deferred        winex11<elf>
  \-PE	7e4f0000-7e574000	\               winex11
ELF	7e629000-7e64a000	Deferred        libexpat.so.1
ELF	7e64a000-7e674000	Deferred        libfontconfig.so.1
ELF	7e674000-7e689000	Deferred        libz.so.1
ELF	7e689000-7e6f9000	Deferred        libfreetype.so.6
ELF	7e70e000-7e73a000	Deferred        ws2_32<elf>
  \-PE	7e720000-7e73a000	\               ws2_32
ELF	7e73a000-7e752000	Deferred        usp10<elf>
  \-PE	7e740000-7e752000	\               usp10
ELF	7e752000-7e76b000	Deferred        version<elf>
  \-PE	7e760000-7e76b000	\               version
ELF	7e76b000-7e80d000	Deferred        oleaut32<elf>
  \-PE	7e780000-7e80d000	\               oleaut32
ELF	7e80d000-7e8b1000	Deferred        ole32<elf>
  \-PE	7e820000-7e8b1000	\               ole32
ELF	7e8b1000-7e8e7000	Deferred        winspool<elf>
  \-PE	7e8c0000-7e8e7000	\               winspool
ELF	7e8e7000-7e940000	Deferred        shlwapi<elf>
  \-PE	7e8f0000-7e940000	\               shlwapi
ELF	7e940000-7ea4c000	Deferred        shell32<elf>
  \-PE	7e950000-7ea4c000	\               shell32
ELF	7ea4c000-7eaf5000	Deferred        comdlg32<elf>
  \-PE	7ea50000-7eaf5000	\               comdlg32
ELF	7eaf5000-7eb08000	Deferred        libresolv.so.2
ELF	7eb09000-7eb1d000	Deferred        lz32<elf>
  \-PE	7eb10000-7eb1d000	\               lz32
ELF	7eb1d000-7eb3b000	Deferred        iphlpapi<elf>
  \-PE	7eb20000-7eb3b000	\               iphlpapi
ELF	7eb3b000-7eb9c000	Deferred        rpcrt4<elf>
  \-PE	7eb50000-7eb9c000	\               rpcrt4
ELF	7eb9c000-7ebee000	Deferred        advapi32<elf>
  \-PE	7ebb0000-7ebee000	\               advapi32
ELF	7ebee000-7ec89000	Deferred        gdi32<elf>
  \-PE	7ec00000-7ec89000	\               gdi32
ELF	7ec89000-7edcf000	Export          user32<elf>
  \-PE	7eca0000-7edcf000	\               user32
ELF	7edcf000-7ee8e000	Deferred        comctl32<elf>
  \-PE	7ede0000-7ee8e000	\               comctl32
ELF	7efae000-7efc6000	Deferred        libnsl.so.1
ELF	7efc6000-7efeb000	Deferred        libm.so.6
ELF	7efeb000-7eff6000	Deferred        libnss_files.so.2
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	f7cd0000-f7cd3000	Deferred        libxau.so.6
ELF	f7cd3000-f7cdc000	Deferred        libnss_compat.so.2
ELF	f7cdd000-f7ce1000	Deferred        libdl.so.2
ELF	f7ce1000-f7e30000	Deferred        libc.so.6
ELF	f7e31000-f7e49000	Deferred        libpthread.so.0
ELF	f7e5e000-f7f94000	Deferred        libwine.so.1
ELF	f7f96000-f7fb5000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Powersim Studio\Bin\PsStudio.exe
	0000001f    0
	0000001e    0
	0000001d    0
	0000001c    0
	0000001b    0
	0000001a    0
	00000019    0
	00000018    0
	00000009    0 <==
0000000c 
	00000014    0
	00000013    0
	0000000e    0
	0000000d    0
0000000f 
	00000012    0
	00000011    0
	00000010    0
00000015 
	00000017    0
	00000016    0
00000020 
	00000025    0
	00000024    0
	00000023    0
	00000022    0
	00000021    0
Backtrace:
=>1 0x00153a68 (0x0153f304)
  2 0x7ed54808 in user32 (+0xb4808) (0x0153f344)
  3 0x7ed588f5 in user32 (+0xb88f5) (0x0153f814)
  4 0x7ed59220 in user32 (+0xb9220) (0x0153f854)
  5 0x7ece0077 DefDlgProcW+0x87() in user32 (0x0153f884)
  6 0x7ed529ca WINPROC_wrapper+0x1a() in user32 (0x0153f8b4)
  7 0x7ed530ae WINPROC_wrapper+0x6fe() in user32 (0x0153f8f4)
  8 0x7ed59431 in user32 (+0xb9431) (0x0153f934)
  9 0x7ed1b2fa in user32 (+0x7b2fa) (0x0153f9a4)
  10 0x7ed1e5ad in user32 (+0x7e5ad) (0x0153fa04)
  11 0x7ed1ea1a SendMessageW+0x4a() in user32 (0x0153fa44)
  12 0x7ed4f171 in user32 (+0xaf171) (0x0153fb74)
  13 0x7ed4e88e SetWindowPos+0x9e() in user32 (0x0153fbe4)
  14 0x7ed485eb DestroyWindow+0x2cb() in user32 (0x0153fc24)
  15 0x7ed485a7 DestroyWindow+0x287() in user32 (0x0153fc64)
  16 0x0044a6ce in psstudio (+0x4a6ce) (0x0153fc8c)
  17 0x004a0323 in psstudio (+0xa0323) (0x0153fde0)
  18 0x005c0ac9 in psstudio (+0x1c0ac9) (0x0153ff08)
  19 0x7b876447 in kernel32 (+0x56447) (0x0153ffe8)

```

---

