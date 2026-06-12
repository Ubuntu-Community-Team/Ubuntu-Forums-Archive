---
title: "Which java version on Xeon 64bit"
date: 2008-11-18
forum: x86 64-bit Users
---

### Post by ziphyre on 2008-11-18
Hello,

I'm gonna install jdk6 to my ubuntu 8.10 server which runs on Xeon quadcore 64bits processor.

I do not know exactly if xeon is compatible with itanium familiy. Sun provides two package for 64bits

1)JDK 6 Update 10 for generic 64bit machines
2)JDK 6 Update 7 for Intel Itanium®

Should I go for the generic one, or Itanium?

Thanks

---

### Post by jespdj on 2008-11-18
The Itanium family is something completely different than the x86 family of processors.

What version of Ubuntu did you install, the regular amd64 (x86_64) version? As far as I know, there is no version of Ubuntu that runs on Itanium processors.

So your processor is most likely not an Itanium, and you need to use the regular x86 version of Java.

Note: Install Java from the Ubuntu repository, don't download and install it directly from Sun's website, unless you have some special reason to do so. Sun Java 6 update 10 is available in the Ubuntu 8.10 repository, install it with:
```
sudo apt-get install sun-java6-jre
```

---

### Post by ziphyre on 2008-11-18
Thank you very much about your clarification about Itanium.

I have installed the regular amd64 ubuntu server. And downloaded and extracted the 64bit jdk from Sun's site.

Can you tell me why do you suggest not to download from there, and instead, install from repository?

I like the simple unzip and run mechanism of jdk that way. My server is command line, so there is no browser plugin, or etc..

I'd like to know any specific reason behind your warning.

Thanks.

---

### Post by jespdj on 2008-11-18
> **ziphyre said:**
> Can you tell me why do you suggest not to download from there, and instead, install from repository?
You should always prefer to install software using Ubuntu's package management system, because the packages from Ubuntu's repository have been tested and are known to work (and in some cases contain small adjustments to make them work well on Ubuntu), and you will get automatic security updates for software installed from the repository.

The Ubuntu repository is the official source for Ubuntu software. You should only install software manually if you have a special reason to do so (for example, because it isn't available in the repository, or you need a specific version that's not in the repository).
> **ziphyre said:**
> I like the simple unzip and run mechanism of jdk that way. My server is command line, so there is no browser plugin, or etc..
Installing software from the repository from the command line with apt-get is not more complicated than downloading, unzipping and installing it manually. (In fact, it's easier, because you download and install it with one simple "apt-get install" command).

---

