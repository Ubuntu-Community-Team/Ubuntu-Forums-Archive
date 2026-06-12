---
title: "Accidentally deleted a registry key"
date: 2008-03-18
forum: Wine
---

### Post by javafiend on 2008-03-18
As the subject says, I accidentally deleted a registry key.  What is the easiest way to restore it?  I don't mind reinstalling Wine if I have to.

Thanks!

---

### Post by happyhamster on 2008-03-19
Well, if you don't mind re-installing then the easiest way is to just delete the hidden .wine folder in your home dir. Press ctrl-h in nautilus (the standard file manager) to be able to see hidden files.

When that's done, to generate a fresh wine setup, just issue:

winecfg

And you're good to go.

---

### Post by javafiend on 2008-03-19
Sounds pretty simple.  Will I have to reinstall whatever windows applications I had in Wine?

---

### Post by happyhamster on 2008-03-19
> **javafiend said:**
> Sounds pretty simple.  Will I have to reinstall whatever windows applications I had in Wine?
Yes. BTW, do you know which registry key you deleted?

---

### Post by milton1 on 2008-03-19
you should be able to do this without deleting the .wine folder. you may have to delete the registry files, so they can be rebuilt when wine is reinstalled and reconfigured.

Edit: creating new registry files may mess up the functionality of previously installed windows programs, depending on the program, so you may as well remove the entire .wine folder.

---

### Post by javafiend on 2008-03-19
I was installing Gecko and deleted this key:

HKEY_Current_User/Software/Wine/MSHTML

No more MSHTML :(

---

### Post by happyhamster on 2008-03-19
- In that case, before getting rid of .wine, try:

wine iexplore [http://www.winehq.org](http://www.winehq.org)

- And if that fails, copy & paste the next lines in an empty text file:```

[HKEY_USERS\S-1-5-4\Software\Wine\MSHTML]

"GeckoUrl"="http://source.winehq.org/winegecko.php"



[HKEY_USERS\S-1-5-4\Software\Wine\MSHTML\0.1.0]

"GeckoPath"="C:\\windows\\gecko\\0.1.0\\wine_gecko"
```
Name it "last-hope.reg" :) and import it into the registry using:

wine regedit last-hope.reg

---

### Post by happyhamster on 2008-03-19
Err, sorry, that should be:

```

[HKEY_CURRENT_USER\Software\Wine\MSHTML]

"GeckoUrl"="http://source.winehq.org/winegecko.php"

[HKEY_CURRENT_USER\Software\Wine\MSHTML\0.1.0]

"GeckoPath"="C:\\windows\\gecko\\0.1.0\\wine_gecko"
```

---

### Post by javafiend on 2008-03-19
Thanks!  I'll give that a try as soon as I get home this evening.

---

### Post by javafiend on 2008-03-19
This is my output:

```
fixme:ole:CoResumeClassObjects stub
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x12b0cc)->((null) 1 0x34e548 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b0cc)->((null) 25 2 0x34e570 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b0cc)->((null) 26 2 0x34e570 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x12b0cc)->(0x34e5bc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b0cc)->({000214d1-0000-0000-c000-000000000046} 37 0 0x34e6c0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b0cc)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x34e730)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x34cab3, 0x34cab4): stub
fixme:urlmon:ObtainUserAgentString (0, 0x12f5f8, 0x34cab4): stub
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x12d008)->(0x34ced0 0x34cab4 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b0cc)->((null) 29 2 0x34fc90 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x12b0cc)
fixme:shdocvw:ClientSite_GetContainer (0x12b0cc)->(0x34fb1c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12b0cc)->(0xf7eb6f38)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b0cc)->((null) 25 2 0x34fa30 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b0cc)->((null) 26 2 0x34fa30 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b0cc)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12b0cc)->((null) 28 2 0x34fb00 (nil))
fixme:mshtml:HttpNegotiate_OnResponse (0x12d008)->(200 L"HTTP/1.1 200 OK\r\nDate: Wed, 19 Mar 2008 22:23:38 GMT\r\nServer: Apache/2.2.3 (Debian) PHP/5.2.0-8+etch10\r\nX-Powered-By: PHP/5.2.0-8+etch10\r\nExpires: Mon, 26 Jul 1997 05:00:00 GMT\r\nLast-Modified: Wed, 19 Mar 2008 22:23:38 GMT\r\nCache-Control: no-store, no-cache, must-revalidate\r\nCache-Contr"... (null) 0x34f9b8)

```

Does this mean it worked?

Just checked registry and keys aren't in there.  Going to try last-hope.

---

