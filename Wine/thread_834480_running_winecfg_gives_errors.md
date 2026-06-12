---
title: "running winecfg gives errors"
date: 2008-06-19
forum: Wine
---

### Post by portlandor on 2008-06-19
Hi,

I am running Hardy with wine  1.0.0~winehq-ubuntu~8.04-1.  I get the following errors upon running winecfg.  What could be wrong?  Seams like some library problem.

Thanks,  Rob




/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/wine)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/wine)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/wine)~
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libwine.so.1)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libwine.so.1)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libwine.so.1)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libwine.so.1)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libwine.so.1)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libwine.so.1)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /lib/tls/i686/cmov/libpthread.so.0)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /lib/tls/i686/cmov/libpthread.so.0)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /lib/tls/i686/cmov/libpthread.so.0)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /lib/tls/i686/cmov/libpthread.so.0)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /lib/tls/i686/cmov/libpthread.so.0)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /lib/tls/i686/cmov/libpthread.so.0)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libc.so.6)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libc.so.6)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libc.so.6)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libc.so.6)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /usr/bin/../lib/libc.so.6)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /lib/tls/i686/cmov/libdl.so.2)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /lib/tls/i686/cmov/libdl.so.2)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /lib/tls/i686/cmov/libdl.so.2)
/usr/bin/wine: /usr/bin/../lib/libc.so.6: no version information available (required by /lib/tls/i686/cmov/libdl.so.2)
/usr/bin/wine: relocation error: /lib/tls/i686/cmov/libdl.so.2: symbol _libc_intl_domainname, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

---

### Post by cogadh on 2008-06-19
Definitely looks like a lib problem. Did you do a custom install or compile of a libc6 library at any time? Have you tried to fix the problem by reinstalling Wine and/or libc6?

---

### Post by portlandor on 2008-06-19
Hi,

I believe libc came along with the distribution.  I definitely haven't compiled it.  I tried reinstalling it and wine, but still get the same errors.

Searches here and on Google don't show anybody having this same problem, so I guess I'm SOL.

Rob.

---

