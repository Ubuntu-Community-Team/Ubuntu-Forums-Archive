---
title: "OpenOffice.org and libstdc++.so.6"
date: 2006-06-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by chessforce on 2006-06-19
If you are getting the following error when trying to run OpenOffice (64-bit):
```

/usr/lib/openoffice/program/javaldx: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
/usr/lib/openoffice/program/pagein: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
/usr/lib/openoffice/program/soffice.bin: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory

```

you can try (re-)installing the "lib32stdc++6" package.

---

### Post by rx_ubulin on 2008-04-08
Another solution would be:

$ strace ooffice <*your-document.doc*

Look for the path for which ooffice is looking for libstdc++ SO file.
Most probably it will not be the valid version. Simply rename that file to anything else.
Now when ooffice looks for this file, it will fail. Then it will look for the same file in the standard INSTALLED location of libstdc++ file. That will be matching version with other SO file as well.

In my case it was looking for CXXABI_1.3.1 version in the wrongly identified libstdc++.so.6 file.
It was in /lib/tls/i686/sse2 folder. I renamed it to libstdc++.so.6.OLD.
After wards it started working fine.

---

