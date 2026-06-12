---
title: "lib32gcc1 but it is not going to be installed (9.04)"
date: 2009-08-04
forum: x86 64-bit Users
---

### Post by emamm on 2009-08-04
Hello

I have just installed 9.04 x64 on my dell notebook.  The whole installation process went fine.   Now I need to install crossover but the system complains by issuing the following error msgs:

You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  ia32-crossover-pro: Depends: libc6-i386 but it is not going to be installed
                      Depends: lib32gcc1 but it is not going to be installed
                      Depends: lib32nss-mdns but it is not going to be installed
                      Depends: lib32z1 but it is not going to be installed
  ia32-libs: Depends: lib32gcc1 but it is not going to be installed
             Depends: libc6-i386 (>= 2.3.6-2) but it is not going to be installed
             Depends: lib32z1 but it is not going to be installed
             Depends: lib32stdc++6 but it is not going to be installed
             Depends: lib32asound2 but it is not going to be installed
             Depends: lib32ncurses5 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


The option -f doesn't help at all.

many thanks

Ed

---

### Post by JohnLau on 2009-08-04
What if you install the package libc6-i386 first?
John

---

### Post by emamm on 2009-08-05
Hello

Problem solved.  The previous attempt to install a package had somehow confused apt-get.  By removing any trace of it, the other libs were installed.

Many thanks

---

