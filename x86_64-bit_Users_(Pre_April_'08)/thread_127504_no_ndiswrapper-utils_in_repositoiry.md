---
title: "no ndiswrapper-utils in repositoiry"
date: 2006-02-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by gig1957 on 2006-02-09
Installed Ubuntu for ppc 5.10 from downloaded iso yesterday. All worked fine until I wanted to set up my usb wireless NIC. Nothing in menus for wireless networking and when searching repository no ndidwrapper-utils is found. Any ideas anyone. I have tried to install dapper drake instead but it has a problem installing kernel

I am installing on powerbook G4.

Thanks in advance

---

### Post by el3ktro on 2006-02-09
ndis-wrapper is used to let WINDOWS DLLs run under Linux, and this doesn't work on PPC at all. You're better of buying a wlan card that is directly supported by Linux. I have the same problem on my iBook G4, the onboard WLAN is not supported - but help is on the way, there's a project aiming to reverse-engineer the WLAN chip in iBooks and they make good process.

Tom

---

### Post by Ptero-4 on 2006-02-09
Or you can use the Mac-on-Linux wrapper hack. But be aware that this hack will have an OSX open all the time you use your wlan and if you close it the wlan goes offline.

---

