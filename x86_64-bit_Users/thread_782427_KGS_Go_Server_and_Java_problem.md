---
title: "KGS Go Server and Java problem"
date: 2008-05-04
forum: x86 64-bit Users
---

### Post by saru411 on 2008-05-04
Hello friends,

I recently reinstalled my system with Hardy Heron AMD64. I had [[COLOR="Green"]KGS[/COLOR]]("http://www.gokgs.com/download.xhtml")running fine. Now i find myself not remembering how I got it to work. I was hoping someone could help me resolve my problem.

The error I am currently stuck on is

```
XXXX@XXXXXXX:~$ javaws http://files.gokgs.com/javaBin/cgoban.jnlp
netx: Launch Error: Could not launch JNLP file. (java.lang.NullPointerException null)

```

Thanks for your time

---

### Post by saru411 on 2008-05-05
Hello again,

I found CGoban3 in /tmp/cache/http/files.gokgs.com/javaBin/cgoban.jar

I can open this file with sun java runtime 6 just fine by right clicking it and choosing to run it in sun java 6. What im afraid of is that this is a cache folder and it will be overwritten when it gets full. Does anyone know 1.) should i move this entire folder to my home folder and work with it from there.
2.) how to make this an executable lauch button on my top task bar.

Thanks for your time

---

### Post by dbd on 2008-05-18
I was having the same problem and I think it's due to this bug:
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/182971](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/182971)

To fix it just run this command:
sudo update-java-alternatives -s java-6-sun

---

