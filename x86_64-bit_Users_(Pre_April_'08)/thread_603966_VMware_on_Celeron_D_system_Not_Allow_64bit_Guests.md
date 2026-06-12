---
title: "VMware on Celeron D system Not Allow 64bit Guests"
date: 2007-11-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by trmentry on 2007-11-05
I reinstalled my server onto a Celeron D system and isntalled Ubuntu 64 bit fine.   I then installed VMWare with no issues.   

However vmware won't allow me to install a 64bit guest OS.   I'm at a loss as to why since my system is 64bit.  

I installed vmware on my AMD Windows system and it allowed me to isntall a 64bit guest there so I'm a bit confused.

Thanks

---

### Post by cmost on 2007-11-05
Just a thought, but did you install the 64 bit version of VMware or the 32 bit version (which works on 64 bit systems but may no allow 64 bit guests?)

Also, perhaps this article might help you as 64 bit guests require specific hardware minimums be met.

[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1901](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1901)

---

### Post by x0as on 2007-11-05
Celeron D doesn't have VT support so you can't run 64bit guests.

---

### Post by trmentry on 2007-11-05
> **x0as said:**
> Celeron D doesn't have VT support so you can't run 64bit guests.

Bummer.  I was building the new server on the cheap and just interested in the 64bit for the OS primarily and didn't think about virtualization till I reinstalled vmware.

Oh well... food for thought on the next server.

Thanks for help.

---

### Post by lonniehenry on 2007-11-07
How do I determine which revision my AMD Turion 64 x2 tl-50 is? Will it support 64 bit client if I install 64 bit host?  I tried to find out more about the cpu but don't know how to get the information.
Thanks in advance.

---

