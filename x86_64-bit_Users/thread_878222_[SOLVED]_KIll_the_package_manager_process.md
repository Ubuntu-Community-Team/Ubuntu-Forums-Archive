---
title: "[SOLVED] KIll the package manager process"
date: 2008-08-02
forum: x86 64-bit Users
---

### Post by vikrant_me on 2008-08-02
I am trying to install opera_9.51.2061.gcc4.qt3_amd64.deb when i double click it the package manger opens up and hangs, how do i kill it?? closing the package manager does nothing.

---

### Post by Yellow Pasque on 2008-08-02
You can either restart your system (which you've probably done by now) or kill it by going to System -> Administration -> System Monitor and looking for a process named gdebi.

---

### Post by opr8ive on 2008-08-03
wouldnt opening a terminal and entering **sudo killall gdebi** work just as well?

Jason

---

### Post by Yellow Pasque on 2008-08-03
Yeah, but it requires typing :\

---

### Post by punkybouy on 2008-08-03
Why not just install it by right clicking the file and using the package manager installation option?

---

