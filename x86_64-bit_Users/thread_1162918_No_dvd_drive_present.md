---
title: "No dvd drive present"
date: 2009-05-18
forum: x86 64-bit Users
---

### Post by hounddog65 on 2009-05-18
Hi Guys
I am new to the Linux world so be gentle.

I have installed Ubuntu 9.04 finding my way around and getting used to things.
I have a dvd burner and  a cd rom. when both are connected the system will not find the dvd drive. if i disconnect the cd drive the I can read the dvd drive. Can you please help wiith a solution.

---

### Post by ptn107 on 2009-05-18
From a terminal (Applications -> Accessories -> Terminal) type the following:
```
ls -l /media
```
and paste the output here.

---

### Post by hounddog65 on 2009-05-18
Results from ls 
total 8
lrwxrwxrwx 1 root root    6 2009-05-14 13:52 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-05-14 13:52 cdrom0
lrwxrwxrwx 1 root root    7 2009-05-14 13:52 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2009-05-14 13:52 floppy0

Note: The both devices work in windows xp so I dont think there is a hardware conflict.

---

