---
title: "eror when i get syanptic !!!"
date: 2005-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by erez1012 on 2005-11-20
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release Candidate powerpc (20051005) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20Candidate%20powerpc%20(20051005)_dists_breezy_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release Candidate powerpc (20051005) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20Candidate%20powerpc%20(20051005)_dists_breezy_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)



what cen i do???:(
i cent sudo apt-get install from the terminal also

---

### Post by linbetwin on 2005-11-20
That's strange... It asks for your CD. Did you try disabling it in the repository list?

---

### Post by erez1012 on 2005-11-21
when i want to install something "sudo apt-get install ..."
 i get this:
root@erez:~# sudo apt-get install totem-xine
Reading package lists... Done
Building dependency tree... Done
Package totem-xine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libtotem-plparser0 libtotem-plparser-dev
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release Candidate powerpc (20051005) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20Candidate%20powerpc%20(20051005)_dists_breezy_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release Candidate powerpc (20051005) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20Candidate%20powerpc%20(20051005)_dists_breezy_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package totem-xine has no installation candidate
root@erez:~#

---

### Post by ssam on 2005-11-21
in synaptic go to settings -> repositories. select the cd line, and remove it. then click ok.

press the reload button, and hopefully all will be well.

---

### Post by erez1012 on 2005-11-21
:):):)
thanks man it work!!!

---

