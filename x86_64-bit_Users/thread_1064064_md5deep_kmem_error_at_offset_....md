---
title: "md5deep: kmem: error at offset ..."
date: 2009-02-08
forum: x86 64-bit Users
---

### Post by u-slayer on 2009-02-08
I tried to run md5deep on a directory. It was working at first, but when I came back in the mourning, this was filling my screen...

```
md5deep: kmem: error at offset 2121440772096: Bad address
md5deep: kmem: error at offset 2121440780288: Bad address
md5deep: kmem: error at offset 2121440788480: Bad address
md5deep: kmem: error at offset 2121440796672: Bad address
md5deep: kmem: error at offset 2121440804864: Bad address
md5deep: kmem: error at offset 2121440813056: Bad address
md5deep: kmem: error at offset 2121440821248: Bad address
md5deep: kmem: error at offset 2121440829440: Bad address
md5deep: kmem: error at offset 2121440837632: Bad address
md5deep: kmem: error at offset 2121440845824: Bad address
md5deep: kmem: error at offset 2121440854016: Bad address
md5deep: kmem: error at offset 2121440862208: Bad address
md5deep: kmem: error at offset 2121440870400: Bad address
md5deep: kmem: error at offset 2121440878592: Bad address
md5deep: kmem: error at offset 2121440886784: Bad address
md5deep: kmem: error at offset 2121440894976: Bad address
md5deep: kmem: error at offset 2121440903168: Bad address
md5deep: kmem: error at offset 2121440911360: Bad address
```

What does it mean? I googled it to no avail. Is my hard drive failing?

---

### Post by u-slayer on 2009-02-09
Okay, I found the cause of the problem. Md5deep was traveling down a symbolic link into my wine directory and apparently got lost in the bowels of my file-system. Removing the SymLink fixed the problem.

---

