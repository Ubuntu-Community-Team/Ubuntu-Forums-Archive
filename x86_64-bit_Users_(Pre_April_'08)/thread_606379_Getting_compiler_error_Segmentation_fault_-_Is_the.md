---
title: "Getting compiler error: Segmentation fault - Is there a flag?"
date: 2007-11-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Mark Grice on 2007-11-07
I'm compiling the GNUStep examples on my Ubuntu 64 and getting segmentation errors frequently.

Strange thing is sometimes I can go back and rerun make, and everything compiles (and runs) fine.

I'm thinking there must be a gcc flag I need to set to make this work right in 64 bit. 

Is there?

This is what I'm getting from MAKE:
```

Making all for bundle NSSavePanel-test...
 Compiling file NSSavePanel-test.m ...
NSSavePanel-test.m: In function ‘-[NSSavePanelTest init]’:
NSSavePanel-test.m:240: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.
The bug is not reproducible, so it is likely a hardware or OS problem.

```

---

### Post by fyrestrtr on 2007-11-07
I suggest you run memest. Are you experiencing anything else strange on your machine?

---

### Post by Mark Grice on 2007-11-08
> **fyrestrtr said:**
> I suggest you run memest. Are you experiencing anything else strange on your machine?

I ran it. Everything comes back fine.

And the machine has been running fine... no problems with anything except this...

---

