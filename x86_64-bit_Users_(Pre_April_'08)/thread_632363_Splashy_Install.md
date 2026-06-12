---
title: "Splashy Install"
date: 2007-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by mcgodx on 2007-12-05
I tried to install Splashy recently, using the tar.gz file on [Their site]("http://alioth.debian.org/frs/?group_id=30657"), however when I try to install, this is what happens:

```
mylan@laptop:~/Temporary/splashy-0.3.6$ sudo ./configure --prefix=/ && make && make install
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

``` 
I am not so sure what I need to do to fix this, it doesn't seem many people get this error.  This is a relatively fresh install of Ubuntu if that helps.  I just switched over from Fedora not too long ago (again).

---

### Post by flick on 2007-12-06
Try installing the kernel-headers ( that match your kernel, uname -a will find out what kernel you're running ) and glibc-dev packages first.

Hope that helps.

Flick

---

### Post by bash on 2007-12-09
```
sudo apt-get build-dep splashy libsplashy1
```

should do the trick. After that just run the normal ./configure && make && make install/checkinstall

---

