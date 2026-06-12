---
title: "[SOLVED] How to deactivate NX/XD-Bit support in 64 Bit mode?"
date: 2008-05-15
forum: x86 64-bit Users
---

### Post by jmp0r on 2008-05-15
Hello everybody,

I am using Ubuntu 8.04 (64 Bit version). I am working on a program that generates code and executes it. Thus I do not want to use the NX/XD-feature of today's processors. But I need the 64 Bit environment...

Since Linux activates NX/XD-Bit support by default in 64 Bit mode I have a problem :-( 

After installing the "prelink" package I am able do deactivate the NX/XD-Bit for single programs/libs with the command

```
execstack -s a.out
```

But I prefer a more comfortable (but insecurer) configuration. Does anybody know how to deactivate the NX/XD-Bit in general? Maybe recompiling the Kernel with special options?

Greetz

---

### Post by sduden on 2008-05-15
I'm sorry I don't know how to disable this on the entire machine, but I'm wondering.  Why not just use mprotect() on the memory block that you need to have executable code?

---

### Post by Yellow Pasque on 2008-05-15
If you have an "enthusiast" motherboard, it should let you control the option in the BIOS. I did not see an option in the 2.6.24 kernel (screenshot provided)

---

### Post by jmp0r on 2008-05-16
Hey,

as I found out you can boot the Kernel with the option noexec=off... Works well for me :-)

[http://osdir.com/ml/kernel.kernel-traffic/2004-06/msg00006.html](http://osdir.com/ml/kernel.kernel-traffic/2004-06/msg00006.html) (search for "noexec")

Greetz

---

