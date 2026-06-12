---
title: "Trying to install Microsoft FORTRAN Powerstation"
date: 2014-08-25
forum: Wine
---

### Post by cyclingchap on 2014-08-25
Hi,

I'm pretty inexperienced in using Wine, although I have successfully installed Office 2000 which just ran with no tweaking at all.

However, I am now trying to install an old Windows 95 package call MS Fortran Powerstation.

I used to use this to write windows GUIs for scientific FORTRAN code a long time ago. I really don't know if the Powerstation developer suite was 16 or 32 bit (!), but I do know that the Powerstation suite and the GUIs that I wrote ran in 32bit Windows XP, AND that my GUIs run happily in Wine 1.6 with zero fiddling.

However, I'm gaving no succes trying to install the Powerstation suite in wine (which I would like to do to tweak some of my old GUIs).

When I run wine (for the setup.exe on the install CD) on the command line I'm getting:

```

modify_ldt: Invalid argument
modify_ldt: Invalid argument
modify_ldt: Invalid argument
modify_ldt: Invalid argument
modify_ldt: Invalid argument
err:module:attach_process_dlls "krnl386.exe16" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winevdm.exe" failed, status c0000005

```

Googling this suggests that the install program is 16 bit?

I've read that I might just need to change settings in Wine config, but I'm a bit confused about how to do this, and I don't want to screw up the Wine settngs for Office 2000 (which is working).

Can any wine gurus offer me any advice?

I'm using Ubuntu 12.04 LTS.

Cheers,

Paul

---

### Post by Claus7 on 2014-08-25
Hello,

this is a quick reply:

1) I would try to create a new bottle in wine, and, since your windows fortran package is old I would suggest you to use the oldest version offered. For example windows 2000 instead of windows xp. That way, even if something goes wrong with the new bottle, you erase it, and the other bottle, with your office installation, remains intact.

2) I would install a text editor (vim is a nice choice since you are using an ubuntu/linux box and try to run my codes from there). If you need graphical environment for your codes in fortran gvim or geany might be nice alternatives. I have to admit that I did not understand very well the GUI-fortran part that you mentioned. You will use coding in order to create graphics?

Regards!

---

### Post by cyclingchap on 2014-09-01
Ok, thanks. I'll look into that. I compiled wine 1.4 but that only lets me compile a wine64 binary, and when I try and compile a 32 bit version (or a version using libraries effectively emulating 32 bit) it fails with unmet dependencies.

I don't know what 'bottles' are .. I suspect they're merely different windows environments you create for a given wine installation? I'll research that.

The Powerstation was basically a FORTRAN version of Visual C++ or Visual BASIC. It compiled standard FORTRAN 77/90 to run as a command line binary (wndows .exe), or allowed you to create GUIs using Windows libraries (that I think were originally written in C) that you called from within your FORTRAN code. Using its GUI developer environment it let you create dialogue boxes and drop down menus etc. very quickly using these libraries.

Now if I wanted a GUI front end for FORTRAN codes I would use GTK, but most of my codes now don't use them. But I still use FORTRAN most of the time..., it's the standard where I work, and still as good as any other language for number crunching, even on massively parallel architectures.

I only wanted to ressurect POWERSTATION so I could fiddle with old stuff I did years ago.

---

### Post by Claus7 on 2014-09-02
Hello,

yes, bottles are different windows environments. Depending on what you choose you will be able to get winxp, win 2000, e.t.c.. The difference is that some programs might not work with one bottle, since they require a specific environment, rather than another.

About wine 32 bit - 64 bit I think that you should take a look here:
[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

I'm using fortran as well (gfortran compiler or intel's) just using (mostly) vim text editor. The coding is the same (apart from extreme differences that one compiler might have from the other).

I do not have dealt with the other things you are mentioning.

Best of luck,
Regards!

---

