---
title: "wine staging scrollbar bug"
date: 2018-10-14
forum: Wine
---

### Post by redmisao on 2018-10-14
Hello! I'm having an issue running a certain program, BioEdit 7.0.5, with wine staging.
Specifically, the scrollbars doesn't show up, so I can't move properly inside the windows, look at the attached picture for reference.
I had been using wine stable before (3.0.3) and BioEdit showed no problems, until I needed to change wine's version to staging (to test games :oops:). Then the scrollbars became "hollow" or transparent.
As far as I know, there is no difference between Windows versions or enabling CSMT, VAAPI and/or EAX.

Additional information:
Wine version: wine-3.18 (Staging)
Ubuntu version: Ubuntu 18.04.1 LTS
I've modified the following in winetricks: installed corefonts and ie8  ("The installation doesn't support your architecture" error), yet the  scrollbars remain glitched even without installing these two.
Video Card: VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R4/R5 Graphics] (rev 45).

Running inside the terminal gives these errors:
```
wine: created the configuration directory '/home/redmisao/.wine'
 0009:err:file:init_redirects cannot open L"C:\\windows" (c000000f)
 000b:fixme:winediag:start_process Wine Staging 3.18 is a testing version containing experimental patches.
 000b:fixme:winediag:start_process Please mention your exact version when filing bug reports on winehq.org.
 0012:err:ole:marshal_object couldn't get IPSFactory buffer for interface {00000131-0000-0000-c000-000000000046}
 0012:err:ole:marshal_object couldn't get IPSFactory buffer for interface {6d5140c1-7436-11ce-8034-00aa006009fa}
 0012:err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80004002
 0012:err:ole:CoMarshalInterface Failed to marshal the interface {6d5140c1-7436-11ce-8034-00aa006009fa}, 80004002
 0012:err:ole:get_local_server_stream Failed: 80004002
 0014:err:ole:marshal_object couldn't get IPSFactory buffer for interface {00000131-0000-0000-c000-000000000046}
 0014:err:ole:marshal_object couldn't get IPSFactory buffer for interface {6d5140c1-7436-11ce-8034-00aa006009fa}
 0014:err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80004002
 0014:err:ole:CoMarshalInterface Failed to marshal the interface {6d5140c1-7436-11ce-8034-00aa006009fa}, 80004002
 0014:err:ole:get_local_server_stream Failed: 80004002
 0017:fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
 0017:err:mscoree:LoadLibraryShim error reading registry key for installroot
 0017:err:mscoree:LoadLibraryShim error reading registry key for installroot
 0017:err:mscoree:LoadLibraryShim error reading registry key for installroot
 0017:err:mscoree:LoadLibraryShim error reading registry key for installroot
 0017:fixme:msi:internal_ui_handler internal UI not implemented for message 0x0b000000 (UI level = 1)
 0017:fixme:msi:internal_ui_handler internal UI not implemented for message 0x0b000000 (UI level = 1)
 001b:fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
 001b:fixme:msi:internal_ui_handler internal UI not implemented for message 0x0b000000 (UI level = 1)
 001b:fixme:msi:internal_ui_handler internal UI not implemented for message 0x0b000000 (UI level = 1)
 0010:err:winediag:SECUR32_initNTLMSP ntlm_auth was not  found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your  path. Usually, you can find it in the winbind package of your  distribution.
 0010:fixme:dwmapi:DwmIsCompositionEnabled 0x6dbd1518
 001d:fixme:iphlpapi:NotifyIpInterfaceChange (family 0,  callback 0x69ebd3de, context 0x90c250, init_notify 0, handle 0x11cfa10):  stub
 0039:fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
 0039:fixme:msi:internal_ui_handler internal UI not implemented for message 0x0b000000 (UI level = 1)
 0039:fixme:msi:internal_ui_handler internal UI not implemented for message 0x0b000000 (UI level = 1)
 0037:err:winediag:SECUR32_initNTLMSP ntlm_auth was not  found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your  path. Usually, you can find it in the winbind package of your  distribution.
 0037:fixme:dwmapi:DwmIsCompositionEnabled 0x6d5d3018
 003b:fixme:iphlpapi:NotifyIpInterfaceChange (family 0,  callback 0x6a0cb608, context 0x83b6c0, init_notify 0, handle 0x104fc88):  stub
 wine: configuration in '/home/redmisao/.wine' has been updated.
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\comdlg32.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\comdlg32.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\shell32.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\shell32.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\shlwapi.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\shlwapi.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\user32.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\user32.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\gdi32.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\gdi32.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\advapi32.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\advapi32.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\version.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\version.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\aclui.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\aclui.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\usp10.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\usp10.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\imm32.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\imm32.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\winspool.drv" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\winspool.drv" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\ole32.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\ole32.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\rpcrt4.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\rpcrt4.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\winmm.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\winmm.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\uxtheme.dll" because of wrong architecture
 0009:fixme:module:find_dll_file skipping L"C:\\windows\\system32\\uxtheme.dll" because of wrong architecture
 004c:fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
 004c:fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
```

---

