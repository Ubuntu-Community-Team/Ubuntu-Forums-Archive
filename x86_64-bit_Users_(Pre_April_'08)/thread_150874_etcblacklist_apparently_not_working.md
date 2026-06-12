---
title: "/etc/blacklist apparently not working"
date: 2006-03-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Aphorism on 2006-03-26
Hrm... been a while since I tried my cardreader.

Needless to say, I had the problem resolved with the wonderful 
support staff of Ubuntu -- and my cardreader recognized easily.


The problem was that ehci_hcd was being loaded at boot and 
was obscuring my cardreader from being recognized.

I added ehci_hcd to my /etc/hotplug/blacklist listing, and it worked
fine until a few updates ago.

Now when I lsmod, I see ehci_hcd listed.  When I rmmod the ehci_hcd,
the cardreader appears as normal.  Why isn't the blacklist file
behaving?

Any ideas?

---

