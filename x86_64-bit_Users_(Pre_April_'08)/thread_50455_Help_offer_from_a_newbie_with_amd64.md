---
title: "Help offer from a newbie with amd64"
date: 2005-07-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by eolo999 on 2005-07-20
Hi all,
I've an Amd 64 laptop (acer aspire 1524wlmi) and i would like to help people who know how to program to port 32bit apps to 64bit. The only thing i can do is to test and report bugs, but i'm ready to receive proposal...
edoardo batini

---

### Post by filterban on 2005-07-20
[QUOTE=eolo999]Hi all,
I've an Amd 64 laptop (acer aspire 1524wlmi) and i would like to help people who know how to program to port 32bit apps to 64bit. The only thing i can do is to test and report bugs, but i'm ready to receive proposal...
edoardo batini[/QUOTE]

You don't need to know how to program to make packages for 64bit.  All you need to do is know how to compile a program from source and make .debs, which is different.   

Compiling basically consists of downloading the source code and typing:

./configure
make
make install

After it's installed you then make the .deb of the installed files.

While it is a lot to learn for a "newbie", I think you'll end up learning a lot more about your computer if you gave it a shot. :)

I'm sure Tamir would like testers, though.  See the "amd64 packages" thread and the "help make amd64 better" thread.

---

