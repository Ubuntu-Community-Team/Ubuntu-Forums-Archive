---
title: "Tomcat 6 help"
date: 2008-11-12
forum: x86 64-bit Users
---

### Post by Lex-Man on 2008-11-12
I've installed Tomcat 6.

I want to set up netbeans to run with Tomcat 6 but I can't find the Catalina home.  Where is the base file located.  

Also I'm not sure I've set it up right.

---

### Post by jespdj on 2008-11-12
Did you install Tomcat via Synaptic or apt-get? You can use the following command to see which files were installed for a package:
```
dpkg -L <packagename>
```

---

### Post by dynamethod on 2008-11-13
I'm also having the same problem, heres a SS of what i got stuck on:

[http://img224.imageshack.us/my.php?image=wtftd3.png](http://img224.imageshack.us/my.php?image=wtftd3.png)

---

### Post by praxis1949 on 2008-12-06
I have it installed and running, after overcoming a "Permissions" problem with Tomcat directories. Mine were owned by "Root", and thus could not be seen by Netbeans, so I could not load the Tomcat server (its error message was "server.xml file corrupt". I was using Netbeans via the Synoptic Package Loader, and a copy of Tomcat from Apache-Tomcat. The location of Catalina_Home was usr/share/Tomcat6. The problem was resolved by giving myself (the user) ownership (via Nautilus).

John S

---

