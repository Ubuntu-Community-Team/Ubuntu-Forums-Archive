---
title: "Wine Issues"
date: 2008-10-04
forum: Wine
---

### Post by aja on 2008-10-04
Could someone please help me ?? I am trying to load The software that came with me Canon camera under wine. I was able to load one of the programs, but he other one i get get this message

"an application has made an attempt to load the C runtime library incorrectly "

Does any one have any thoughts??

Thanks
aja

---

### Post by david_kt on 2008-10-04
> **aja said:**
> Could someone please help me ?? I am trying to load The software that came with me Canon camera under wine. I was able to load one of the programs, but he other one i get get this message

"an application has made an attempt to load the C runtime library incorrectly "

Does any one have any thoughts??

Thanks
aja

It is probably due to different version of msvcrt.dll or MSVBVM60.DLL. You could try to put native file of the above dlls and probably use dlloverrides and see how it works.

DK

---

### Post by jacksaff on 2008-10-04
Digikam supports most cameras these days (well, the underlying libs do so there should be lots of linux photo app that do). Is there anything your canon software does that there is no linux alternative to?

---

