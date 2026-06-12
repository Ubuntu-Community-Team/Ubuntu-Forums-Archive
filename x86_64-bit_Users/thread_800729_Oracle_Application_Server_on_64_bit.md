---
title: "Oracle Application Server on 64 bit?"
date: 2008-05-20
forum: x86 64-bit Users
---

### Post by janpla on 2008-05-20
I am trying to install oap - any version - on my AMD64 with the latest Ubuntu. I have some sort of 32 bit environment - I can start the install under linux32, but when I reach the linking stage it fails because it can't find the necessary tools - most recently libgcc 32 bit. I know this work on 64 bit Redhat, so of course it can be made to work on Ubuntu as well - is there a simple way to get "all the 32 bit development tools", loosely speaking?

---

### Post by Cappy on 2008-05-20
There is lib32gcc1 for that
```
sudo apt-get install lib32gcc1
```

which will also pull in libc6-i386.

You may need to also install lib32nss-mdns so that the app can access the internet
```
sudo apt-get install lib32nss-mdns
```

---

### Post by janpla on 2008-05-20
Unfortunately this doesn't work - here is the error message:

/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libgcc.a when searching for -lgcc

---

### Post by Cappy on 2008-05-20
Ah, you want the multi-lib package.

```
sudo apt-get install gcc-4.1-multilib gcc-4.1
```

There's also a gcc 4.2 version if that doesn't work out
```
sudo apt-get install gcc-4.2-multilib gcc-4.2
```

[http://packages.ubuntu.com](http://packages.ubuntu.com) is useful for finding what packages contain a file.

---

### Post by janpla on 2008-05-21
Thanks for taking the time!

This has brought me a bit further - now it can't find 'libc_nonshared.a':

/usr/bin/ld: skipping incompatible /usr/lib/libc_nonshared.a when searching for /usr/lib/libc_nonshared.a

- but I can see that it is in /usr/lib32; I just have to figure out how to tell the Oracle installer.

---

### Post by Cappy on 2008-05-21
The problem seems to be that the path to that library is hardcoded.

The easiest thing to do is just to move /usr/lib/libc_nonshared.a and
```
sudo ln -s /usr/lib32/libc_nonshared.a /usr/lib/libc_nonshared.a
```
temporarily (at least).

If that doesn't work there are other ways but could interfere with md5 checks if it checks for consistency.

If that's the case or you have lots of these problems then you may want to look into using a chroot.

---

### Post by janpla on 2008-05-28
Well, yes, but I would prefer to 'do it properly' - not that what you suggest isn't 'proper', but I would have preferred to leave everything where it is and set up some environment variables or parameters somewhere. Sigh. I'll keep digging, I'm bound to find a way in the end.

---

