---
title: "how to run 32bit jackd? (or: why can't I force install this .deb)"
date: 2008-05-16
forum: x86 64-bit Users
---

### Post by Dr.Ninethousand on 2008-05-16
I have 64bit Ubuntu installed, and it encodes video about 12x as fast, so I'm keeping it.  However, I need to run jackd in 32 bit, for another app (Renoise) that depends on it.

I tried getting the .deb for i386, but get this error:


rick@Kutulu:~/Packages$ sudo dpkg -i –force-architecture jackd_0.103.0-6ubuntu1_i386.deb
dpkg: error processing –force-architecture (--install):
 cannot access archive: No such file or directory
dpkg: error processing jackd_0.103.0-6ubuntu1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 –force-architecture
 jackd_0.103.0-6ubuntu1_i386.deb



would appreciate some help...

---

### Post by Sef on 2008-06-03
Check out [Cappy's Tutorial]("http://ubuntuforums.org/showthread.php?t=474790").  You need to install getlibs.  You can't just install 32-bits on a 64-bits.

---

### Post by Dr.Ninethousand on 2008-06-04
yes I have getlibs, but maybe I don't know how to use it correctly for this?.

---

### Post by Cappy on 2008-06-04
My suggestions:
```
sudo apt-get install jackd
```

```
sudo getlibs /usr/local/bin/renoise
```

```
sudo getlibs -p libjack0
```

If none of those solve the problem then post the specific error message you are getting please.

---

