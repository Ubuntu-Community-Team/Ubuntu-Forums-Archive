---
title: "Mpi"
date: 2007-08-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by yogevor on 2007-08-31
Hi,
 I'm running a simple hello world program using MPI, no matter how many processes I'm specifying using np I'm always getting 0 of 1, does anyone had this problem before.

---

### Post by marpi on 2008-03-02
I'm experiencing the same trouble.
Does anybody know how to get around this "0 of 1" issue?

marpi

---

### Post by marpi on 2008-03-04
it's working fine with MPICH2 now

---

### Post by aswinms on 2008-05-10
> **marpi said:**
> it's working fine with MPICH2 now

Can you please tell me what are the steps I need to take to compile?! I used to do:
~$lamboot
~$mpic++ program.cpp
~$mpirun -np 5 ./a.out

I obviously can't do a lamboot with MPICH, and it doesn't compile with "mpic++", so what should I do? LAM/MPI was giving me a lot of problems and I was asked to use MPICH [here]("http://ubuntuforums.org/showthread.php?t=549047") but I'm having problems compiling!

---

