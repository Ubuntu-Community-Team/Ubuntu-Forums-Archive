---
title: "How can you tell which version is running?"
date: 2007-06-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by onering on 2007-06-27
I just moved over to Ubuntu 7.04 64 Bit, installed on an AMD 64X2.  Yeah!

Is there a command that returns which version of Ubuntu (32 or 64 bit) and Linux Kernel (32 or 64 bit) are running?

I know the following, but it only returns a kernel name, without reference to if it was compiled for 32 or 64 bits:
 ```
uname -r
```

---

### Post by uaeB on 2007-06-27
The uname has many tricks up it's sleeves. Try: uname -a

---

### Post by onering on 2007-06-27
> **uaeB said:**
> The uname has many tricks up it's sleeves. Try: uname -a

ah yes, I see, this worked thanks...
```
Linux 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux

```

---

### Post by wjp.reg on 2007-06-27
> **onering said:**
> I just moved over to Ubuntu 7.04 64 Bit, installed on an AMD 64X2.  Yeah!

Is there a command that returns which version of Ubuntu (32 or 64 bit) and Linux Kernel (32 or 64 bit) are running?

I know the following, but it only returns a kernel name, without reference to if it was compiled for 32 or 64 bits:
 ```
uname -r
```

Is the following what you are looking for:

```
uname -a
```

On my system it returns

```
 uname -a
Linux ubuntu 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
wolf@ubuntu:~$ 

```

and 

```
cat /etc/issue
```

returns

```
Ubuntu 7.04 \n \l
```

on my system (intel centrino duo 32bit)

Does that help?

---

### Post by onering on 2007-07-14
To find out which version of the Linux architecture is running you can also type:
```
arch
```
which in the case of my system returns :
```
x86_64
```

---

### Post by kah00na on 2007-10-23
Run this command.  I've provided output from my box.  Important info removed though.  :)

```
userid@hostname:~/scripts$** lsb_release -a**
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy
userid@hostname:~/
```

---

