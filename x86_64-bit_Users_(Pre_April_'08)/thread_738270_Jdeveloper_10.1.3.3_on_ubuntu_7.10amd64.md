---
title: "Jdeveloper 10.1.3.3 on ubuntu 7.10/amd64"
date: 2008-03-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by e2npau on 2008-03-28
Hello,

After some fiddling around I finaly got jdeveloper 10.1.3.3 running on ubuntu 7.10/amd64.

Here's what I did to get it up and running.

[LIST=1]
[*] Install java sdk 1.5 if that isn't installed already, do **NOT**  try to use java-6-* as they will result in a core dump.
```

$ sudo apt-get install sun-java5-jdk
```
[*] Download jdeveloper Base Install/Studio edition from [http://www.oracle.com/technology/software/products/jdev/htdocs/soft10133.html](http://www.oracle.com/technology/software/products/jdev/htdocs/soft10133.html) (registration required).
[*] Unzip the archive.
```

$ cd
$ mkdir jdev
$ cd jdev
$ unzip -q <path-to-downloaded-archve>/jdevstudiobase10133.zip
```
[*] Edit the jdev.conf and comment out the "SetJavaVM hotspot" option
```

$ cd jdev/bin
$ vi jdev.conf
```
Replace the line
```
SetJavaVM hotspot
```
With the following line
```
# SetJavaVM hotspot
```
[*] Update the jdev start-script
```
$ vi jdev
```
On the second line - add the following
```
export AWT_TOOLKIT=XToolkit
```
Adding the line "export AWT_TOOLKIT=MToolkit" is suggested at places - that however will also result in a segfault if you are running amd64,
[*] Now you should be able to start jdeveloper. You will get asked for the full path to your java installation the first time you start jdeveloper - the response is marked in bold below.
```
$ **./jdev**

Oracle JDeveloper 10g 10.1.3.3
Copyright 1997, 2007 Oracle.  All Rights Reserved

Type the full pathname of a J2SE installation (or Ctrl-C to quit), the path will be stored in ~/.jdev_jdk
**/usr/lib/jvm/java-1.5.0-sun**

```
[/LIST]
If this works for you - please make a quick reply in this thread and confirm!

---

### Post by sshabas on 2008-04-17
just came across this post and figured i'd give it a shot. i'm going to be taking a java class this summer so why not? i followed your steps word for word except i used nano instead of vi since i'm more familiar.

so the program starts, but all isee is a window titled "Oracle JDeveloper : Start Page" with no contents (see attached screenshot). if i move the mouse around i eventually mouse over what i assume to be buttons. i clicked one for tutorials, i guess, because it brought me to the jdev tutorials page.

any ideas for a fix to this?

---

### Post by e2npau on 2008-04-19
If you are about to take java class - I would suggest that you started out with something else then jdeveloper - such as emacs/vi and javac - or eclipse if you want an IDE.

Jdeveloper is actually more of a punishment for your sins in a previous lifen rather then a comforting enviroment for developers. Sometimes I'm forced to use jdeveloper at work and I figured maybe someone else also was....

As to you problem with a broken jdeveloper window - try the replacing the line jdev file with  "export AWT_TOOLKIT=MToolkit" and see if that helps.

---

### Post by shan420 on 2008-04-28
Awesome Tutorial Man !!!!, it works for me, exactly., I'm running UBUNTU 8.04 Studio edition on KDE, on a DELL Inspiron 9200, Intel 1.8 Mhz Mobile, 512 MB RAM, but I didn't care to install the great graphics or Desktop Effects.:guitar:


> **e2npau said:**
> Hello,

After some fiddling around I finaly got jdeveloper 10.1.3.3 running on ubuntu 7.10/amd64.

Here's what I did to get it up and running.

[LIST=1]
[*] Install java sdk 1.5 if that isn't installed already, do **NOT**  try to use java-6-* as they will result in a core dump.
```

$ sudo apt-get install sun-java5-jdk
```
[*] Download jdeveloper Base Install/Studio edition from [http://www.oracle.com/technology/software/products/jdev/htdocs/soft10133.html](http://www.oracle.com/technology/software/products/jdev/htdocs/soft10133.html) (registration required).
[*] Unzip the archive.
```

$ cd
$ mkdir jdev
$ cd jdev
$ unzip -q <path-to-downloaded-archve>/jdevstudiobase10133.zip
```
[*] Edit the jdev.conf and comment out the "SetJavaVM hotspot" option
```

$ cd jdev/bin
$ vi jdev.conf
```
Replace the line
```
SetJavaVM hotspot
```
With the following line
```
# SetJavaVM hotspot
```
[*] Update the jdev start-script
```
$ vi jdev
```
On the second line - add the following
```
export AWT_TOOLKIT=XToolkit
```
Adding the line "export AWT_TOOLKIT=MToolkit" is suggested at places - that however will also result in a segfault if you are running amd64,
[*] Now you should be able to start jdeveloper. You will get asked for the full path to your java installation the first time you start jdeveloper - the response is marked in bold below.
```
$ **./jdev**

Oracle JDeveloper 10g 10.1.3.3
Copyright 1997, 2007 Oracle.  All Rights Reserved

Type the full pathname of a J2SE installation (or Ctrl-C to quit), the path will be stored in ~/.jdev_jdk
**/usr/lib/jvm/java-1.5.0-sun**

```
[/LIST]
If this works for you - please make a quick reply in this thread and confirm!

---

