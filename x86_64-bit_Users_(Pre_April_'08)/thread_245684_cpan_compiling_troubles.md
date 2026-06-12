---
title: "cpan compiling troubles"
date: 2006-08-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by alexn on 2006-08-28
Hi,
I have some troubles with installing CPAN modules:
it doen't want to do "make". I've already installed build-essentials, make, autoconf. Apache was builded and installed successfully.
 What is going wrong? :-$ 
 Any ideas?

---

### Post by alexn on 2006-08-28
Solved!
Thgere was no path for make in /etc/perl/CPAN/Config.pm

---

