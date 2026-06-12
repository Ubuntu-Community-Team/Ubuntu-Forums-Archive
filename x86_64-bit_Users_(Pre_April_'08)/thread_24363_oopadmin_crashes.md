---
title: "oopadmin crashes"
date: 2005-04-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Crad on 2005-04-06
Loving ubuntu, not loving my amd64 experience all that much, regardless of distro... just because stuff isn't quite there yet...  Anyway...

oopadmin runs but when I try and do anything with it it crashes.  Running it from bash, I get lots of library debugging messages... Here are the last 6:

/usr/lib/openoffice/program/libvcl645li.so(_ZN6Dialog7ExecuteEv+0x1f5)[0x55765b31]
/usr/lib/openoffice/program/spadmin.bin(_ZN5MyApp4MainEv+0x3e8)[0x804a352]
/usr/lib/openoffice/program/libvcl645li.so(_Z6SVMainv+0x4a)[0x5566a9b8]
/usr/lib/openoffice/program/libvcl645li.so(main+0x4c)[0x5581fe68]
/lib32/tls/libc.so.6(__libc_start_main+0x108)[0x55f2e7f8]
/usr/bin/oopadmin: line 4: 30653 Aborted                 ./spadmin

Any suggestions?  I can't print from OO which is a problem in trying to actually do work on this machine :|

---

