---
title: "[SOLVED] Internet Explorer Just Sits There"
date: 2008-06-24
forum: Wine
---

### Post by Jesdisciple on 2008-06-24
Why does IE not even display any toolbars?  Here's my terminal output from opening and closing it:```
chris@Jesdisciple-laptop:~/.wine/drive_c/Program Files/Internet Explorer$ wine iexplore.exe
fixme:ole:CoResumeClassObjects stub
fixme:shdocvw:go_home stub
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:iphlpapi:NotifyAddrChange (Handle 0x7dc219e8, overlapped 0x7dc219cc): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x102ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x129c9c)->((null) 1 0x33e118 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x129c9c)->((null) 25 2 0x33e140 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x129c9c)->((null) 26 2 0x33e140 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x129c9c)->(0x33e18c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x129c9c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33e290 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x129c9c)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x33e300)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:ClOleCommandTarget_Exec (0x129c9c)->((null) 29 2 0x33fc90 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x129c9c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x129c9c)->((null) 26 2 0x33fc80 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x129c9c)->((null) 29 2 0x33fc90 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x129c9c)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x129c9c)->((null) 35 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x129c9c)->((null) 28 2 0x33fbc0 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x129c9c)->(0x33fb1c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x129c9c)->(0xb7e39c3c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x129c9c)->((null) 25 2 0x33fa30 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x129c9c)->((null) 26 2 0x33fa30 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x129c9c)->((null) 21 2 (nil) (nil))
fixme:shdocvw:DocHostUIHandler_ShowContextMenu default action not implemented
```

Thanks!

---

### Post by cookies on 2008-06-25
As far as I know, it never had them in Wine. To launch IE with a webpage (browsing is rather broken, be warned) use 

wine iexplore.exe [http://www.google.com](http://www.google.com)

IEs4Linux is a better choice: 
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

---

### Post by YokoZar on 2008-06-25
Keep in mind that the "Internet Explorer" included in Wine is just the Gecko (firefox) rendering engine in front of a window.  It's really only there for applications that use it internally (eg, when Steam renders the Steam store).

If you want to surf, just use FireFox (perhaps with the user agent switcher spoofing IE).  If you want to use Internet Explorer, you'll have to install it natively (that is, from Microsoft) using either the instructions on the WineHQ AppDB or with something like IEs4linux

---

### Post by Jesdisciple on 2008-06-30
Sorry for the delay; my laptop hasn't had internet for a few days.  I didn't know Wine's IE wasn't really intended to be a browser, so thanks!

---

