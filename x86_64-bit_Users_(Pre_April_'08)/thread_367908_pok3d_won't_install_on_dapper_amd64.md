---
title: "pok3d won't install on dapper amd64"
date: 2007-02-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by ravalox on 2007-02-22
Okay, I'm trying to follow these instructions: [http://www.pok3d.com/download.php](http://www.pok3d.com/download.php)

When I attempt those instructions I get: ```
Package python-poker3d is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-poker3d has no installation candidate
```

Any notions as to why this is happening?

---

### Post by Kilz on 2007-02-22
> **ravalox said:**
> Okay, I'm trying to follow these instructions: [http://www.pok3d.com/download.php](http://www.pok3d.com/download.php)

When I attempt those instructions I get: ```
Package python-poker3d is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-poker3d has no installation candidate
```

Any notions as to why this is happening?

Its a 32bit application. You are trying to install a 32bit repository and application with apt/synaptic. It isnt possible in the 64bit version.

---

