---
title: "[SOLVED] Wine version?? + application installation problems"
date: 2008-10-17
forum: Wine
---

### Post by PeterVR on 2008-10-17
Hi

Trying to install Office 2003 in Ubuntu I installed Wine using the Add/Remove menu. After installation, it seems I have Wine 0.9.59 installed... This is not the latest Wine version?? I'd expect to install the latest version of a program when using the default installation tools. What do I do, stick with 0.9.59 or upgrade?

Anyway, ignoring the version, I'm trying to install M$ Office 2003. So, according to one of the many howto's I type  
```
sudo wine /media/OFFICE11/setup.exe
```
Result:
```
wine: /home/peter/.wine is not owned by you
```
So I tried this:
```
wine /media/OFFICE11/setup.exe
```
Result: 
```
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:imm:ImmDisableIME (-1): stub
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
```

...Help?

---

### Post by asdfoo on 2008-10-17
> **PeterVR said:**
> Hi

Trying to install Office 2003 in Ubuntu I installed Wine using the Add/Remove menu. After installation, it seems I have Wine 0.9.59 installed... This is not the latest Wine version?? I'd expect to install the latest version of a program when using the default installation tools. What do I do, stick with 0.9.59 or upgrade?

Anyway, ignoring the version, I'm trying to install M$ Office 2003. So, according to one of the many howto's I type  
```
sudo wine /media/OFFICE11/setup.exe
```
Result:
```
wine: /home/peter/.wine is not owned by you
```
So I tried this:
```
wine /media/OFFICE11/setup.exe
```
Result: 
```
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:imm:ImmDisableIME (-1): stub
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
```

...Help?

why are you using sudo to run wine?  don't do that.  wine runs as a user, not as root.

If you run the Ubunte updater tool it should upgrade you to Wine-1.0

As for the preloader message:


[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

### Post by PeterVR on 2008-10-17
Yes!

Thanks a lot.
PVR

---

