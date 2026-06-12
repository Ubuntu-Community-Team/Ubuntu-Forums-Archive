---
title: "Installing Java sun jre 1.4 on a x86_64 system"
date: 2009-06-13
forum: x86 64-bit Users
---

### Post by ceriall on 2009-06-13
Hello im trying to install Java Sun jre 1.4.x on my ubuntu x86_64 system 
anyone have a workaround so i can install it ? 
Thanks in advance :)

---

### Post by dcstar on 2009-06-14
> **ceriall said:**
> Hello im trying to install Java Sun jre 1.4.x on my ubuntu x86_64 system 
anyone have a workaround so i can install it ? 
Thanks in advance :)

What is wrong with the JRE 5 or 6 packages in the repositories?

---

### Post by Amilo1718 on 2009-06-14
or with open JDK Java?
:popcorn:

---

### Post by ceriall on 2009-06-14
I can use JDK Java but i need the 1.4 version to get a program running, 
Ore else i would use Java6

---

### Post by jespdj on 2009-06-14
What program do you have that requires Java 1.4? Newer versions of Java are downward compatible with older versions, so any program written with Java 1.4 should run without any modifications on Java 5 or Java 6. If it doesn't, then the program has been badly written.

Did you try running it on Java 6? Does it not work properly? Do you get any error messages? If yes, then what are the error messages?

Install the Java 6 JDK with this command:
```
sudo apt-get install sun-java6-jdk
```

---

