---
title: "Solidworks runs but doesnt not create new file"
date: 2013-02-26
forum: Wine
---

### Post by cqc on 2013-02-26
Hi! i have installed SW2010 on Ubuntu 12.10 using wine 1.5.24. First i coludnt installed sw so i used
```
winetricks vcrun2005 vcrun2008 
```
and installed fine. 
I can run Solidworks but i cant create new file. I run SW from terminal and got this messages.
```
stojakov@stojakov-Inspiron-N5050:~$ '/home/stojakov/.wine/drive_c/Program Files (x86)/SolidWorks/SLDWORKS.exe' 
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
fixme:font:get_outline_text_metrics failed to read style_nameW for font L"femkeklaver"!
fixme:wincodecs:PngDecoder_Block_GetCount 0x11edc80,0x1d3e328: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0x11da3f8,0x1d3e328: stub
fixme:font:get_outline_text_metrics failed to read face_nameW for font L"UKIJ_Mac Basma"!
fixme:font:get_outline_text_metrics failed to read full_nameW for font L"UKIJ_Mac Basma"!
fixme:font:get_outline_text_metrics failed to read face_nameW for font L"UKIJ_Mac Ekran"!
fixme:font:get_outline_text_metrics failed to read full_nameW for font L"UKIJ_Mac Ekran"!
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:toolbar:TOOLBAR_Restore send TBN_GETBUTTONINFO for each button
fixme:wincodecs:PngDecoder_Block_GetCount 0x130c480,0x32e798: stub
fixme:ieframe:PersistStreamInit_InitNew (0x1357490)
fixme:ieframe:navigate_url Unsupported args (Flags 0x32f838:3; TargetFrameName 0x32f848:8)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:iphlpapi:NotifyAddrChange (Handle 0xbf4e8d0, overlapped 0xbf4e8dc): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32c3b8,0x00000000), stub!
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 84 of CGID_ShellDocView
fixme:ieframe:ClOleCommandTarget_QueryStatus (0x1357544)->((null) 1 0x32d22c (nil))
fixme:ieframe:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 37 of CGID_ShellDocView
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 84 of CGID_ShellDocView
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ieframe:ClientSite_GetContainer (0x1357544)->(0x32d24c)
fixme:mshtml:nsChannel_GetContentDisposition (0x169a508)->(0x32c97c)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0x169a508)->(0x32c1a4)
fixme:ieframe:ClientSite_GetContainer (0x1357544)->(0x32e31c)
fixme:imm:ImmReleaseContext (0x10718, 0x1690860): stub
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:client_security_SetBlanket 0xf5f6df90, 0x17a72b8, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xf5f6df90
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:client_security_SetBlanket 0xf5f6df90, 0x17a7258, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xf5f6df90
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 74080 (device=7 access=1 func=20 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4100c (device=4 access=0 func=403 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 41018 (device=4 access=0 func=406 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d0c10 (device=2d access=0 func=304 method=0)
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:msxml:domdoc_setProperty Ignoring property L"NewParser", value -1
fixme:msxml:domdoc_get_parseError (0x1809e94)->(0x32fad0): creating a dummy parseError
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files (x86)\\swvba.tlb" failed with error 2
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files (x86)\\sldworks.tlb" failed with error 2
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:win:EnumDisplayDevicesW ((null),0,0x32ef5c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x32ef5c,0x00000000), stub!
fixme:wbemprox:client_security_SetBlanket 0xf5f6df90, 0xef76598, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xf5f6df90
fixme:wbemprox:client_security_SetBlanket 0xf5f6df90, 0xef76e70, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xf5f6df90
fixme:wbemprox:client_security_SetBlanket 0xf5f6df90, 0xef76688, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xf5f6df90
fixme:win:EnumDisplayDevicesW ((null),0,0x32dd14,0x00000000), stub!
fixme:wbemprox:client_security_SetBlanket 0xf5f6df90, 0xef7c700, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xf5f6df90
fixme:win:EnumDisplayDevicesW ((null),0,0x32dd14,0x00000000), stub!
fixme:wbemprox:client_security_SetBlanket 0xf5f6df90, 0xef77b20, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xf5f6df90
fixme:win:EnumDisplayDevicesW ((null),0,0x32dd14,0x00000000), stub!
fixme:ole:ItemMonikerImpl_Construct lpszDelim is NULL. Using empty string which is possibly wrong.
err:ole:CoGetClassObject class {96a10940-fa33-4105-bc52-53f19ad9a243} not registered
err:ole:CoGetClassObject no class object {96a10940-fa33-4105-bc52-53f19ad9a243} could be created for context 0x1
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x783ccc24): stub
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x32ed54): stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xf20c360,0x32f3b8: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xf20be90,0x32f238: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0x12e9940,0x32f2a8: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0x12e9868,0x32f2f8: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0x12e99a8,0x32f358: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xf20f828,0x32f428: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xf20f828,0x32f448: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0x12e9ee8,0x32ed28: stub
fixme:ieframe:PersistStreamInit_InitNew (0xf213610)
fixme:ieframe:navigate_url Unsupported args (Flags 0x32fad0:3; TargetFrameName 0x32fae0:8)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 84 of CGID_ShellDocView
fixme:ieframe:ClOleCommandTarget_QueryStatus (0xf2136c4)->((null) 1 0x32d4bc (nil))
fixme:ieframe:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 37 of CGID_ShellDocView
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 84 of CGID_ShellDocView
fixme:ieframe:ClientSite_GetContainer (0xf2136c4)->(0x32d4dc)
fixme:mshtml:nsChannel_GetContentDisposition (0xf229698)->(0x32cc0c)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf229698)->(0x32c434)
fixme:ieframe:ClientSite_GetContainer (0xf2136c4)->(0x32e5ac)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
err:ole:CoGetClassObject class {00000514-0000-0010-8000-00aa006d2ea4} not registered
err:ole:CoGetClassObject class {00000514-0000-0010-8000-00aa006d2ea4} not registered
err:ole:create_server class {00000514-0000-0010-8000-00aa006d2ea4} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {00000514-0000-0010-8000-00aa006d2ea4} could be created for context 0x17
err:ole:CoGetClassObject class {00000514-0000-0010-8000-00aa006d2ea4} not registered
err:ole:CoGetClassObject class {00000514-0000-0010-8000-00aa006d2ea4} not registered
err:ole:create_server class {00000514-0000-0010-8000-00aa006d2ea4} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {00000514-0000-0010-8000-00aa006d2ea4} could be created for context 0x17
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x783ccc24): stub
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x32eca4): stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xf2b1ee8,0x32ec68: stub
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x783ccc24): stub
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=0x32eca4): stub
fixme:ieframe:DocHostUIHandler_GetDropTarget (0x1357544)
fixme:ieframe:DocHostUIHandler_GetDropTarget (0xf2136c4)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2d22d0)->(0x32e228)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentDispositionHeader (0x15d1d20)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0x15d2808)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0x15d3138)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0x15d3228)->(0x32e228)
compilation error: element stylesheet
xsltParseStylesheetProcess : document is not a stylesheet
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2d78c0)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2d8338)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2c0178)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2c0cd8)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0x15cfda0)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2bb668)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2b5a10)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2b64c0)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2b65b8)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2da148)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2daae8)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2db460)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2dbb70)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2dc698)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2dd028)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2ddc28)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2bac90)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2df5d8)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2dffc8)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2e0c70)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2d93b8)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2e2768)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2e33c8)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2e3d88)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf2e4810)->(0x32e228)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x13a8260)->(0x1bf8d0)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0xf215a38)->(0x1bf8d0)
fixme:vbscript:VBScript_QueryInterface (0x17ce000)->({4954e0d0-fbc7-11d1-8410-006008c3fbfc} 0x32f48c)
fixme:vbscript:VBScript_QueryInterface (0x17ce000)->({4954e0d0-fbc7-11d1-8410-006008c3fbfc} 0x32f48c)
fixme:vbscript:VBScript_QueryInterface (0x17ce000)->({4954e0d0-fbc7-11d1-8410-006008c3fbfc} 0x32f48c)
fixme:vbscript:parse_script parser failed around L"//$c25 PEL 02/20/08 Update to .17.\r\n' $c24  JPS 11/17/07 Added call to new RunInternalCommand function.\r\n' $c23  JPS 03/05/07 Updating to SwHtmlControl.SwHtmlInterface.18 for SW2008 Beta1. Replaced all individual CreateObject calls with getSWHtmlControl().\r\n' $c22  JPS 01/15/07 Added GetSWVersi"...
fixme:jscript:JScriptProperty_SetProperty Unimplemented property 70000001
fixme:jscript:JScriptProperty_SetProperty Unimplemented property 70000002
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 69 of CGID_Explorer
fixme:ieframe:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 69 of CGID_Explorer
fixme:mshtml:find_event_target for L"window" not supported
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0xf215a38)->(0x1bf8d0)
fixme:vbscript:VBScript_QueryInterface (0xf24c420)->({4954e0d0-fbc7-11d1-8410-006008c3fbfc} 0x32f48c)
fixme:vbscript:VBScript_QueryInterface (0xf24c420)->({4954e0d0-fbc7-11d1-8410-006008c3fbfc} 0x32f48c)
fixme:vbscript:VBScript_QueryInterface (0xf24c420)->({4954e0d0-fbc7-11d1-8410-006008c3fbfc} 0x32f48c)
fixme:vbscript:parse_script parser failed around L"//$c25 PEL 02/20/08 Update to .17.\r\n' $c24  JPS 11/17/07 Added call to new RunInternalCommand function.\r\n' $c23  JPS 03/05/07 Updating to SwHtmlControl.SwHtmlInterface.18 for SW2008 Beta1. Replaced all individual CreateObject calls with getSWHtmlControl().\r\n' $c22  JPS 01/15/07 Added GetSWVersi"...
fixme:jscript:JScriptProperty_SetProperty Unimplemented property 70000001
fixme:jscript:JScriptProperty_SetProperty Unimplemented property 70000002
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 69 of CGID_Explorer
fixme:ieframe:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 69 of CGID_Explorer
fixme:mshtml:find_event_target for L"window" not supported
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf6a7580)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf6aaff8)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf6ab638)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf6abc68)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf6ac208)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf6ac8a0)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf6ace50)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf6ad488)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf6adc20)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf65ffa0)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf660718)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf660788)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf6614e8)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf661b28)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf662018)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf662b20)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf65f9a8)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf65d7f8)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf65e000)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf660b68)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf65efc8)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf65f2f0)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf65c0d0)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf65c8f0)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf65d198)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf662e80)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf6c5300)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf6c5b78)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf6c6258)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf6c62d8)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf717220)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf725cf0)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf730a80)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf731840)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf738d08)->(0x32e228)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf787170)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf78b530)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf78e0c8)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf78ebe8)->(0x32e1e8)
fixme:mshtml:nsChannel_GetContentDispositionHeader (0xf78f2f8)->(0x32e1e8)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 103 of CGID_ShellDocView
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 2315 of group {de4ba900-59ca-11cf-9592-444553540000}
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 103 of CGID_ShellDocView
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 2315 of group {de4ba900-59ca-11cf-9592-444553540000}
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0x13a8260)->(0x1bf8d0)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0xf215a38)->(0x1bf8d0)
fixme:vbscript:DispatchEx_Invoke (0xf78df20)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0x16ca008)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0xf215a38)->(0x1bf8d0)
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0xf215a38)->(0x1bf8d0)
fixme:vbscript:DispatchEx_Invoke (0xf78df20)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0x16ca008)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0xf78df20)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0x16ca008)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0xf78df20)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0x16ca008)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0xf78df20)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0x16ca008)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0xf78df20)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0x16ca008)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:mshtml:OleInPlaceActiveObject_TranslateAccelerator (0xf215a38)->(0x1bf8d0)
fixme:vbscript:DispatchEx_Invoke (0xf78df20)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0x16ca008)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0xf78df20)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0x16ca008)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0xf78df20)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0x16ca008)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:wincodecs:PngDecoder_Block_GetCount 0xf6e2748,0x32f688: stub
fixme:vbscript:DispatchEx_Invoke (0xf78df20)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0x16ca008)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0xf78df20)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0x16ca008)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0xf78df20)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0x16ca008)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0xf78df20)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0x16ca008)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0xf78df20)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0x16ca008)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0xf78df20)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0x16ca008)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0xf78df20)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0x16ca008)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:wincodecs:PngDecoder_Block_GetCount 0x15d77f0,0x32f6d8: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0x15d77f0,0x32f6b8: stub
fixme:vbscript:DispatchEx_Invoke (0xf78df20)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:vbscript:DispatchEx_Invoke (0x16ca008)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f9e0 0x32f9d0 0x32f9b0 (nil))
fixme:wincodecs:PngDecoder_Block_GetCount 0xf642260,0x32ec88: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xf642260,0x32ec68: stub
fixme:wincodecs:PngDecoder_Block_GetCount 0xf642260,0x32ec68: stub
fixme:vbscript:DispatchEx_Invoke (0xf78df20)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f370 0x32f360 0x32f340 (nil))
fixme:vbscript:DispatchEx_Invoke (0x16ca008)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f370 0x32f360 0x32f340 (nil))
fixme:wincodecs:PngDecoder_Block_GetCount 0x17d9318,0x32ee48: stub
fixme:vbscript:DispatchEx_Invoke (0xf78df20)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f370 0x32f360 0x32f340 (nil))
fixme:vbscript:DispatchEx_Invoke (0x16ca008)->(0 {00000000-0000-0000-0000-000000000000} 0 1 0x32f370 0x32f360 0x32f340 (nil))
fixme:storage:Storage_ConstructTransacted Unimplemented flags 210040
fixme:wincodecs:PngDecoder_Block_GetCount 0xf63f008,0x32e2b8: stub
err:dib:init_opengl glAccum not found in libOSMesa.so.6, disabling.
err:dbghelp:pe_load_dbg_file Couldn't find .DBG file "Vbe6.dbg" ("\x14")
err:dbghelp:pe_load_dbg_file Couldn't find .DBG file "vbe6intl.dbg" ("\x14")
stojakov@stojakov-Inspiron-N5050:~$ fixme:ole:CoCreateInstance no instance created for interface {00000000-0000-0000-c000-000000000046} of class {dd455e00-18bc-11da-8cd6-0800200c9a66}, hres is 0x80040111

```
I dont know what to do and i really need this program to work.

---

### Post by Mark Phelps on 2013-02-27
From the link on the WineHQ site, solidworks 2010 is rated GARBAGE -- meaning that's it's not going to work:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=318]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=318")

---

### Post by cqc on 2013-02-27
> **Mark Phelps said:**
> From the link on the WineHQ site, solidworks 2010 is rated GARBAGE -- meaning that's it's not going to work:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=318]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=318")
It is rated gold. Check again Solidworks 2010. Anyway i fixed this problem with solution found here[http://www.codeweavers.com/compatibility/browse/name/?app_id=8103;tips=1]("http://www.codeweavers.com/compatibility/browse/name/?app_id=8103;tips=1") Now im having another problem. When i create new file i can see menus and stuff but i cant do the drawing. Area where i need to do that is not shown. In SW options there is performance menu where i can see that use Software OpenGL is checked and can not be changed. Maybe it cant use drivers properly. I use Intel hd 3000 and it works good. I really need this program to work please help
thanks

---

### Post by Mark Phelps on 2013-03-01
> **cqc said:**
> It is rated gold. Check again Solidworks 2010. 

Sorry ... my mistake.  Its 2012 that is rated Garbage, not 2010.

However ... reading the following from the so-called GOLD rating: 

> What does not
- unstable: application is quite crash prone
- section headings in the property manager are overdrawn by their background every time the right hand graphics area is updated, see screenshot.. - actually happens incrementally from left to ride side like a download bar
- right side task pane has multiple issues: text drawing glitches, internet resources non-working
- hole wizard button gives 'Out of memory or other error trying to initialize data source from standards file "C:\users\empee584\Application Data\SolidWorks\SolidWorks 2010\HoleWizardFavorites.mdb"' because that file is indeed missing for whatever reason (standard installation) 

Would make me rate it as Silver, at best -- and since the claim is that it is crash-prone, which prevents it from being really useful, I would further argue that it deserves no better than Bronze.

ANYTHING you run from MS Windows that really need to work needs to be rated a genuine gold -- meaning -- there are no real problems with the app and it does nearly everything that it does in Windows.

Sorry, but if you really need this to work, you need to consider running Windows in a VM.

---

