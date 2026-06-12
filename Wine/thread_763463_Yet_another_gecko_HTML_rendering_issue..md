---
title: "Yet another gecko HTML rendering issue."
date: 2008-04-23
forum: Wine
---

### Post by hauj0bb on 2008-04-23
Hi,

I'm having major trouble getting the gecko html engine to work. when I run "wine iexplore http://winehq.com" I get this string of errors:

OS: Ubuntu 8.04 AMD64 Hardy

```
fixme:ole:CoResumeClassObjects stub
fixme:iphlpapi:NotifyAddrChange (Handle 0x7dc3ca08, overlapped 0x7dc3c9ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x101ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x12bcec)->((null) 1 0x32e69c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12bcec)->((null) 25 2 0x32e6b0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12bcec)->((null) 26 2 0x32e6b0 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x12bcec)->(0x32e6ec)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12bcec)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32e7b0 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x12c0e8)->(L"" L"" 0 0x32e7e8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12bcec)->((null) 29 2 0x32fca0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x12bcec)
fixme:shdocvw:ClientSite_GetContainer (0x12bcec)->(0x32fb2c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12bcec)->(0xf7e617c9)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12bcec)->((null) 25 2 0x32fa60 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12bcec)->((null) 26 2 0x32fa60 (nil))
err:mshtml:before_async_open GetWineURL returned NULL
fixme:shdocvw:ClOleCommandTarget_Exec (0x12bcec)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12bcec)->((null) 28 2 0x32fb18 (nil))

```

The browser window loads, but instead of the framework being displayed, I have a big white screen.

I am not behind a proxy, or firewall.

I've tried the automatic install, winetools install, and manual install (with manual registry entry), and nothing seems to do the trick.

I've also broken down and reinstalled Ubuntu two different times, which also didn't help.

Any insight on this matter would be much appreciated!

Thanks

---

### Post by hauj0bb on 2008-04-23
IE4Linux works using the wine extension, but this doesn't replace the HTML engine used in game launchers (wow launcher, steam community site, etc). so I still get the "unable to get URL".

If anyone has any experience with this I would greatly appreciate it.

Thanks,

---

### Post by hauj0bb on 2008-04-24
I fixed this issue by doing a fresh install of ubuntu 8.04 AMD64, updating system to the current build, installing restricted nvidia drivers, installing wine 0.9.59, installing wow /w burning crusade, running the wow launcher, and downloading/installing the automatic gecko update *ONLY*. I touched nothing else other than what was stated above.

It seems that one of my apps (no telling which one) was conflicting with the gecko engine, so in short -- installing the bare minimum on a clean install resulted the gecko engine running properly.

Now, to install my apps and see if anything changes!

---

