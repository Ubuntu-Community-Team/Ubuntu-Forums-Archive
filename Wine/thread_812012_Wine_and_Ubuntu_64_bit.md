---
title: "Wine and Ubuntu 64 bit"
date: 2008-05-29
forum: Wine
---

### Post by angloman on 2008-05-29
Hey,

I was just wondering how running Windows 32 bit applications under wine on a 64bit system would work?

I am currently running Unbunt 8.04 64bit on a Core 2 Quad and I'm trying to get Simply Accounting to run properly through Wine.

These are the errors I'm getting when I try to open a file through simply accounting and I get this error in the terminal after Simply tells me it can't open the file

```
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PROCESSOR_PERFORMANCE_INFORMATION
fixme:atl:AtlModuleInit SEMI-STUB (0x3e1618 0x3e00d8 0x3d0000)
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PROCESSOR_PERFORMANCE_INFORMATION

```

Is this because I'm using a 64 bit edition to run 32 bit windows applications?

---

### Post by doorknob60 on 2008-05-30
No, Wine has no problem whatsoever on 64 bit Ubuntu, it would probably give the same error on 32 bit also.

---

### Post by ajackson on 2008-05-30
[AppDB]("http://appdb.winehq.org/appview.php?iAppId=819") often contains some very useful information, why people don't use it I'll never know.

---

