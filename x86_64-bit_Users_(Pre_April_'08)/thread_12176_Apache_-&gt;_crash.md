---
title: "Apache -&gt; crash"
date: 2005-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by litbos on 2005-01-22
I have a amazing bug with apache.
If i want to connect my apache server from a other computer via my web browser, the PC freeze and I need to reset the PC. 

But if I open a terminal session on the server with SSH or directly on the server with the keyboard. the server don't crash and the web site work fine.

Do you have a solution.

(sorry for my english)

---

### Post by s_p_a_r_k_y on 2005-01-22
Have you taken a look at the apache logs to see what happened the last time it crashed? usually in /var/log/apache/error.log and access.log

Try that to see what the last line before it crashed the computer said. 

You could also try disabling all modules to see if its a module causing it to crash...however this is Linux and software shouldn't be able to take down the whole computer. Might be bad ram causing a kernel panic or something??? Look through the syslog in /var/log/syslog and messages.

---

### Post by litbos on 2005-01-22
I don't find information in syslog but in error.log , i found an information

```
[Sat Jan 22 19:16:52 2005] [notice] Apache/2.0.50 (Ubuntu) PHP/4.3.8 configured -- resuming normal operations
``` 

I think that the problem occur when a .php module is load.

PS : I use Apache2 web server

---

### Post by s_p_a_r_k_y on 2005-01-22
if you unload all the modules does it crash the server? If not, then add one at a time, test and see if it crashes. If not add the next one until it does crash, that way you will figure out which one is actually causing the crash. Then google the module for bugs.

---

### Post by litbos on 2005-01-23
I din't why a module crash , because all work correctly if I am log in the system.

---

### Post by litbos on 2005-01-24
I have made a memtest86 during the weekend and the memory have no problem.

some body have a solution  :-(

---

### Post by litbos on 2005-01-30
Hello,

Somebody have a soltution , it's very strange

---

