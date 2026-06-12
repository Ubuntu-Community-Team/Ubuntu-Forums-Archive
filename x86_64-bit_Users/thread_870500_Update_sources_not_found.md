---
title: "Update sources not found?"
date: 2008-07-25
forum: x86 64-bit Users
---

### Post by NeilBlanchard on 2008-07-25
Hi,

I've updated to v8.04 and when the Update Manager checks the sources, I get this error:

> Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

How do I fix this?

---

### Post by Yellow Pasque on 2008-07-26
Remove the offending repos from sources.list
```
gksudo gedit /etc/apt/sources/list
```
Nice to see you on the Ubuntu forums, silent warrior.

---

### Post by NeilBlanchard on 2008-07-26
Hi,

Thanks for your reply.  The list (/etc/apt/sources) -gedit ... is blank?

---

### Post by Sef on 2008-07-26
> Thanks for your reply. The list (/etc/apt/sources) -gedit ... is blank? 

There was a mistake in the coding.  It should be

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by NeilBlanchard on 2008-07-26
Thank you very much -- that worked perfectly!:)

---

