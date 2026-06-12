---
title: "steam problem"
date: 2008-01-03
forum: Wine
---

### Post by Lokine on 2008-01-03
I've been running Steam under Wine for some time now and haven't had any trouble until recently. I have updated to the latest version of Wine and now when I load Steam it logs in and closes just before it should finish logging in. No message or anything. I tried deleting my ClientRegistry.blob and it started up, opened My Games window and it closed, no message. What's going on here and how can I fix it?

EDIT: Here's the terminal output:

```
fixme:shdocvw:ViewObject_SetAdvise (0xf0cd0e8)->(1 00000002 0x149d550)
fixme:shdocvw:PersistStreamInit_InitNew (0xf0cd0e8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xf0cd0e8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xf0cd0e8)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x10b182a8)->(1 00000002 0x149d5b8)
fixme:shdocvw:PersistStreamInit_InitNew (0x10b182a8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10b182a8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10b182a8)->(ffffffff)
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:win:SetLayeredWindowAttributes (0x1009c,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10098,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002a,0x00000000,0,2): stub!
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xf0cd180)->((null) 1 0x33bc28 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xf0cd180)->((null) 25 2 0x33bc50 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xf0cd180)->((null) 26 2 0x33bc50 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0xf0cd180)->(0x33bc9c)
fixme:shdocvw:ClOleCommandTarget_Exec (0xf0cd180)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33bd90 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xf0cd180)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x33be00)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x33a253, 0x33a254): stub
fixme:urlmon:ObtainUserAgentString (0, 0x10ab2f10, 0x33a254): stub
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x10adea28)->(0x33a670 0x33a254 0)
err:systray:delete_icon invalid tray icon ID specified: 1
fixme:shdocvw:ClOleCommandTarget_Exec (0xf0cd180)->((null) 29 2 0x33c0c0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0xf0cd180)
fixme:shdocvw:ClientSite_GetContainer (0xf0cd180)->(0x33c0d0)
fixme:shdocvw:InPlaceFrame_SetStatusText (0xf0cd180)->(0xb7ed6714)
fixme:shdocvw:ClOleCommandTarget_Exec (0xf0cd180)->((null) 25 2 0x33bfe4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xf0cd180)->((null) 26 2 0x33bfe4 (nil))
```

---

### Post by Nexusx6 on 2008-01-08
I had a similar problem, which complete restart (not just a gui one) fixed. If that didn't work, and no one is able to help you, a re-install of steam&games might fix it.

Sorry I can't help you any further :(

---

### Post by Amstell on 2008-01-08
normally when I have an issue with Steam I just uninstall wine and reinstall it again.  Usually fixes any glitches with actual steam.

---

