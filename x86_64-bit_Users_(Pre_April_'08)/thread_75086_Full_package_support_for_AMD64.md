---
title: "Full package support for AMD64"
date: 2005-10-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by medication on 2005-10-13
With the release of Breezy can the 64bit community expect to see more support?  Can we expect a repository that includes most of the packages available to the rest of the Breezy community?

---

### Post by estel on 2005-10-13
And...
Was OpenOffice 2 actually included in the default release in this version?

---

### Post by bytter on 2005-10-13
I sure hope so...
Like Wine... I want to use it with my AMD64 Ubuntu...

---

### Post by emrys on 2005-10-13
[QUOTE=estel]And...
Was OpenOffice 2 actually included in the default release in this version?[/QUOTE]
Yes, OpenOffice2 is included and works like a charm.

But forget about Wine.

---

### Post by bytter on 2005-10-13
[QUOTE=emrys]But forget about Wine.[/QUOTE]

Why?

---

### Post by RAOF on 2005-10-13
Because AFIAK it doesn't actually build on a 64bit system.  And even if it did, I think you'd only be able to run XP-64 programs.

You could possibly build a 32bit wine, but you'd need to be carefull to include 32bit versions of all the libraries it links to as well.  It'd just be a lot more effort :(

---

### Post by DancingSun on 2005-10-14
[QUOTE=RAOF]Because AFIAK it doesn't actually build on a 64bit system.  And even if it did, I think you'd only be able to run XP-64 programs.

You could possibly build a 32bit wine, but you'd need to be carefull to include 32bit versions of all the libraries it links to as well.  It'd just be a lot more effort :([/QUOTE]
Well, that's what they did for OpenOffice2.

---

### Post by estel on 2005-10-14
[QUOTE=emrys]Yes, OpenOffice2 is included and works like a charm.
[/QUOTE]

Great news :).

Is it a pure 64 bit build, or a 32 bit one on some sort of emulation layer?

---

### Post by DancingSun on 2005-10-14
[QUOTE=estel]Great news :).

Is it a pure 64 bit build, or a 32 bit one on some sort of emulation layer?[/QUOTE]
Like I implied above, OpenOffice2 is pure 32-bit.  No emulation layer, just 32-bit OO2 along with the 32-bit libraries that OO2 depends on.

---

### Post by picklestix on 2005-10-14
[QUOTE=RAOF]Because AFIAK it doesn't actually build on a 64bit system.  And even if it did, I think you'd only be able to run XP-64 programs.

You could possibly build a 32bit wine, but you'd need to be carefull to include 32bit versions of all the libraries it links to as well.  It'd just be a lot more effort :([/QUOTE]

Wine works great on my gentoo laptop, it does build against some of the x86 libs according to the ebuild though. Works as expected though once it's installed (Not only with 64 bit windoze programs.).

May be possible to install a gentoo64bit chroot, inside ubuntu64,  and then you could build some of these unsupported packages by using portage...? Just an idea.

---

