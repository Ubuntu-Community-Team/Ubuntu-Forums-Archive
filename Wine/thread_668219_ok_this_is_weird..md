---
title: "ok this is weird."
date: 2008-01-15
forum: Wine
---

### Post by zzzPOOHzzz on 2008-01-15
when i start World of Warcraft... it also starts steam... no matter how i start WoW, (AWN Launcher, Applications Menu, even from the Terminal... no clue why it would do that at all

in case you were wondering if it i start steam, it doesn't start WoW


no clue what any of the code means in the terminal but here it is


```
pooh@pooh-desktop:~/.wine/drive_c/Program Files/World of Warcraft$ wine WoW.exe 
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7ca90000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7ca90000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed78,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34eccc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f29c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f400,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f57c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f574,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f4fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f4ec,0x00000000), stub!
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\program files\steam\bin\ *.mix
dir: C:\program files\steam\bin\ *.asi
dir: C:\program files\steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34efd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f118,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:reg:GetNativeSystemInfo (0x374029c4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x7bbfe494) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:shdocvw:ViewObject_SetAdvise (0x10c70078)->(1 00000002 0x14adbc0)
fixme:shdocvw:PersistStreamInit_InitNew (0x10c70078)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10c70078)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10c70078)->(ffffffff)
fixme:imm:ImmAssociateContextEx (0x30030, (nil), 16): stub
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:shdocvw:ViewObject_SetAdvise (0x10600298)->(1 00000002 0x14adc30)
fixme:shdocvw:PersistStreamInit_InitNew (0x10600298)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10600298)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10600298)->(ffffffff)
pooh@pooh-desktop:~/.wine/drive_c/Program Files/World of Warcraft$ err:systray:delete_icon invalid tray icon ID specified: 1
err:ole:RevokeDragDrop invalid hwnd 0x2002a
err:ole:RevokeDragDrop invalid hwnd 0x10046
err:ole:RevokeDragDrop invalid hwnd 0x10048
err:ole:RevokeDragDrop invalid hwnd 0x1004a
err:ole:RevokeDragDrop invalid hwnd 0x1004c
err:ole:RevokeDragDrop invalid hwnd 0x10090
err:ole:RevokeDragDrop invalid hwnd 0x10092
err:ole:RevokeDragDrop invalid hwnd 0x10094
err:ole:RevokeDragDrop invalid hwnd 0x10096
err:ole:RevokeDragDrop invalid hwnd 0x10098
err:ole:RevokeDragDrop invalid hwnd 0x30034
err:ole:RevokeDragDrop invalid hwnd 0x1009a
err:ole:RevokeDragDrop invalid hwnd 0x2002e
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x10600298)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x10600298)
fixme:shdocvw:OleObject_Close (0x10600298)->(1)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x10c70078)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x10c70078)
fixme:shdocvw:OleObject_Close (0x10c70078)->(1)
Shutting down. . .
9fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open

```

---

### Post by karth on 2008-01-15
Maybe steam is configured to launch at windows start, though it also seems wierd to me.

Maybe launching Wine triggers a "Windows start" event since the last updates, if you have an up to date version.

edit: from winehq.org:

> Wine 0.9.53 was released today, with the following main changes:

**RunOnce and Run entries now executed on startup.**
Beginnings of support for emulated disk devices.
Many Richedit improvements.
Nicer looking color dialog.
Lots of bug fixes.

I think this is what lanches Steam. It may be registered under the Run registry key, in the same wineprefix than your WoW installation. Simply unchecking the "Launch Steam at startup" in the Steam options may solve your problem.

---

