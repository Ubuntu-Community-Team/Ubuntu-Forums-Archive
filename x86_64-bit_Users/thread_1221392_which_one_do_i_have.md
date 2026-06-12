---
title: "which one do i have"
date: 2009-07-23
forum: x86 64-bit Users
---

### Post by hedoe on 2009-07-23
okay
im am wondering how i would know which version of ubuntu (32 or 64 bit) that i got on a cd?
its and ISO image so i can run it live from my current pc
but im just not sure of where to look for that info
none of the packaging tells me which one i have either
thanks for your help

---

### Post by wojox on 2009-07-23
Applications > Accessories > Terminal

Open a terminal:

```
uname -a 
```

i686 = 32 bit

x86_64 = 64 bit

---

### Post by Sub101 on 2009-07-23
Type:

```
uname -m
```

into the terminal.

---

### Post by hedoe on 2009-07-23
okay which one is it?

uname -m
uname -a

ive gotten 2 different replys and that just confuses me
thanks btw

---

### Post by synapsys on 2009-07-23
Post the results of uname -m

---

### Post by jocko on 2009-07-24
> **hedoe said:**
> okay which one is it?

uname -m
uname -a

ive gotten 2 different replys and that just confuses me
thanks btw
Any will do. "-m" just gives you the **m**achine architecture (i686 or x86_64) of your kernel, while "-a" gives you **a**ll info.

---

