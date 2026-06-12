---
title: "India Income Tax Utility for AY 2021-22."
date: 2021-04-17
forum: Wine
---

### Post by kagashe on 2021-04-17
Since AY 2013-14 India Income Tax website was providing utility based on JRE and I could use it on Ubuntu to prepare the Income Tax Return. The output of the utility was xml file which you had to upload to the website to file the return.

For AY 2021-22 they have switched to JSON but providing the utility only for Windows. The utility for Linux may or may not come.

I downloaded the exe file and installed it using Wine on Ubuntu 20.04 but the installed exe provided blank screen.

Then I added [WineHq repository]("https://wiki.winehq.org/Ubuntu") and installed Wine 6.6 (Staging).
The installed utility works till you prepare the return, verify and validate it.  On last page when you click to download the output JSON file it says "Download failed".

The utility seems to be built on Electron.

NB: On Windows the utility is working including download of output JSON file.

The [download link]("https://www.incometaxindiaefiling.gov.in/downloads/incomeTaxReturnUtilities?lang=eng") for income tax website for exe file.

Kamalakar

---

### Post by TheFu on 2021-04-20
You've made statements. Is there a question that someone might be able to help?
Can't you just print out the paper and mail it in?  I know ZERO about India's tax laws.

---

### Post by kagashe on 2021-04-21
> **TheFu said:**
> You've made statements. Is there a question that someone might be able to help?
Can't you just print out the paper and mail it in?  I know ZERO about India's tax laws.

I wrote "On last page when you click to download the output JSON file it says "Download failed". Question is how to make it work and download the output file which is the purpose of the utility.

I have run the application with the command:
$ wine ITDe-Filing.exe &> mylog.txt

and get the following error in mylog.txt
```
02b8:fixme:shell:file_operation_SetOperationFlags (0x27fc80, 100e14): stub.
Download failed: interrupted
```

The entire text of mylog.txt after removing repeated entries is as follows:
```
002c:fixme:winediag:LdrInitializeThunk wine-staging  is a testing version containing experimental patches.
002c:fixme:winediag:LdrInitializeThunk Please mention your exact version when filing bug reports on winehq.org.
002c:fixme:font:get_name_record_codepage encoding 20 not handled, platform 1.
0060:err:winedevice:ServiceMain Failed to load L"C:\\windows\\system32\\win32k.sys"
0024:fixme:heap:RtlSetHeapInformation 00000000 1 00000000 0 stub

0024:fixme:ntdll:EtwEventRegister ({d2d578d9-2936-45b6-a09f-30e32715f42d}, 01E37670, 057B6E30, 05813F88) stub.
0024:fixme:nls:RtlGetThreadPreferredUILanguages 00000038, 0021FC00, 00000000 0021FBFC
0024:fixme:nls:get_dummy_preferred_ui_language (0x38 0021FC00 00000000 0021FBFC) returning a dummy value (current locale)
 SYSTEM_PERFORMANCE_INFORMATION
013c:fixme:kernelbase:AppPolicyGetThreadInitializationType FFFFFFFA, 0909FEF8
0024:fixme:ver:GetPackageFamilyName (FFFFFFFF 0021F9B8 0021F9BC): stub
0024:fixme:process:GetProcessMitigationPolicy (FFFFFFFF, 4, 0021EE64, 4): stub
0160:fixme:font:get_name_record_codepage encoding 20 not handled, platform 1.
0024:fixme:msg:ChangeWindowMessageFilterEx 0002006A 4a 1 00000000
0024:fixme:combase:RoGetActivationFactory (L"Windows.UI.ViewManagement.UIViewSettings", {3694dbf9-8f68-44be-8ff5-195c98ede8a6}, 0021F820): semi-stub
0024:err:combase:RoGetActivationFactory Failed to find library for L"Windows.UI.ViewManagement.UIViewSettings"
0024:fixme:winsock:WSALookupServiceBeginW (0x21f8e0 0x00000ff0 0x21f91c) Stub!
0024:fixme:iphlpapi:NotifyAddrChange (Handle 0x21fb0c, overlapped 0x975d9d0): stub
0024:fixme:system:GetDisplayConfigBufferSizes (0x2 0021F764 0021F760): semi-stub
0024:fixme:system:DisplayConfigGetDeviceInfo Unimplemented packet type: 11
0024:fixme:combase:RoActivateInstance (08EE4F40, 0021F618): semi-stub
0024:fixme:combase:RoGetActivationFactory (L"Windows.UI.ViewManagement.UISettings", {00000035-0000-0000-c000-000000000046}, 0021F5CC): semi-stub
0024:err:combase:RoGetActivationFactory Failed to find library for L"Windows.UI.ViewManagement.UISettings"
0170:fixme:wtsapi:WTSRegisterSessionNotification Stub 00020062 0x00000001
0178:fixme:ntdll:NtFilterToken support for restricting sids not yet implemented
0178:fixme:ntdll:NtSetInformationToken TokenIntegrityLevel stub!
0178:fixme:process:GetProcessMitigationPolicy (FFFFFFFF, 5, 0581E8F8, 16): stub
0178:fixme:process:CreateProcessInternalW Unsupported attribute 0x2000e.
0178:fixme:ntdll:NtQueryInformationToken QueryInformationToken( ..., TokenAppContainerSid, ...) semi-stub
018c:fixme:heap:RtlSetHeapInformation 00000000 1 00000000 0 stub
018c:fixme:ntdll:EtwEventRegister ({d2d578d9-2936-45b6-a09f-30e32715f42d}, 01E37670, 057B6E30, 05813F88) stub.
018c:fixme:process:GetProcessMitigationPolicy (FFFFFFFF, 4, 05C0FD14, 4): stub
0024:fixme:service:I_ScRegisterDeviceNotification Notification filters are not yet implemented.
0024:fixme:system:EnableNonClientDpiScaling (00010080): stub
0170:fixme:wtsapi:WTSRegisterSessionNotification Stub 00020068 0x00000000
0024:fixme:dwmapi:DwmSetWindowAttribute (00010080, 2, 0021EF28, 4) stub
0178:fixme:sync:NtSetInformationJobObject stub: 0x538 4 0xc2df72c 4
0024:fixme:system:GetDisplayConfigBufferSizes (0x2 0021E4F4 0021E4F0): semi-stub
0024:fixme:system:DisplayConfigGetDeviceInfo Unimplemented packet type: 11
0024:fixme:shcore:GetCurrentProcessExplicitAppUserModelID 0021E9EC: stub
0024:fixme:manipulation:viewport_ActivateConfiguration 08EF1868, 823
0024:fixme:manipulation:viewport_SetViewportOptions 08EF1868, 2
0024:fixme:manipulation:viewport_AddEventHandler 08EF1868, 00010088, 0A016568, 0A03CBAC
0024:fixme:manipulation:viewport_Stop 08EF1868
0024:fixme:manipulation:viewport_RemoveEventHandler 08EF1868, 4543317
0024:fixme:manipulation:viewport_Abandon 08EF1868
0024:fixme:manipulation:direct_manip_Deactivate 08EE4A90, 00010088
http://125.16.30.183:2033/updates/win/
09:55:46.362 > Checking for update
09:55:46.509 > [code-updater ] AppPath: C:\users\vidya\Local Settings\Application Data\Programs\ITDe-Filing\resources\app.asar/
01b4:fixme:font:get_name_record_codepage encoding 20 not handled, platform 1.
01b4:fixme:font:get_name_record_codepage encoding 20 not handled, platform 1.
09:55:46.516 > [code-updater ] AppPathFolder: C:\users\vidya\Local Settings\Application Data\Programs\ITDe-Filing\resources\
09:55:46.521 > [code-updater ] 0.1.1
01b4:fixme:heap:RtlSetHeapInformation 00000000 1 00000000 0 stub
01b4:fixme:ntdll:EtwEventRegister ({d2d578d9-2936-45b6-a09f-30e32715f42d}, 01E37670, 057B6E30, 05813F88) stub.
01b4:fixme:process:GetProcessMitigationPolicy (FFFFFFFF, 4, 05C0FD14, 4): stub
01e0:fixme:winsock:WSALookupServiceBeginW (0x909f230 0x00000ff0 0x909f26c) Stub!
01e0:fixme:iphlpapi:NotifyAddrChange (Handle 0x909f45c, overlapped 0x759e678): stub
01c0:fixme:font:get_name_record_codepage encoding 20 not handled, platform 1.
01e0:fixme:wlanapi:WlanEnumInterfaces (00000001, 00000000, 0909EDD4) semi-stub
0024:fixme:manipulation:viewport_ActivateConfiguration 08EF2868, 823
0024:fixme:manipulation:viewport_SetViewportOptions 08EF2868, 2
0024:fixme:manipulation:viewport_AddEventHandler 08EF2868, 00010088, 09FE26C8, 10338184
0024:fixme:manipulation:viewport_Stop 08EF2868
0024:fixme:manipulation:viewport_RemoveEventHandler 08EF2868, 0
0024:fixme:manipulation:viewport_Abandon 08EF2868
0024:fixme:manipulation:direct_manip_Deactivate 08EF5AA8, 00010088
0024:fixme:manipulation:viewport_ActivateConfiguration 08EF15A8, 823
0024:fixme:manipulation:viewport_SetViewportOptions 08EF15A8, 2
0024:fixme:manipulation:viewport_AddEventHandler 08EF15A8, 00010088, 10337D68, 09FD99A4

null
null
014c:fixme:file:NtLockFile I/O completion on lock not implemented yet
0024:fixme:iphlpapi:GetBestRoute2 (0x103530c3, 0, (nil), 0x10353525, 0x00000000, 0x21e2f8, 0x21e2dc): stub
0024:fixme:system:GetDisplayConfigBufferSizes (0x2 0021F3C4 0021F3C0): semi-stub
0024:fixme:system:DisplayConfigGetDeviceInfo Unimplemented packet type: 11
01c0:fixme:heap:RtlSetHeapInformation 00000000 1 00000000 0 stub
01c0:fixme:ntdll:EtwEventRegister ({d2d578d9-2936-45b6-a09f-30e32715f42d}, 01E37670, 057B6E30, 05813F88) stub.
01c0:fixme:process:GetProcessMitigationPolicy (FFFFFFFF, 4, 05C0FD14, 4): stub
01c0:fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
01c8:fixme:font:get_name_record_codepage encoding 20 not handled, platform 1.
01c8:fixme:font:get_name_record_codepage encoding 20 not handled, platform 1.
01ec:fixme:file:NtLockFile I/O completion on lock not implemented yet
09:55:47.371 > [code-updater ] Error: connect ECONNREFUSED 127.0.0.1:4000
    at TCPConnectWrap.afterConnect [as oncomplete] (net.js:1056:14)
09:55:47.390 > [code-updater ] Could not connect
01e0:fixme:wlanapi:WlanEnumInterfaces (00000001, 00000000, 0909EDD4) semi-stub
01c8:fixme:heap:RtlSetHeapInformation 00000000 1 00000000 0 stub
01c8:fixme:ntdll:EtwEventRegister ({d2d578d9-2936-45b6-a09f-30e32715f42d}, 01E37670, 057B6E30, 05813F88) stub.
01c8:fixme:process:GetProcessMitigationPolicy (FFFFFFFF, 4, 05C0FD14, 4): stub
01c8:fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
09:55:47.614 > Error: Error: net::ERR_CONNECTION_REFUSED
(node:32) UnhandledPromiseRejectionWarning: Error: net::ERR_CONNECTION_REFUSED
(node:32) UnhandledPromiseRejectionWarning: Error: net::ERR_CONNECTION_REFUSED
(node:32) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 1)
(node:32) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). (rejection id: 1)
(node:32) [DEP0018] DeprecationWarning: Unhandled promise rejections are deprecated. In the future, promise rejections that are not handled will terminate the Node.js process with a non-zero exit code.
(node:32) [DEP0018] DeprecationWarning: Unhandled promise rejections are deprecated. In the future, promise rejections that are not handled will terminate the Node.js process with a non-zero exit code.
0258:fixme:kernelbase:AppPolicyGetThreadInitializationType FFFFFFFA, 0B05FEF8
01c8:fixme:ver:GetPackageFamilyName (FFFFFFFF 05C0E6AC 05C0E6B0): stub
018c:fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
0264:fixme:thread:QueryThreadCycleTime (00000138,083BFDF0): stub!
018c:fixme:d3d11:d3d11_device_CheckFeatureSupport Returning fake Options support data.
nt1 Ignored present parameters 0x5c0f260.
0268:fixme:d3d:state_linepattern_w Setting line patterns is not supported in OpenGL core contexts.
0294:fixme:kernelbase:AppPolicyGetThreadInitializationType FFFFFFFA, 0B1BFEF8
01c0:fixme:ver:GetPackageFamilyName (FFFFFFFF 05C0E6AC 05C0E6B0): stub
0024:fixme:server:invoke_system_apc syscall frame changed in APC function, frame (nil), saved_frame 0x21f5d4.
01c0:fixme:thread:QueryThreadCycleTime (FFFFFFFE,05C0F7D0): stub!
021c:fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
018c:fixme:dxgi:d3d11_swapchain_Present1 Ignored present parameters 0x5c0f250.
0180:fixme:file:ReplaceFileW Ignoring flags 2
01c0:fixme:dwrite:dwritefontface5_HasVariations 05C83178: stub
02ac:fixme:file:NtLockFile I/O completion on lock not implemented yet
0024:fixme:manipulation:viewport_ActivateConfiguration 08F11800, 823
0024:fixme:manipulation:viewport_SetViewportOptions 08F11800, 2
0024:fixme:manipulation:viewport_AddEventHandler 08F11800, 00010092, 10388F70, 1044DE14
01c8:fixme:thread:QueryThreadCycleTime (FFFFFFFE,05C0F7C0): stub!
018c:fixme:dxgi:d3d11_swapchain_Present1 Ignored present parameters 0x5c0f250.
 SYSTEM_PERFORMANCE_INFORMATION
02d4:fixme:ntdll:EtwEventUnregister (deadbeef) stub.
02d4:fixme:kernelbase:AppPolicyGetProcessTerminationMethod FFFFFFFA, 05C0FEAC
01a8:fixme:shell:file_operation_SetOperationFlags (0x8f12288, 100e14): stub.
Download failed: interrupted
018c:fixme:dxgi:d3d11_swapchain_Present1 Ignored present parameters 0x5c0f250.

```
There are so many fixme since it is Development Version of Wine.

Please note that the application is built on Electron and uses .NET on Windows and Mono on wine.

Kamalakar

---

### Post by mastablasta on 2021-04-22
might be easier to create a virtual machine (e.g. virtualbox) with windows in it.

---

