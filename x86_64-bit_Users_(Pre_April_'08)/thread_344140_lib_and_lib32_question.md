---
title: "lib and lib32 question"
date: 2007-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by mfgobbi on 2007-01-22
Hi there - I use Ubuntu 64 bit on a AMD64 bit machine. After I installed ia32 libs, I noticed that it installed them in /usr/lib32. The lib file names all replicate the /usr/lib files (which are all 64 bit I suppose). Now the question: how a program is supposed to know where is it going to find the correct library? For example suppose I install a 32 bit debian or rpm (alien) package that depend on  glibc and I am forcing the architecture to install the 32 bit version . Is it going to find the correct 32 bit automatically?

A case in hand. The 64 bit intel compilers requests the 32 bit versions of several packages. BUT it looks for them in /usr/lib directory, and, because it cannot find them there (they are in /usr/lib32), it gives me an install error...

Can anyone clarify how these 64 bit distros deal with this issue? 

Thanks

---

### Post by Ribs on 2007-01-22
As far as I'm aware (And I'm no expert, by any means), the OS should be taking care of that. Basically, if a 32-bit application asks for 'mylibv1.0' then Linux (or ldconfig, I believe), will feed it the 32-bit version of the library, if it finds it. Similarly, if the program is a 64-bit program, it'll get the 64-bit version of the library. 

The program itself does not care. It just asks for what it needs, and the OS does the hard work in figuring out which version of the library is required.

Correct me if I'm wrong, but this is how I see the issue with my (very limited) knowledge.

---

