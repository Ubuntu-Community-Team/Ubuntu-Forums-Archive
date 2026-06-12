---
title: "[SOLVED] Does Synaptic Package Manager Automatically install 64-bit versions of softw"
date: 2008-04-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by boyofford on 2008-04-13
Hi, new to linux, and even newer to 64-bit (ubuntu studio)

Does Synaptic Package Manager Automatically install 64-bit versions of software?
Don't want to install 32bit versions of software when 64bit versions are available.:confused:

---

### Post by artfwo on 2008-04-13
Sure! If you installed 64-bit version of Ubuntu Studio, then all the software you pick from the repositories is also built for amd64.

---

### Post by kwaanens on 2008-04-13
Small correction:
Some packages, like wine and flashplugin-nonfree does not exist in 64 bit, so they are installed with a 32 bit wrapper. You will not be able to tell the differece from a user perspective -- and there is no alternative if you want flash over gnash (which is not good enough for everyday use so far) and wine.
Preferred Java runtime is icedtea, and that is 64 bit native, I think.

I think that you will be told that the architecture is wrong if you try to install standard 32 bit packages with Synaptic.

---

### Post by felker2 on 2008-04-13
> **boyofford said:**
> Hi, new to linux, and even newer to 64-bit (ubuntu studio)


you're welcome! ;-)

> **boyofford said:**
> 
Does Synaptic Package Manager Automatically install 64-bit versions of software?

Yes, it does.

> **boyofford said:**
> 
Don't want to install 32bit versions of software when 64bit versions are available.:confused:

Iif you want to check that an installed executable is really 64-bit, you can check that with the 'file' command:

```
sander@ubuntu804:~$ which perl
/usr/bin/perl
sander@ubuntu804:~$ file /usr/bin/perl
/usr/bin/perl: ELF **64-bit LSB executable, x86-64**, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped
sander@ubuntu804:~$

```

or, in one step:

```
sander@ubuntu804:~$ file `which perl`
/usr/bin/perl: ELF **64-bit LSB executable, x86-64**, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped
sander@ubuntu804:~$
```


HTH

---

### Post by boyofford on 2008-04-13
Thanks all for clearing that up:)!

---

