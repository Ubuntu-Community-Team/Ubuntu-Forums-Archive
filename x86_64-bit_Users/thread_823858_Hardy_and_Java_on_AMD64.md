---
title: "Hardy and Java on AMD64"
date: 2008-06-09
forum: x86 64-bit Users
---

### Post by graylion on 2008-06-09
hiya

I have migrated my gutsy to hardy and I am still having java applet probs

the things don't start. I may have too much java stuff installed:

graylion@lionscage:~$ dpkg --get-selections | grep java
ia32-sun-java6-bin				install
icedtea-java7-bin				deinstall
icedtea-java7-doc				install
java-common					install
java-gcj-compat					install
java-gcj-compat-dev				install
java-gcj-compat-headless			install
java-gcj-compat-plugin				install
libaccess-bridge-java				install
libbcel-java					install
libcommons-lang-java				install
libecj-java					install
libecj-java-gcj					install
libgetopt-java					install
libgnu-regexp-java				install
libhsqldb-java					install
libjaxp1.3-java					install
libjgoodies-forms-java				install
libjibx-java					install
libjline-java					install
liblog4j1.2-java				install
libmx4j-java					install
libregexp-java					install
libservlet2.3-java				install
libservlet2.4-java				install
libxalan2-java					install
libxerces2-java					install
libxpp3-java					install
openoffice.org-java-common			install
sun-java5-bin					install
sun-java5-jre					install
sun-java6-bin					install
sun-java6-fonts					install
sun-java6-jre					install
 
any suggestions?

thanks

graylion

---

### Post by Kilz on 2008-06-09
> **graylion said:**
> hiya

I have migrated my gutsy to hardy and I am still having java applet probs

the things don't start. I may have too much java stuff installed:

any suggestions?

thanks

graylion

what are the results of ```
ls -al /usr/lib/mozilla/plugins
``` and ```
ls -al /usr/lib/firefox-addons/plugins
``` 

When you say that Java doesnt work, what sites are you going to that dont work, please give a link.

---

### Post by graylion on 2008-06-09
it is being contrary. it noticed that I am asking for help and now of course works ...

thanks :)

Bernhard

---

