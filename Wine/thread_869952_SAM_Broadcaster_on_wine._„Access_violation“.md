---
title: "SAM Broadcaster on wine. „Access violation“"
date: 2008-07-25
forum: Wine
---

### Post by Dub Throatflex on 2008-07-25
Hello,
I have this problem with any SAMBC version:
&#8222;Access violation at address 004049C7 in module 'Setup_BC.exe'. Read of address 0F0000FC&#8220; when clicked &#8222;next&#8220; too choose the database.
Terminal output:
```
fixme:shdocvw:PersistStreamInit_Load (0x138618)->(0x14f890)
fixme:shdocvw:OleControl_OnAmbientPropertyChange Unknown dispID -1
fixme:shdocvw:navigate_url Unsupported args (Flags 0x4f9d10:10; TargetFrameName 0x4f9d10:10)
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:iphlpapi:NotifyAddrChange (Handle 0x7dbb89f8, overlapped 0x7dbb89dc): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x13def34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1386b4)->((null) 1 0x33c7a0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->((null) 25 2 0x33c7b4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->((null) 26 2 0x33c7b4 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1386b4)->(0x33c7f0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33c8b4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x33c944)
fixme:service:EnumServicesStatusA 0x12853f8 type=30 state=3 0x767008 24024 0x33eec0 0x33eebc 0x33eeb8
fixme:shdocvw:navigate_url Unsupported args (Flags 0x4f9d10:10; TargetFrameName 0x4f9d10:10)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->((null) 29 2 0x33e54c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1386b4)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x33e49c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x33e49c)
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shdocvw:ClientSite_GetContainer (0x1386b4)->(0x33d7c0)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1386b4)->(0xb7dd76d1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->((null) 25 2 0x33d6f4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->((null) 26 2 0x33d6f4 (nil))
fixme:mshtml:HlinkTarget_SetBrowseContext (0x15abf8)->((nil))
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x13def34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1386b4)->((null) 1 0x33c090 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->((null) 25 2 0x33c0a4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->((null) 26 2 0x33c0a4 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1386b4)->(0x33c0e0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33c1a4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x33c234)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->((null) 29 2 0x33e54c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1386b4)
fixme:shdocvw:ClientSite_GetContainer (0x1386b4)->(0x33d7c0)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1386b4)->(0xb7dd76d1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->((null) 25 2 0x33d6f4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->((null) 26 2 0x33d6f4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x33e4a4)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x33e4a4)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->((null) 26 2 0x33e52c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->((null) 29 2 0x33e53c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->({000214d1-0000-0000-c000-000000000046} 103 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1386b4)->(0x7bca3a6c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->((null) 28 2 0x33e4a4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1386b4)->((null) 21 2 (nil) (nil))
```

Please help me :(

---

