---
title: "gutsy version"
date: 2008-01-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by oxman on 2008-01-27
I have been running dapper amd64 for since it came out. Recently I noticed that certain applications I wish to run are not being updated so I installed gutsy on another drive. 
A friend burned the iso for me and the install went fine BUT I am not sure that he actually burned the amd64 bit gutsy. 
The kernel version in grub says generic and nothing about 64bit. Is there a cli command to discover if the 64 bit version of gutsy is installed? I have already used ```
cat /etc/issue
``` and ```
/etc/lsb-release
```. They don't say I am using the 64 bit version. Where else should I look?
Any help is appreciated.

---

### Post by dcstar on 2008-01-27
> **oxman said:**
> I have been running dapper amd64 for since it came out. Recently I noticed that certain applications I wish to run are not being updated so I installed gutsy on another drive. 
A friend burned the iso for me and the install went fine BUT I am not sure that he actually burned the amd64 bit gutsy. 
The kernel version in grub says generic and nothing about 64bit. Is there a cli command to discover if the 64 bit version of gutsy is installed? I have already used ```
cat /etc/issue
``` and ```
/etc/lsb-release
```. They don't say I am using the 64 bit version. Where else should I look?
Any help is appreciated.

```
uname -a
```

---

### Post by oxman on 2008-01-27
Wow! Don't you just love it! Even have the install date recorded.   Linux and the Ubuntu community are so powerful.   Thank you very much David.

---

