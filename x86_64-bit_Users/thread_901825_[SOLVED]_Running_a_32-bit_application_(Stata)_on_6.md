---
title: "[SOLVED] Running a 32-bit application (Stata) on 64-bit Ubuntu"
date: 2008-08-26
forum: x86 64-bit Users
---

### Post by knattlhuber on 2008-08-26
I'm trying to run a 32-bit application (the statistical software package Stata 9) under 64-bit Ubuntu. The terminal version of the application runs without problems but when I start the GUI version I get an error:

```
xstata: error while loading shared libraries: libgmodule-1.2.so.0: cannot open shared object file: No such file or directory
```

I downloaded the 32-versions of libgtk1.2, libgtk1.2-common, and libglib1.2-dbg, extracted the files in the /usr folders and copied them into /usr/lib32, but I keep getting the above error message.

Is there another place where I should copy the files to?
Any other suggestions to get this running?

(I know, there is a 64-bit version of Stata but I rather forego using the GUI version than paying them $$$ for switching the license)

---

### Post by IanW on 2008-08-27
Try this:-
```

sudo aptitude update
sudo aptitude install getlibs
sudo getlibs /path/to/xstata

```

Getlibs should automatically download and correctly install any 32-bit libraries xstata needs.

---

### Post by felker2 on 2008-08-27
> getlibs: Automatically solves dependencies for 32-bit programs on 64-bit
   On 64-bit systems it downloads and installs libraries needed for 32-bit programs and 64-bit programs.
   On 32-bit systems it downloads and installs libraries needed for 32-bit programs.

Wow, what a cool tool. Thank you!

---

### Post by knattlhuber on 2008-08-27
> **IanW said:**
> Try this:-
```

sudo aptitude update
sudo aptitude install getlibs
sudo getlibs /path/to/xstata

```

Getlibs should automatically download and correctly install any 32-bit libraries xstata needs.

It worked!
Thanks, mate.

---

