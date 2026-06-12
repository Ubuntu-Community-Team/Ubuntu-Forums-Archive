---
title: "Azureus under Java 1.5 (JRE 5.0 Update 2)"
date: 2005-04-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by shomi on 2005-04-02
hello , 

iv'e just installed JRE (latest) with no problems but when i run azareus this is what i get:
```
Starting Azureus...
Java exec not found in PATH, starting auto-search...
ls: /usr/java: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://java.sun.com
``` 

how do i fix this ??

---

### Post by blahrus on 2005-04-02
[QUOTE=shomi]hello , 

iv'e just installed JRE (latest) with no problems but when i run azareus this is what i get:
```
Starting Azureus...
Java exec not found in PATH, starting auto-search...
ls: /usr/java: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://java.sun.com
``` 

how do i fix this ??[/QUOTE]
 You do the last few lines from the ubuntuguide?

$ sudo ln -s /usr/java/jre1.5.0_01/bin/java /usr/bin/java
$ sudo ln -s /usr/java/jre1.5.0_01/bin/java_vm /usr/bin/java_vm
$ sudo cp /etc/bash.bashrc /etc/bash.bashrc_backup
$ sudo gedit /etc/bash.bashrc

---

### Post by shomi on 2005-04-02
i did what u said...
heres what  i get :

```
Starting Azureus...
Java exec not found in PATH, starting auto-search...
ls: /usr/java: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://java.sun.com
``` 

???

---

### Post by blahrus on 2005-04-02
[QUOTE=shomi]i did what u said...
heres what  i get :

```
Starting Azureus...
Java exec not found in PATH, starting auto-search...
ls: /usr/java: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://java.sun.com
``` 

???[/QUOTE]
 Did you fallow the whole guide or just the part I sent, how did you install it in the first place?

---

### Post by bored2k on 2005-04-02
Build a Java package just like it is said [http://www.ubuntulinux.org/wiki/Java](http://www.ubuntulinux.org/wiki/Java) . With that I have no problems with any Java application.

---

