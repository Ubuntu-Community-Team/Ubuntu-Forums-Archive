---
title: "eclipse 3.0 ,  libgtk-x11-2.0.so.0 error"
date: 2004-12-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by litbos on 2004-12-29
when i run eclipse 
i have this error 

[HTML]./eclipse: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory[/HTML] 

can you help me

i have a second problem , how to set JAVA_HOME , i have put it in  /etc/profile but it seems that ubuntu not load the file at login

sorry for my english :oops:

---

### Post by rbran100 on 2004-12-29
The first thing to look at is the Wiki for eclipse on ubuntu, if you still have trouble after the dependencies are satisfied, let me know.

[COLOR=Olive]https://www.ubuntulinux.org/wiki/EclipseIDE[/COLOR]

---

### Post by litbos on 2004-12-29
Now i can use java but eclipse doesn't run yet.

i have now try the AMD64 version but i have this error

[HTML]java.version=1.5.0_01
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=amd64, WS=gtk, NL=fr_FR

!ENTRY org.eclipse.osgi dÃ©c. 29, 2004 19:15:33.744
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /home/vincent/My Downloads/eclipse64/eclipse/plugins/org.eclipse.swt.gtk64_3.0.1/os/linux/amd64/libswt-pi-gtk-3063.so: /home/vincent/My Downloads/eclipse64/eclipse/plugins/org.eclipse.swt.gtk64_3.0.1/os/linux/amd64/libswt-pi-gtk-3063.so: cannot open shared object file: No such file or directory[/HTML] 


did you have a solution ?

---

