---
title: "wine 0.9.41 on new 7.04 x64 install segfault!"
date: 2007-07-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by lebel on 2007-07-31
Hello,

I just installed Ubuntu 7.04 (x64 version) on my XPS 710 Dell (QuadCore QX6700 with 4GB of RAM with an nVidia 8800GTX, I know, you all hate me now :)) and I installed according to the docs Wine 0.9.41 on it.  Followed the simple instructions and now, wine just segfaults when I just try to launch it.

lebel@eowyn:~$ winecfg
wine: creating configuration directory '/home/lebel/.wine'...
Segmentation fault (core dumped)
wine: wineprefixcreate failed while creating '/home/lebel/.wine'.

It just segfaults.  Any reasons why it might do that?

---

### Post by stmiller on 2007-07-31
The Wine team provides an apt-get repo for debs. Try their updated packages:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

