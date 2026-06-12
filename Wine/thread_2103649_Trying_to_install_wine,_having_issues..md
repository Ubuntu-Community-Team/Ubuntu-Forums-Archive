---
title: "Trying to install wine, having issues."
date: 2013-01-10
forum: Wine
---

### Post by poeticink626 on 2013-01-10
Ok, so I run apt updates and all that, but when I type in sudo apt-get install wine1.5 in terminal. 

I get this

The following packages have unmet dependencies:
 wine1.5 : Depends: wine1.5-i386 (= 1.5.21-0ubuntu1) but it is not installable
E: Unable to correct problems, you have held broken packages.

If I try the software center, I get this message. 

Package dependencies cannot be resolved

then in details, it says. 
wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not going to be installed

I even tried aptitude and dpkg. Nothing is working.

---

### Post by SOSTALAS on 2013-01-21
I too am having the same error message - Package dependencies cannot be resolved.  I am running an AMD 64bit. I seem to have trouble intalling most programs I have tried to install through the Software Center.

---

### Post by sffvba[e0rt on 2013-01-22
*Thread moved to **Wine**.*


404

---

### Post by Tweak42 on 2013-01-25
Have you tried installing synaptic and looking up the broken packages under custom filters?

Also can you remove wine1.4, then try installing wine1.5?

> **poeticink626 said:**
> Ok, so I run apt updates and all that, but when I type in sudo apt-get install wine1.5 in terminal. 

I get this

The following packages have unmet dependencies:
 wine1.5 : Depends: wine1.5-i386 (= 1.5.21-0ubuntu1) but it is not installable
E: Unable to correct problems, you have held broken packages.

If I try the software center, I get this message. 

Package dependencies cannot be resolved

then in details, it says. 
wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not going to be installed

I even tried aptitude and dpkg. Nothing is working.

---

