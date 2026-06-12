---
title: "MPICH on 64-bit vs 32-bit Hardy"
date: 2008-07-10
forum: x86 64-bit Users
---

### Post by johanseland on 2008-07-10
I am currently deploying an existing Navier Stokes simulator written in Fortran 90 and MPI on a Quad Core Intel box running Ubuntu Hardy.

The performance of the simulator was very poor, and I have spent the better parts of the last two days to track it down. Unfortunately, the simulator code is very complex, and I have not yet been able to create a small example which clearly isolates the problem.

Let me first summarize my findings:
[LIST]
[*]Simulator runs at full speed on Hardy 32-bit using repository MPICH and gfortran.
[*]Simulator runs at full speed on Gentoo 32-big using repository versions of MPICH and gfortran.
[*]Simulator runs very slow on Hardy 64-bit using repository MPICH and gfortran
[*]Simulator runs at full speed on Hardy 64-bit when _MPICH_ (not the simulator itself!) is compiled with Intel Fortran (ifort). It does not matter if the simulator itself is compiled with ifort or gfortran. 
[*]Simulator runs very slow on Hardy 64-bit when _MPICH_ is compiled using gfortran. It does not matter if the simulator itself is compiled with ifort or gfortran.
[/LIST]

This behavior is consistent across several different machines (both dual and quad cores). 
 
The difference between "very slow" and full speed is around 50x. Profiling shows that this time is spent in MPI synchronization routines.

I initially thought the Gnu Fortran compiler was the culprit, but now I am not so sure anymore. 

Any advice would be helpful.

---

