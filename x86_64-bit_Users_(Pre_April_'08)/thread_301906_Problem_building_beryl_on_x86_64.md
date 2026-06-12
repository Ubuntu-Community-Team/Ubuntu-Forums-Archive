---
title: "Problem building beryl on x86_64"
date: 2006-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by enigma_0Z on 2006-11-17
I am trying to build beryl from subversion on my x86_64 system, but I keep getting this same error:

```

make  all-recursive
make[1]: Entering directory `beryl-core'
Making all in mesa
make[2]: Entering directory `beryl-core/mesa'
make -C src
make[3]: Entering directory `beryl-core/mesa/src'
Making sources for linux-dri
make[4]: Entering directory `beryl-core/mesa/src/glx/x11'
make[4]: *** No rule to make target `/usr/include/gnu/stubs-32.h', needed by `glcontextmodes.o'.  Stop.
make[4]: Leaving directory `beryl-core/mesa/src/glx/x11'
make[3]: *** [subdirs] Error 1
make[3]: Leaving directory `beryl-core/mesa/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `beryl-core/mesa'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `beryl-0.1.2/beryl-core'

```

What can I do to fix this?

---

### Post by RAOF on 2006-11-18
Why the hell does beryl-core contain a copy of some mesa-source?

Anyway, it seems that it's trying to make some 32bit code for some reason.  It shouldn't be.  File a bug.  Alternatively, you could install the **ia32-libs** package, and add -I/usr/include/i486-linux-gnu/gnu/ to the CFLAGS for beryl.

---

### Post by enigma_0Z on 2006-11-18
Actually, my fix was:

```
$ grep -R stubs-32.h * | while read input; do sed s/stubs-32.h/stubs-64.h/g `echo ${input} | cut -d: -f1`; done
```

basically, replace instances of stubs-32 with stubs-64. perhaps this can be simply replaced with stubs? Anyway, I'll file a  bug, and thanks.

---

### Post by RAOF on 2006-11-18
> **enigma_0Z said:**
> ...
perhaps this can be simply replaced with stubs? Anyway, I'll file a  bug, and thanks.

/usr/include/gnu/stubs.h basically selects between stubs-32.h and stubs-64.h, depending on WORDSIZE.  So, yes, just replacing it should work.

---

