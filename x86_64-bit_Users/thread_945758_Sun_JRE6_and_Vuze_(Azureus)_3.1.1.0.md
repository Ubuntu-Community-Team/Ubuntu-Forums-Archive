---
title: "Sun JRE6 and Vuze (Azureus) 3.1.1.0"
date: 2008-10-12
forum: x86 64-bit Users
---

### Post by sstecken on 2008-10-12
I'm running Hardy 8.04 and have sun-java6-jre installed from the software repository.

After extracting azureus and running ./azureus, I have the following error:

Starting Azureus...
Java is GCJ.. looking for Sun Java..
Java exec not found in PATH, starting auto-search...
ls: cannot access /usr/java/latest: No such file or directory
ls: cannot access /usr/java: No such file or directory
ls: cannot access /usr/lib/jvm/latest: No such file or directory
Java exec found in  /usr/lib/jvm/java-gcj/bin/
Java is GCJ.. looking for Sun Java..


How do I correct this error to get Azureus up and running?

Thanks.

---

### Post by sstecken on 2008-10-12
sudo update-alternatives --config java

Change default java selection.

---

