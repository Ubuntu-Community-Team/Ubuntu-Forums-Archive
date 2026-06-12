---
title: "No Such File but it's there - executing java"
date: 2008-07-08
forum: x86 64-bit Users
---

### Post by darenw on 2008-07-08
I have two machines running Ubuntu 7.04 x86_64, with the same proprietary software installed in /usr/local, which contains its own copy of java.   In the java directory's bin/ i can run "./java" and get something sensible (a complaint about no class file) on the "good" machine, but the "naughty" machine reports only 
  bash: ./java: No such file or directory

The same thing happens if i try to run anything in the java bin/ directory on the "naughty" machine.  The files contained therein are identical to the ones on the good machine, with the same permissions and so on.   Use of ldd, file, readelf, or any other executable or file inspection tools on any of the executables on the good machine tell me they're 32-bit ELF executables in whatever level of detail i ask for.  On the naughty machine, i may get an error resembling "file not found" or get the same output as on the good machine.   

That the operating system and software are 64-bit but the executables in question are 32 bit is not the problem, for it works fine on the "good" machine. I wonder if the 32-bit-running magic has gone askew on the other machine?   Or maybe it is something completely different. Any ideas?

---

