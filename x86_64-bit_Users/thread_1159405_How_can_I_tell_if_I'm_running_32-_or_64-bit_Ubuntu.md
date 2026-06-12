---
title: "How can I tell if I'm running 32- or 64-bit Ubuntu?"
date: 2009-05-14
forum: x86 64-bit Users
---

### Post by Deeday on 2009-05-14
Hi all,

apologies if it's already been asked, but I had installed Intrepid 64-bit and just upgraded to Jaunty through Update Manager, so I wonder if I actually got the 64-bit version of it. I would expect so, but - in general - how can I check? (System Monitor only says 9.04 jaunty).

Cheers!

---

### Post by PatrickVogeli on 2009-05-14
uname -a 

If it says x86_64 then you're running 64 bits.

---

### Post by lensman3 on 2009-05-14
The pseudo file exported  by the running kernel "/proc/version" has more info than "uname -a" (at least on my system).  This file even has the version of gcc that built the kernel (way too much info, but good for debug).

Look at the file /proc/cpuinfo.  This file reports the cpu specs that the kernel is running.

---

### Post by jespdj on 2009-05-15
> **Deeday said:**
> apologies if it's already been asked, but I had installed Intrepid 64-bit and just upgraded to Jaunty through Update Manager, so I wonder if I actually got the 64-bit version of it.
If your Intrepid installation was 64-bit and you upgraded (not re-installed the whole system), then your Jaunty is also 64-bit. There is no way that an upgrade switches the architecture.

---

### Post by Deeday on 2009-05-16
I see now, thanks.

It could be worthwhile to add the 32- or 64-bit text to the release number, in System Monitor, if I can make a suggestion.

Cheers!

---

