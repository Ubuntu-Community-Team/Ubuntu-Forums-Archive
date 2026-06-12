---
title: "Jbuider"
date: 2005-10-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Neuw on 2005-10-04
Hello guys!.
I am trying to install jbuider 2005 sdk, (the ones that is free).
I have downloaded j2r1.5 and installed it from sun but the jbuider is ...... making me :confused:  I tried the borland webpage and I have all the things ok but the installation doesnt work. This is the output of the terminal, Anybody nows why this?

e/1.4/bin/java
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libresolv.so.2: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/usr/lib/j2se/1.4/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory



thank you  and (sorry for my english). Byee

---

### Post by DancingSun on 2005-10-04
[QUOTE=Neuw]Hello guys!.
I am trying to install jbuider 2005 sdk, (the ones that is free).
I have downloaded j2r1.5 and installed it from sun but the jbuider is ...... making me :confused:  I tried the borland webpage and I have all the things ok but the installation doesnt work. This is the output of the terminal, Anybody nows why this?
e/1.4/bin/java
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libresolv.so.2: cannot open shared object file: No such file or directory
Launching installer...
grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/usr/lib/j2se/1.4/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
thank you  and (sorry for my english). Byee[/QUOTE]
A few things first...
[LIST=1]
[*]What is the command that you use to get those outputs?
[*]I see a reference to "1.4/bin/java", but I thought you installed Java 1.5?
[*]Why is the first set of output extracting JRE when you already have JRE installed?
[/LIST]

---

