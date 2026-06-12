---
title: "64 bit errors during boot-up"
date: 2006-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by spelingchampeon on 2006-08-12
My specs:
AMD64 3400+
Gigabyte GA-K8VM800M  Rev 2 (latest bios)
1gig OCZ DDR400 Ram
WD 80gig IDE HD
Aspire TurboLink 500W PS
Samsung SD-616 DVD Master 16E Internal IDE DVD-ROM

I have been trying to install both the 64 bit desktop, and the alternative 64 bit. Each time, I get stopped about 5 seconds after making my selection as to what type of install. I normally would try the TEXT or OEM.. but neither work. I try to run a CD Check, and get stopped immediately with errors. When I try to install in TEXT mode, I get the following:

ubuntu-6.06-desktop-amd64;  [COLOR="Red"]PANIC: Early exception RIP 666666C3  Error 10 CR2 666666C3[/COLOR]
ubuntu-6.06-alternate-amd64;  [COLOR="red"]PANIC: Early Exception RIP 10 Error ffffffff8046fb92  CR2 0[/COLOR]
On other errors, I usually get a different PANIC message, but it is accompanied by an entire page of errors. I have checked both downloads with MD5 (verification). 

Any clues?

---

### Post by spelingchampeon on 2006-08-15
Quite a few looksee's but no one knows anything about this?

*[I hate when I shamefully have to type something like the above, just to get my post back on page 1]*

---

### Post by Kilz on 2006-08-15
> **spelingchampeon said:**
> Quite a few looksee's but no one knows anything about this?

*[I hate when I shamefully have to type something like the above, just to get my post back on page 1]*

I dont know a lot about kernel panic's. But I do know there are options to load the kernel in the help files in the disks. Perhaps one will let you load the kernel cleanly.

---

### Post by kuja on 2006-08-15
> I try to run a CD Check, and get stopped immediately with errors.

It's quite likely a bad burn if that's the case. I had a bad burn myself. I experienced similar issues. Try burning at a slower speed, or, if that doesn't work, in a different mode.

---

