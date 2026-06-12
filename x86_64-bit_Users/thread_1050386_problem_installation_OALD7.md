---
title: "problem installation OALD7"
date: 2009-01-25
forum: x86 64-bit Users
---

### Post by Florian_ on 2009-01-25
How can I solve the problem that causes this while trying to install OALD7  ?

Verifying archive integrity... All good.
Uncompressing ..........................
/home/florian/.setup7951: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
Couldn't load 'atal'
The setup program seems to have failed on x86/glibc-2.1

Please contact Loki Technical Support at [email]support@lokigames.com[/email]
The program returned an error code (1)

 Thanks
(PS: Im a German in form 10. Please don't worry about my grammer)

---

### Post by Yellow Pasque on 2009-01-25
Execute:
```
sudo apt-get install libgtk1.2
```
If that does not fix your error message, then OALD7 is probably a 32-bit program, use getlibs to install the libraries it needs:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by Florian_ on 2009-01-26
Thank you!

---

### Post by 7oto on 2009-08-02
hi

i cant install it. i have tried getlib, nut no success ... pls help me ...

---

### Post by klett69 on 2009-11-15
I have the same problem.
In the past i installed OALD/ on ubuntu 8.04 (now i have u. 9.10).

I don't remember what i did then, probbaly installed those libraries.

I think glib-1.2.10 is obsolete for ubuntu 9.10
i have been able to install glib-2.22.2
since it says "or superior"; is that too much superior

then gtk+-1.2.10 wants the old glib1.3 or superior

i am surely making errors somewhere; need clearer ideas

i hope somebody who has solved this problem will read the thread

thank you

---

