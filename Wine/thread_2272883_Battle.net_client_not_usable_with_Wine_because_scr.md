---
title: "Battle.net client not usable with Wine because screen output changes all the time"
date: 2015-04-09
forum: Wine
---

### Post by erik-brangs on 2015-04-09
I'm trying to use the Battle.net app ( [https://appdb.winehq.org/objectManager.php?sClass=version&iId=28855](https://appdb.winehq.org/objectManager.php?sClass=version&iId=28855) ) on Ubuntu 14.10 with wine-staging 1.7.40~ubuntu14.10.1 from the ppa pipelight-stable ( [https://launchpad.net/~pipelight/+archive/ubuntu/stable](https://launchpad.net/~pipelight/+archive/ubuntu/stable) ) and wine1.7, wine1.7-amd64 and wine1.7-i386:i386 (all 1:1.7.38-0ubuntu1). I'm using the open source radeon drivers. AFAIK the propiertary drivers are not usable for my graphics card ( 01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV515/M54 [Mobility Radeon X1400] ) because it's too old.

The post " Graphic Problems with Battle.net Launcher" by Sosinho at [https://appdb.winehq.org/objectManager.php?sClass=version&iId=28855](https://appdb.winehq.org/objectManager.php?sClass=version&iId=28855) describes the same problem that I have. There is a reply at [https://appdb.winehq.org/commentview.php?iAppId=15365&iVersionId=28855&iThreadId=94248](https://appdb.winehq.org/commentview.php?iAppId=15365&iVersionId=28855&iThreadId=94248) which suggests to install the newest Intel drivers. That doesn't sound like it would help in my case because I have an AMD graphics chip.

Terminal output when running wine:
```

fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:exec:SHELL_execute flags ignored: 0x00004100
brangs@brangs-laptop:~$ fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl discovery via DHCP not supported
fixme:wininet:InternetSetOptionW Option 77 STUB
err:wininet:open_http_connection create_netconn failed: 12029
fixme:wininet:InternetSetOptionW Option 77 STUB
err:wininet:open_http_connection create_netconn failed: 12029
fixme:wininet:InternetSetOptionW Option 77 STUB
err:wininet:open_http_connection create_netconn failed: 12029
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:wininet:InternetSetOptionW Option 77 STUB
err:wininet:open_http_connection create_netconn failed: 12029
fixme:wininet:InternetSetOptionW Option 77 STUB
err:wininet:open_http_connection create_netconn failed: 12029
fixme:wininet:InternetSetOptionW Option 77 STUB
err:wininet:open_http_connection create_netconn failed: 12029
fixme:wininet:InternetSetOptionW Option 77 STUB
err:wininet:open_http_connection create_netconn failed: 12029
fixme:wininet:InternetSetOptionW Option 77 STUB
err:wininet:open_http_connection create_netconn failed: 12029
fixme:wininet:InternetSetOptionW Option 77 STUB
err:wininet:open_http_connection create_netconn failed: 12029
fixme:wininet:InternetSetOptionW Option 77 STUB
err:wininet:open_http_connection create_netconn failed: 12029
fixme:wininet:InternetSetOptionW Option 77 STUB
err:wininet:open_http_connection create_netconn failed: 12029
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:wininet:InternetSetOptionW Option 77 STUB
err:wininet:open_http_connection create_netconn failed: 12029
fixme:wbemprox:wbem_locator_ConnectServer unsupported flags
fixme:wbemprox:client_security_SetBlanket 0x7d13b67c, 0x14fb00, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0x7d13b67c
fixme:wininet:InternetSetOptionW Option 77 STUB
err:wininet:open_http_connection create_netconn failed: 12029
fixme:wininet:InternetSetOptionW Option 77 STUB
err:wininet:open_http_connection create_netconn failed: 12029
fixme:wbemprox:client_security_SetBlanket 0x7d13b67c, 0x151690, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0x7d13b67c
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl discovery via DHCP not supported
fixme:wininet:InternetSetOptionW Option 77 STUB
fixme:wbemprox:enum_class_object_Next timeout not supported
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33fd00 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33fba0 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33fa90 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33fba8 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33fd50 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33f028 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33f0b8 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33f678 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33f678 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33f598 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33f634 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33f634 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33f5ac 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33f654 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33f654 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33f5b8 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33f654 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33f5ac 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33f654 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33f640 1 C) semi-stub
fixme:msvcrt:type_info_name_internal_method type_info_node parameter ignored
fixme:file:FindFirstFileExW flags not implemented 0x00000002
fixme:system:SetProcessDPIAware stub!
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33f484 1 C) semi-stub
fixme:winsock:WSALookupServiceBeginW (0x2aae570 0x00000ff0 0x2aae5b8) Stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x2aae448, overlapped 0x1b31e88): stub
fixme:winsock:WSALookupServiceBeginW (0x2aae5b4 0x00000ff0 0x2aae5fc) Stub!
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33ef10 1 C) semi-stub
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl discovery via DHCP not supported
fixme:font:RemoveFontMemResourceEx (0x83bb2161) stub
fixme:font:RemoveFontMemResourceEx (0x83ba8b49) stub
fixme:font:RemoveFontMemResourceEx (0x83846de1) stub
fixme:file:FindFirstFileExW flags not implemented 0x00000002
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_QueryInterface interface {00000126-0000-0000-c000-000000000046} not implemented
fixme:shell:SetCurrentProcessExplicitAppUserModelID L"BlizzardEntertainment.Battlenet.beta": stub
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:msg:ChangeWindowMessageFilterEx 0x2007e c058 1 (nil)
fixme:systray:wine_notify_icon unhandled tray message: 4
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:ole:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme:dwmapi:DwmIsCompositionEnabled 0x33cbc8
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:win:FlashWindowEx 0x33bc2c
fixme:win:FlashWindowEx 0x33d54c
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:wbemprox:enum_class_object_Next timeout not supported
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:wbemprox:enum_class_object_Next timeout not supported
fixme:wbemprox:enum_class_object_Next timeout not supported
fixme:wbemprox:enum_class_object_Next timeout not supported
fixme:wbemprox:enum_class_object_Next timeout not supported
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:file:FindFirstFileExW flags not implemented 0x00000002
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x100b6 0x00000000
fixme:d3d9:D3DPERF_GetStatus (void) : stub
fixme:thread:start_thread Started native thread 00000062
fixme:win:EnumDisplayDevicesW ((null),0,0x33b768,0x00000000), stub!
fixme:d3d9:d3d9_device_CreateTexture Resource sharing not implemented, *shared_handle (nil).
fixme:d3d9:D3DPERF_GetStatus (void) : stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d:state_lastpixel Last Pixel Drawing Disabled, not handled yet
fixme:wbemprox:enum_class_object_Next timeout not supported
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:uniscribe:ScriptShapeOpenType Ranges not supported yet
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:wbemprox:enum_class_object_Next timeout not supported
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:wbemprox:enum_class_object_Next timeout not supported
fixme:wbemprox:enum_class_object_Next timeout not supported
fixme:wbemprox:enum_class_object_Next timeout not supported
fixme:wbemprox:enum_class_object_Next timeout not supported
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x100b6
fixme:iphlpapi:CancelIPChangeNotify (overlapped 0x1b31e88): stub
fixme:font:RemoveFontMemResourceEx (0x8387d7e1) stub
fixme:font:RemoveFontMemResourceEx (0x8386b9c9) stub
fixme:font:RemoveFontMemResourceEx (0x83802261) stub
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
fixme:msvcrt:__clean_type_info_names_internal (0x3d028830) stub
fixme:msvcrt:__clean_type_info_names_internal (0xc39341c) stub
fixme:msvcrt:__clean_type_info_names_internal (0xbd0d81c) stub
fixme:msvcrt:__clean_type_info_names_internal (0xa79341c) stub
fixme:msvcrt:__clean_type_info_names_internal (0x399c79c) stub
fixme:msvcrt:__clean_type_info_names_internal (0x2f653fc) stub
fixme:msvcrt:__clean_type_info_names_internal (0x31c1c1c) stub
fixme:msvcrt:__clean_type_info_names_internal (0x2f573fc) stub
fixme:msvcrt:__clean_type_info_names_internal (0x2f1340c) stub
fixme:msvcrt:__clean_type_info_names_internal (0x2cc6434) stub
fixme:msvcrt:__clean_type_info_names_internal (0x2cb63fc) stub
fixme:msvcrt:__clean_type_info_names_internal (0x20449cc) stub
fixme:msvcrt:__clean_type_info_names_internal (0x6102573c) stub
fixme:msvcrt:__clean_type_info_names_internal (0x145d5bc) stub
fixme:msvcrt:__clean_type_info_names_internal (0x65412a0c) stub
fixme:msvcrt:__clean_type_info_names_internal (0x13f85bc) stub
fixme:msvcrt:__clean_type_info_names_internal (0x662644ac) stub
fixme:msvcrt:__clean_type_info_names_internal (0x3d0a8c) stub
fixme:msvcrt:__clean_type_info_names_internal (0x640a77ec) stub
fixme:msvcrt:__clean_type_info_names_internal (0x10c955c) stub
fixme:msvcrt:__clean_type_info_names_internal (0x6744fe1c) stub
fixme:wbemprox:enum_class_object_Next timeout not supported
fixme:wbemprox:enum_class_object_Next timeout not supported
fixme:wbemprox:enum_class_object_Next timeout not supported
fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform

```

---

