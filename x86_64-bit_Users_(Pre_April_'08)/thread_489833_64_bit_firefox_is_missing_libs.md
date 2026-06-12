---
title: "64 bit firefox is missing libs"
date: 2007-07-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by fakie_flip on 2007-07-01
Does this happen to anyone else? Why are these missing libs not included with Ubuntu 64 bit version?

```
chris@ubuntu:~$ ldd /usr/lib/firefox/firefox-bin | grep not
        libmozjs.so => not found
        libxpcom.so => not found
        libxpcom_core.so => not found
chris@ubuntu:~$ ldd /usr/lib/swiftfox/swiftfox-bin | grep not
        libmozjs.so => not found
        libxpcom.so => not found
        libxpcom_core.so => not found
        libplds4.so => not found
        libplc4.so => not found
        libnspr4.so => not found
        libsmime3.so => not found
        libssl3.so => not found
        libnss3.so => not found
        libsoftokn3.so => not found
        libxpcom_compat.so => not found
chris@ubuntu:~$ 
```

---

### Post by Kilz on 2007-07-01
> **fakie_flip said:**
> Does this happen to anyone else? Why are these missing libs not included with Ubuntu 64 bit version?

```
chris@ubuntu:~$ ldd /usr/lib/firefox/firefox-bin | grep not
        libmozjs.so => not found
        libxpcom.so => not found
        libxpcom_core.so => not found
chris@ubuntu:~$ ldd /usr/lib/swiftfox/swiftfox-bin | grep not
        libmozjs.so => not found
        libxpcom.so => not found
        libxpcom_core.so => not found
        libplds4.so => not found
        libplc4.so => not found
        libnspr4.so => not found
        libsmime3.so => not found
        libssl3.so => not found
        libnss3.so => not found
        libsoftokn3.so => not found
        libxpcom_compat.so => not found
chris@ubuntu:~$ 
```

I used the command you did for Firefox and got the same results, then I looked in the folder. The files exist.

---

### Post by RAOF on 2007-07-02
Because they are not in LD_LIBARY_PATH, but the firefox wrapper script sets LD_LIBARY_PATH to the right thing before running firefox-bin.  In short, expected behaviour.

---

