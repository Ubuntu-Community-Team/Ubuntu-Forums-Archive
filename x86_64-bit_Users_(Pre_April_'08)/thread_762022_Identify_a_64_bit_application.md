---
title: "Identify a 64 bit application?"
date: 2008-04-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by photopath on 2008-04-21
Is there a quick and easy way to tell if an application is running as 64bit or if it's a "ported" 32 bit application?

(if there's not a quick and easy way - is there a roundabout and difficult way???)  :)

If, for instance, I had a 32 bit app running on Ubuntu 64 - how much memory could the application access?

---

### Post by Cappy on 2008-04-21
> **photopath said:**
> 
If, for instance, I had a 32 bit app running on Ubuntu 64 - how much memory could the application access?

4gb, same as on 32-bit ubuntu

You can see if a program is 32-bit or 64-bit using "file"
> 
file /usr/bin/wine
/usr/bin/wine: ELF **32-bit** LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped


> 
file /usr/bin/gcalctool 
/usr/bin/gcalctool: ELF **64-bit** LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped


---

### Post by photopath on 2008-04-22
Thanks Cappy

:)

---

