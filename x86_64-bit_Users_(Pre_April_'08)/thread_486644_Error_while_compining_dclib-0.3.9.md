---
title: "Error while compining dclib-0.3.9"
date: 2007-06-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by shivkiyer on 2007-06-28
Dear all,
I am trying to install Valknut 0.3.9 on Ubuntu 6.10 for an AMD 64-bit system. I need to first install dclib-0.3.9 on which valknut is dependent. I can only find Valknut 0.3.7 on the repositories so I proceeded to install through source codes.

I configured dclib-0.3.9 without any error. I ensured that bzlib.h was available. On running 'make' I got the following error:

-------------------------------------------------------
/usr/bin/ld: /usr/local/lib/libbz2.a(bzlib.o): relocation R_X86_64_32S against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libbz2.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [libdc.la] Error 1
make[3]: Leaving directory `/home/shivkvi/downloads/dclib/dclib-0.3.9/dclib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/shivkvi/downloads/dclib/dclib-0.3.9/dclib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/shivkvi/downloads/dclib/dclib-0.3.9'
make: *** [all] Error 2
--------------------------------------------------------

I went back and picked up the bzip2 executable provided on the bzip2 site for 64 bit processors but I got the same error again.

Thanks in advance for any suggestions or solutions.
Best regards,
Shivkumar Iyer.

---

