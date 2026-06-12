---
title: "APTonCD?"
date: 2008-11-12
forum: openSUSE and SUSE Linux Enterprise
---

### Post by chrispche on 2008-11-12
Is there an equivalent to ubuntu/debians APTonCD on openSUSE? It would be useful to back up my system once I have it as I want it.

---

### Post by logos34 on 2008-11-12
doesn't look like there's an .rpm, so you'll have to build it from the tar.gz source code. Get it from the official website

---

### Post by 67GTA on 2008-11-12
There currently is no equivalent. In version 11, you can turn on caching for zypper, but there is no front end to gather them like aptoncd. You can manually put the cached packages on CD. They are kept in /var/cache/zypp. Info for turning on zypper cache is here: [http://lizards.opensuse.org/2008/10/06/zypper-best-feature/](http://lizards.opensuse.org/2008/10/06/zypper-best-feature/) or you can turn on caching for every repo with ```
zypper mr -ka
```

---

