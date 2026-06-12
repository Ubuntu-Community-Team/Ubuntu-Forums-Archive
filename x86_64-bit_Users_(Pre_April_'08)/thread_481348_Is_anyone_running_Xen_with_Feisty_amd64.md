---
title: "Is anyone running Xen with Feisty amd64?"
date: 2007-06-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by explainer on 2007-06-22
I am having a host of problems getting Xen installed and running.  The version of XenLinux downloaded with XenExpress and Virtual Iron, as well as the binary download from XenSource all don't recognize my NIC, a RealTek 8211.  This has forced me to attempt to build Xen 3.1 from source.  I have resolved almost all of the build problems, except for an unresolved reference to missing openssl (see below)

From the build stdout:

Checking check_openssl_devel: 
 *** Check for openssl headers FAILED
Checking check_python: OK

Can someone point me to the correct package to resolve this?  I have installed most of the packages even remotely referring to "openssl", to no avail.

---

### Post by incubus on 2007-06-22
> **explainer said:**
> 
Can someone point me to the correct package to resolve this?  I have installed most of the packages even remotely referring to "openssl", to no avail.

This is just a guess, but how about this package:
```

libssl-dev

```

incubus

---

### Post by explainer on 2007-06-23
Thanks, that got me to the next issue.  I am making progress;)

---

