---
title: "Chris H"
date: 2007-09-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Chris Halliwell on 2007-09-17
Hi,

Just loaded Uuntu and didn't take much notice of what I put in as username. And consequently won't let me log in.

Any idea's how I can get round the user name and password or find out what it is?

Ta
Chris

---

### Post by Jouke74 on 2007-09-17
If you still know your root password, then you can start Ubuntu in the recovery mode. The will open a terminal window. Login is "root" password is the root password you gave (should also be your userpassword). Subsequently type "cd \home" and "ls". The name of the directory will be your username.
Take note that Linux is case sensitive, also with usernames (that might solve it). (And I am sure there is a more simple way to get around this by the linux pro's).

---

### Post by Chris Halliwell on 2007-09-17
Hi Thanks for your help. I have started in recovery. It comes up with root@chris-desktop:~#

Not sure what to type now, any more pointers?

---

### Post by Jouke74 on 2007-09-17
cd \home [enter]
ls [enter]

you should see something with your name listed in blue.

That is also your login name.

---

