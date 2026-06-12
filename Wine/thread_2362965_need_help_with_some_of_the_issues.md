---
title: "need help with some of the issues"
date: 2017-06-04
forum: Wine
---

### Post by ahmad-nahali on 2017-06-04
1.when I try to launch LOL it wont start and this is what I get in debug.

```
[06/04/17 14:15:00] - Running wine-1.9.2-LeagueOfLegends5 lol.launcher.admin.exe (Working directory : /home/ahmad/.PlayOnLinux/wineprefix/LeagueOfLegends/drive_c/Riot Games/League of Legends)
[06/04/17 14:15:02] - Running wine-1.9.2-LeagueOfLegends5 lol.launcher.admin.exe (Working directory : /home/ahmad/.PlayOnLinux/wineprefix/LeagueOfLegends/drive_c/Riot Games/League of Legends)
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33f8c4 1 C) semi-stub
wine: Call from 0x7b83eb22 to unimplemented function api-ms-win-crt-runtime-l1-1-0.dll._initialize_onexit_table, aborting
fixme:advapi:EventRegister {2f9efe86-4af7-4f37-a40f-94b909a157d6}, 0x484200, 0x6851d0, 0x68e5d0
fixme:advapi:EventRegister {ea08c559-95a8-4aa2-afa6-18738eec6d37}, 0x484200, 0x685198, 0x68e5c8
fixme:advapi:EventRegister {10f6728c-ef92-4bf1-8397-49e693a6eb74}, 0x484200, 0x685208, 0x68e520
fixme:advapi:EventRegister {46dd7f96-60cb-416b-8085-da5cd8f491dd}, 0x484200, 0x685240, 0x68e608
fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
fixme:ver:GetCurrentPackageId (0x33fcbc (nil)): stub
fixme:advapi:EventRegister {2f9efe86-4af7-4f37-a40f-94b909a157d6}, 0x100555b0, 0x100906c0, 0x10094ad0
fixme:advapi:EventRegister {ea08c559-95a8-4aa2-afa6-18738eec6d37}, 0x100555b0, 0x10090768, 0x10094ac8
fixme:advapi:EventRegister {10f6728c-ef92-4bf1-8397-49e693a6eb74}, 0x100555b0, 0x100906f8, 0x10094b10
fixme:advapi:EventRegister {46dd7f96-60cb-416b-8085-da5cd8f491dd}, 0x100555b0, 0x10090730, 0x10094b08
fixme:advapi:EventRegister {2f9efe86-4af7-4f37-a40f-94b909a157d6}, 0x4b1c90, 0x89ad10, 0x8d9e10
fixme:advapi:EventRegister {ea08c559-95a8-4aa2-afa6-18738eec6d37}, 0x4b1c90, 0x89adb8, 0x8d9e08
fixme:advapi:EventRegister {10f6728c-ef92-4bf1-8397-49e693a6eb74}, 0x4b1c90, 0x89ad48, 0x8d9e50
fixme:advapi:EventRegister {46dd7f96-60cb-416b-8085-da5cd8f491dd}, 0x4b1c90, 0x89ad80, 0x8d9e48
fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
fixme:ver:GetCurrentPackageId (0x33f1b4 (nil)): stub
fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
fixme:advapi:RegisterTraceGuidsW (0x762732, (nil), {f7b697a3-4db5-4d3b-be71-c4d284e6592f}, 7, 0x899bac, (null), (null), 0x8d5620): stub
fixme:advapi:RegisterTraceGuidsW   register trace class {72b14a7d-704c-423e-92f8-7e6d64bcb92a}
fixme:advapi:RegisterTraceGuidsW   register trace class {e2091f8a-1e0a-4731-84a2-0dd57c8a5261}
fixme:advapi:RegisterTraceGuidsW   register trace class {e8a3bf1f-a86b-4390-9c60-5390b969d22c}
fixme:advapi:RegisterTraceGuidsW   register trace class {5727a00f-50be-4519-8256-f7699871fecb}
fixme:advapi:RegisterTraceGuidsW   register trace class {7e854ec7-cdc4-405a-b5b2-aaf7c9e7d40c}
fixme:advapi:RegisterTraceGuidsW   register trace class {79a60dc6-5fc8-4952-a41c-1163aeec5eb8}
fixme:advapi:RegisterTraceGuidsW   register trace class {2718d25b-5bf5-4479-8e88-babc64bdbfca}
fixme:process:GetNumaHighestNodeNumber (0x33eea8): semi-stub
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:file:UnlockFileEx Unimplemented overlapped operation
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:wbemprox:enum_class_object_Next timeout not supported
err:winediag:init_driver_info Invalid GPU override 8086:1916 specified, ignoring.
fixme:win:EnumDisplayDevicesW ((null),0,0x340d5c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x340d3b8,0x00000000), stub!
fixme:ddraw:ddraw7_Initialize Ignoring guid {aeb2cdd4-6e41-43ea-941c-8361cc760781}.
err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
fixme:advapi:EventRegister {2f9efe86-4af7-4f37-a40f-94b909a157d6}, 0x482ec0, 0x6dd120, 0x6e66d0
fixme:advapi:EventRegister {ea08c559-95a8-4aa2-afa6-18738eec6d37}, 0x482ec0, 0x6dd1c8, 0x6e66c8
fixme:advapi:EventRegister {10f6728c-ef92-4bf1-8397-49e693a6eb74}, 0x482ec0, 0x6dd158, 0x6e6710
fixme:advapi:EventRegister {46dd7f96-60cb-416b-8085-da5cd8f491dd}, 0x482ec0, 0x6dd190, 0x6e6708
fixme:ver:GetCurrentPackageId (0x33f518 (nil)): stub
fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
fixme:advapi:RegisterTraceGuidsW (0x62e5a0, (nil), {f7b697a3-4db5-4d3b-be71-c4d284e6592f}, 7, 0x6dcb68, (null), (null), 0x6e34b0): stub
fixme:advapi:RegisterTraceGuidsW   register trace class {72b14a7d-704c-423e-92f8-7e6d64bcb92a}
fixme:advapi:RegisterTraceGuidsW   register trace class {e2091f8a-1e0a-4731-84a2-0dd57c8a5261}
fixme:advapi:RegisterTraceGuidsW   register trace class {e8a3bf1f-a86b-4390-9c60-5390b969d22c}
fixme:advapi:RegisterTraceGuidsW   register trace class {5727a00f-50be-4519-8256-f7699871fecb}
fixme:advapi:RegisterTraceGuidsW   register trace class {7e854ec7-cdc4-405a-b5b2-aaf7c9e7d40c}
fixme:advapi:RegisterTraceGuidsW   register trace class {79a60dc6-5fc8-4952-a41c-1163aeec5eb8}
fixme:advapi:RegisterTraceGuidsW   register trace class {2718d25b-5bf5-4479-8e88-babc64bdbfca}
fixme:process:GetNumaHighestNodeNumber (0x33f05c): semi-stub
fixme:process:SetProcessDEPPolicy (3): stub
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:imm:ImmDisableTextFrameService Stub
fixme:thread:GetThreadPreferredUILanguages 56, 0x33ec58, (nil) 0x33ec5c
fixme:winsock:WSALookupServiceBeginW (0x33eb2c 0x00000ff0 0x33eb68) Stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x33ec94, overlapped 0x19aa7c): stub
fixme:win:RegisterDeviceNotificationW (hwnd=0x2005e, filter=0x33eca0,flags=0x00000000) returns a fake device notification handle!
fixme:win:RegisterDeviceNotificationW (hwnd=0x2005e, filter=0x33eca0,flags=0x00000000) returns a fake device notification handle!
fixme:ver:GetCurrentPackageId (0x2e3ea08 (nil)): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33e5c4,0x00000000), stub!
fixme:ver:GetCurrentPackageId (0x362e260 (nil)): stub
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x20078 0x00000000
fixme:msctf:InputProcessorProfileMgr_GetActiveProfile (0x3a840b8)->({34745c63-b2f0-4784-8b67-5e12c8701a31} 0x33ea6c)
fixme:advapi:RegisterTraceGuidsW (0x10144ff0, 0x11fec2e0, {3dada31d-19ef-4dc1-b345-037927193422}, 1, 0x11fc0360, (null), (null), 0x11fec2f8): stub
fixme:advapi:RegisterTraceGuidsW   register trace class {00000000-0000-0000-0000-000000000000}
err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
fixme:advapi:EventRegister {2f9efe86-4af7-4f37-a40f-94b909a157d6}, 0x482ec0, 0x6dd120, 0x6e66d0
fixme:advapi:EventRegister {ea08c559-95a8-4aa2-afa6-18738eec6d37}, 0x482ec0, 0x6dd1c8, 0x6e66c8
fixme:advapi:EventRegister {10f6728c-ef92-4bf1-8397-49e693a6eb74}, 0x482ec0, 0x6dd158, 0x6e6710
fixme:advapi:EventRegister {46dd7f96-60cb-416b-8085-da5cd8f491dd}, 0x482ec0, 0x6dd190, 0x6e6708
fixme:ver:GetCurrentPackageId (0x33f518 (nil)): stub
fixme:process:SetProcessDEPPolicy (3): stub
fixme:heap:RtlSetHeapInformation (nil) 1 (nil) 0 stub
fixme:advapi:RegisterTraceGuidsW (0x10144ff0, 0x11fec2e0, {3dada31d-19ef-4dc1-b345-037927193422}, 1, 0x11fc0360, (null), (null), 0x11fec2f8): stub
fixme:advapi:RegisterTraceGuidsW   register trace class {00000000-0000-0000-0000-000000000000}
fixme:gdi:GdiInitializeLanguagePack stub
fixme:ver:GetCurrentPackageId (0x297ea08 (nil)): stub
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {33d9a761-90c8-11d0-bd43-00a0c911ce86} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:wbemprox:client_security_SetBlanket 0x7d1b1ba8, 0x3c7b5b8, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0x7d1b1ba8
fixme:win:EnumDisplayDevicesW ((null),0,0x340dfd8,0x00000000), stub!
fixme:module:load_library unsupported flag(s) used (flags: 0x00000800)
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:ver:GetCurrentPackageId (0x683ea08 (nil)): stub
fixme:win:FlashWindowEx 0x33e524 - semi-stub
fixme:cryptnet:verify_cert_revocation_from_aia_ext OCSP URL = L"http://ocsp2.globalsign.com/cloudsslsha2g3"
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x20078
fixme:advapi:UnregisterTraceGuids deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:win:UnregisterDeviceNotification (handle=0xcafeaffe), STUB!
fixme:win:UnregisterDeviceNotification (handle=0xcafeaffe), STUB!
fixme:iphlpapi:CancelIPChangeNotify (overlapped 0x19aa7c): stub
fixme:advapi:UnregisterTraceGuids deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:file:UnlockFileEx Unimplemented overlapped operation
fixme:file:UnlockFileEx Unimplemented overlapped operation
wine: Call from 0x7b83eb22 to unimplemented function api-ms-win-crt-runtime-l1-1-0.dll._initialize_onexit_table, aborting
err:module:attach_process_dlls "zlib.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Riot Games\\League of Legends\\RADS\\projects\\league_client\\releases\\0.0.0.78\\deploy\\LeagueClient.exe" failed, status 80000100
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33fa78 1 C) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33f8b8 1 C) semi-stub
```

2.How do install Java 64 bit and install minecraft?

---

### Post by howefield on 2017-06-04
Thread moved to the "*Wine*" forum.

---

