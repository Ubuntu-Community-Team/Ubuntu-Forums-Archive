---
title: "Opera. Problem with libqt-mt.so.3"
date: 2006-06-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Alinoe on 2006-06-10
Hi

I have a problem with opera.

```
alinoe@HAL:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.0-20060609.6/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

```

libqt-mt is installed

Thanks for any help and sorry for my english

---

### Post by kuja on 2006-06-10
Try getting the package of opera that has QT statically linked in, then you probably won't have to worry about it :)

---

### Post by _mobius_ on 2006-06-21
[QUOTE=kuja]Try getting the package of opera that has QT statically linked in, then you probably won't have to worry about it :)[/QUOTE]

I don't know why you'd smile about that.  Sure, I installed the static package to solve this problem.  However, others are running the shared package without issue.  Why not I?

---

### Post by _mobius_ on 2006-06-22
I've detailed how to fix the problem here:

[http://ubuntuforums.org/showpost.php?p=1167982&postcount=62](http://ubuntuforums.org/showpost.php?p=1167982&postcount=62)

---

### Post by -rafael- on 2007-09-09
tanks u

now, i can use opera.

---

