---
title: "Ld_library_path"
date: 2007-01-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by sajjad on 2007-01-09
How to edit the LD_LIBRARY_PATH in Ubuntu EDGY eft 64 bit.


i included the directories in /etc/ld.so.conf file and then run ldconfig

still i m having problem to run the examples for OpenSceneGraph saying that error while loading the shared libraries, no files or directory found.


Sajjad](*,)

---

### Post by po0f on 2007-01-09
sajjad,

Can you post the exact error message you are getting?  Also, how are you trying to run the program in question?

---

### Post by rockets on 2007-01-10
Also, make sure you are not forcing a 32 bit compile ( -m32 in GCC ). If you are, then the system might be looking for the 32 bit libraries. You will need to add the 32 bit libraries paths to your ld.so.conf. Also , check this bug I reported: 

[https://bugs.launchpad.net/ubuntu/+bug/77987](https://bugs.launchpad.net/ubuntu/+bug/77987)

---

