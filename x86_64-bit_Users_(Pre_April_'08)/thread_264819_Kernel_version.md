---
title: "Kernel version"
date: 2006-09-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by bogey on 2006-09-25
I thought that I had downloaded the 32 bit version of Ubuntu 6.06, but after installation I noticed that this kernel was installed.  

/boot/vmlinuz-2.6.15-27-amd64-generic

I assume that this is the 64 bit kernel, is that correct (I do have a AMD64 bit system)?  Silly question, but just want to make sure before I go about configuring my system.
Thx

---

### Post by JAwuku on 2006-09-25
To get the name of the kernel running on your system, type this command:

```
uname -r
```

and it will give you the current version.

---

### Post by Sarisar on 2006-09-25
uname -r
That command should tell you.  Mine says '2.6.15-27-386' for example for the 386 verion.  It should say something like '2.6.15-27-amd64-generic' on the 64 bit version :)

---

### Post by bogey on 2006-09-25
Thanks, I will check when I get back home. Sounds like I have the 64 bit version.

---

### Post by jdong on 2006-09-25
From that kernel name, it appears like you've installed the 64-bit edition.

---

