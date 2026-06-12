---
title: "libdvdcss"
date: 2006-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by proud2bcan8dn on 2006-03-24
Good day,

I have been trying to run sudo /usr/share/doc/libdvdread3/examples/install-css.sh
 and I keep getting this error after it has downloaded all the files it needs:

checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [build-stamp] Error 77

also, I cant seem to find the 'config.log' anywhere.

any ideas?

---

### Post by proud2bcan8dn on 2006-03-24
ok....I found that I was missing build-essentials, so I downloaded and installed that.

ran install-css.sh and it installed fine.

However, totem still says "cant read title from dvd"

---

