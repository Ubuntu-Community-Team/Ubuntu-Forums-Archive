---
title: "Problems with Weather Display"
date: 2008-06-10
forum: Wine
---

### Post by LakeWind on 2008-06-10
I've been able to run Weather Display under wine since 7.04. Weather Display is a "Gold" rated program according to the wine database and it worked perfectly for me with 7.04 & 7.10.

Since upgrading to 8.04, I've tried installing Weather Display under wine and the program just hangs at the start up screen. Running from the command prompt here is the output:

---------------------------------------------------------------

preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:keyboard:RegisterHotKey (0x10036,49250,0x00000008,115): stub
err:seh:setup_exception_record stack overflow 268 bytes in thread 0009 eip 7b2e21b0 esp 7f121224 stack 0x7f120000-0x7f121000-0x7f220000
------------------------------------------------------------------
Also, I'm wondering where the menu entries are for wine in Ubuntu 8.04? In 7.04 & 7.10 I had menu entries for not only my windows programs but for configuring wine. They are no longer there under 8.04. 

Any help would be greatly appreciated?

Thanks!

---

