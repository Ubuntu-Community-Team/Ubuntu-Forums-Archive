---
title: "apt-get hangs up while building dependency tree"
date: 2007-05-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by janosch on 2007-05-18
hello

i am new to ubuntu and so to apt-get. I just installed my ubuntu server 7.04 (amd64). 
When i was adding some additional software it occured that when apt-get builds the
dependency tree it hangs up at exactly 50% progress. When I am opening a new
console and am doing a "top" i see apt-get using some 99.9% of cpu capacity. but it won't
finish its process. 

canceling the process and restarting it allways results in returning to the hang. 

For what i found out so far all I can do is restarting the hole system for getting it working again.

Does that sound familiar to anyone? I would be really greatfull for any hint, Thank you in advance!

---

### Post by Ken_Lewis81 on 2007-05-25
Does Aptitude (as in 'sudo aptitude update' & 'sudo aptitude upgrade') have the same problem at the command line?

Does 'apt-get clean' help?

Take care.
Ken.

---

### Post by dabl on 2007-05-25
I have seen that slow apt-get install situation before, when a repository server was having some heavy traffic or bandwidth problem.  If you go away and let it run, it will probably finish.  If you watch it, it never will ...

;)

---

