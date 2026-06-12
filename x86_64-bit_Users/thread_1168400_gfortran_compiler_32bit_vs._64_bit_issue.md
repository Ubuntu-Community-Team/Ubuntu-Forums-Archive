---
title: "gfortran compiler 32bit vs. 64 bit issue"
date: 2009-05-24
forum: x86 64-bit Users
---

### Post by lazer on 2009-05-24
OK I've been working with a FORTRAN code on a 32-bit machine for about 3 years.  I recently tried compiling this code on a 64-bit Mac.  It compiles fine on both machines with the following command

```
gfortran code.f -o code
```

Here's the fun part.  On the 32-bit Kubuntu machine it works just fine.  On the 64-bit machine it appears to get a floating underflow/overflow (divide by 0 issue).  The code uses a finite difference method to integrate a set of fluid equations.  I'm guessing the issue here is the assumed precision of the data type 'real.'  Anyway, what I want to know is what I need to do in order to get the code to compile with the 32-bit precision on the 64-bit machine.  Thanks.

---

### Post by lazer on 2009-05-24
I believe the problem is with the usage of 4byte vs 8byte (32bit vs. 64bit) floats.  The code seems to work on the 64 bit machine when I change all the
```
REAL
```
to
```
REAL*8
```
Now I just need to update my visualization routines in matlab to read the new datafiles.

---

