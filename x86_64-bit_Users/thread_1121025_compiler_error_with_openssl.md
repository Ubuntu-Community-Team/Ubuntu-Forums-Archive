---
title: "compiler error with openssl"
date: 2009-04-09
forum: x86 64-bit Users
---

### Post by kewlinux on 2009-04-09
Hi,
I'm compiling a program using openssl, I get below compilation error on ubuntu, but it works well on redhat.

/usr/bin/ld: cannot find -lkrb5

openssl is installed on ubuntu.

thanks,

---

### Post by kevmitch on 2009-04-10
That message is telling you that it is looking for a "krb5" library. That is a kerberos library, not openssl. But you might have expected that since as you say, openssl is installed. 

The library naming scheme is typically "lib<library>.so", though the trailing extension may vary. The good news is that you didn't have to know that krb5 mean kerberos if you have apt-file installed. 

```

apt-file search libkrb5

```

Will give you a list of packages that contain files whos name contains libkrb5. Typically when you are trying to compile something, you need not only the package in question, but also the "-dev" package. It looks like "libkrb5-dev" is what you're looking for.

---

