---
title: "MPICH issue using quad core with Ubuntu"
date: 2008-06-09
forum: x86 64-bit Users
---

### Post by maximillian3000 on 2008-06-09
Sorry if a little off on a tangent but I just installed ubuntu with an intel quad core chip and installed MPICH which is an implementation of MPI for parallelized programming across the cores.

When running an exe using 'mpirun' I get this error. Anyone have experience with this? I cannot even ssh into my machine.

ssh: connect to host mymachine port 22: Connection refused

$ ~/codestuff$ mpirun -np 2 my_exe

localhost: Connection refused
p0_25474:  p4_error: Child process exited while making connection to remote process on localhost: 0
p0_25474: (33.003906) net_send: could not write to fd=4, errno = 32

---

### Post by edantes on 2008-06-10
I have very little experience with MPI.  I was looking for a version to install in my dual core AMD and decided on OpenMPI because it looked better supported in Ubuntu.  All I can report is that it runs on the HelloWorld variations I tried.

---

### Post by Tom Mann on 2008-06-10
tried preceding the command with sudo?

---

### Post by maximillian3000 on 2008-06-10
yes sudo does not make a difference.

---

### Post by sharrah on 2008-06-30
I am having the same problem. However, to ssh into your own machine, try:

sudo apt-get install ssh

Hope this helps!

-SM

---

### Post by Saponsky09 on 2008-10-09
Make sure you have OpenSSH Server installed. You may have ssh client but not the server version.

---

