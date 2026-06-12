---
title: "why is ubuntu starting slow?"
date: 2007-12-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Lukasz Tarkowski on 2007-12-25
Dear Support
It says starting up then unallocated region 7 and 8, then it just starts slow !!
I am using it on external disk usb 2.0
The Ubuntu 7.10 supported till 2009
I installed my graphic card correctly and games work fast it just starting up problem :(
Do I have to edit something in fstab?

---

### Post by kuja on 2007-12-26
Try installing bootchart and see what's going on during your boot process that could be slowing it down. Also take a look at your logs (/var/log/*). I think messages and dmesg would probably be good places to start. Bootchart stores its charts by default in /var/log/bootchart/)

---

### Post by Epic Plecostomus on 2007-12-26
Also look here:  [http://ubuntuforums.org/showthread.php?t=580903](http://ubuntuforums.org/showthread.php?t=580903)

One of the solutions within helped fix my slow boot issue.

---

### Post by Lukasz Tarkowski on 2007-12-26
Hey Thank You
I figured where it is located on Ubuntu irc Chanel :)

---

