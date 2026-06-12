---
title: "[SOLVED] Can only change the Background once?!?"
date: 2008-02-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by shane2peru on 2008-02-16
Ok, I stumbled accidentally upon this error, and now it is bothering me.  When I go to change the background I can only do it one time per boot!  The second time it just ties up my processor for quite a bit of time, and never does anything, till I manually kill it.  Here are the logs:

```

dmesg | grep gnome-appearanc
[  213.994827] gnome-appearanc[7182]: segfault at 00002b65643f96e0 rip 00002b65643f96e0 rsp 00007fff5277f928 error 14
[  406.815947] gnome-appearanc[7774]: segfault at 00002b8cdf06d6e0 rip 00002b8cdf06d6e0 rsp 00007fffd7b0ce38 error 14
[ 1291.579067] gnome-appearanc[8509]: segfault at 00002ba8dfb276e0 rip 00002ba8dfb276e0 rsp 00007fffd7052378 error 14
[ 1382.307420] gnome-appearanc[8556]: segfault at 00002ba159f8c6e0 rip 00002ba159f8c6e0 rsp 00007fff5cbeb408 error 14

```

Any one else having this problem?  Anyone know of a fix?  Is this a real bug? :lol:

Shane

---

### Post by shane2peru on 2008-02-19
I think this was just a really odd problem, a CLEAN install of my 64bit system fixed this issue.  

Shane

---

