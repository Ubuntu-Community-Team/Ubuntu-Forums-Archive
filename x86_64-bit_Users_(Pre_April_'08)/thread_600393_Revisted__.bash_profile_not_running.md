---
title: "Revisted:  .bash_profile not running"
date: 2007-11-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by professor-g on 2007-11-02
Dear All,

I have read previous threads on .bash_profile.
Still dont have my answer.

Running a small master+7 node Ubuntu 7.04 cluster on intel duo-core (2.13GHz), 2GB RAM, for quantum mechanical/chemical/molecular computations ... to take-over the world of course.

Anyways, was updating to 7.04 on one of the nodes. Cop[ied over my .bashrc and .bash_profile from other machines where it is working.

.bash_profile doesnt run 'automagically' on login - whereas it does on the other machines ?

Fine, I can start it with xterm -ls and it goes (found that one out)
I can also copy anything required in .bash_profile to .bashrc and all works.


By WHY - is the question - does .bash_profile not run on this node, considering an exact duplicate install and setup ?
(clearly not exact)

Want to understand the workings of .bash_profile and .bashrc relative to one another and the system.

Thx,


G.

---

### Post by lolindrath on 2007-11-02
Hi Professor-g, 

checkout this site: [http://joshstaiger.org/archives/2005/07/bash_profile_vs.html](http://joshstaiger.org/archives/2005/07/bash_profile_vs.html)

It gives an explanation of the differences between the two files.

--Lolindrath

---

