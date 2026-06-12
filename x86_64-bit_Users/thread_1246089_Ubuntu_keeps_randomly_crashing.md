---
title: "Ubuntu keeps randomly crashing"
date: 2009-08-21
forum: x86 64-bit Users
---

### Post by kehon on 2009-08-21
ubuntu keeps randomly freezing where the system monitor stops moving, the mouse will move, but no hard drive activity and it won't stop doing it either so i have to hard reset. is there some key combination to tell it to shut down when it is giving me no response and how can i fix this because it's becoming annoying

---

### Post by jwaffolter on 2009-08-21
are you able to switch to a console when it freezes?
<ctrl><alt><f1>

if so login and type the following
sudo /etc/init.d/gdm restart

---

### Post by anthw27 on 2009-08-21
First thing you could try is, disabling the system monitor and see if that makes a difference.

If not and you continue experiencing  freezes and crashes, I would be testing your memory to see if it hasn't developed a problem.

Get a copy of memtest preferably an iso and get some one to burn it for you
then boot from the CD and test to make sure there are no memory errors.

---

