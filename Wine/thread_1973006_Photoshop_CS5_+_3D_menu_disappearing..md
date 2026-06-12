---
title: "Photoshop CS5 + 3D menu disappearing."
date: 2012-05-04
forum: Wine
---

### Post by Janiporo on 2012-05-04
Video:Nvidia EN8400GS
Motherboard: 
-Asrock K10N78D
-4 gigs memory
-AMD Athlon X2 64bit 5200+ (If I remember correctly)

Software:
-Xubuntu 12.04 / 32bit
-Wine 1.4
-Photoshop CS5 (12.0.4 x32)
-OpenGL 3.3 ("3.3.0 NVIDIA 295.40" is what window$ program "OpenGL Extensions Viewer 4.04" running under wine reports, for some reason it says memory is 0MB)
-Compiz enabled or disabled, does not matter
This might effect ubuntu / Kubuntu also.

Fresh Photoshop CS5 install using this guide --> [http://diogoosorio.com/blog/entry/how-to-install-photoshop-cs5-ubuntu-mint](http://diogoosorio.com/blog/entry/how-to-install-photoshop-cs5-ubuntu-mint)

When installed and start up application --> I have 3D menu, but when I enable OpenGL from settings 3d Menu disappears :(

Can not get it back without reinstall O_o

Any ideas?

I installed photoshop to another window$ machine, so some registry setting might be off? (did NOT want to install that peace of **** to this computer)

Also could be that wine does not know how to use OpenGL? I read somewhere that if computer (in window$) is not capable for 3D OpenGL, 3D menu will not appear.

Also having trouble assigning del-button to "command clear", but that is solvable, did it once allready (don't remember how :rolleyes:)

Suggestions?

(I think proper place for this is Ubuntu Forums > The Ubuntu Forum Community > Other Community Discussions > Gaming & Leisure > Wine, But I dont know how to move this)

---

### Post by Janiporo on 2012-05-04
More data.

Installed .NET framework 2.0, some test program demanded it to test open gl. It seems to crash in some options O_o


Here is terminal output with workind 3D (fresh install). Output is copied from start-state to --> program running-state:
```
STARTING UP WITH WORKING 3D
janiporo@janiporo-pc:~/Työpöytä$ wine "/home/janiporo/.wine/drive_c/Program Files/Adobe/Adobe Photoshop CS5/Photoshop.exe"
fixme:process:SetProcessShutdownParameters (00000380, 00000000): partial stub.
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-w0yBGm/pkcs11: Tiedostoa tai hakemistoa ei ole
err:shell:HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:system:SetProcessDPIAware stub!
fixme:ntdll:NtSetInformationToken unimplemented class 24
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x21f1fc 0x21f208 0x21f2d0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD" 1 -2147483644 0x21f29c 0x21f2a8 0x21f370 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x21f2c4 0x21f2d0 0x21f398 (nil)
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x21f3f0, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x32d69c)
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\janiporo\\Temp\\swtag.log" 1 -2147483644 0x21fd94 0x21fda0 0x60304a8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data\\regid.1986-12.com.adobe" 1 -2147483644 0x21fd94 0x21fda0 0x60304a8 (nil)
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-w0yBGm/pkcs11: Tiedostoa tai hakemistoa ei ole
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:win:EnumDisplayDevicesW ((null),0,0x32e7b8,0x00000000), stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),1,3,(nil),0,(nil)) - stub!
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
Failed to find Node Failed to find Node Failed to find Node Failed to find Node Failed to find Node Failed to find Node Failed to find Node Failed to find Node fixme:wia:wiadevmgr_QueryInterface interface {00000003-0000-0000-c000-000000000046} not implemented
fixme:wia:wiadevmgr_QueryInterface interface {00000003-0000-0000-c000-000000000046} not implemented
Failed to find Node fixme:font:WineEngRemoveFontResourceEx (L"C:\\Program Files\\adobe\\Adobe Photoshop CS5\\Required\\\\ADMUI3.fon", 0, (nil)): stub
Failed to find Node Failed to find Node fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x3fbf534 0x3fbf540 0x3fbf608 (nil)
Failed to find Node Failed to find Node Failed to find Node Failed to find Node Failed to find Node Failed to find Node fixme:imm:ImmReleaseContext (0x10a1a, 0x3e999c8): stub
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD" 1 -2147483644 0x624407c 0x6244088 0x6244150 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x62440a4 0x62440b0 0x6244178 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x62440a4 0x62440b0 0x6244178 (nil)
fixme:dwmapi:DwmIsCompositionEnabled 0x32ed44
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x20058 0x00000001
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x60c969c 0x60c96a8 0x1e9bc8 (nil)
fixme:win:DisableProcessWindowsGhosting : stub
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=(nil)): stub
fixme:win:LockWindowUpdate (0x20058), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=(nil)): stub
fixme:dciman:DCICreatePrimary 0x1728 0xea632ac
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETTASKBARPOS, hwnd=(nil)): stub
fixme:win:LockWindowUpdate (0x20058), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x20058), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:ole:CoResumeClassObjects stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x606fa34 0x606fa40 0x606fa70 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD" 1 -2147483644 0x606fa34 0x606fa40 0x608ae80 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x606fa34 0x606fa40 0x608ae80 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\janiporo\\Temp\\swtag.log" 1 -2147483644 0x606fa34 0x606fa40 0x608ae80 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data\\regid.1986-12.com.adobe" 1 -2147483644 0x606fa34 0x606fa40 0x608ae80 (nil)
fixme:exec:SHELL_execute flags ignored: 0x00004000
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x6437eec 0x6437ef8 0x6437fd8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x6437eec 0x6437ef8 0x6437fd8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x6437eec 0x6437ef8 0x6437fd8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x6437eec 0x6437ef8 0x6437fd8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x6437eec 0x6437ef8 0x6437fd8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x6437eec 0x6437ef8 0x6437fd8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x6437eec 0x6437ef8 0x6437fd8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x6437eec 0x6437ef8 0x6437fd8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x6437eec 0x6437ef8 0x6437fd8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x6437eec 0x6437ef8 0x6437fd8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x6437eec 0x6437ef8 0x6437fd8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x6437eec 0x6437ef8 0x6437fd8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x6437f14 0x6437f20 0x6438000 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x6437f14 0x6437f20 0x6438000 (nil)
fixme:win:LockWindowUpdate (0x20058), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:imm:ImmReleaseContext (0x10e74, 0x62df890): stub
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl discovery via DHCP not supported
Failed to find Node Failed to find Node Failed to find Node Failed to find Node 
```

Here is same shutting down (Output is copied from running-state to --> program ending-state):
```
SHUTTING DOWN WITH WORKING 3D:
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:ole:CoSuspendClassObjects 
fixme:font:WineEngRemoveFontResourceEx (L"C:\\Program Files\\adobe\\Adobe Photoshop CS5\\Required\\\\ADMUI3.fon", 0, (nil)): stub
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD" 1 -2147483644 0x6033abc 0x6033ac8 0x6234048 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x1e9a8c 0x1e9a98 0x6226d70 (nil)
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
err:ole:get_unmarshaler_from_stream Failed to read common OBJREF header, 0x00000000
```



And now the same thing with not working 3D:
```

STARTING UP WITHOUT 3D
janiporo@janiporo-pc:~/Työpöytä$ wine "/home/janiporo/.wine/drive_c/Program Files/Adobe/Adobe Photoshop CS5/Photoshop.exe"
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-w0yBGm/pkcs11: Tiedostoa tai hakemistoa ei ole
err:shell:HCR_GetFolderAttributes should be called for simple PIDL's only!
fixme:system:SetProcessDPIAware stub!
fixme:ntdll:NtSetInformationToken unimplemented class 24
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x21f48c 0x21f498 0x21f560 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD" 1 -2147483644 0x21f52c 0x21f538 0x21f600 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x21f554 0x21f560 0x21f628 (nil)
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x21f680, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x32d69c)
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\janiporo\\Temp\\swtag.log" 1 -2147483644 0x21fd54 0x21fd60 0x21fe28 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data\\regid.1986-12.com.adobe" 1 -2147483644 0x21fd54 0x21fd60 0x21fe28 (nil)
fixme:win:EnumDisplayDevicesW ((null),0,0x32e7b8,0x00000000), stub!
fixme:font:WineEngRemoveFontResourceEx (L"C:\\Program Files\\adobe\\Adobe Photoshop CS5\\Required\\\\ADMUI3.fon", 0, (nil)): stub
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD" 1 -2147483644 0x61fa904 0x61fa910 0x61fa9d8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x61fa92c 0x61fa938 0x61faa00 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\caps" 1 -2147483644 0x61fa92c 0x61fa938 0x61faa00 (nil)
fixme:dwmapi:DwmIsCompositionEnabled 0x32ed44
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x209de 0x00000001
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x608110c 0x6081118 0x6081178 (nil)
fixme:win:DisableProcessWindowsGhosting : stub
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:win:LockWindowUpdate (0x209de), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:dciman:DCICreatePrimary 0x1748 0xe9112ac
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:win:LockWindowUpdate (0x209de), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:win:LockWindowUpdate (0x209de), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
fixme:ole:CoResumeClassObjects stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x6027a24 0x6027a30 0x6027a60 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD" 1 -2147483644 0x6027a24 0x6027a30 0x6027a60 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x6027a24 0x6027a30 0x6027ad8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\janiporo\\Temp\\swtag.log" 1 -2147483644 0x6027a24 0x6027a30 0x6027a60 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\users\\Public\\Application Data\\regid.1986-12.com.adobe" 1 -2147483644 0x6027a24 0x6027a30 0x6027a60 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x63efbb4 0x63efbc0 0x63efca0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x63efbb4 0x63efbc0 0x63efca0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x63efbb4 0x63efbc0 0x63efca0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x63efbb4 0x63efbc0 0x63efca0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x63efbb4 0x63efbc0 0x63efca0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x63efbb4 0x63efbc0 0x63efca0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x63efbb4 0x63efbc0 0x63efca0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x63efbb4 0x63efbc0 0x63efca0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x63efbb4 0x63efbc0 0x63efca0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x63efbb4 0x63efbc0 0x63efca0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x63efbb4 0x63efbc0 0x63efca0 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x63efbb4 0x63efbc0 0x63efca0 (nil)
fixme:win:LockWindowUpdate (0x209de), partial stub!
fixme:win:LockWindowUpdate ((nil)), partial stub!
```

And same profile shutting down:
```
SHUTTING DOWN WITHOUT 3D
*******fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:ole:CoSuspendClassObjects 
fixme:font:WineEngRemoveFontResourceEx (L"C:\\Program Files\\adobe\\Adobe Photoshop CS5\\Required\\\\ADMUI3.fon", 0, (nil)): stub
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD" 1 -2147483644 0x5febb14 0x5febb20 0x61d4da8 (nil)
fixme:advapi:SetNamedSecurityInfoW L"C:\\Program Files\\Common Files\\Adobe\\Adobe PCD\\cache" 1 -2147483644 0x1e9d1c 0x1e9d28 0x61dd5f8 (nil)
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
err:ole:get_unmarshaler_from_stream Failed to read common OBJREF header, 0x00000000
```

If this is any help for anyone O_o

If I just start up photoshop and shut it down, menu does not disappear, I HAVE TO enable OpenGL, and then all is lost :evil:

---

### Post by Janiporo on 2012-05-05
I found one other way to install CS5 from youtube with almost "one click". It installs 12.0.3 x32 version.

It does install CS5 / silently / (almost) everything works, even the OpenGL 3D.

I would like to find out what it does differently, so people can install original photoshops.

It seems to have installed following .NET framworks:
v1.1.4322
v2.0.50727
v3.0
v4.0.30319

Do not know what else.

When I copy my windows folders + files + registry settings over them, the 3D menu disappears again O_o

Some clitches in using that, so it is not user friendly with this version of wine.

---

