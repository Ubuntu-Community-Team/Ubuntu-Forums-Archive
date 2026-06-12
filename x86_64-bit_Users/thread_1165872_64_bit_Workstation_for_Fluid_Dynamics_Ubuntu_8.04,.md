---
title: "64 bit Workstation for Fluid Dynamics: Ubuntu 8.04, OpenSuse 11.1 or Fedora 10?"
date: 2009-05-21
forum: x86 64-bit Users
---

### Post by herger on 2009-05-21
Hi all.
I know it may look strange, but I have to ask You a question.
In my office they have bought a new pc: 2 Xeon quad-core, 48 Gbyte RAM.
We will use it for fluid dynamics and numerical simulations.

Which **64 bit OS** would be more suited? We will use commerical softwares like ANSYS FLUENT and AVL FIRE for CFD, C and FORTRAN compilers for parallel Lattice Boltzmann applications.

On my Dell laptop I have Ubuntu 8.04 32 bit, definitely good for personal use and good for the long term stability, but I have never succeeded in solving the following problems:

- X11 management via SSH: using gnuplot on external servers, I cannot see 
  the graphical outputs at all (I have tried everything that is written in this forum...);
- Audio (volume always too low, besides all the suggestions in this 
  forum);
- microphone (doesn't work, as above);
- Web management: when I am outside, it takes several minutes to start 
  up, since it doesn't recognise the web settings;

Since the new workstation would be just for work use, I have some doubts that Ubuntu could be the best choice.
I have also to say that the other workstation in the research group have Red Hat-based distros (Fedora, CentOS...).

Can You help me in my choiche?
Thanks and the best regards

Herger

---

### Post by cb951303 on 2009-05-21
I would go with something like CentOS for the sake of stability

OpenSuse 11.1 and Fedora 10 are both for desktop use with latest softwares just like Ubuntu. Centos is the recompilation of Red Hat Enterprise distro. It has outdated software thus it's inherently more stable :)

EDIT: Oh, Debian stable or Ubuntu LTS would do the job too...

---

### Post by Random-penguin on 2009-05-21
As this is a workstation at your office why not consider Redhat or Suse?

They are both very stable and you get the bonus of support from both companies; something your employer would probably really appreciate!

Good luck with the project.:)

---

### Post by marcelkoopman on 2009-05-21
Dont go for Centos because it has very very old software. And if you need a new version of something, you cant install it because you then need to upgrade the whole distro.

So Ubuntu is your best choice, I would go for the 8.10 AMD64 version though.

---

### Post by LO Matt on 2009-05-22
[http://www.ansys.com/services/ss-platform-support.asp](http://www.ansys.com/services/ss-platform-support.asp)

[http://www.avl.com/wo/webobsession.servlet.go/encoded/YXBwPWJjbXMmcGFnZT12aWV3JiZub2RlaWQ9NDAwMDYzMTIw.html](http://www.avl.com/wo/webobsession.servlet.go/encoded/YXBwPWJjbXMmcGFnZT12aWV3JiZub2RlaWQ9NDAwMDYzMTIw.html)

Use what is supported.  It will make things alot easier when you have support questions.  Looks like suse or red hat.

---

### Post by cb951303 on 2009-05-22
> **marcelkoopman said:**
> Dont go for Centos because it has very very old software.
that's the idea behind enterprise distros.

---

### Post by herger on 2009-05-27
Hi, Guys!
Thanks truly much for Your answers.
I think I will choose a FEDORA 10, since it is substantially Red Hat, it is free and also up-to-date.
I will let You know if I have some problems.
Thanks again and regards

Herger

---

