---
title: "UbuntuPPC + IBM Java 1.5 + Netbeans"
date: 2006-03-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by amklinux on 2006-03-20
Hi.

I'm trying to use UbuntuPPC as my main platform, but I'm having some problems with Java. I know that Sun doesn't have a Linux PPC version of its JDK. So, I installed the IBM JDK 1.5. I need to run Netbeans, but when I try to do that, I get the following error:

JVMJ9VM007E Command-line option unrecognised: -XX:PermSize=32m
It was not possible to create a Java Virtual Machine

Searching in ubuntuforums.org and google did not produced useful results.

Any help would be greatly appreciated.

Thanks,

amklinux.

---

### Post by sulobanks on 2006-03-21
I had the same problem, unfortunately.  In my situation, I was just curious about netbeans, so I didn't try very hard and never got it to work.  I know it doesn't fix your problem, but I thought it might help to see that it's not just something weird with your installation.  My basic assumption is that Netbeans just doesn't work on the IBM ppc version of java.  I will probably have time today to play with it again.  I'll let you know if I have any luck.

---

### Post by funkyade on 2006-03-29
I can confirm that the majority of Sun tools will not work on PPC. They support only x86 and sparc.

If you are a developer try installing eclipse as that gives you quite a lot of Java tools, although you do need a JRE or SDK installed first.

The best free java that I have found is GIJ. The IBM java is good but difficult to setup and get working and uses LOTS of memory.

I have contacted sun regarding support for PPC linux but have not yet had a response.

hth

---

