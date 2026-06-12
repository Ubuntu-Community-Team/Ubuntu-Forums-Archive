---
title: "java problem"
date: 2005-12-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by tmeier on 2005-12-06
I am working on installing Java on a Tibook 1ghz.  I followed the wiki and got to the point of trying to see what version with the line of "java -showversion".  The response I get from the terminal is "bash:java command not found"  I even tried it in correct directory.  Kind of stumped, any help is appreciated.  Thanks.

---

### Post by lisje on 2005-12-06
try:
java -version

what java are you trying to install?

---

### Post by tmeier on 2005-12-06
I get the same result "command not found"

I am installing the beta ibm-java2-ppc-50, that is named in the JavaPPC wiki.

I used the beta for iseries/pseries 32bit  from the referenced website.

---

### Post by khc on 2005-12-09
By default, it installs in /opt, so it's not going to be in your PATH. You will need to either add that to your path manually, or specify the full path when you run it.

---

