---
title: "Which kernel ?"
date: 2009-10-26
forum: x86 64-bit Users
---

### Post by Tex-Twil on 2009-10-26
Hello,
I'm currently running the **2.6.24-19-generic** kernel. I would like to run on a 64bit kernel because I need to run a vmware of a 64bit OS. I have this CPU:

```

model name      : Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz

```

If I'm not not wrong, this cpu is 64bits so I could run my OS in 64bits right ? Which kernel do I have to install ? Or do I have to set some boot options ? The description of my current installed kernel says
> 
This package contains the Linux kernel image for version 2.6.24 on
x86/x86_64.

So it looks like it is also for 64.

Thanks for your help,
Tex

---

### Post by amauk on 2009-10-26
can you post the output of
```
uname -a
```

---

### Post by Tex-Twil on 2009-10-26
sure 
```

uname -a
Linux myhostname 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux


```

---

### Post by tymek666 on 2009-10-26
You can't just change kernel, you need to fresh install of AMD64 version of desired disto.

---

### Post by Tex-Twil on 2009-10-26
> **tymek666 said:**
> You can't just change kernel, you need to fresh install of AMD64 version of desired disto.
really ? why not ?

---

### Post by tymek666 on 2009-10-26
Because 64-bit kernel need also 64-bit libraries etc. It's like upgrading car engine. You usually can't change engine without changing electrical wires, gearbox, software etc..

---

### Post by Tex-Twil on 2009-10-26
> **tymek666 said:**
> Because 64-bit kernel need also 64-bit libraries etc. It's like upgrading car engine. You usually can't change engine without changing electrical wires, gearbox, software etc..

Isn't it possible just to install all the libraries instead of reinstalling the entire OS ?


I have another Debian server which was running a 32bit kernel, I just installed the "amd64" kernel, rebooted and it's booting on the 64 kernel so I thought I can do the same on Ubuntu.

---

### Post by Slim Odds on 2009-10-26
> **Tex-Twil said:**
> Isn't it possible just to install all the libraries instead of reinstalling the entire OS ?

Almost anything is "possible". There is just no reason for the Ubuntu devs to waste time on 32->64 "upgrades".

> I have another Debian server which was running a 32bit kernel, I just installed the "amd64" kernel, rebooted and it's booting on the 64 kernel so I thought I can do the same on Ubuntu.

I find that highly doubtful.

---

### Post by Tex-Twil on 2009-10-27
> **Slim Odds said:**
> 
I find that highly doubtful.
ok :) 

Thanks for the information.

T.

---

### Post by epek on 2009-11-08
Installing just the amd64-kernel or even the compatibility libraries will never ever make the system a real 64-bit system. The other fellows are right.
If you don´t believe this, try to install adobe reader or opera's 64 bit binaries. You'll get it then, I am sure :-)

---

