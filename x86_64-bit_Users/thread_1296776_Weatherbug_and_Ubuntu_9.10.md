---
title: "Weatherbug and Ubuntu 9.10"
date: 2009-10-21
forum: x86 64-bit Users
---

### Post by dunvar on 2009-10-21
I have download the 64 bit deb file for Weatherbug and the Package Installer comes up with Error: Dependency is not satisfiable: libswt3.2-gtk-java (>= 3.2)

I have download and installed the libswt-gtk-3.4-java and libswt-gtk-3.5-java as there is no libswt3.2-gtk-java.  Even though, I have installed the above two files, I still get the error and I am unable to install Weatherbug.  Has anyone ran into this and know how I can get this up and running?

Thanks

---

### Post by kartook on 2009-10-21
you can try this way may it will help you 

> sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
sudo apt-get install lib*

---

### Post by dunvar on 2009-10-21
Not sure how to change this thread to solve, but I have figured it out.  I removed all of the cji files and install sun-java6-jre and it now runs.

---

