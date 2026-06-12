---
title: "installing curl-devel on amd64"
date: 2008-07-23
forum: x86 64-bit Users
---

### Post by hautzi on 2008-07-23
Hello,

I'm trying to install pecl_http via the php-pecl installer which results in this error:

```

...
checking for curl/curl.h... not found
configure: error: could not find curl/curl.h
```

I figured out, that i need the package **curl-devel** to install, but this package is not part of the repository?

Can anybody tell me how to install it?

Thank you :-)

Best regards
Christoph Hautzinger

---

### Post by hautzi on 2008-07-23
got it by myself:

need to install **libcurl4-gnutls-dev**

---

