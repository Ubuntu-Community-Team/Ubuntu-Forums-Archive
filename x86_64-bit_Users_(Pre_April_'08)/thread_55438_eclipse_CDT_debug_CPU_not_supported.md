---
title: "eclipse CDT debug CPU not supported"
date: 2005-08-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by mattjackets on 2005-08-08
Hi all,

I'm new to the whole 64-bit thing, and I already have a problem...

I'm running the 64bit version of sun's jdk 1.5 (from sun, packaged with the java packager) with eclipse 3.1.0 (64bit) and CDT 2.1.1...

So, here's the problem:
I'll create a new managed make C++ project and throw a little "hello world" in there.  The auto-builder compiles and builds it without a problem...but when I go to configure  and run it (either as debug, or release) I get the following error (in the upper left-hand corner of the run/debug config window):

"The CPU is not supported by the selected debugger."

I have GDB selected as my debugger, and I've tried creating a "linux" platform in my gdb config as well as changing the supported cpus to '*' under platform '*' in the gdb config.  none of this helped... ](*,) 

ideas anyone?

thanks,
Matt

---

### Post by mattjackets on 2005-08-08
wow, every time I ask for help, i usualy find the solution myself anyway!

For anyone else who has this problem, here's what you can do:
1) download the new release candiate of CDT (3.0.0) and install it bu un-taring it into your eclipse directory
2) open "manage configuration" under help>software updates
3) disable CDT 2.1.1 and restart eclipse
4) enable CDT 3.0.0 and restart eclipse

this got my code running, but when I run the debugger on it it breaks...

The console output says "Stopped due to shared library event" a few times then dies a painful death...

ideas?

thanks
Matt

---

