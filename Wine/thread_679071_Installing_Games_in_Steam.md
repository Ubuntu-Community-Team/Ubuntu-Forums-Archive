---
title: "Installing Games in Steam"
date: 2008-01-26
forum: Wine
---

### Post by ShatteredBlade on 2008-01-26
Been using Ubuntu as my main OS or a few weeks, loving it.

Ok, so I have Steam up and running fine, chat works, etc.

But now when I try to install & download any games, it automatically closes. I have the terminal about below.

```
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:shdocvw:ViewObject_SetAdvise (0x10fe5b68)->(1 00000002 0x14bd538)
fixme:shdocvw:PersistStreamInit_InitNew (0x10fe5b68)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10fe5b68)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10fe5b68)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x10fe61e8)->(1 00000002 0x14bd5a0)
fixme:shdocvw:PersistStreamInit_InitNew (0x10fe61e8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10fe61e8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10fe61e8)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x10fabf98)->(1 00000002 0x14beed0)
fixme:shdocvw:PersistStreamInit_InitNew (0x10fabf98)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10fabf98)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10fabf98)->(ffffffff)
fixme:iphlpapi:NotifyAddrChange (Handle 0x77ea49c8, overlapped 0x77ea49ac): stub
fixme:system:SetProcessDPIAware stub!
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x10fac030)->((null) 1 0x3373e8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x10fac030)->((null) 25 2 0x337410 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x10fac030)->((null) 26 2 0x337410 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x10fac030)->(0x33745c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x10fac030)->({000214d1-0000-0000-c000-000000000046} 37 0 0x337570 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x10fad828)->(L"" L"" 0 0x3374ec)
fixme:mshtml:fix_headers Ignoring User-Agent header
fixme:win:SetLayeredWindowAttributes (0x10098,0x00000000,0,2): stub!
fixme:shdocvw:ClOleCommandTarget_Exec (0x10fac030)->((null) 29 2 0x33c0b8 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x10fac030)
fixme:shdocvw:ClientSite_GetContainer (0x10fac030)->(0x33c068)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x10fac030)->(0xb7ec9734)
fixme:shdocvw:ClOleCommandTarget_Exec (0x10fac030)->((null) 25 2 0x33bf7c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x10fac030)->((null) 26 2 0x33bf7c (nil))
fixme:mshtml:HTMLBodyElement_put_scroll (0x10fcc7a8)->(L"no")
fixme:mshtml:HTMLDocument_put_ondragstart (0x10fcd2f8)
fixme:mshtml:HTMLBodyElement_put_scroll (0x10fcc7a8)->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll (0x10fcc7a8)->(L"no")
fixme:win:SetLayeredWindowAttributes (0x10098,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002a,0x00000000,0,2): stub!
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x10fe5c00)->((null) 1 0x33b770 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x10fe5c00)->((null) 25 2 0x33b798 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x10fe5c00)->((null) 26 2 0x33b798 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x10fe5c00)->(0x33b7e4)
fixme:shdocvw:ClOleCommandTarget_Exec (0x10fe5c00)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33b8f8 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x10bdfa90)->(L"" L"" 0 0x33b874)
fixme:mshtml:fix_headers Ignoring User-Agent header
err:systray:delete_icon invalid tray icon ID specified: 1
fixme:shdocvw:ClOleCommandTarget_Exec (0x10fe5c00)->((null) 29 2 0x33c0b8 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x10fe5c00)
fixme:shdocvw:ClientSite_GetContainer (0x10fe5c00)->(0x33c068)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x10fe5c00)->(0xb7ec9734)
fixme:shdocvw:ClOleCommandTarget_Exec (0x10fe5c00)->((null) 25 2 0x33bf7c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x10fe5c00)->((null) 26 2 0x33bf7c (nil))
fixme:mshtml:HTMLBodyElement_put_scroll (0x10b31a40)->(L"no")
fixme:mshtml:HTMLDocument_put_ondragstart (0x10b31f28)
fixme:mshtml:HTMLBodyElement_put_scroll (0x10b31a40)->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll (0x10b31a40)->(L"no")
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:mshtml:HTMLBodyElement_put_scroll (0x10c54a88)->(L"no")
fixme:shdocvw:ClOleCommandTarget_Exec (0x10fac030)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x10fac030)->((null) 28 2 0x33bf78 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x10fe5c00)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x10fe5c00)->((null) 28 2 0x33bf78 (nil))
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:win:SetLayeredWindowAttributes (0x10098,0x00000000,195,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10098,0x00000000,195,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10098,0x00000000,102,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10098,0x00000000,102,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10098,0x00000000,0,2): stub!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x10fabf98)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x10fabf98)
fixme:shdocvw:OleObject_Close (0x10fabf98)->(1)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x10fcd2f8)->((nil))
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set

```

That's from start to finish btw.

Also, in winecfg I have it emulating XP, no window manager.
Running it with a Intel 965 integrated, which plays it fine in XP.

---

### Post by fulcrum89 on 2008-03-07
bump, i have the exact same problem

---

### Post by Brynster on 2008-03-07
I have all kinds of problems installing games in steam, 

the My games tab works ok, but new games that according to AppDB @ winehq should work fail because of steam, I fould that using wine 0.9.49  works better than later versions but not perfectly.

I would try that first of all,

---

### Post by Hoods on 2008-04-16
having the same problem is there anything to fix this yet?

---

### Post by aoanla on 2008-04-16
What version of Wine are you all using?

The newer versions of Wine are better for buying stuff in Steam.

It may also be the case that having "Steam Friends" enabled will break some games in Wine. I'm not sure if that's been fixed, yet (because I've not tried reenabling Steam Friends since the bug existed...)

---

### Post by PsYcO~KJ on 2008-04-16
Well this si gonna sound stupid, but how do you disable steam friends?

---

### Post by alex_mufc_08 on 2008-04-19
Hey

I have managed to install Steam. I'm currently downloading CounterStrike:Source but i cant use chat and the Steam window is too big and I can only just click on friends at the bottom.

Can anyone help with this?

Thanks

---

