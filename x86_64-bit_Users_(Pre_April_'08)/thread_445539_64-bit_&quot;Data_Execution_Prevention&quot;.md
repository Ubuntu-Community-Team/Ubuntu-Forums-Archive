---
title: "64-bit &quot;Data Execution Prevention&quot; ?"
date: 2007-05-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by RTrev on 2007-05-16
As we all know, many of the exploits of Windows have to do with buffer overrun situations, where bounds-checking of an allocated heap or stack hasn't been implemented correctly (or at all) and so a whole bunch of code can be injected into what is supposed to be a *data* buffer, the instruction pointer can be aimed at an entry point in that code, and wham -- the exploit code is running on the machine.

The new 64-bit processors offer DEP, or Data Execution Prevention, but it does no good unless the operating system is working hand-in-hand with the CPU to avoid DEP.  (AMD decided to get creative and made up the utterly silly term "Enhanced Virus Protection", but it's the same thing.)

If you want to learn more  about this, the best place I know is:

[http://www.grc.com/securable.htm](http://www.grc.com/securable.htm)

I'm able to run his freebie little test routine under Wine, and am told that I *do* have DEP and it's enabled in the BIOS.  My question is.. can it be enabled in Ubuntu 7.04?  If so, how?  

Thanks,
Bob

---

### Post by sonofusion82 on 2007-05-16
Linux kernel seems to support that: [http://en.wikipedia.org/wiki/NX_bit](http://en.wikipedia.org/wiki/NX_bit)
But I don't know if it is enabled in Ubuntu.
Or do we need to recompile the kernel?

---

### Post by Ken_Lewis81 on 2007-05-16
Support for not running programs from memory marked as 'data' been in the Linux Kernel since version 2.6.7, which was released in June 2004.  This feature was sufficiently important that it was made the default behaviour.  There's no need to recompile the kernel, and if you did you'd find no 'CONFIG_NX' option to turn it on or off either.

Take care.
Ken.

---

### Post by RTrev on 2007-05-16
> **Ken_Lewis81 said:**
> Support for not running programs from memory marked as 'data' been in the Linux Kernel since version 2.6.7, which was released in June 2004.  This feature was sufficiently important that it was made the default behaviour.  There's no need to recompile the kernel, and if you did you'd find no 'CONFIG_NX' option to turn it on or off either.

Take care.
Ken.

Why am I not surprised to find that Linux has us covered, while MS is still screwing around on this issue.  Sure, their OS supports hardware DEP -- it's just that they ship with it disabled, and if you enable it you find that half of your programs no longer work.

Thanks for the info!
Bob

---

