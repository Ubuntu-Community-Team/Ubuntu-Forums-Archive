---
title: "[Tutorial] Wine: Dreamweaver 8 ODBC32.dll Fix!"
date: 2008-05-21
forum: Wine
---

### Post by SidStudios on 2008-05-21
I've just created a quite easy tutorial for those who are having problems with Dreamweaver 8.
The problem is with ODBC32.DLL, and affects the following versions of Wine:

[LIST]
[*]0.9.58
[*]0.9.59
[*]0.9.60
[*]0.9.61
[*]1.0-rc1
[/LIST]

It's at [http://51.sidstudios.org/archives/9/dreamweaver-8-odbc32dll-problem-wine-fix](http://51.sidstudios.org/archives/9/dreamweaver-8-odbc32dll-problem-wine-fix)

If you like it, please post here ;)

---

### Post by BlackDragonBE on 2008-05-23
My Dreamweaver 8 still won't work after this fix, it just show the splash screen for a moment then shuts down itself..
This is what I get:
> 
wineric@eric-laptop:~$ wine '/home/eric/.wine/drive_c/Program Files/Macromedia/Dmweaver 8/Dreamweaver.exe'
fixme:win:EnumDisplayDevicesW ((null),0,0x33f7a0,0x00000000), stub!
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.

I've been getting this since like the last 5 versions of wine or something :(

---

### Post by BlackDragonBE on 2008-05-24
bump

---

### Post by deathrail on 2008-05-28
I am having the same problem as Blackdragon.. When I first install Dreamweaver it worked fine, but i noticed yesterday after going back to it that it will now only load splash screen and then crash. This is the output i got:

> preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
[B]fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f7a0,0x00000000), stub!
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception[/B].

been trying to figure this out but no luck, if anyone could help would be greatly appreciated.

---

### Post by YokoZar on 2008-05-28
Your link gives a 403 error.  Is this still a problem with Wine rc2?

---

### Post by SidStudios on 2008-06-03
> **YokoZar said:**
> Your link gives a 403 error.  Is this still a problem with Wine rc2?

Sorry about that.
I migrated to Drupal:
[http://sidstudios.org/ftw/node/3](http://sidstudios.org/ftw/node/3)

---

### Post by SidStudios on 2008-06-03
> **deathrail said:**
> I am having the same problem as Blackdragon.. When I first install Dreamweaver it worked fine, but i noticed yesterday after going back to it that it will now only load splash screen and then crash. This is the output i got:



been trying to figure this out but no luck, if anyone could help would be greatly appreciated.

Here's the fix for your out of range error:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)

---

### Post by BlackDragonBE on 2008-06-05
Even after SidStudios fix I get this:
```

err:winedevice:ServiceMain driver L"DritekPortIO" failed to load
fixme:win:EnumDisplayDevicesW ((null),0,0x33f7a0,0x00000000), stub!
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.

```

---

