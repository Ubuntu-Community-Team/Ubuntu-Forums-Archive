---
title: "problem installing zimbra desktop"
date: 2009-05-18
forum: x86 64-bit Users
---

### Post by prinson on 2009-05-18
prinson
Ubuntu 9.04 x86_64
Hi,
I could not install zimbra desktop. I downloaded 'zdesktop_1_0_build_1537_linux_i686.sh'
from zimbra website and run the commands but it returns error.

Terminal:

prinson@prinson-ubuntu:~$ cd Desktop
prinson@prinson-ubuntu:~/Desktop$ sh zdesktop_1_0_build_1537_linux_i686.sh
Unpacking JRE ...
Preparing JRE ...
zdesktop_1_0_build_1537_linux_i686.sh: 251: bin/unpack200: not found
Error unpacking jar files. Aborting.
You might need administrative priviledges for this operation.
prinson@prinson-ubuntu:~/Desktop$ 

I tried login as a root but the same thing repeated.
Can anyone help me

---

### Post by ptn107 on 2009-05-18
Install OpenJDK Java runtime from a terminal:
```
sudo aptitude install openjdk-6-jre -y
```
and try again.

---

### Post by prinson on 2009-05-18
):P    

Thanks ptn107.
It worked without any problem.

---

