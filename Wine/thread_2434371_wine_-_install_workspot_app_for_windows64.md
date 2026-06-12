---
title: "wine - install workspot app for windows64"
date: 2020-01-04
forum: Wine
---

### Post by marchello_lippi2 on 2020-01-04
Hi all, 
I'm trying to install workspot app for windows64 using wine. 
It's for my work. 
They encourage me to switch to windows instead ](*,)

First of all, my wine version: 
```
[FONT=monospace][COLOR=#000000]$ wine --version[/COLOR]
wine-4.0.3
[/FONT]
```

My ubuntu version:
```
[FONT=monospace][COLOR=#000000]$ lsb_release -a[/COLOR]
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:        18.04
Codename:       bionic
[/FONT]
```

What happens when I run installer: 
```
[FONT=monospace][COLOR=#000000]$ wine msiexec /i /home/user1/Downloads/WorkspotClientSetup64.msi        [/COLOR]
0009:fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
0009:err:msi:ITERATE_Actions Execution halted, action L"LaunchConditions" returned 1603
[/FONT]
```

Also application itself shows error: 
> You need to run Windows Update on this system before you can install Workspot Client. See [http://workspot.zendesk.com/hc/en-us/articles/209993933](http://workspot.zendesk.com/hc/en-us/articles/209993933) for help.

What I understood from the article above, it requires (1) [COLOR=#444444][FONT=Helvetica]Windows 7 SP1 and (2) [/FONT][/COLOR][COLOR=#444444][FONT=Helvetica]RDP 8.1, I stuck on the (1) first one.

Upd: I switched wine to windows 10 and managed to install it. But it crashes after I enter my username in the program. See more details below. 
[/FONT][/COLOR]```
$ env WINEPREFIX="/home/user1/.wine" wine C:\\Program\ Files\\Workspot\\Workspot\ Client\\WorkspotClient.exe
002b:err:mscoree:FixupVTableEntry unsupported vtable fixup flags 0
002b:fixme:file:FindFirstFileExW flags not implemented 0x00000002
002b:fixme:file:FindFirstFileExW flags not implemented 0x00000002
002b:fixme:ver:GetFileVersionInfoSizeExW flags 0x2 ignored
002b:fixme:ver:GetFileVersionInfoExW flags 0x2 ignored
002b:fixme:seh:RtlCaptureStackBackTrace (0, 62, 0x7226518, (nil)) stub!
002b:fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
002b:fixme:ntdll:EtwEventRegister ({d2d578d9-2936-45b6-a09f-30e32715f42d}, 0x2251140, 0x6732bd8, 0x678bd08) stub.
002b:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x23e8f0, (nil) 0x23e8ec
002b:fixme:nls:get_dummy_preferred_ui_language (0x38 0x23e8f0 (nil) 0x23e8ec) returning a dummy value (current locale)
002b:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x23e8f0, 0x7235c60 0x23e8ec
002b:fixme:nls:get_dummy_preferred_ui_language (0x38 0x23e8f0 0x7235c60 0x23e8ec) returning a dummy value (current locale)
0035:fixme:dwrite:get_name_record_codepage encoding 20 not handled, platform 1.
0035:fixme:dwrite:get_name_record_codepage encoding 20 not handled, platform 1.
0035:fixme:winsock:WSALookupServiceBeginW (0x979f690 0x00000ff0 0x979f708) Stub!
[0104/195452.062:ERROR:network_change_notifier_win.cc(157)] WSALookupServiceBegin failed with: 0
0035:fixme:iphlpapi:NotifyAddrChange (Handle 0x979f910, overlapped 0x7254730): stub
003a:fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10066 0x00000001
0035:fixme:win:RegisterDeviceNotificationW (hwnd=0x1006e, filter=0x979f6b8,flags=0x00000000) returns a fake device notification handle!
0035:fixme:win:GetDisplayConfigBufferSizes (0x2 0x979f354 0x979f350): stub
0035:fixme:combase:RoActivateInstance (0x9830700, 0x979f108): semi-stub
0035:fixme:combase:RoGetActivationFactory (L"Windows.UI.ViewManagement.UISettings", {00000035-0000-0000-c000-000000000046}, 0x979f000): semi-stub
0035:err:combase:RoGetActivationFactory Failed to find library for L"Windows.UI.ViewManagement.UISettings"
0035:fixme:win:GetDisplayConfigBufferSizes (0x2 0x979f354 0x979f350): stub
0034:fixme:file:FindFirstFileExW flags not implemented 0x00000002
0034:fixme:file:FindFirstFileExW flags not implemented 0x00000002
002f:fixme:wlanapi:WlanEnumInterfaces (0x1, (nil), 0x913ed40) semi-stub
002b:fixme:netprofm:connection_point_Advise 0x983dc50, 0x6f62cc0, 0x6f61db8 - semi-stub
002b:fixme:netprofm:ConnectionPointContainer_FindConnectionPoint interface {dcb00004-570f-4a9b-8d69-199fdba5723b} not implemented
002b:fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
002b:fixme:toolhelp:Heap32ListFirst : stub
0051:fixme:wlanapi:WlanGetAvailableNetworkList (0x1, {00000000-0000-0000-0000-000000000000}, 0x0, (nil), 0xc33b8b0) stub
0042:err:mscoree:FixupVTableEntry unsupported vtable fixup flags 0
0042:fixme:file:FindFirstFileExW flags not implemented 0x00000002
0042:fixme:seh:RtlCaptureStackBackTrace (0, 62, 0x7226cc8, (nil)) stub!
0042:fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
0042:fixme:ntdll:EtwEventRegister ({d2d578d9-2936-45b6-a09f-30e32715f42d}, 0x2251140, 0x6732bd8, 0x678bd08) stub.
0042:fixme:ntdll:NtQueryInformationToken QueryInformationToken( ..., TokenElevation, ...) semi-stub
0042:fixme:win:EnumDisplayDevicesW ((null),0,0x23e130,0x00000000), stub!
0056:fixme:time:QueryThreadCycleTime (0x114,0x907fb90): stub!
0042:fixme:win:EnumDisplayDevicesW ((null),0,0x23d070,0x00000000), stub!
002b:fixme:nls:get_dummy_preferred_ui_language (0x8 0x23ecc0 0x23ec10 0x23ecc8) returning a dummy value (current locale)
0042:fixme:d3d11:d3d11_device_CheckFeatureSupport Returning fake Options support data.
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 85, format_support 0xcd114 partial-stub!
0042:fixme:d3d:wined3d_check_device_multisample_type multisample_type 32 not handled yet.
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 115, format_support 0xcd11c partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 86, format_support 0xcd124 partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 88, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 88, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 87, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 87, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 87, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 87, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 91, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 91, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 65, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 28, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 28, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 28, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 11, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 28, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 28, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 28, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 24, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 11, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 55, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 45, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 45, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 61, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 56, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 49, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 35, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 54, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 41, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 34, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 16, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 64, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 62, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 59, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 57, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 43, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 42, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 52, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 50, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 38, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 36, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 18, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 17, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 2, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 2, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 2, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 2, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 2, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 10, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 10, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 10, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 10, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 10, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 45, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 26, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 29, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 29, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 40, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 20, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 45, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 28, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 28, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 3, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 3, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 12, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 12, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 30, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 30, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 4, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 4, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 14, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 14, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 32, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 32, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 25, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 56, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 35, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 28, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 29, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 28, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 29, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 28, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 29, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 87, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xd7818, format 87, format_support 0x23daac partial-stub!
0042:fixme:d3d11:d3d11_immediate_context_Flush iface 0xd7848 stub!
002b:fixme:font:get_outline_text_metrics failed to read full_nameW for font L"Ani"!
0042:fixme:mfplat:MFStartup (131184, 1): stub
[0104/195452.807:ERROR:mf_helpers.cc(14)] Error in dxva_video_decode_accelerator_win.cc on line 373
002b:fixme:win:EnumDisplayDevicesW ((null),0,0x23de30,0x00000000), stub!
002b:fixme:win:EnumDisplayDevicesW ((null),0,0x23da70,0x00000000), stub!
002b:fixme:dwmapi:DwmExtendFrameIntoClientArea (0x2009e, 0x23f130) stub
0064:fixme:file:FindFirstFileExW flags not implemented 0x00000002
002b:fixme:font:get_nearest_charset TCI failing on 20000000
002b:fixme:font:get_nearest_charset returning DEFAULT_CHARSET face->fs.fsCsb[0] = 20000000 file = L"/usr/share/fonts/truetype/fonts-gujr-extra/aakar-medium.ttf"
002b:fixme:msg:ChangeWindowMessageFilterEx (nil) c05f 1 (nil)
002b:err:ole:CoGetClassObject class {8b918b82-7985-4c24-89df-c33ad2bbfbcd} not registered
002b:err:ole:create_server class {8b918b82-7985-4c24-89df-c33ad2bbfbcd} not registered
002b:fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
002b:err:ole:CoGetClassObject no class object {8b918b82-7985-4c24-89df-c33ad2bbfbcd} could be created for context 0x15
002b:fixme:dwmapi:DwmIsCompositionEnabled 0x23ba40
0067:err:mscoree:FixupVTableEntry unsupported vtable fixup flags 0
0067:fixme:file:FindFirstFileExW flags not implemented 0x00000002
0067:fixme:seh:RtlCaptureStackBackTrace (0, 62, 0x7227118, (nil)) stub!
0067:fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
0067:fixme:ntdll:EtwEventRegister ({d2d578d9-2936-45b6-a09f-30e32715f42d}, 0x2251140, 0x6732bd8, 0x678bd08) stub.
0067:fixme:ntdll:NtQueryInformationToken QueryInformationToken( ..., TokenElevation, ...) semi-stub
006c:fixme:time:QueryThreadCycleTime (0x114,0x907fb90): stub!
0067:err:vulkan:wine_vk_instance_load_physical_devices Failed to enumerate physical devices, res=-3
0067:err:vulkan:wine_vkCreateInstance Failed to load physical devices, res=-3
0067:err:vulkan:wine_vk_instance_load_physical_devices Failed to enumerate physical devices, res=-3
0067:err:vulkan:wine_vkCreateInstance Failed to load physical devices, res=-3
0067:fixme:ntdll:EtwEventUnregister (deadbeef) stub.
002b:fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
002b:fixme:winhttp:WinHttpDetectAutoProxyConfigUrl discovery via DHCP not supported


Unhandled Exception:
System.TypeLoadException: Could not load type of field 'o1OidcLibrary.O1Oidc:window' (3) due to: Could not load file or assembly 'PresentationFramework, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies. assembly:PresentationFramework, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35 type:<unknown type> member:<none>
[ERROR] FATAL UNHANDLED EXCEPTION: System.TypeLoadException: Could not load type of field 'o1OidcLibrary.O1Oidc:window' (3) due to: Could not load file or assembly 'PresentationFramework, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies. assembly:PresentationFramework, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35 type:<unknown type> member:<none>
user1@PC:~$ 0042:fixme:ntdll:EtwEventUnregister (deadbeef) stub.

```[COLOR=#444444][FONT=Helvetica]

Upd: I overrided the above by running 
[/FONT][/COLOR][FONT=monospace][COLOR=#000000]```
winetricks -q dotnet40
```

[/COLOR]Now the application doesn't crash immediately after I enter my login, but it crashes a moment later. See details below. 
```


```[/FONT]```
[FONT=monospace][COLOR=#000000]$ env WINEPREFIX="/home/ymarkiv/.wine" wine C:\\Program\ Files\\Workspot\\Workspot\ Client\\WorkspotClient.exe[/COLOR]
0012:fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
0012:fixme:process:SetProcessDEPPolicy (1): stub
0012:fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
0019:fixme:process:SetProcessShutdownParameters (00000380, 00000000): partial stub.
001c:fixme:heap:RtlSetHeapInformation 0x240000 0 0x23e870 4 stub
001c:fixme:heap:RtlSetHeapInformation 0x350000 0 0x23e830 4 stub
001c:fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
0022:fixme:process:SetProcessShutdownParameters (00000380, 00000000): partial stub.
0022:fixme:heap:RtlSetHeapInformation 0x8a0000 0 0x77ef40 4 stub
0038:fixme:heap:RtlSetHeapInformation 0x7550000 0 0x23e7f0 4 stub
0038:fixme:heap:RtlSetHeapInformation 0x7770000 0 0x23de10 4 stub
0038:fixme:ver:GetFileVersionInfoSizeExW flags 0x2 ignored
0038:fixme:ver:GetFileVersionInfoExW flags 0x2 ignored
0038:fixme:seh:RtlCaptureStackBackTrace (0, 62, 0x7336518, (nil)) stub!
0038:fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
0038:fixme:ntdll:EtwEventRegister ({d2d578d9-2936-45b6-a09f-30e32715f42d}, 0x2251140, 0x6732bd8, 0x678bd08) stub.
0038:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x23e8f0, (nil) 0x23e8ec
0038:fixme:nls:get_dummy_preferred_ui_language (0x38 0x23e8f0 (nil) 0x23e8ec) returning a dummy value (current locale)
0038:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x23e8f0, 0x7345c60 0x23e8ec
0038:fixme:nls:get_dummy_preferred_ui_language (0x38 0x23e8f0 0x7345c60 0x23e8ec) returning a dummy value (current locale)
0042:fixme:dwrite:get_name_record_codepage encoding 20 not handled, platform 1.
0042:fixme:dwrite:get_name_record_codepage encoding 20 not handled, platform 1.
0042:fixme:winsock:WSALookupServiceBeginW (0x9bdf690 0x00000ff0 0x9bdf708) Stub!
[0104/200750.756:ERROR:network_change_notifier_win.cc(157)] WSALookupServiceBegin failed with: 0
0042:fixme:iphlpapi:NotifyAddrChange (Handle 0x9bdf910, overlapped 0x7364750): stub
0046:fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10066 0x00000001
0042:fixme:win:RegisterDeviceNotificationW (hwnd=0x1006e, filter=0x9bdf6b8,flags=0x00000000) returns a fake device notification handle!
0042:fixme:win:GetDisplayConfigBufferSizes (0x2 0x9bdf354 0x9bdf350): stub
0042:fixme:win:GetDisplayConfigBufferSizes (0x2 0x9bdf354 0x9bdf350): stub
0041:fixme:file:FindFirstFileExW flags not implemented 0x00000002
0041:fixme:file:FindFirstFileExW flags not implemented 0x00000002
003c:fixme:wlanapi:WlanEnumInterfaces (0x1, (nil), 0x957ed40) semi-stub
0038:fixme:netprofm:connection_point_Advise 0x9c4fbb0, 0x6f62f00, 0x6f61468 - semi-stub
0038:fixme:netprofm:ConnectionPointContainer_FindConnectionPoint interface {dcb00004-570f-4a9b-8d69-199fdba5723b} not implemented
0038:fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
0038:fixme:toolhelp:Heap32ListFirst : stub
005e:fixme:wlanapi:WlanGetAvailableNetworkList (0x1, {00000000-0000-0000-0000-000000000000}, 0x0, (nil), 0xc66b8b0) stub
004f:fixme:heap:RtlSetHeapInformation 0x7550000 0 0x23e7f0 4 stub
004f:fixme:heap:RtlSetHeapInformation 0x7770000 0 0x23de10 4 stub
004f:fixme:seh:RtlCaptureStackBackTrace (0, 62, 0x73370a8, (nil)) stub!
004f:fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
004f:fixme:ntdll:EtwEventRegister ({d2d578d9-2936-45b6-a09f-30e32715f42d}, 0x2251140, 0x6732bd8, 0x678bd08) stub.
004f:fixme:ntdll:NtQueryInformationToken QueryInformationToken( ..., TokenElevation, ...) semi-stub
004f:fixme:win:EnumDisplayDevicesW ((null),0,0x23e130,0x00000000), stub!
0063:fixme:time:QueryThreadCycleTime (0x12c,0x94bfb90): stub!
0038:fixme:nls:get_dummy_preferred_ui_language (0x8 0x23ecc0 0x23ec10 0x23ecc8) returning a dummy value (current locale)
0038:fixme:font:get_outline_text_metrics failed to read full_nameW for font L"Ani"!
0038:fixme:win:EnumDisplayDevicesW ((null),0,0x23de30,0x00000000), stub!
0038:fixme:win:EnumDisplayDevicesW ((null),0,0x23da70,0x00000000), stub!
0038:fixme:dwmapi:DwmExtendFrameIntoClientArea (0x2009e, 0x23f130) stub
0038:fixme:font:get_nearest_charset TCI failing on 20000000
0038:fixme:font:get_nearest_charset returning DEFAULT_CHARSET face->fs.fsCsb[0] = 20000000 file = L"/usr/share/fonts/truetype/fonts-gujr-extra/aakar-medium.ttf"
0038:fixme:msg:ChangeWindowMessageFilterEx (nil) c05d 1 (nil)
0038:err:ole:CoGetClassObject class {8b918b82-7985-4c24-89df-c33ad2bbfbcd} not registered
0038:err:ole:create_server class {8b918b82-7985-4c24-89df-c33ad2bbfbcd} not registered
0038:fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
0038:err:ole:CoGetClassObject no class object {8b918b82-7985-4c24-89df-c33ad2bbfbcd} could be created for context 0x15
0038:fixme:dwmapi:DwmIsCompositionEnabled 0x23ba40
0038:fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
0038:fixme:winhttp:WinHttpDetectAutoProxyConfigUrl discovery via DHCP not supported
0038:fixme:heap:RtlSetHeapInformation 0x108f0000 0 0x23a900 4 stub
0038:fixme:thread:SetThreadStackGuarantee (0x23ae28): stub
0038:fixme:shell:URL_ParseUrl failed to parse L"O1IdentityWrapper"
0038:fixme:nls:get_dummy_preferred_ui_language (0x0 0x239d80 (nil) 0x239d84) returning a dummy value (current locale)
0038:fixme:nls:get_dummy_preferred_ui_language (0x0 0x239d80 0x9ccac40 0x239d84) returning a dummy value (current locale)
0038:fixme:ntdll:EtwRegisterTraceGuidsW (0x10a0073c, (nil), {8e9f5090-2d75-4d03-8a81-e5afbf85daf1}, 1, 0x237548, (null), (null), 0x10db84f0): stub
0038:fixme:ntdll:EtwRegisterTraceGuidsW   register trace class {8e9f5090-2d75-4d03-8a81-e5afbf85daf1}
0038:fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime"): stub
0038:fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003ff,(nil),0x0001,0x00000000,0x237430,(nil)): stub
0038:err:eventlog:ReportEventW L"Application: WorkspotClient.exe\nFramework Version: v4.0.30319\nDescription: The process was terminated due to an internal error in the .NET Runtime at IP 000006447F207FE2 (0000064
47F100000) with exit code 80131506.\n"
0038:fixme:advapi:DeregisterEventSource (0xcafe4242) stub
0076:fixme:heap:RtlSetHeapInformation 0x7550000 0 0x23e7f0 4 stub
0076:fixme:heap:RtlSetHeapInformation 0x7770000 0 0x23de10 4 stub
0076:fixme:seh:RtlCaptureStackBackTrace (0, 62, 0x73375b8, (nil)) stub!
0076:fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
0076:fixme:ntdll:EtwEventRegister ({d2d578d9-2936-45b6-a09f-30e32715f42d}, 0x2251140, 0x6732bd8, 0x678bd08) stub.
0076:fixme:ntdll:NtQueryInformationToken QueryInformationToken( ..., TokenElevation, ...) semi-stub
007f:fixme:time:QueryThreadCycleTime (0x12c,0x94bfb90): stub!
[/FONT]
```[FONT=monospace]
[/FONT][COLOR=#444444][FONT=Helvetica]
Additionally, wine shows backtrace details in its UI: 
[/FONT][/COLOR]```
0x000000007bc93905 DbgBreakPoint+0x1 in ntdll: ret    
Modules:
Module    Address                    Debug info    Name (260 modules)
PE              240000-          339000    Deferred        libiconv
PE              340000-          54d000    Deferred        libeay32
PE              550000-         6d3e000    Deferred        libcef
PE             6d50000-         6e00000    Deferred        chrome_elf
PE             6e00000-         6e49000    Deferred        o1identitywrapper
PE             6e50000-         6eac000    Deferred        ssleay32
PE            29ef0000-        2a3ae000    Deferred        mscorlib
ELF            7a800000-        7a9e2000    Deferred        opengl32<elf>
  \-PE            7a850000-        7a9e2000    \               opengl32
ELF            7b400000-        7b821000    Dwarf           kernel32<elf>
  \-PE            7b420000-        7b821000    \               kernel32
ELF            7bc00000-        7bd20000    Dwarf           ntdll<elf>
  \-PE            7bc20000-        7bd20000    \               ntdll
ELF            7c000000-        7c004000    Deferred        <wine-loader>
PE           140000000-       141fd8000    Deferred        workspotclient
PE           180000000-       18016e000    Deferred        libxml2
PE         6427ee50000-     6427eebf000    Deferred        mscoree
PE         6447f100000-     6447fa65000    Deferred        clr
PE         6447faf0000-     6447fc67000    Deferred        clrjit
PE         6447fd00000-     6447fdd1000    Deferred        msvcr100_clr0400
PE         644ff4f0000-     644ff500000    Deferred        culture
PE         644ff540000-     644ff5d0000    Deferred        mscoreei
PE         644ffae0000-     644ffaf4000    Deferred        nlssorting
PE         7ff33a60000-     7ff33a78000    Deferred        dxva2
ELF        7f0b661f8000-    7f0b68000000    Deferred        libnvidia-glcore.so.390.116
ELF        7f0b94af5000-    7f0b94cf9000    Deferred        libnvidia-tls.so.390.116
ELF        7f0b94cf9000-    7f0b95036000    Deferred        libglx_nvidia.so.0
ELF        7f0b9507d000-    7f0b95333000    Deferred        libgldispatch.so.0
ELF        7f0b95333000-    7f0b95564000    Deferred        libglx.so.0
ELF        7f0b95564000-    7f0b957f0000    Deferred        libgl.so.1
ELF        7f0b95817000-    7f0b95a1e000    Deferred        libnss_dns.so.2
ELF        7f0b95a1e000-    7f0b95c21000    Deferred        libnss_mdns4_minimal.so.2
ELF        7f0b95c21000-    7f0b95eca000    Deferred        libvorbisenc.so.2
ELF        7f0b95eca000-    7f0b960f5000    Deferred        libvorbis.so.0
ELF        7f0b960f5000-    7f0b962fe000    Deferred        libogg.so.0
ELF        7f0b962fe000-    7f0b96575000    Deferred        libflac.so.8
ELF        7f0b96575000-    7f0b9677b000    Deferred        libasyncns.so.0
ELF        7f0b9677b000-    7f0b969f4000    Deferred        libsndfile.so.1
ELF        7f0b969f4000-    7f0b96bfe000    Deferred        libwrap.so.0
ELF        7f0b96bfe000-    7f0b96e7c000    Deferred        libpulsecommon-11.1.so
ELF        7f0b96e7c000-    7f0b970cc000    Deferred        libpulse.so.0
ELF        7f0b9714f000-    7f0b97190000    Deferred        rsaenh<elf>
  \-PE        7f0b97160000-    7f0b97190000    \               rsaenh
ELF        7f0b97190000-    7f0b971b1000    Deferred        netprofm<elf>
  \-PE        7f0b971a0000-    7f0b971b1000    \               netprofm
ELF        7f0b971b1000-    7f0b971c7000    Deferred        wlanapi<elf>
  \-PE        7f0b971c0000-    7f0b971c7000    \               wlanapi
ELF        7f0b971c7000-    7f0b971f4000    Deferred        winepulse<elf>
  \-PE        7f0b971d0000-    7f0b971f4000    \               winepulse
ELF        7f0b971f4000-    7f0b9721a000    Deferred        mmdevapi<elf>
  \-PE        7f0b97200000-    7f0b9721a000    \               mmdevapi
ELF        7f0b9721a000-    7f0b9723b000    Deferred        wintab32<elf>
  \-PE        7f0b97220000-    7f0b9723b000    \               wintab32
ELF        7f0b97381000-    7f0b973a1000    Deferred        concrt140<elf>
  \-PE        7f0b97390000-    7f0b973a1000    \               concrt140
ELF        7f0b973a1000-    7f0b973b5000    Deferred        api-ms-win-core-localization-obsolete-l1-2-0<elf>
  \-PE        7f0b973b0000-    7f0b973b5000    \               api-ms-win-core-localization-obsolete-l1-2-0
ELF        7f0b973b5000-    7f0b973c9000    Deferred        api-ms-win-core-datetime-l1-1-1<elf>
  \-PE        7f0b973c0000-    7f0b973c9000    \               api-ms-win-core-datetime-l1-1-1
ELF        7f0b973c9000-    7f0b973dd000    Deferred        api-ms-win-core-string-l1-1-0<elf>
  \-PE        7f0b973d0000-    7f0b973dd000    \               api-ms-win-core-string-l1-1-0
ELF        7f0b973dd000-    7f0b973f2000    Deferred        api-ms-win-core-localization-l1-2-1<elf>
  \-PE        7f0b973e0000-    7f0b973f2000    \               api-ms-win-core-localization-l1-2-1
ELF        7f0b973f2000-    7f0b97406000    Deferred        api-ms-win-core-fibers-l1-1-1<elf>
  \-PE        7f0b97400000-    7f0b97406000    \               api-ms-win-core-fibers-l1-1-1
ELF        7f0b97406000-    7f0b9761b000    Deferred        libgpg-error.so.0
ELF        7f0b9761b000-    7f0b97936000    Deferred        libgcrypt.so.20
ELF        7f0b97936000-    7f0b97b52000    Deferred        liblz4.so.1
ELF        7f0b97b52000-    7f0b97d78000    Deferred        liblzma.so.5
ELF        7f0b97d78000-    7f0b97ffc000    Deferred        libsystemd.so.0
ELF        7f0b97ffc000-    7f0b98204000    Deferred        libffi.so.6
ELF        7f0b98204000-    7f0b98408000    Deferred        libkeyutils.so.1
ELF        7f0b98408000-    7f0b98655000    Deferred        libdbus-1.so.3
ELF        7f0b98655000-    7f0b988d6000    Deferred        libgmp.so.10
ELF        7f0b988d6000-    7f0b98b0a000    Deferred        libhogweed.so.4
ELF        7f0b98b0a000-    7f0b98d40000    Deferred        libnettle.so.6
ELF        7f0b98d40000-    7f0b98f53000    Deferred        libtasn1.so.6
ELF        7f0b98f53000-    7f0b992d1000    Deferred        libunistring.so.2
ELF        7f0b992d1000-    7f0b994ee000    Deferred        libidn2.so.0
ELF        7f0b994ee000-    7f0b9981d000    Deferred        libp11-kit.so.0
ELF        7f0b9981d000-    7f0b99a28000    Deferred        libkrb5support.so.0
ELF        7f0b99a28000-    7f0b99c2c000    Deferred        libcom_err.so.2
ELF        7f0b99c2c000-    7f0b99e5e000    Deferred        libk5crypto.so.3
ELF        7f0b99e5e000-    7f0b9a134000    Deferred        libkrb5.so.3
ELF        7f0b9a134000-    7f0b9a345000    Deferred        libavahi-client.so.3
ELF        7f0b9a345000-    7f0b9a551000    Deferred        libavahi-common.so.3
ELF        7f0b9a551000-    7f0b9a8b6000    Deferred        libgnutls.so.30
ELF        7f0b9a8b6000-    7f0b9ab01000    Deferred        libgssapi_krb5.so.2
ELF        7f0b9ab01000-    7f0b9ad8d000    Deferred        libcups.so.2
ELF        7f0b9ad9f000-    7f0b9adb4000    Deferred        api-ms-win-core-synch-l1-2-0<elf>
  \-PE        7f0b9ada0000-    7f0b9adb4000    \               api-ms-win-core-synch-l1-2-0
ELF        7f0b9adb4000-    7f0b9afba000    Deferred        libxfixes.so.3
ELF        7f0b9afba000-    7f0b9b1c4000    Deferred        libxcursor.so.1
ELF        7f0b9b1c4000-    7f0b9b3d4000    Deferred        libxi.so.6
ELF        7f0b9b3d4000-    7f0b9b5d7000    Deferred        libxcomposite.so.1
ELF        7f0b9b5d7000-    7f0b9b7e2000    Deferred        libxrandr.so.2
ELF        7f0b9b7e2000-    7f0b9b9ec000    Deferred        libxrender.so.1
ELF        7f0b9b9ec000-    7f0b9bbf2000    Deferred        libxxf86vm.so.1
ELF        7f0b9bbf2000-    7f0b9bdf5000    Deferred        libxinerama.so.1
ELF        7f0b9bdf5000-    7f0b9bffd000    Deferred        librt.so.1
ELF        7f0b9bffd000-    7f0b9c212000    Deferred        libbsd.so.0
ELF        7f0b9c212000-    7f0b9c418000    Deferred        libxdmcp.so.6
ELF        7f0b9c418000-    7f0b9c61c000    Deferred        libxau.so.6
ELF        7f0b9c61c000-    7f0b9c844000    Deferred        libxcb.so.1
ELF        7f0b9c844000-    7f0b9cb7c000    Deferred        libx11.so.6
ELF        7f0b9cb7c000-    7f0b9cd8e000    Deferred        libxext.so.6
ELF        7f0b9cd98000-    7f0b9cdb3000    Deferred        kerberos<elf>
  \-PE        7f0b9cda0000-    7f0b9cdb3000    \               kerberos
ELF        7f0b9cdb5000-    7f0b9ce59000    Deferred        winex11<elf>
  \-PE        7f0b9cdd0000-    7f0b9ce59000    \               winex11
ELF        7f0b9cedd000-    7f0b9d10f000    Deferred        libexpat.so.1
ELF        7f0b9d10f000-    7f0b9d354000    Deferred        libfontconfig.so.1
ELF        7f0b9d354000-    7f0b9d586000    Deferred        libpng16.so.16
ELF        7f0b9d586000-    7f0b9d83a000    Deferred        libfreetype.so.6
ELF        7f0b9d83a000-    7f0b9da64000    Deferred        libtinfo.so.5
ELF        7f0b9da64000-    7f0b9dc87000    Deferred        libncurses.so.5
ELF        7f0b9dcae000-    7f0b9dec9000    Deferred        libresolv.so.2
ELF        7f0b9dedc000-    7f0b9def0000    Deferred        api-ms-win-crt-locale-l1-1-0<elf>
  \-PE        7f0b9dee0000-    7f0b9def0000    \               api-ms-win-crt-locale-l1-1-0
ELF        7f0b9def0000-    7f0b9df12000    Deferred        dnsapi<elf>
  \-PE        7f0b9df00000-    7f0b9df12000    \               dnsapi
ELF        7f0b9df12000-    7f0b9df50000    Deferred        uxtheme<elf>
  \-PE        7f0b9df20000-    7f0b9df50000    \               uxtheme
ELF        7f0b9e050000-    7f0b9e15d000    Deferred        msvcr120<elf>
  \-PE        7f0b9e080000-    7f0b9e15d000    \               msvcr120
ELF        7f0b9e15d000-    7f0b9e2a7000    Deferred        msvcp140<elf>
  \-PE        7f0b9e1a0000-    7f0b9e2a7000    \               msvcp140
ELF        7f0b9e2a7000-    7f0b9e2bd000    Deferred        dhcpcsvc<elf>
  \-PE        7f0b9e2b0000-    7f0b9e2bd000    \               dhcpcsvc
ELF        7f0b9e2bd000-    7f0b9e2d6000    Deferred        ncrypt<elf>
  \-PE        7f0b9e2c0000-    7f0b9e2d6000    \               ncrypt
ELF        7f0b9e2d6000-    7f0b9e3da000    Deferred        cryptui<elf>
  \-PE        7f0b9e2e0000-    7f0b9e3da000    \               cryptui
ELF        7f0b9e3da000-    7f0b9e3f8000    Deferred        jsproxy<elf>
  \-PE        7f0b9e3e0000-    7f0b9e3f8000    \               jsproxy
ELF        7f0b9e3f8000-    7f0b9e43b000    Deferred        winhttp<elf>
  \-PE        7f0b9e400000-    7f0b9e43b000    \               winhttp
ELF        7f0b9e43b000-    7f0b9e4fb000    Deferred        urlmon<elf>
  \-PE        7f0b9e450000-    7f0b9e4fb000    \               urlmon
ELF        7f0b9e4fb000-    7f0b9e583000    Deferred        d3d11<elf>
  \-PE        7f0b9e500000-    7f0b9e583000    \               d3d11
ELF        7f0b9e583000-    7f0b9e655000    Deferred        msvcrt<elf>
  \-PE        7f0b9e5a0000-    7f0b9e655000    \               msvcrt
ELF        7f0b9e755000-    7f0b9e7a5000    Deferred        d3d9<elf>
  \-PE        7f0b9e760000-    7f0b9e7a5000    \               d3d9
ELF        7f0b9e7a5000-    7f0b9e816000    Deferred        dbghelp<elf>
  \-PE        7f0b9e7b0000-    7f0b9e816000    \               dbghelp
ELF        7f0b9e816000-    7f0b9e989000    Deferred        wined3d<elf>
  \-PE        7f0b9e840000-    7f0b9e989000    \               wined3d
ELF        7f0b9e989000-    7f0b9e9be000    Deferred        dxgi<elf>
  \-PE        7f0b9e990000-    7f0b9e9be000    \               dxgi
ELF        7f0b9e9be000-    7f0b9ea41000    Deferred        dwrite<elf>
  \-PE        7f0b9e9d0000-    7f0b9ea41000    \               dwrite
ELF        7f0b9ea41000-    7f0b9ea5a000    Deferred        dwmapi<elf>
  \-PE        7f0b9ea50000-    7f0b9ea5a000    \               dwmapi
ELF        7f0b9ea5a000-    7f0b9ea85000    Deferred        propsys<elf>
  \-PE        7f0b9ea60000-    7f0b9ea85000    \               propsys
ELF        7f0b9ea85000-    7f0b9ea9e000    Deferred        userenv<elf>
  \-PE        7f0b9ea90000-    7f0b9ea9e000    \               userenv
ELF        7f0b9ea9e000-    7f0b9eab8000    Deferred        hid<elf>
  \-PE        7f0b9eaa0000-    7f0b9eab8000    \               hid
ELF        7f0b9eab8000-    7f0b9ead2000    Deferred        wtsapi32<elf>
  \-PE        7f0b9eac0000-    7f0b9ead2000    \               wtsapi32
ELF        7f0b9ead2000-    7f0b9eb3a000    Deferred        oleacc<elf>
  \-PE        7f0b9eae0000-    7f0b9eb3a000    \               oleacc
ELF        7f0b9eb3a000-    7f0b9ecb5000    Deferred        oleaut32<elf>
  \-PE        7f0b9eb60000-    7f0b9ecb5000    \               oleaut32
ELF        7f0b9ecb5000-    7f0b9ece3000    Deferred        msacm32<elf>
  \-PE        7f0b9ecc0000-    7f0b9ece3000    \               msacm32
ELF        7f0b9ece3000-    7f0b9eda8000    Deferred        winmm<elf>
  \-PE        7f0b9ecf0000-    7f0b9eda8000    \               winmm
ELF        7f0b9eda8000-    7f0b9edd5000    Deferred        mpr<elf>
  \-PE        7f0b9edb0000-    7f0b9edd5000    \               mpr
ELF        7f0b9edd5000-    7f0b9eff2000    Deferred        libz.so.1
ELF        7f0b9f005000-    7f0b9f019000    Deferred        psapi<elf>
  \-PE        7f0b9f010000-    7f0b9f019000    \               psapi
ELF        7f0b9f019000-    7f0b9f0a6000    Deferred        wininet<elf>
  \-PE        7f0b9f030000-    7f0b9f0a6000    \               wininet
ELF        7f0b9f0a6000-    7f0b9f0d7000    Deferred        credui<elf>
  \-PE        7f0b9f0b0000-    7f0b9f0d7000    \               credui
ELF        7f0b9f0d7000-    7f0b9f0ef000    Deferred        ntdsapi<elf>
  \-PE        7f0b9f0e0000-    7f0b9f0ef000    \               ntdsapi
ELF        7f0b9f0ef000-    7f0b9f104000    Deferred        api-ms-win-crt-conio-l1-1-0<elf>
  \-PE        7f0b9f0f0000-    7f0b9f104000    \               api-ms-win-crt-conio-l1-1-0
ELF        7f0b9f104000-    7f0b9f119000    Deferred        api-ms-win-crt-filesystem-l1-1-0<elf>
  \-PE        7f0b9f110000-    7f0b9f119000    \               api-ms-win-crt-filesystem-l1-1-0
ELF        7f0b9f119000-    7f0b9f133000    Deferred        api-ms-win-crt-math-l1-1-0<elf>
  \-PE        7f0b9f120000-    7f0b9f133000    \               api-ms-win-crt-math-l1-1-0
ELF        7f0b9f133000-    7f0b9f147000    Deferred        api-ms-win-crt-utility-l1-1-0<elf>
  \-PE        7f0b9f140000-    7f0b9f147000    \               api-ms-win-crt-utility-l1-1-0
ELF        7f0b9f147000-    7f0b9f15d000    Deferred        api-ms-win-crt-string-l1-1-0<elf>
  \-PE        7f0b9f150000-    7f0b9f15d000    \               api-ms-win-crt-string-l1-1-0
ELF        7f0b9f15d000-    7f0b9f172000    Deferred        api-ms-win-crt-time-l1-1-0<elf>
  \-PE        7f0b9f160000-    7f0b9f172000    \               api-ms-win-crt-time-l1-1-0
ELF        7f0b9f172000-    7f0b9f187000    Deferred        api-ms-win-crt-heap-l1-1-0<elf>
  \-PE        7f0b9f180000-    7f0b9f187000    \               api-ms-win-crt-heap-l1-1-0
ELF        7f0b9f187000-    7f0b9f19b000    Deferred        api-ms-win-crt-environment-l1-1-0<elf>
  \-PE        7f0b9f190000-    7f0b9f19b000    \               api-ms-win-crt-environment-l1-1-0
ELF        7f0b9f19b000-    7f0b9f1b1000    Deferred        api-ms-win-crt-convert-l1-1-0<elf>
  \-PE        7f0b9f1a0000-    7f0b9f1b1000    \               api-ms-win-crt-convert-l1-1-0
ELF        7f0b9f1b1000-    7f0b9f1c7000    Deferred        api-ms-win-crt-runtime-l1-1-0<elf>
  \-PE        7f0b9f1c0000-    7f0b9f1c7000    \               api-ms-win-crt-runtime-l1-1-0
ELF        7f0b9f1c7000-    7f0b9f1dd000    Deferred        api-ms-win-crt-stdio-l1-1-0<elf>
  \-PE        7f0b9f1d0000-    7f0b9f1dd000    \               api-ms-win-crt-stdio-l1-1-0
ELF        7f0b9f1dd000-    7f0b9f2f6000    Dwarf           ucrtbase<elf>
  \-PE        7f0b9f210000-    7f0b9f2f6000    \               ucrtbase
ELF        7f0b9f2f6000-    7f0b9f30d000    Deferred        vcruntime140<elf>
  \-PE        7f0b9f300000-    7f0b9f30d000    \               vcruntime140
ELF        7f0b9f30d000-    7f0b9f32f000    Deferred        bcrypt<elf>
  \-PE        7f0b9f310000-    7f0b9f32f000    \               bcrypt
ELF        7f0b9f32f000-    7f0b9f41a000    Deferred        crypt32<elf>
  \-PE        7f0b9f340000-    7f0b9f41a000    \               crypt32
ELF        7f0b9f41a000-    7f0b9f450000    Deferred        netapi32<elf>
  \-PE        7f0b9f420000-    7f0b9f450000    \               netapi32
ELF        7f0b9f450000-    7f0b9f48e000    Deferred        secur32<elf>
  \-PE        7f0b9f460000-    7f0b9f48e000    \               secur32
ELF        7f0b9f48e000-    7f0b9f4d6000    Deferred        winspool<elf>
  \-PE        7f0b9f4a0000-    7f0b9f4d6000    \               winspool
ELF        7f0b9f4d6000-    7f0b9f4fe000    Deferred        imm32<elf>
  \-PE        7f0b9f4e0000-    7f0b9f4fe000    \               imm32
ELF        7f0b9f4fe000-    7f0b9f54c000    Deferred        usp10<elf>
  \-PE        7f0b9f510000-    7f0b9f54c000    \               usp10
ELF        7f0b9f54c000-    7f0b9f6a1000    Deferred        comctl32<elf>
  \-PE        7f0b9f560000-    7f0b9f6a1000    \               comctl32
ELF        7f0b9f6a1000-    7f0b9f73d000    Deferred        rpcrt4<elf>
  \-PE        7f0b9f6b0000-    7f0b9f73d000    \               rpcrt4
ELF        7f0b9f73d000-    7f0b9f8e0000    Deferred        ole32<elf>
  \-PE        7f0b9f760000-    7f0b9f8e0000    \               ole32
ELF        7f0b9f8e0000-    7f0b9f908000    Deferred        shcore<elf>
  \-PE        7f0b9f8f0000-    7f0b9f908000    \               shcore
ELF        7f0b9f908000-    7f0b9f923000    Deferred        version<elf>
  \-PE        7f0b9f910000-    7f0b9f923000    \               version
ELF        7f0b9f923000-    7f0b9faa1000    Deferred        gdi32<elf>
  \-PE        7f0b9f940000-    7f0b9faa1000    \               gdi32
ELF        7f0b9faa1000-    7f0b9fd09000    Deferred        user32<elf>
  \-PE        7f0b9fac0000-    7f0b9fd09000    \               user32
ELF        7f0b9fd09000-    7f0b9fd8e000    Deferred        shlwapi<elf>
  \-PE        7f0b9fd20000-    7f0b9fd8e000    \               shlwapi
ELF        7f0b9fd8e000-    7f0ba0791000    Deferred        shell32<elf>
  \-PE        7f0b9fdb0000-    7f0ba0791000    \               shell32
ELF        7f0ba0791000-    7f0ba0897000    Deferred        comdlg32<elf>
  \-PE        7f0ba07a0000-    7f0ba0897000    \               comdlg32
ELF        7f0ba0897000-    7f0ba092a000    Deferred        advapi32<elf>
  \-PE        7f0ba08b0000-    7f0ba092a000    \               advapi32
ELF        7f0ba092a000-    7f0ba095a000    Deferred        iphlpapi<elf>
  \-PE        7f0ba0930000-    7f0ba095a000    \               iphlpapi
ELF        7f0ba095a000-    7f0ba0999000    Deferred        ws2_32<elf>
  \-PE        7f0ba0960000-    7f0ba0999000    \               ws2_32
ELF        7f0ba0b99000-    7f0ba0dab000    Deferred        libnss_files.so.2
ELF        7f0ba0dab000-    7f0ba0fc5000    Deferred        libnsl.so.1
ELF        7f0ba0fc5000-    7f0ba11d1000    Deferred        libnss_nis.so.2
ELF        7f0ba11d1000-    7f0ba13db000    Deferred        libnss_compat.so.2
ELF        7f0ba2122000-    7f0ba233a000    Deferred        libgcc_s.so.1
ELF        7f0ba233a000-    7f0ba26d8000    Deferred        libm.so.6
ELF        7f0ba26da000-    7f0ba28de000    Deferred        libdl.so.2
ELF        7f0ba28de000-    7f0ba2ccf000    Deferred        libc.so.6
ELF        7f0ba2ccf000-    7f0ba2eee000    Deferred        libpthread.so.0
ELF        7f0ba2ef9000-    7f0ba2f15000    Deferred        wsock32<elf>
  \-PE        7f0ba2f00000-    7f0ba2f15000    \               wsock32
ELF        7f0ba32bc000-    7f0ba34e6000    Deferred        ld-linux-x86-64.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000035    0
    00000032    0
    0000002d    0
    00000029    0
    00000026    0
    00000020    0
    00000015    0
    00000010    0
    0000000f    0
00000011 mscorsvw.exe
    0000001a    0
    00000019    0
    00000018    0
    00000012    0
00000013 explorer.exe
    0000001f    0
    0000001e    0
    0000001d    0
    00000014    0
0000001b mscorsvw.exe
    00000023    0
    00000022    0
    00000021    0
    0000001c    0
00000024 winedevice.exe
    0000002a    0
    00000028    0
    00000027    0
    00000025    0
0000002b plugplay.exe
    0000002f    0
    0000002e    0
    0000002c    0
00000030 winedevice.exe
    00000036    0
    00000034    0
    00000033    0
    00000031    0
00000037 (D) C:\Program Files\Workspot\Workspot Client\WorkspotClient.exe
    00000074    2
    00000073    0
    00000072    0
    00000071    0
    00000070    0
    0000006f   15
    0000006e    0
    0000005f    0
    0000005e    0
    0000005d    0
    0000005c    0
    0000005b    0
    0000005a    0
    00000059    0
    00000058    0
    00000057    0
    00000056    0
    00000055    0
    00000054   -2
    00000053    0
    00000052    0
    00000051    0
    0000004e    0
    0000004d    0
    0000004c    0
    0000004b   -2
    0000004a    0
    00000049    0
    00000048    0
    00000046    0
    00000045    0
    00000044    0
    00000043    0
    00000042    0
    00000041   -2
    00000040   -2
    0000003f    0
    0000003e    0
    0000003d    0
    0000003c    0
    0000003b    0
    0000003a    0
    00000039    0
    00000038    0 <==
0000004f WorkspotClient.exe
    0000006d    0
    0000006c    0
    0000006b    0
    0000006a    0
    00000069    0
    00000068   -2
    00000067   -2
    00000066    0
    00000065    0
    00000064    0
    00000062    0
    00000061    0
    00000060    0
    00000050    0
00000077 wineconsole.exe
    00000078    0
0000007a WorkspotClient.exe
    0000007b    0
System information:
    Wine build: wine-4.0.3
    Platform: x86_64
    Version: Windows 5.1 (0)
    Host system: Linux
    Host version: 4.15.0-72-generic

```
[COLOR=#444444][FONT=Helvetica]
Upd: ok, I googled it and it seems I need to install dotnet45 instead... looking into it now.

Upd: I installed dotnet472. The workspot program doesn't crash anymore in wine. But it shows another error in workspot program UI now: > [/FONT][/COLOR]Azure Active Directory token expired. Please check your system clock.[COLOR=#444444][FONT=Helvetica]
Tried to google this and found windows desktop client updates: 
[/FONT][/COLOR][https://docs.microsoft.com/en-us/windows-server/remote/remote-desktop-services/clients/windowsdesktop-whatsnew](https://docs.microsoft.com/en-us/windows-server/remote/remote-desktop-services/clients/windowsdesktop-whatsnew)
Instaleed the latest, ran > wineboot -r
But it didn't help me. Still showing "token expired" error in workspot program UI.

Please advise.

---

### Post by marchello_lippi2 on 2020-01-04
Ok, I need to continue in different message. 
This is latest command run trace: 
```

$ env WINEPREFIX="/home/user1/.wine" wine C:\\Program\ Files\\Workspot\\Workspot\ Client\\WorkspotClient.exe
0012:fixme:wer:WerSetFlags (2) stub!
0012:fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
0019:fixme:process:SetProcessShutdownParameters (00000380, 00000000): partial stub.
0019:fixme:ntdll:EtwEventRegister ({319dc449-ada5-50f7-428e-957db6791668}, 0x993780, 0x9e1b20, 0x9e1b38) stub.
0019:fixme:ntdll:EtwEventSetInformation (deadbeef, 2, 0x973109, 28) stub
001c:fixme:heap:RtlSetHeapInformation 0x240000 0 0x23e830 4 stub
001c:fixme:wer:WerSetFlags (2) stub!
001c:fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
0022:fixme:process:SetProcessShutdownParameters (00000380, 00000000): partial stub.
0022:fixme:ntdll:EtwEventRegister ({319dc449-ada5-50f7-428e-957db6791668}, 0x8383e0, 0x8affa0, 0x8affc0) stub.
0022:fixme:ntdll:EtwEventSetInformation (deadbeef, 2, 0x8863bd, 28) stub
0037:fixme:heap:RtlSetHeapInformation 0x7550000 0 0x23e7f0 4 stub
0037:fixme:ntdll:EtwEventRegister ({319dc449-ada5-50f7-428e-957db6791668}, 0x77883e0, 0x77fffa0, 0x77fffc0) stub.
0037:fixme:ntdll:EtwEventSetInformation (deadbeef, 2, 0x77d63bd, 28) stub
0037:fixme:file:FindFirstFileExW flags not implemented 0x00000002
0037:fixme:file:FindFirstFileExW flags not implemented 0x00000002
0037:fixme:ver:GetFileVersionInfoSizeExW flags 0x2 ignored
0037:fixme:ver:GetFileVersionInfoExW flags 0x2 ignored
0037:fixme:seh:RtlCaptureStackBackTrace (0, 62, 0x7336518, (nil)) stub!
0037:fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
0037:fixme:ntdll:EtwEventRegister ({d2d578d9-2936-45b6-a09f-30e32715f42d}, 0x2251140, 0x6732bd8, 0x678bd08) stub.
0037:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x23e8f0, (nil) 0x23e8ec
0037:fixme:nls:get_dummy_preferred_ui_language (0x38 0x23e8f0 (nil) 0x23e8ec) returning a dummy value (current locale)
0037:fixme:nls:GetThreadPreferredUILanguages 00000038, 0x23e8f0, 0x7345c60 0x23e8ec
0037:fixme:nls:get_dummy_preferred_ui_language (0x38 0x23e8f0 0x7345c60 0x23e8ec) returning a dummy value (current locale)
0041:fixme:dwrite:get_name_record_codepage encoding 20 not handled, platform 1.
0041:fixme:dwrite:get_name_record_codepage encoding 20 not handled, platform 1.
0041:fixme:winsock:WSALookupServiceBeginW (0x9b6f690 0x00000ff0 0x9b6f708) Stub!
[0104/223019.716:ERROR:network_change_notifier_win.cc(157)] WSALookupServiceBegin failed with: 0
0041:fixme:iphlpapi:NotifyAddrChange (Handle 0x9b6f910, overlapped 0x7364740): stub
0046:fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10066 0x00000001
0041:fixme:win:RegisterDeviceNotificationW (hwnd=0x1006e, filter=0x9b6f6b8,flags=0x00000000) returns a fake device notification handle!
0041:fixme:win:GetDisplayConfigBufferSizes (0x2 0x9b6f354 0x9b6f350): stub
0041:fixme:win:GetDisplayConfigBufferSizes (0x2 0x9b6f354 0x9b6f350): stub
[0104/223019.860:ERROR:display_layout.cc(576)] display_id must not be same as parent_display_id
0040:fixme:file:FindFirstFileExW flags not implemented 0x00000002
0040:fixme:file:FindFirstFileExW flags not implemented 0x00000002
003b:fixme:wlanapi:WlanEnumInterfaces (0x1, (nil), 0x950ed40) semi-stub
0037:fixme:netprofm:connection_point_Advise 0x9c31bc0, 0x6f61d20, 0x6f61668 - semi-stub
0037:fixme:netprofm:ConnectionPointContainer_FindConnectionPoint interface {dcb00004-570f-4a9b-8d69-199fdba5723b} not implemented
0037:fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
0037:fixme:toolhelp:Heap32ListFirst : stub
005d:fixme:wlanapi:WlanGetAvailableNetworkList (0x1, {00000000-0000-0000-0000-000000000000}, 0x0, (nil), 0xc70b8b0) stub
004e:fixme:heap:RtlSetHeapInformation 0x7550000 0 0x23e7f0 4 stub
004e:fixme:ntdll:EtwEventRegister ({319dc449-ada5-50f7-428e-957db6791668}, 0x77883e0, 0x77fffa0, 0x77fffc0) stub.
004e:fixme:ntdll:EtwEventSetInformation (deadbeef, 2, 0x77d63bd, 28) stub
004e:fixme:file:FindFirstFileExW flags not implemented 0x00000002
004e:fixme:seh:RtlCaptureStackBackTrace (0, 62, 0x7337098, (nil)) stub!
004e:fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
004e:fixme:ntdll:EtwEventRegister ({d2d578d9-2936-45b6-a09f-30e32715f42d}, 0x2251140, 0x6732bd8, 0x678bd08) stub.
004e:fixme:ntdll:NtQueryInformationToken QueryInformationToken( ..., TokenElevation, ...) semi-stub
004e:fixme:win:EnumDisplayDevicesW ((null),0,0x23e130,0x00000000), stub!
0062:fixme:time:QueryThreadCycleTime (0x12c,0x944fb90): stub!
004e:fixme:win:EnumDisplayDevicesW ((null),0,0x23d070,0x00000000), stub!
0037:fixme:nls:get_dummy_preferred_ui_language (0x8 0x23ecc0 0x23ec10 0x23ecc8) returning a dummy value (current locale)
0037:fixme:font:get_outline_text_metrics failed to read full_nameW for font L"Ani"!
004e:fixme:d3d11:d3d11_device_CheckFeatureSupport Returning fake Options support data.
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 85, format_support 0xc29d4 partial-stub!
004e:fixme:d3d:wined3d_check_device_multisample_type multisample_type 32 not handled yet.
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 115, format_support 0xc29dc partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 86, format_support 0xc29e4 partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 88, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 88, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 87, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 87, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 87, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 87, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 91, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 91, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 65, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 28, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 28, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 28, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 11, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 28, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 28, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 28, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 24, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 11, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 55, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 45, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 45, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 61, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 56, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 49, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 35, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 54, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 41, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 34, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 16, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 64, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 62, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 59, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 57, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 43, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 42, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 52, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 50, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 38, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 36, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 18, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 17, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 2, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 2, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 2, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 2, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 2, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 10, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 10, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 10, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 10, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 10, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 45, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 26, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 29, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 29, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 40, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 20, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 45, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 28, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 28, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 3, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 3, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 12, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 12, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 30, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 30, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 4, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 4, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 14, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 14, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 32, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 32, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 25, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 56, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 35, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 28, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 29, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 28, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 29, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 28, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 29, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 87, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_device_CheckFormatSupport iface 0xcd0d8, format 87, format_support 0x23daac partial-stub!
004e:fixme:d3d11:d3d11_immediate_context_Flush iface 0xcd108 stub!
0037:fixme:win:EnumDisplayDevicesW ((null),0,0x23de30,0x00000000), stub!
0037:fixme:win:EnumDisplayDevicesW ((null),0,0x23da70,0x00000000), stub!
0037:fixme:dwmapi:DwmExtendFrameIntoClientArea (0x2009e, 0x23f130) stub
0070:fixme:file:FindFirstFileExW flags not implemented 0x00000002
0037:fixme:font:get_nearest_charset TCI failing on 20000000
0037:fixme:font:get_nearest_charset returning DEFAULT_CHARSET face->fs.fsCsb[0] = 20000000 file = L"/usr/share/fonts/truetype/fonts-gujr-extra/aakar-medium.ttf"
0037:fixme:msg:ChangeWindowMessageFilterEx (nil) c05e 1 (nil)
0037:err:ole:CoGetClassObject class {8b918b82-7985-4c24-89df-c33ad2bbfbcd} not registered
0037:err:ole:create_server class {8b918b82-7985-4c24-89df-c33ad2bbfbcd} not registered
0037:fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
0037:err:ole:CoGetClassObject no class object {8b918b82-7985-4c24-89df-c33ad2bbfbcd} could be created for context 0x15
0037:fixme:dwmapi:DwmIsCompositionEnabled 0x23ba40
0019:fixme:service:QueryServiceConfig2W Level 6 not implemented
0019:fixme:service:QueryServiceConfig2W Level 6 not implemented
0019:fixme:service:QueryServiceConfig2W Level 6 not implemented
0019:fixme:service:QueryServiceConfig2W Level 6 not implemented
0019:fixme:service:QueryServiceConfig2W Level 6 not implemented
0022:fixme:service:QueryServiceConfig2W Level 6 not implemented
0022:fixme:service:QueryServiceConfig2W Level 6 not implemented
0022:fixme:service:QueryServiceConfig2W Level 6 not implemented
0022:fixme:service:QueryServiceConfig2W Level 6 not implemented
0022:fixme:service:QueryServiceConfig2W Level 6 not implemented
0075:fixme:heap:RtlSetHeapInformation 0x7550000 0 0x23e7f0 4 stub
0075:fixme:ntdll:EtwEventRegister ({319dc449-ada5-50f7-428e-957db6791668}, 0x77883e0, 0x77fffa0, 0x77fffc0) stub.
0075:fixme:ntdll:EtwEventSetInformation (deadbeef, 2, 0x77d63bd, 28) stub
0075:fixme:file:FindFirstFileExW flags not implemented 0x00000002
0075:fixme:seh:RtlCaptureStackBackTrace (0, 62, 0x73375b8, (nil)) stub!
0075:fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
0075:fixme:ntdll:EtwEventRegister ({d2d578d9-2936-45b6-a09f-30e32715f42d}, 0x2251140, 0x6732bd8, 0x678bd08) stub.
0075:fixme:ntdll:NtQueryInformationToken QueryInformationToken( ..., TokenElevation, ...) semi-stub
007a:fixme:time:QueryThreadCycleTime (0x12c,0x944fb90): stub!
0075:err:vulkan:wine_vk_instance_load_physical_devices Failed to enumerate physical devices, res=-3
0075:err:vulkan:wine_vkCreateInstance Failed to load physical devices, res=-3
0075:err:vulkan:wine_vk_instance_load_physical_devices Failed to enumerate physical devices, res=-3
0075:err:vulkan:wine_vkCreateInstance Failed to load physical devices, res=-3
0075:fixme:ntdll:EtwEventUnregister (deadbeef) stub.
0075:fixme:ntdll:EtwEventUnregister (deadbeef) stub.
0037:fixme:winhttp:get_system_proxy_autoconfig_url no support on this platform
0037:fixme:winhttp:WinHttpDetectAutoProxyConfigUrl discovery via DHCP not supported
0037:fixme:ntdll:EtwEventRegister ({319dc449-ada5-50f7-428e-957db6791668}, 0x10f9eff0, 0x113cf240, 0x113cf260) stub.
0037:fixme:ntdll:EtwEventSetInformation (deadbeef, 2, 0x111cd83c, 28) stub
0037:fixme:kernelbase:QuirkIsEnabled3 (0x23a5e0, 0xffffffff) stub!
0037:fixme:process:GetNumaHighestNodeNumber (0x23ae58): semi-stub
0037:fixme:thread:SetThreadStackGuarantee (0x23ae20): stub
0037:fixme:ntdll:EtwEventRegister ({e13c0d23-ccbc-4e12-931b-d9cc2eee27e4}, 0x10eb4350, 0x113c40d0, 0x113d2d78) stub.
0037:fixme:ntdll:EtwEventRegister ({763fd754-7086-4dfe-95eb-c01a46faf4ca}, 0x10eb4350, 0x113c4890, 0x113c4e68) stub.
0037:fixme:ntdll:EtwEventRegister ({a669021c-c450-4609-a035-5af59af4df18}, 0x10eb4350, 0x113d1570, 0x113d2d88) stub.
0037:fixme:ntdll:EtwEventRegister ({cc2bcbba-16b6-4cf3-8990-d74c2e8af500}, 0x10eb4350, 0x113c4220, 0x113d2d90) stub.
0037:fixme:wer:WerRegisterRuntimeExceptionModule (L"C:\\windows\\Microsoft.NET\\Framework64\\v4.0.30319\\mscordacwks.dll", 0x10a80000) stub!
0037:fixme:ntdll:EtwEventRegister ({319dc449-ada5-50f7-428e-957db6791668}, 0x2a702bc0, 0x2a72b8a0, 0x2a72b8c0) stub.
0037:fixme:ntdll:EtwEventSetInformation (deadbeef, 2, 0x2a717e91, 28) stub
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 4 0x9d19bd8 0x235960 0x236350 (nil)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 3 0x9d19bb0 0x2360c0 0x236ab0 (nil)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 3 0x9d19bb0 0x2360c0 0x236ab0 (nil)
0037:fixme:shell:URL_ParseUrl failed to parse L"O1IdentityWrapper"
0037:fixme:nls:LocaleNameToLCID unsupported flags 8000000
0037:fixme:nls:LCIDToLocaleName unsupported flags 8000000
0037:fixme:nls:get_dummy_preferred_ui_language (0x8 0x239ea0 (nil) 0x239ea4) returning a dummy value (current locale)
0037:fixme:nls:get_dummy_preferred_ui_language (0x8 0x239ea0 0x9d22820 0x239ea4) returning a dummy value (current locale)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x9d1a698 0x2381c0 0x238bb0 (nil)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x9d1a698 0x238920 0x239310 (nil)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x9d1a808 0x237090 0x237a80 (nil)
0037:fixme:shell:URL_ParseUrl failed to parse L"O1Identity"
0037:fixme:shell:URL_ParseUrl failed to parse L"o1OidcLibrary"
0037:fixme:shell:URL_ParseUrl failed to parse L"Microsoft.Identity.Client"
0037:fixme:shell:URL_ParseUrl failed to parse L"System"
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x9d2e848 0x235e00 0x2367f0 (nil)
0037:fixme:shell:URL_ParseUrl failed to parse L"System.Net.Http"
0037:fixme:shell:URL_ParseUrl failed to parse L"System.Core"
0037:fixme:shell:URL_ParseUrl failed to parse L"System.IdentityModel.Tokens.Jwt"
0037:fixme:shell:URL_ParseUrl failed to parse L"Microsoft.IdentityModel.Tokens"
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 5 0x9d396e8 0x235f40 0x236930 (nil)
0037:fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
0037:fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 4 0x9d43df0 0x234b20 0x235510 (nil)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 3 0x9d41f48 0x235280 0x235c70 (nil)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 3 0x9d41f48 0x235280 0x235c70 (nil)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 4 0x9d432e8 0x234b20 0x235510 (nil)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 3 0x9d41f30 0x235280 0x235c70 (nil)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 3 0x9d41f30 0x235280 0x235c70 (nil)
0037:fixme:bcrypt:BCryptGetFipsAlgorithmMode 0x2390e0 - semi-stub
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 4 0x9d42ee8 0x235910 0x236300 (nil)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 3 0x9d42ec0 0x236070 0x236a60 (nil)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 3 0x9d42ec0 0x236070 0x236a60 (nil)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x9d4ad70 0x2367d0 0x2371c0 (nil)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x9d4ad70 0x236f30 0x237920 (nil)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x9d4ad70 0x236f30 0x237920 (nil)
0037:fixme:nls:LCMapStringEx unsupported lparam 9d225f0
0037:fixme:nls:GetFileMUIPath stub: 0x10, L"C:\\windows\\system32\\tzres.dll", (null), 0x23a000, 0x9d4cbe0, 0x23a008, 0x239ff8
0037:fixme:nls:GetFileMUIPath stub: 0x10, L"C:\\windows\\system32\\tzres.dll", (null), 0x23a000, 0x9d4cbe0, 0x23a008, 0x239ff8
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x9d58948 0x236360 0x236d50 (nil)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x9d58948 0x236360 0x236d50 (nil)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x9d593f0 0x234aa0 0x235490 (nil)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x9d593f0 0x235200 0x235bf0 (nil)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x9d593f0 0x235200 0x235bf0 (nil)
0037:fixme:ntdll:EtwEventRegister ({8e9f5090-2d75-4d03-8a81-e5afbf85daf1}, 0x7818bec, (nil), 0x11ab88c0) stub.
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 4 0x9d58778 0x233600 0x233ff0 (nil)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 3 0x9d4cac8 0x233d60 0x234750 (nil)
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 3 0x9d4cac8 0x233d60 0x234750 (nil)
0037:fixme:ras:RasEnumConnectionsW (0x9d61fd0,0x238b10,0x238b18),stub!
0037:fixme:ras:RasEnumConnectionsW RAS support is not implemented! Configure program to use LAN connection/winsock instead!
0037:err:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request failed with status 0x2733
0037:err:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request failed with status 0x2733
0037:fixme:ras:RasConnectionNotificationW (0xffffffffffffffff,0x56c,0x00000003),stub!
0037:fixme:ntdll:EtwEventRegister ({38ed3633-5e3f-5989-bf25-f0b1b3318c9b}, 0x7818d1c, (nil), 0x11ac92b8) stub.
0037:fixme:ntdll:EtwEventSetInformation (deadbeef, 2, 0x11ac9260, 53) stub
0037:fixme:crypt:SystemFunction041 (0x9d63768, 10, 0): stub [RtlDecryptMemory]
0037:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x9d64408 0x2341a0 0x234b90 (nil)
0037:fixme:combase:RoGetActivationFactory (L"Windows.Foundation.Diagnostics.AsyncCausalityTracer", {50850b26-267e-451b-a890-ab6a370245ee}, 0x237d08): semi-stub
0037:err:combase:RoGetActivationFactory Failed to find library for L"Windows.Foundation.Diagnostics.AsyncCausalityTracer"
0037:fixme:ntdll:EtwEventRegister ({2e5dba47-a3d2-4d16-8ee0-6671ffdcd7b5}, 0x7818d7c, (nil), 0x11acd508) stub.
0037:fixme:ntdll:EtwEventSetInformation (deadbeef, 2, 0x11acd4c0, 40) stub
0088:fixme:sync:SetWaitableTimerEx (0x5a0, 0x2bcffca0, 500, (nil), (nil), (nil), 50) semi-stub
0087:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x9d617e8 0x2bbeaf70 0x2bbeb960 (nil)
0087:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x9d6c4e8 0x2bbe9eb0 0x2bbea8a0 (nil)
0087:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x9d6c4e8 0x2bbe9eb0 0x2bbea8a0 (nil)
0087:fixme:winsock:convert_aiflag_w2u Unhandled windows AI_xxx flags 0x20000
0087:err:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request failed with status 0x2733
0087:err:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request failed with status 0x2733
0087:fixme:ntdll:EtwEventRegister ({6906e6e1-f9cd-5b3b-c846-27578fd8d69e}, 0x7818ddc, (nil), 0x11ae2bd8) stub.
0087:fixme:ntdll:EtwEventSetInformation (deadbeef, 2, 0x11ae2b88, 46) stub
0087:fixme:process:FlushProcessWriteBuffers : stub
008c:fixme:crypt:CertAddCertificateLinkToStore (0x9d82eb0, 0x9d82bb8, 00000004, (nil)): semi-stub
008b:fixme:shell:URL_ParseUrl failed to parse L"System.Runtime.Serialization"
008b:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x2c2553f8 0x2c0d60e0 0x2c0d6ad0 (nil)
008b:fixme:shell:URL_ParseUrl failed to parse L"SMDiagnostics"
008b:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x2c25abd8 0x2c0d8840 0x2c0d9230 (nil)
008b:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x2c25abd8 0x2c0d8840 0x2c0d9230 (nil)
008b:fixme:shell:URL_ParseUrl failed to parse L"System.ServiceModel.Internals"
008b:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 4 0x2c2591f8 0x2c0d47a0 0x2c0d5190 (nil)
008b:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 3 0x2c263a40 0x2c0d4f00 0x2c0d58f0 (nil)
008b:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 3 0x2c263a40 0x2c0d4f00 0x2c0d58f0 (nil)
008b:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 4 0x2c259210 0x2c0d4550 0x2c0d4f40 (nil)
008b:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 3 0x2c2591e8 0x2c0d4cb0 0x2c0d56a0 (nil)
008b:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 3 0x2c2591e8 0x2c0d4cb0 0x2c0d56a0 (nil)
008b:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 4 0x2c25ee00 0x2c0d6c10 0x2c0d7600 (nil)
008b:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 3 0x2c25ede0 0x2c0d7370 0x2c0d7d60 (nil)
008b:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 3 0x2c25ede0 0x2c0d7370 0x2c0d7d60 (nil)
008b:fixme:ntdll:EtwEventRegister ({c651f5f6-1c0d-492e-8ae1-b4efd7c9d503}, 0x7818edc, (nil), 0x11b29910) stub.
008b:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x2c25eda8 0x2c0d8460 0x2c0d8e50 (nil)
008d:fixme:bcrypt:BCryptCreateHash ignoring object buffer
008d:fixme:bcrypt:BCryptCreateHash ignoring object buffer
008d:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x2c2750c8 0xaa77280 0xaa77c70 (nil)
008d:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x2c2750c8 0xaa779e0 0xaa783d0 (nil)
008d:fixme:combase:RoGetParameterizedTypeInstanceIID stub: 2 0x2c2750c8 0xaa779e0 0xaa783d0 (nil)
008e:fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms"
008e:fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
008e:fixme:shell:URL_ParseUrl failed to parse L"Accessibility"
008d:fixme:ver:GetCurrentPackageId (0xaa77610 (nil)): stub
008d:fixme:ntdll:EtwEventRegister ({35167f8e-49b2-4b96-ab86-435b59336b5e}, 0x781874c, (nil), 0x11ab6678) stub.
008d:fixme:ntdll:EtwEventSetInformation (deadbeef, 2, 0x11ab6610, 65) stub
0037:fixme:win:EnumDisplayDevicesW ((null),0,0x239b90,0x00000000), stub!
0037:fixme:win:FlashWindowEx 0x23a030 - semi-stub
008b:fixme:thread:NtQueryInformationThread ThreadIsIoPending info class not supported yet
008c:fixme:thread:NtQueryInformationThread ThreadIsIoPending info class not supported yet
008c:fixme:thread:NtQueryInformationThread ThreadIsIoPending info class not supported yet
0087:fixme:thread:NtQueryInformationThread ThreadIsIoPending info class not supported yet
0089:fixme:thread:NtQueryInformationThread ThreadIsIoPending info class not supported yet

```
Please advise.

---

### Post by marchello_lippi2 on 2020-01-04
Update: As workspot application has also 32 bit version installer, I created 32 bit wine profile
```

WINEPREFIX="$HOME/prefix32" WINEARCH=win32 wine wineboot

```
And now I'm in process of installing dotnet 4.7.2 for 32 bit
```

WINEPREFIX="$HOME/prefix32" WINEARCH=win32 ~/winetricks --force dotnet472

```

Upd: 32 bit approach did not work for me, got initial error > [COLOR=#000000]*You need to run Windows Update on this system before you can install Workspot Client. See *[/COLOR][http://workspot.zendesk.com/hc/en-us/articles/209993933](http://workspot.zendesk.com/hc/en-us/articles/209993933)[COLOR=#000000]* for help.*[/COLOR]

---

### Post by marchello_lippi2 on 2020-01-04
ok, looking back into the latest trace, all 'token' mentions start from 'fixme' keyword, thus I believe this functionality is just not implemented in wine itself. Asked this on wine forum, but my messages are premoderated and did not appear online yet.

---

### Post by marchello_lippi2 on 2020-01-06
Ok, as a workaround, I use virtualbox with windows 10, it works fine...
Also got advise to try wine dev version, if doesn't help, then open wine bug ticket. Will do this when time permits.

---

### Post by marchello_lippi2 on 2020-01-12
[COLOR=#333333][FONT=&amp]Can't install both dev and stage versions.
[/FONT][/COLOR]```
[FONT=monospace][COLOR=#000000]user@pc:~$ sudo apt install --install-recommends wine-staging[/COLOR]
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine-staging : Depends: wine-staging-i386 (= 5.0~rc5~bionic)
                Depends: wine-staging-amd64 (= 5.0~rc5~bionic) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
user@pc:~$ sudo apt install --install-recommends wine-devel
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine-devel : Depends: wine-devel-i386 (= 5.0~rc5~bionic)
              Depends: wine-devel-amd64 (= 5.0~rc5~bionic) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
[/FONT]
```
[COLOR=#333333][FONT=&amp]also 
[/FONT][/COLOR]```
[FONT=monospace][COLOR=#000000]$ sudo apt-get install wine-devel-amd64[/COLOR]
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine-devel-amd64 : Depends: libfaudio0 but it is not installable
E: Unable to correct problems, you have held broken packages.
[/FONT]
```[COLOR=#333333][FONT=&amp]
Please advise.[/FONT][/COLOR]

---

