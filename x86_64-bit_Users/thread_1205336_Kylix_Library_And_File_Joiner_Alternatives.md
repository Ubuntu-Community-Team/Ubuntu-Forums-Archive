---
title: "Kylix Library And File Joiner Alternatives"
date: 2009-07-05
forum: x86 64-bit Users
---

### Post by TheHorror on 2009-07-05
I'm trying to install the Kylix library and this is what I have in the terminal:

```
username@computername:~/.hjsplit/kylixlibs3-borqt$ sudo ./install.sh
cp: cannot create symbolic link `libborqt-6.9-qt2.3.so' to `libborqt-6.9.0-qt2.3.so': File exists
[: 12: 1: unexpected operator

```

I did the chmod a+rw to the file before this also.  Or maybe somebody can give me an alternative file joiner that doesn't have the Kylix dependency.  Thanks.

---

### Post by zaddik01 on 2009-07-26
> **TheHorror said:**
> I'm trying to install the Kylix library and this give me an alternative file joiner that doesn't have the Kylix dependency.  Thanks.

If you are trying to join files together, try cat

---

