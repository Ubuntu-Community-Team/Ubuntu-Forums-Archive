---
title: "Oy, I killed apt!  (kind of)."
date: 2009-05-23
forum: x86 64-bit Users
---

### Post by skullmunky on 2009-05-23
Synaptic hangs whenever I try to update the package lists.  What's going on, I wonder?  apt-get update reveals this:
```

Convert: acl 2.2.47-2
Convert: alsa-lib 1.0.20-1
Convert: arts 1.5.9-3
Convert: atk1.0 1.26.0-1
Convert: at-spi 1.26.0-1
Convert: attr 1:2.4.43-2
Error: Binary / source version mismatch, skipping.
Convert: audiofile 0.2.6-7

```
(very slowly).

oh dear, is it trying to convert every package into something else?  I installed some bunch of ia32 packages  while fooling around with Java ... is that what's done it?

---

### Post by unutbu on 2009-05-23
Maybe by looking in /var/log/dpkg.log you can figure out which ia32 packages you've recently installed, uninstall them, and/or reinstall the proper version for your Ubuntu release.

---

