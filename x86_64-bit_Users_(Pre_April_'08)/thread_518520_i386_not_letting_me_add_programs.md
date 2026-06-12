---
title: "i386 not letting me add programs"
date: 2007-08-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by josephh on 2007-08-06
I don't know what happened, but I was unable to logon to Ubuntu, and had to reinstall.  After doing so, I am now unable to reload all the programs I had before.  I get a message saying something about i386.

What can I do to to allow all the programs I had before?

System Information:

Computer:  Dell e1505 inspiron, 1 gb memory, 80 gig hd partitioned into three 20+ gigs, including one running Windows xp.  dual core 32 bit.

---

### Post by dfreer on 2007-08-06
What does this command in terminal return?:
```
uname -m
```
Can you get us the specific error message?

---

### Post by josephh on 2007-08-06
uname -m gives me :  i686

---

### Post by Kilz on 2007-08-06
> **josephh said:**
> uname -m gives me :  i686

You are running the 32bit version of ubuntu or i386. This section is mostly for those running the amd64 version of Ubuntu. But just in case you just need some knowlage,[ look here. ]("http://www.monkeyblog.org/ubuntu/installing/")

---

### Post by dfreer on 2007-08-06
Could the problem be that you are trying to install 64-bit programs, and you are running 32-bit ubuntu? What programs in particular are you trying to reload, and how are you doing so?

---

### Post by josephh on 2007-08-06
It won't install anything that's not on the cd

---

### Post by dfreer on 2007-08-07
aha, that's a bit different. Can you post your /etc/apt/sources.list file, it is likely you just need to add the right repositories.

---

### Post by josephh on 2007-08-07
> **dfreer said:**
> aha, that's a bit different. Can you post your /etc/apt/sources.list file, it is likely you just need to add the right repositories.

That was it.  Solved the problem and I'm up and running.

Thanx!

---

