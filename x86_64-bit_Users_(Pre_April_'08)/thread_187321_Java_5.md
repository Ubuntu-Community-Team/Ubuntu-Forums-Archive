---
title: "Java 5"
date: 2006-06-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by ormandj on 2006-06-02
Is there support for Java/64bit? I do a lot of Java EE 5 development using Netbeans 5.5, and need 64-bit Java for my work (I'm using oodles of ram). It seems like many things in the Linux world aren't 64-bit yet for whatever reasons, I'm curious if this is the case with Java too.

Thanks. :)

---

### Post by JoWilly on 2006-06-02
Sun java 5 is in the multiverse repos.

---

### Post by Arc Owner on 2006-06-02
Yes, there is support for Java in 64-bit, but it is currently very poor. If you plan on developing with Java or doing anything other than use in basic apps, then it would be better to use the x86-kernel and x86-java.

---

### Post by ormandj on 2006-06-02
[QUOTE=Arc Owner]Yes, there is support for Java in 64-bit, but it is currently very poor. If you plan on developing with Java or doing anything other than use in basic apps, then it would be better to use the x86-kernel and x86-java.[/QUOTE]

That is what I was afraid of, I guess no Ubuntu for me. :(

Thanks again.

---

### Post by JoWilly on 2006-06-02
[QUOTE=ormandj]It seems like many things in the Linux world aren't 64-bit yet for whatever reasons, I'm curious if this is the case with Java too.

Thanks. :)[/QUOTE]

Well, 64bit support on Linux is much better than on windows. So if this is not enough for you, I wonder what platform you are developing on.... Sun or Mac ?

---

### Post by yaggo on 2006-07-06
Just for general info:

I had strange problem with amd64 version of JDK 1.5: some database operations totally slowed down a java program, while my co-worker was running the same program on 64-bit java just fine. We both run amd64 Dapper and K8 kernel. Switching to 32bit java solved my problem.

So, I installed 32bit java from Sun's website to /opt and kept 64bit from multiverse as a default JDK.

---

### Post by zaddik01 on 2006-08-19
If you are doing J2EE on Linux you are stuck with 32bit version J2EESDK because Sun hasn't released a 64bit. I am curious why there is a 64bit JVM, but not an appserver? Is there a difference in 64bit bytecode versus 32? Also, is Tomcat in the repositories a 64bit version?

---

### Post by Kilz on 2006-08-20
Tomcat5 is in the 64bit repositories, but it doesnt say if its a 64bit application. Odds are it is.

---

### Post by Jonnycat26 on 2006-08-20
> **ormandj said:**
> That is what I was afraid of, I guess no Ubuntu for me. :(


I use the 64bit JDK and have yet to have any problems (other than the usual bugs with Netbeans).  :)

---

