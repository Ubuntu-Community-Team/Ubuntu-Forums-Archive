---
title: "is there an 64 bit app for my capture card?"
date: 2008-07-21
forum: x86 64-bit Users
---

### Post by mendo on 2008-07-21
i just installed the 64 bit ubuntu and all is well so far.  but when i search supported applications for a program to let me watch tv via the tuner on my capture card, i don't see anything.

is it possible that these apps are only available for 32 bit installs?  if so, could i install wine and then run a program to do what i want?

thanks.

---

### Post by soxs on 2008-07-21
> **mendo said:**
> i just installed the 64 bit ubuntu and all is well so far.  but when i search supported applications for a program to let me watch tv via the tuner on my capture card, i don't see anything.

is it possible that these apps are only available for 32 bit installs?  if so, could i install wine and then run a program to do what i want?

thanks.

iam not very familiar with capture cards, but if they are recognized correctly by ubuntu, the acrch isn't an obstacle. All opensource apps are availiable as 32 as aswell 64 bit apps.

You my check if it got recognizted at via "lspci" (search for your cards chip/name in the output file)

---

### Post by cariboo on 2008-07-21
TV  time is what I use. It would help it you told us what make and model and chipset if possible of your tv tuner card. Like the previous poster suggested, in a terminal type:

```
lspci
```

Paste the output into your next post.

Jim

---

