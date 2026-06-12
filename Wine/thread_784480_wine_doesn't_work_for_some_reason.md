---
title: "wine doesn't work for some reason"
date: 2008-05-06
forum: Wine
---

### Post by rabbitnightmare on 2008-05-06
all I get when trying to run a wine app is:

preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:module:import_dll Library uxtheme.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winecfg.exe" failed, status c0000135

and then just fails to start any thoughts?

---

### Post by cogadh on 2008-05-06
This will take care of the preloader errors:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)
Not sure if it will also fix the DLL error.

---

