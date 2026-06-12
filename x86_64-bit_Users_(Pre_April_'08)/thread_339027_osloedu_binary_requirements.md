---
title: "osloedu binary requirements"
date: 2007-01-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by mikecalder on 2007-01-15
I want to run a commercial package that is only supplied binary (the OSLO lens designer - there seems to be no capable open source package for this application) - I'm trying to run the OSLOEDU free educational version (on Dapper Drake, AMD64).

Of course it is a 32 bit compile, and I've done all the usual stuff, I think.  It called for the 32 bit version of libXm.so.3, which I managed to install using some instructions I found on the net.

Unfortunately, this libXm calls for GLIBC_2.4 in libc.  Now I'm getting to the edge of my capability in this area, but from what I see this is an old version of glibc.

Is there any safe way of getting access to this version, and if so could anyone provide a step-by-step idiot's guide? I don't want to overwrite the version of libc I have because I suspect that will zap a lot of other apps I run.  Normally I'd either compile from source or ask the vendor to fix, but since there's no source, and the vendor has explicitly said they are only supporting Red Hat and Suse, but are working on a "future version" which will be more generic, I suspect I'm not going to get a lot of assistance from them on a freebie version of a commercial product.

---

