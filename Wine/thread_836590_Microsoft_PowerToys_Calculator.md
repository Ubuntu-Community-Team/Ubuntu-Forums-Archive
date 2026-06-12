---
title: "Microsoft PowerToys Calculator"
date: 2008-06-21
forum: Wine
---

### Post by jamiemac2005 on 2008-06-21
Hey, i've been having a problem getting microsoft's powertoy calculator running on wine, actually it runs fine, just the interface uses webdings rather than a readable font... I've tried fixing this (by messing with font files) but i can't get it done and i haven't successfully modified the registry to change fonts in wine yet...

Anyway, i've attached a screenshot to show you the problem... and the image here: [http://dubhlaidh.blogspot.com/2007/06/vista-w-powertoys-power-calculator.html](http://dubhlaidh.blogspot.com/2007/06/vista-w-powertoys-power-calculator.html) depicts what it should look like... I do have alternative calculators etc. but i'd much rather get this one working (i'm used to it and i like it...).

Thanks to anyone who can help me,
Jamey

---

### Post by cogadh on 2008-06-21
Run the app from the terminal and post the output. It may contain some error message that will explain what is happening.

---

### Post by jamiemac2005 on 2008-06-21
hey, when i run it from the terminal i get:

 ./PowerCalc.exe 
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report


sorry i'm a bit of a linux and wine noob so i don't know a lot about this...

Cheers if you can help me,
Jamey

p.s. incase it helps i'm running wine 0.9.59 on hardy

---

### Post by z.s.tar.gz on 2008-06-21
Do you _have_ to use powercalc? If not, have you looked into alternatives like kmplot and speedcrunch? If you have to use it, sorry I don't use wine that much.

---

### Post by cogadh on 2008-06-21
> **jamiemac2005 said:**
> hey, when i run it from the terminal i get:

 ./PowerCalc.exe 
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report


sorry i'm a bit of a linux and wine noob so i don't know a lot about this...

Cheers if you can help me,
Jamey

p.s. incase it helps i'm running wine 0.9.59 on hardy

First things first, upgrade to Wine 1.0, it is way better than 0.9.59:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
After doing that, run it again from the terminal and see what happens. If you still get those preloader errors, follow the instructions here:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)
Then try running it again.

---

### Post by jamiemac2005 on 2008-06-22
Hey, thanks for the help cogadh, the problem is still not resolved but the preloader errors are gone... I upgraded to 1.0, ran it from the terminal again and got the following output:

```
./PowerCalc.exe 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
```

I'm unsure of what this is, and have tried searching to no avail... 

(To z.s.tar.gz:) no i don't have to use powercalc, i've tried looking for alternatives(not found anything exactly like it but i will check out the two alternatives you suggest thanks), the reason i like the powertoy calculator is it's history view, and customiseable variables&functions so if either has that i'd be just as happy, i simply have used this calculator for a year or two and am used to it's notation and usage...

Still if anyone has a workaround/fix for this (if anyone knows how to rid of the font/replace it[i dont specifically need the font webdings nor do i use it in any other programs in wine]) i'd be very thankful...

Cheers,
Jamey

p.s. i will still try to fix this even if an alternative is found so any further help is much appreciated(bodge/workaround will suit me just as well as a proper fix)

---

### Post by jamiemac2005 on 2008-06-22
Ignore what i just said, i've just tried speedcrunch (thanks z.s.tar.gz) It works better than MS PowerCalc, (has a syntax-highligting like function)... I don't think i need the fix anymore, thanks everyone for the help...

Cheers,
Jamey

---

