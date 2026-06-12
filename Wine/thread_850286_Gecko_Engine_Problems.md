---
title: "Gecko Engine Problems"
date: 2008-07-05
forum: Wine
---

### Post by JPtux on 2008-07-05
I've been trying to install the gecko engine. but I've had some troubles. I can't install the engine directly because the servers are down and the alternate install doesn't seem to work either. All the keys that are supposed to be in the registry are in the registry. I'm running wine 1.1.0. This is the output when I test gecko.
```
fixme:ole:CoResumeClassObjects stub
err:mshtml:check_version Could not open VERSION file
fixme:urlmon:ObtainUserAgentString (0, 0x7e0831c7, 0x7e0831c0): stub
fixme:urlmon:ObtainUserAgentString (0, 0x131268, 0x7e0831c0): stub
fixme:wininet:InternetLockRequestFile STUB
err:cabinet:FDICopy FDIIsCabinet failed.
err:mshtml:check_version Could not open VERSION file
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x129e3c)->((null) 1 0x32e69c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x129e3c)->((null) 25 2 0x32e6b0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x129e3c)->((null) 26 2 0x32e6b0 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x129e3c)->(0x32e6ec)
fixme:shdocvw:ClOleCommandTarget_Exec (0x129e3c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32e7b0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x129e3c)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32e840)
fixme:urlmon:ObtainUserAgentString (0, 0x32cfe7, 0x32cfe0): stub
fixme:urlmon:ObtainUserAgentString (0, 0x12f1b0, 0x32cfe0): stub
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x12cf78)->(0x32cfe8 0x32cfe0 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x129e3c)->((null) 29 2 0x32fca0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x129e3c)
fixme:shdocvw:ClientSite_GetContainer (0x129e3c)->(0x32fb2c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x129e3c)->(0xb7ec46d1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x129e3c)->((null) 25 2 0x32fa60 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x129e3c)->((null) 26 2 0x32fa60 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x129e3c)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x129e3c)->((null) 28 2 0x32fb18 (nil))
fixme:mshtml:HttpNegotiate_OnResponse (0x12cf78)->(200 L"HTTP/1.1 200 OK\r\nDate: Sat, 05 Jul 2008 16:08:42 GMT\r\nServer: Apache/2.2.3 (Debian) PHP/5.2.0-8+etch11\r\nX-Powered-By: PHP/5.2.0-8+etch11\r\nExpires: Mon, 26 Jul 1997 05:00:00 GMT\r\nLast-Modified: Sat, 05 Jul 2008 16:08:42 GMT\r\nCache-Control: no-store, no-cache, must-revalidate\r\nCache-Contr"... (null) 0x32f9d8)

```

---

