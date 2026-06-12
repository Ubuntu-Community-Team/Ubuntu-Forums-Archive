---
title: "Java 1.5 ppc"
date: 2005-12-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by ccars on 2005-12-28
Have followed the instructions from JavaPPC web site.
Downloaded correct version to desktop, then opened terminal and entered the following and received this:
 tar -zxf ibm-java2-sdk-50-linux-ppc.tgz
tar: ibm-java2-sdk-50-linux-ppc.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Have tried this over several weeks and each time frustration level increases.
Any help will be appreciated.
Al

---

### Post by Brian McConnell on 2005-12-28
[QUOTE=ccars]Have followed the instructions from JavaPPC web site.
Downloaded correct version to desktop, then opened terminal and entered the following and received this:
 tar -zxf ibm-java2-sdk-50-linux-ppc.tgz
tar: ibm-java2-sdk-50-linux-ppc.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Have tried this over several weeks and each time frustration level increases.
Any help will be appreciated.
Al[/QUOTE]
You probably ought to:
```
cd /home/YOURUSERNAME/desktop
```

see if that gets you going :lol:

---

### Post by ccars on 2005-12-28
Brian 
thanks for quick response.
Opened terminal and typed:
al@ubuntu:~$ cd /home/al/desktop
bash: cd: /home/al/desktop: No such file or directory

here is what I got
Al

---

### Post by trash on 2005-12-28
upper and lower case letters are not the same in linux..

cd /home/al/Desktop

---

