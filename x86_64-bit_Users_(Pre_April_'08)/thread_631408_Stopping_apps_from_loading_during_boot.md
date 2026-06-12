---
title: "Stopping apps from loading during boot?"
date: 2007-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by acidblue on 2007-12-04
How do i stop programs from starting when i boot?
When ever i boot into  Ubuntu xmms and some other apps
load and start automaticlly.

---

### Post by mozkill on 2007-12-04
well, there used to be a thing called an "init level editor" that you got with every distro of unix.  now we have a "services" control panel that only shows a few of the init services.

what you need is a run level editor that edits all 6 run levels. 

do some research... it  will take a little time but you will figure it out.

also, do a man of the "init" command.   you should also understand that typing "sudo init 6" will reboot the computer.

also, there is another way to start programs called "xinetd", which i am not too familiar with and so dont assume that the solution to your problem is in one of the /etc/init.d  scripts.

---

