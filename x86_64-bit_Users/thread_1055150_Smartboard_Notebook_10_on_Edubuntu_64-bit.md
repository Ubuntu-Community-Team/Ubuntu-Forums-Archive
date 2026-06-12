---
title: "Smartboard Notebook 10 on Edubuntu 64-bit"
date: 2009-01-30
forum: x86 64-bit Users
---

### Post by nbotticelli on 2009-01-30
I have just recently set up a fresh "perfect" dual boot system on a tower that I would like to dedicate to a SmartBoard that is in my computer lab in an elementary school.

Just for kicks I installed Edubuntu 64-bit for the first time (I've only ever used 32-bit software before) and so far zero problems in terms of installing and getting everything to run.

I downloaded the new smartboard notebook 10 software/drivers for Linux and I think I tried to install it properly (Extract downloaded folder, go to cli and type in sudo package install filename.package and it started to go through things but then came up with an error about not being able to support the 64-bit architecture.....

Duh! I should have thought about that with this computer. Unfortunately I have already put a lot of time into this "perfect" install and would really like to Not have to revert back to 32-bit for this. 

Is there a way to somehow convert the 32-bit package to 64-bit? Or force it to work?


Any and all help is greatly appreciated!

-Nicco

---

### Post by nbotticelli on 2009-01-30
Can the source be easily recompiled for 64-bit? Is that a difficult task?

Looks like I'm going to have to start over again with 32-bit.

---

### Post by nbotticelli on 2009-01-31
Sorry to have to bump this but is there any solution other than to wait for the smartboard people to release a 64-bit version?

Is there another section of this forum that this question would be better to have posted in?

---

### Post by tnjed111 on 2009-04-01
I have the same problem and found this thread. I'm not sure the whole software has to be redesigned to be compatible. It might be that just the autopackage format has to be changed. Nonetheless, I can't find way to do that. In other words, the software, once installed, may work perfectly well, but the installer itself is what's incompatible.
I could be wrong, but I know ubuntu comes with 32 bit compatibility libraries pre-installed. I also know the autopackage format is not 64 bit friendly.
Maybe you could install the software on a 32 bit system, and see where all the files go, and then cp them over to your 64 bit machine to see if they run. I don't really have the time or energy to do that right now, but if you're desperate enough maybe it's worth a try. At least just get the notebook software to run to at least be able to edit files would be nice.
Otherwise you're probably stuck asking the smarttech people to redistribute their software and maybe even port it to x64 if necessary which I doubt they will be in any hurry to do since relatively few people are running linux anyway, let alone linux 64.
I will let you know if I come up with any solution.

---

### Post by crafty184 on 2009-08-06
I have figured this out. Here is the solution.

First, I am running Ubuntu 9.04 Server 64 bit AMD version.

The basics are that you must install the 32 bit libraries before autopackage will allow you to install the software. The full details are on my [blog]("http://www.crucialthought.com/2009/08/05/how-to-install-smart-notebook-software-on-a-64-bit-ubuntu-machine/")..

[http://www.crucialthought.com/2009/08/05/how-to-install-smart-notebook-software-on-a-64-bit-ubuntu-machine/](http://www.crucialthought.com/2009/08/05/how-to-install-smart-notebook-software-on-a-64-bit-ubuntu-machine/)

I hope this helps, thanks for prodding me in the right direction.

Chris

---

### Post by hamfletta on 2009-09-03
I have been trying to install this on my 64bit ubuntu with little success. I get a error when it is checking for libxkbfile.so saying it is not installed. In fact it is the exact same error as the comment in the blog posting in the previous email. I used linux32 before running it and installed the 32 bit libraries.

I have tried installing the 32 bit libs into /usr/lib32 using getlibs but that does not seem to work. I tried the older version of the software but that dropped out almost immediatly with some GLIB problem which looked like a dead end.

If anyone else has solved this problem i would love to know the solution. I am going to try installing it on a 32bit virtual machine to see if i can just copy the files over to the right place on my 64 bit host. Other than that I am out of ideas. 

Adam

---

