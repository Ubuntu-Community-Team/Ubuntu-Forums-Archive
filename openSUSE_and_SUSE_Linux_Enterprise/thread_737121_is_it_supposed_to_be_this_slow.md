---
title: "is it supposed to be this slow?"
date: 2008-03-27
forum: openSUSE and SUSE Linux Enterprise
---

### Post by MONODA on 2008-03-27
Well I installed OpenSuSE KDE 10.3 and I have noticed that it is pretty slow. When I open system monitor it says I am using 1500 MB of RAM!!! is this normal?

---

### Post by stefangr1 on 2008-03-27
It's normal that a lot of memory is used, since free memory is used to cache programs to increase performance.

---

### Post by MONODA on 2008-03-27
oh... that makes sense. well why doesnt ubuntu do this?

---

### Post by stefangr1 on 2008-03-27
Ubuntu does that too. With the top command, you can see how your memory is used. In my case, almost nothing is left free, and 1.7 out of 2.0 GiB is used for caching. Thats why more memory always results in (some) performance gain.

---

### Post by MONODA on 2008-03-27
that's weird, top returns different info than system monitor...

---

### Post by erginemr on 2008-03-27
> **MONODA said:**
> that's weird, top returns different info than system monitor...

I suggest you to install htop, which reports system monitor compatible results...

You can install it in Ubuntu with:
```
sudo aptitude install htop
```

I am sure Yast should also have this package.

---

### Post by jonmcc33 on 2008-03-29
Got OpenSUSE 10.3 on a Dell Latitude D400 (released 2003) with a 1.8GHz Pentium M, 2GB DDR333 and an 80GB 5400RPM hard drive. It's quite fast.

---

