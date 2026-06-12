---
title: "Wine won't add a proper C drive and Won't work"
date: 2008-06-03
forum: Wine
---

### Post by Detailedghost on 2008-06-03
My current issue is that wine isn't working properly. I tried to add a C drive, but it won't work. I've tried to autodetect and everything but it doesn't seem to work. This ubuntu noob needs help. :confused:

Also when that problem gets firgured out, is installing easy? I'm looking forward to installing games. Thanks for the help.

---

### Post by ajmorris on 2008-06-03
hi there,
can you please start winecfg from a terminal when you try to add the drive, to post any output here.

As for > is installing easy? I'm looking forward to installing games. it is easy... all you do is run wine setup.exe from a terminal, and then from there do what you would do in windows... but, beware, not all games will run on wine. (there are also other alternatives designed for games such as cedega and crossover games, however, these are not free)

AJ

---

### Post by iaculallad on 2008-06-03
> **Detailedghost said:**
> My current issue is that wine isn't working properly. I tried to add a C drive, but it won't work. I've tried to autodetect and everything but it doesn't seem to work. This ubuntu noob needs help. :confused:

Also when that problem gets firgured out, is installing easy? I'm looking forward to installing games. Thanks for the help.

WinE could do wonderful things only if configured properly. How are you trying to add your "C" drive? Try visiting WinE  [HowTo]("http://www.winehq.org/site/howto") website and it's [Application Database]("http://appdb.winehq.org/") to see if what you're trying to install is supported.

---

### Post by Detailedghost on 2008-06-03
ghost@Ghost:~$ winecfg
preloader: Warning: failed to reserve range 00000000-60000000
Warning: the specified Windows directory L"C:\\windows" is not accessible.
Warning: the specified System directory L"C:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/lori', starting in the Windows directory.
preloader: Warning: failed to reserve range 00000000-60000000
Warning: the specified Windows directory L"C:\\windows" is not accessible.
Warning: the specified System directory L"C:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:wineboot:main Cannot set the dir to L"C:\\windows" (2)
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
preloader: Warning: failed to reserve range 00000000-60000000
Warning: the specified Windows directory L"C:\\windows" is not accessible.
Warning: the specified System directory L"C:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

---

### Post by ajmorris on 2008-06-04
your .wine directory seems to be messed up. Backup anything in ~/.wine that you need, do ```
rm -r ~/.wine
``` in a terminal, then run winecfg again, (also, make sure you do not run wine as root)

AJ

---

### Post by bapoumba on 2008-06-04
Moved to "Wine".

---

### Post by mc4man on 2008-06-04
go here and do wine preloader fix 
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)
or go here, add repo and get latest version (don't think it needs fix, not 100% sure)
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

related note; if the current version doesn't require fix then it's probably a good idea for those that did do it to undo it - run the gedit and restore the value (65536)

---

### Post by Detailedghost on 2008-06-04
> **ajmorris said:**
> your .wine directory seems to be messed up. Backup anything in ~/.wine that you need, do ```
rm -r ~/.wine
``` in a terminal, then run winecfg again, (also, make sure you do not run wine as root)

AJ

Ok now it has a working C drive, but now when I try and install something it does this:

[IMG]http://lh3.ggpht.com/dantemaster214/SEa8mthq82I/AAAAAAAACVY/1R9FhJeUVeg/debug.jpg[/IMG]

What do I do now?

---

### Post by BlahMan_of.Doom on 2008-06-04
> **Detailedghost said:**
> Ok now it has a working C drive, but now when I try and install something it does this:

[IMG]http://lh3.ggpht.com/dantemaster214/SEa8mthq82I/AAAAAAAACVY/1R9FhJeUVeg/debug.jpg[/IMG]

What do I do now?

That's a problem with the program, not wine. Go to AppDB.WineHQ.org and see if the app you want is supported.

Get on AIM, ghost (and add me)

---

### Post by ajmorris on 2008-06-04
> **Detailedghost said:**
> Ok now it has a working C drive, but now when I try and install something it does this:

[IMG]http://lh3.ggpht.com/dantemaster214/SEa8mthq82I/AAAAAAAACVY/1R9FhJeUVeg/debug.jpg[/IMG]

What do I do now?

which application are you trying to run?

---

### Post by Detailedghost on 2008-12-12
Well this is something to see when I had no idea what to do. A clean reinstall of wine did the trick for me. no worries. :)

---

