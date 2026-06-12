---
title: "Wine ATI?"
date: 2008-06-17
forum: Wine
---

### Post by IronArjen on 2008-06-17
I am trying to run a software using Wine and I get error messages. I went thru the archive and improved something but still it is not working. The software is called Genedoc and below is something from my terminal which I got when I tried to install it. I configured it first to Windooze 95, and despite the last error message, it really is a 32 bit version. I run Heron on a Phenom machine with ATI video card.
With the winecfg command I get a similar message but it works. Thanks!

arjen@Comparative_Genomics:~/Wine/Genedoc$ wine gd322602.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:load_winedos Could not load winedos.dll, DOS subsystem unavailable
winevdm: unable to exec '--app-name': 16-bit support missing
arjen@Comparative_Genomics:~/Wine/Genedoc$

---

### Post by cogadh on 2008-06-17
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

