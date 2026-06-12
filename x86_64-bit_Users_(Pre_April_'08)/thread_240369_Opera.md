---
title: "Opera"
date: 2006-08-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by nemok on 2006-08-20
How can I get the Opera browser to work with Ubuntu x64. I've downloaded Opera from it's site but it says i cannot install because it has the wrong architecture (32)

---

### Post by kuja on 2006-08-20
Pull up a terminal, navigate to the directory containing the .deb file. 
```
dpkg --install --force-architecture opera*deb
```

There will likely be a problem yet after installation, you can fix it by following this thread - [http://ubuntuforums.org/showpost.php?p=1167982&postcount=62](http://ubuntuforums.org/showpost.php?p=1167982&postcount=62)

---

### Post by hajk on 2006-08-22
Make sure to download the *static* 32-bit deb-package for 386, then install with the  --force-architecture option. The static version of Opera doesn't make any calls to the 64-bit system libraries (which would fail if it did).

---

