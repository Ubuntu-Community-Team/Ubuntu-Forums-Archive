---
title: "[SOLVED] DPKG problems"
date: 2008-07-19
forum: x86 64-bit Users
---

### Post by DON618 on 2008-07-19
I could use some help . every time I try too add/remove a program 
an error message pop up tell me to reconfigure dpkg . 
I have tried to run the command that the message asked with out any success

I reinstalled ubutu and it worked well for a short time but once again
I have run in to this error message trying to install an remove programs

can any one help . how do I fix this  ??

---

### Post by warp99 on 2008-07-19
Need more information. What are the commands and the errors you are receiving?

---

### Post by DON618 on 2008-07-19
E: dpkg was interrupted , you must manually run 'dpkg --configure -a ' to
correct problem .

E:_cache->open() failed , please report 


I have tryed running  'dpkg --configure -a ' in the terminal window 
with out success.

    any suggestion

---

### Post by warp99 on 2008-07-19
> **DON618 said:**
> E: dpkg was interrupted , you must manually run 'dpkg --configure -a ' to
correct problem .

E:_cache->open() failed , please report 


I have tryed running  'dpkg --configure -a ' in the terminal window 
with out success.

    any suggestion

Did you run 'sudo dpkg --configure -a'?

---

### Post by DON618 on 2008-07-20
thank you that seem to have worked well :popcorn:

---

