---
title: "Steam HTML problems."
date: 2008-04-25
forum: Wine
---

### Post by Swarms on 2008-04-25
After I updated to Hardy, Steam couldn't show the HTML pages, instead it gave me an error for each page, like: "storefront.steampowered.com could not be found. Please check the name and try again". I thought it was a problem with Hardy, so I downloaded and burned the final version and installed that instead. But the problem persisted. I tried to delete the Gecko folder and reinstall it, but it didn't solve anything.

---

### Post by Swarms on 2008-04-25
It gives me this when I run the command in wine: ```
wine iexplore http://www.winehq.org

```

```
fixme:ole:CoResumeClassObjects stub
fixme:iphlpapi:NotifyAddrChange (Handle 0x7dc0ca08, overlapped 0x7dc0c9ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x102ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x129404)->((null) 1 0x33e69c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x129404)->((null) 25 2 0x33e6b0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x129404)->((null) 26 2 0x33e6b0 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x129404)->(0x33e6ec)
fixme:shdocvw:ClOleCommandTarget_Exec (0x129404)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33e7b0 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x12a0c8)->(L"" L"" 0 0x33e7e8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x129404)->((null) 29 2 0x33fca0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x129404)
fixme:shdocvw:ClientSite_GetContainer (0x129404)->(0x33fb2c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x129404)->(0xf7df47c9)
fixme:shdocvw:ClOleCommandTarget_Exec (0x129404)->((null) 25 2 0x33fa60 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x129404)->((null) 26 2 0x33fa60 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x129404)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x129404)->((null) 28 2 0x33ebb8 (nil))
```

Any ideas?

---

### Post by Sockerdrickan on 2008-04-25
Same here

---

### Post by andrebrait on 2008-04-26
me too

I already have a thread abot this

are you using x86-64?

---

### Post by kevin11951 on 2008-04-26
there should be a sticky on this, just run: 

```
sudo apt-get install lib32nss-mdns
```

restart computer.

---

### Post by andrebrait on 2008-04-27
vote for sticky

---

