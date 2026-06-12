---
title: "apt-build, apt-src, apt-fu, etc..."
date: 2006-03-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by funkyade on 2006-03-27
Hi folks,

How can I get apt-build or similar to actually optimise for my CPU (G3) as opposed to the generic powerpc architecture as I can when using x86?

If I specify 
```

mcpu = -mcpu=750
march = -march=750

```
in /etc/apt/apt-build.conf, apt-build throws up an error or warning on compilation, however using these as CCFLAGS in a makefile is fine. I REALLY don't want to have to edit debian/rules for each package!

If I use this on a x86 system, everything is fine -
```

mcpu = -mcpu=pentium4
march = -march=pentium4

```
package(s) compile okay...

In addition, anything I place in options, or make_options seems to be ignored. So if I try to put the CCFLAGS in there, either nothing happens and they seem to be ignored or apt-build throws up an unrecognised parameter error.

A bit confused... help appreciated!

Also, I have wanted to use apt-fu, as this is more configurable and may be the answer, however there is no current .deb for it, and it seems to have disappearred (I have a source tarball form 2004, which I can't get to work btw). Anyone know anything about this?

Many thanks if anyone can help!

---

### Post by ssam on 2006-03-27
i dont know the answer, but i dont think you get much improvement. the G4 has altivec and may get improvments in some places. if you really want to do this gentoo is the distro to use. or if you want to speed things up a bit use a slightly lighter desktop (xfce). dapper has many optimisations, and will be faster than what you could get by building processor specific code.

---

### Post by funkyade on 2006-03-28
Thanks for the advice, I was noticing about a 5-10% speed improvement on x86 (p4 and athlonxp) using source builds optimised for those CPUs. I wanted to get the same kind of result on PPC... I am tempted to stick with Gentoo for ppc as it is super-fast, but am using Ubuntu/Debian everywhere else (x86), so would like to keep all machines in the same distro or thereabouts.

* I have PPC laptops, and x86 desktops... I run XFCE and Blackbox on everything already!

---

