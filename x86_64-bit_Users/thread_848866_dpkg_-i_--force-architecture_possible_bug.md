---
title: "dpkg -i --force-architecture possible bug??"
date: 2008-07-03
forum: x86 64-bit Users
---

### Post by sickofthesea on 2008-07-03
I've just installed my i386 deb package of crossover office on amd64 Xubuntu 8.04 with sudo dpkg -i --force-architecture. It installed ok and seems to work but it does not show up in synaptic and dpkg -r says it is not an installed package when it quite clearly is!!

I tried this with another i386 package with the same result - does not show up in the list of installed packages. Does anyone know if this is by design behaviour or a possible dpkg bug or a dodgy system set-up on my computer? Can anyone replicate? Thanks.

Rgds,

Martin

---

### Post by Cappy on 2008-07-04
32-bit packages don't show up in Synaptic. The packages are kept track of by dpkg and you are probably not using the correct package name.

Use
```
dpkg -l '*[Cc]rossover*'
```
and it will probably list the package name

---

### Post by sickofthesea on 2008-07-04
Doh! You speak the truth - Thank you for your help.

Rgds,

Martin

---

### Post by soxs on 2008-07-05
plx mark as solved

---

