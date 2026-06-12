---
title: "ia32-libs update fails"
date: 2009-08-25
forum: x86 64-bit Users
---

### Post by oiper on 2009-08-25
Hey, I've had this issue for a few weeks now. Update Manager lists ia32-libs v2.7ubuntu6.1 needing a security update. It fails with

```
E: /var/cache/apt/archives/ia32-libs_2.7ubuntu6.1_amd64.deb: trying to overwrite `/usr/lib32/at-spi/at-spi-registryd', which is also in package ia32-libs-gtk

```

I tried removing **/usr/lib32/at-spi/at-spi-registryd** but it doesn't exist. Any ideas on where to go from here?

[running Jaunty 64bit]

---

### Post by dverhoeven on 2009-09-02
I had the same issue, and sudo apt-get purge ia32-libs-gtk solved this for me.

---

