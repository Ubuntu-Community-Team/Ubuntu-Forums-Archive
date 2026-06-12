---
title: "Noticed a few things missing (gcj)"
date: 2005-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by feight on 2005-10-18
I was trying to install kLoOge Werks into my pristine installation of Breezy and noticed some problems compiling the java app. Worked fine in every linux installation I've tried that had java installed including Hoary.

I noticed that I didn't have gcj installed, went to install it and lo and behold got this message

```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.0/gcj-4.0_4.0.1-4ubuntu9_amd64.deb  404 Not Found
```

Why it wants a nonexistant package that it was somehow pointed to I have no idea. There are a few gcj-4.0 amd64 deb files on the site, but if I recall the highest was revision 4.

Anyone have any idea why it's looking for revision 9 and how to fix this problem without resorting to dpkg?

---

### Post by feight on 2005-10-18
Suddenly both my GPG key issue and the gcj-4.0_4.0,1-4ubuntu9_amd64.deb package is available... which is strange, I physically went to the website to the very folder it was supposed to be in and it wasn't there.

Anyway, all fixed it seems.

---

