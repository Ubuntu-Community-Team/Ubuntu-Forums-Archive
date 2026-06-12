---
title: "raid 5 and cpu"
date: 2007-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by pnotequalsnp on 2007-09-11
I am running a raid 5 configuration (finished building) and I noticed that one of the cores on my quad core is always at 100% usage.  Is this normal?  The only thing I can think of that I have running is the raid 5.

Thanks for anyone's input on the subject.

---

### Post by tszanon on 2007-09-11
> **pnotequalsnp said:**
> I am running a raid 5 configuration (finished building) and I noticed that one of the cores on my quad core is always at 100% usage.  Is this normal?  The only thing I can think of that I have running is the raid 5.

Thanks for anyone's input on the subject.
I really doubt that the raid array should be causing it. Sure, it increases the cpu use, but shouldn't be that high.

---

### Post by dabl on 2007-09-11
Which process does ```
top
``` say is using all the CPU time?

---

### Post by saru411 on 2007-09-11
i run 2 different arrays, boot is on raid 0. home folder on raid 5. i have not experienced this ever. it most likely is something else. unfortunately i dont have the knowledge to help you.

---

### Post by pnotequalsnp on 2007-09-11
> **dabl said:**
> Which process does ```
top
``` say is using all the CPU time?

Good catch.  The process that is using 100% is ```
mysqld_safe
```.  It doesn't show up in the System Monitor probably because it is running under root.  Any ideas?

---

### Post by dabl on 2007-09-12
I don't know squat about mysql, so can't shed much light.  But I'd be researching that process to see why it needs to be chewing up an entire CPU core all day long.  :)

---

### Post by pnotequalsnp on 2007-09-12
It seems like it was not the raid 5 but instead sql trying to initialize.  I killed the process and restarted, with no adverse effects to mysql.  Thanks for all your input!

---

