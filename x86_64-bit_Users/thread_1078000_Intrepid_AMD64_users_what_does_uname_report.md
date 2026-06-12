---
title: "Intrepid AMD64 users: what does uname report?"
date: 2009-02-22
forum: x86 64-bit Users
---

### Post by rdilliker on 2009-02-22
I upgraded from Dapper to Hardy to Intrepid and my kernel is now listed as this: ```
Linux Athlon 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
```I read a previous thread saying generic just means generic to all 64-bit processors and that the "x86_64" means I am running the 64-bit kernel but I thought the x86_64 is just referring to my processor architecture, not the kernel.

The reason I ask this is because when I was running Dapper the kernel version was amd64 instead of generic.

---

### Post by gila_monster on 2009-02-22
That's what I get as well. Doesn't seem worrisome to me.

---

### Post by rdilliker on 2009-02-22
> **gila_monster said:**
> That's what I get as well. Doesn't seem worrisome to me.

It's more that I am curious so I want to confirm it. I am wondering why the naming convention changed so that in dapper I would see amd64 in the kernel release and now it's just generic. Furthermore, I couldn't really find if "uname -m" is returning the processor architecture or what architecture the kernel was built for.

---

### Post by jocko on 2009-02-23
> **rdilliker said:**
> It's more that I am curious so I want to confirm it. I am wondering why the naming convention changed so that in dapper I would see amd64 in the kernel release and now it's just generic. Furthermore, I couldn't really find if "uname -m" is returning the processor architecture or what architecture the kernel was built for.
Actually, in dapper the kernels for 64 bit were labeled "amd64-generic", "amd64-k8","amd64-server" and "amd64-xeon".
The reason the kernel is only labeled "generic" now and not anything more specific for specific cpu's (-k8, -xeon) is that recent kernels in ubuntu (=after dapper) are built with run-time detection of what cpu you have and will activate all the features and optimizations of the cpu on-the-fly (so the 64 bit "generic" kernel now activates the optimizations for an amd k8 cpu if it is detected).
In older ubuntu releases (dapper and older), some kernels were specifically optimized for only one type of cpu.
The "amd64" part of the kernel name has been dropped (probably because it's not needed). 

uname will report what *kernel* you have, irregardless of what cpu you have (as far as I know, the -m switch tells you what processor architecture the kernel is built for).
If you would run a 32 bit -generic kernel on a 64 bit processor, uname would report i686, not x86_64.

---

### Post by rdilliker on 2009-02-23
Thanks, jocko. That's exactly the kind of explanation I was looking for!

---

