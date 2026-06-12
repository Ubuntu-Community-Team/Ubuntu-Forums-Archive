---
title: "installing a with a .sh file tinker"
date: 2008-10-31
forum: x86 64-bit Users
---

### Post by Kevin1234567 on 2008-10-31
Hi im trying to install Tinker:
[http://dasher.wustl.edu/tinker/](http://dasher.wustl.edu/tinker/)
on my ubuntu system and I'm a total noob conserning linux.
I started the shell file(tinker-linux.sh) with the console.
and it stopped giving me this error message:

tail: „+223“ kann nicht zum Lesen geöffnet werden: No such file or directory

gzip: sfx_archive.tar.gz: not in gzip format
tar: sfx_archive.tar: Kann open nicht ausführen: No such file or directory
tar: Nicht behebbarer Fehler: Programmabbruch.
No suitable Java Virtual Machine could be found on your system.
The version of the JVM must be at least 1.4 and at most 1.5.
Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
You can also try to delete the JVM cache file /home/user/.install4j

I've got a Java version but don't know which one and I can'tmake any sense of the rest. plz help

---

### Post by NTCT on 2008-11-15
I have absolutely the same issue installing Tinker.  Does anyone know, how to resolve it?

---

### Post by kioftes on 2008-11-16
i don't know if it helps but try this
```
sudo apt-get install java-common sun-java6-bin sun-java6-jre libaccess-bridge-java sun-java6-jdk
```
this will install java in your system (in case anything is missing...)

---

### Post by NTCT on 2008-11-16
It didn't help, unfortunately. But still thanks. I'll try contacting the developer of the software.

---

### Post by saru411 on 2008-11-17
Try opening synaptic package manager and then searching for python-tk

Install this package and see if the error continues

Synaptic Package Manager can be found under System>Administration>Synaptic Package Manager

---

### Post by NTCT on 2008-11-18
This also didn't help...

---

