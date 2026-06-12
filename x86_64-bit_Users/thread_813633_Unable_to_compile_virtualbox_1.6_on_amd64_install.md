---
title: "Unable to compile virtualbox 1.6 on amd64 install"
date: 2008-05-31
forum: x86 64-bit Users
---

### Post by Zelut on 2008-05-31
I've been trying to compile / package the latest version of Virtualbox (ose downloaded from virtualbox.org).  I notice that I get this error during compile, which I did not get when building on i386 installation:

> /usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libXext.a when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.so when searching for -lXext
/usr/bin/ld: skipping incompatible /usr/lib/libXext.a when searching for -lXext
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status


Anyone have any ideas how to get around this?

---

### Post by Bataille23 on 2008-05-31
It's been a few months since I got VB up and running, but I seem to remember having the same problem.  Try version 1.5.6.  I'm currently running that, and if my memory serves me correctly, I believe 1.6 was not working very well with 64-bit systems.  Sorry I couldn't give you anything resembling a definite answer, but I really don't recall having any problems with 1.5.6.

---

### Post by dinxter on 2008-06-01
it cant find the lib32 libraries which are there but named diferently, you need to softlink to resolve the problem,

"ln -s /usr/lib32/libXext.so.6 /usr/lib32/libXext.so"

and, there is one more.

" ln -s /usr/lib32/libXmu.so.6  /usr/lib32/libXmu.so"

---

### Post by harvey186 on 2008-06-01
> **Zelut said:**
> I've been trying to compile / package the latest version of Virtualbox (ose downloaded from virtualbox.org).  I notice that I get this error during compile, which I did not get when building on i386 installation:



Anyone have any ideas how to get around this?

why aren't you using the deb from SUN ?? It works perfect.

---

### Post by dinxter on 2008-06-01
1.6 introduces a few regressions, including hardware virtualisation support breakage, which is fixed in svn along with a number of other bugs.

---

