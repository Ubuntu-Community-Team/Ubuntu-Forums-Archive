---
title: "Ragnarok Online/Direct X Issue?"
date: 2008-06-15
forum: Wine
---

### Post by Zaiden on 2008-06-15
Alrighty, for the last few weeks, I've been trying my darnest trying to get Ragnarok Online (Not the offical server, Legacy RO) working. I've sought out the Wineapp DB article, and they suggested a few dlls, but that didn't help. I then found an article [here]("http://wine-review.blogspot.com/2008/03/directx-90c-march-2008-redistributable.html"), but when I got up to the part where you run the wine command in the terminal to install directx, I got the following error:

> mike@mike-desktop:~$ wine directx_mar2008_redist.exe
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"C:\\windows\\system32\\directx_mar2008_redist.exe": Module not found
mike@mike-desktop:~$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report


I did a fix for this, which was found [here]("http://wiki.winehq.org/PreloaderPageZeroProblem"), and I still recieved the error. I even tried running the main exacutable for the RO server (LRO.exe), in the terminal, and recieved:

> mike@mike-desktop:~$ wine LRO.exe 
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"C:\\windows\\system32\\LRO.exe": Module not found
mike@mike-desktop:~$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report


even with the "-1rag1LRO", it gives the same error. Would anyone know a fix for this?

Currently I'm using Wine Version 0.9.59 under Ubuntu 8.04 64bit, and tried all the OS versions and options in the wine configuration menu

---

