---
title: "Winecfg error"
date: 2008-05-28
forum: Wine
---

### Post by Sebelius on 2008-05-28
Hello all,

I installed wine and then i try to start winecfg and this is what happens:

robert@Rlinux-Base:/usr/local/bin$ winecfg
preloader: Warning: failed to reserve range 00000000-60000000
wine: creating configuration directory '/home/robert/.wine'...
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Could not load Mozilla. HTML rendering will be disabled.
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:seh:setup_exception_record stack overflow 840 bytes in thread 0009 eip 7bc65706 esp 7f120fe8 stack 0x7f120000-0x7f121000-0x7f220000
wine: wineprefixcreate failed while creating '/home/robert/.wine'.
robert@Rlinux-Base:/usr/local/bin$ wineserver: could not save registry branch to /home/robert/.wine-S7L4Yf/system.reg : No such file or directory
wineserver: could not save registry branch to /home/robert/.wine-S7L4Yf/userdef.reg : No such file or directory
wineserver: could not save registry branch to /home/robert/.wine-S7L4Yf/user.reg : No such file or directory


What went wrong?

Seb

---

### Post by cogadh on 2008-05-28
The preloader errors can be fixed with this:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

