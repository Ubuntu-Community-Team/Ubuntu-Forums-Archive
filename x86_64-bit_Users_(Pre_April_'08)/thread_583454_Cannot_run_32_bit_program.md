---
title: "Cannot run 32 bit program"
date: 2007-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by clemente on 2007-10-20
Hello, 

I used feisty 64 bit on my amd sempron with "high pleasure and low problems". ;-) 

Today I installed gutsy 64 bit on the same machine and found, that I cannot run any 32 bit programs. 

I.e., I use eclipse for development. If I run eclipse from the command line, bash returns "no such file or directory.". Of course, the executable is there, I can stat it, ... 
Same thing happens on firefox 32 bit (from mozilla.com), thunderbird, java tools (java, javac, javah, ...) and all 32 bit executables I found no my system. 
All these programs ran under feisty 64 bit. 

Does anyone know, what happens here? And - much more important - how I can run all my tools? 

Many, many thanks for every hint, 
Clemente 

P.S: linux32 /run/my/executable gives the same result as stated above.

---

### Post by clemente on 2007-10-20
As so often, I found the solution short after posting my problem... I did search before, honestly. ;-) 
The alternate installation routine - which I prefer - does not install all neccessary libs. 
With: 
apt-get install ia32-libs lsb-core
or same with synaptic, all works fine. 

Greetz,
Clemente

---

