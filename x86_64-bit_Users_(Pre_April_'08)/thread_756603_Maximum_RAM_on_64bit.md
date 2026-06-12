---
title: "? Maximum RAM on 64bit"
date: 2008-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by arman.haghi on 2008-04-16
I have a mobo that supports up to 8gb of RAM (4 x 2).

I use 64bit Ubuntu 7.10

Could anyone tell me what is the maximum amount of RAM Ubuntu 64bit will deal with?

(I've read up to 64GB, [http://ubuntuforums.org/showthread.php?t=229771](http://ubuntuforums.org/showthread.php?t=229771) but has anyone actually tested 8gb?)

Thanks,

Arman.

---

### Post by Half-Left on 2008-04-16
It should work fine, yes 64Gb is the max and I've seen the option in the kernel.

---

### Post by hyper_ch on 2008-04-16
a 64bit system can assign up to 2^64byte --> 16 Exabyte

[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)
> 
The emergence of the 64-bit architecture effectively increases the memory ceiling to 264 addresses, equivalent to approximately 17.2 billion gigabytes, 16.8 million terabytes, or 16 exabytes of RAM.


The only question that now remains is will 16 Exabytes be enough to load the whole internet into ram or will I need a 128bit processor? (And if so, how long will it take to wget [http://*](http://*))

---

### Post by arman.haghi on 2008-04-16
Thanks guys!

---

### Post by jespdj on 2008-04-16
> **hyper_ch said:**
> a 64bit system can assign up to 2^64byte --> 16 Exabyte
Theoretically yes, but not in practice. Current 64-bit AMD and Intel processors have an 48-bit address space, which mean they can address 2^48 bytes (256 TB = 262,144 GB). But even this is theoretical, because the chipsets of current motherboards and operating systems place much lower limits on the address space. See [Wikipedia: x86-64]("http://en.wikipedia.org/wiki/X86-64").

If your motherboard properly supports 8 GB RAM, then that should work without problems on 64-bit Ubuntu.

---

### Post by hyper_ch on 2008-04-16
> **jespdj said:**
> Theoretically yes, but not in practice.

not yet in practice...

"only 3 computer will be needed to do all calculations" --> or something similar was said a while ago ;)

---

