---
title: "GTKRadiant 64bit"
date: 2008-06-19
forum: x86 64-bit Users
---

### Post by obsrv on 2008-06-19
Hello,
How do I install GTKRadiant in KUbuntu 8.04 KDE4 x64?

---

### Post by obsrv on 2008-06-20
Nobody uses it on x64 Ubuntu? :O

---

### Post by obsrv on 2008-07-05
Please answer :/

---

### Post by obsrv on 2008-09-23
150 view and on reply :(:confused::confused::confused:

---

### Post by obsrv on 2008-12-23
BUMP!

Once again I'm back to Ubuntu (from ArchLinux) and now I want to edit Quake 4 maps, How DO I get GTKRadiant work on Ubuntu 9.04A2 64bit enviroment?

---

### Post by obsrv on 2008-12-24
Anyone? :confused:

---

### Post by obsrv on 2008-12-25
BUMP :) Nobody is interested in Map Creation under Linux platform?

---

### Post by crazyfuturamanoob on 2009-01-11
BUMP! I want GtkRadiant too in my Ubuntu 8.10 amd64.

I downloaded, and compiled it, but when I try to run it, I get the Radiant loading logo and then an error pop-up:
> 
radiant/error.cpp:132
runtime error: Didn't find any valid game file descriptions, aborting

errno: No such file or directory
An unrecoverable error has occurred.

----------------
./GtkRadiant/install/radian.x86 [0x5aafc2]
./GtkRadiant/install/radian.x86 [0x5175d9]
./GtkRadiant/install/radian.x86 [0x50441b]
./GtkRadiant/install/radian.x86 [0x57f5f0]
./GtkRadiant/install/radian.x86 [0x516b68]
/lib/libc.so.6(__lib_start_main+0xe6)[0x7f004c0d5466]
./GtkRadiant/install/radian.x86 [0x454969]
----------------

Break into the debugger?

[YES]  [NO]


I got Quake4 and Urban Terror 4.1. Maybe I need to specify a patch to them or something?

Did it even compile correctly?

---

### Post by Slayer93 on 2009-01-17
This is most likely a compile error. I myself use 32 bit linux, but for my Radiant, I found a great instruction manual on how to compile and run GtkRadiant on Ubuntu. Check it out on the Urban Terror forums or follow this link: [http://forums.urbanterror.net/index.php/topic,13504.0.html](http://forums.urbanterror.net/index.php/topic,13504.0.html)

I'm not sure if this will help, but its the best I can do for you.

---

### Post by obsrv on 2009-01-18
I have seen this web page you wrote, but it didn't help.

---

### Post by tpf80 on 2009-01-18
I am interested in map editing and I have X64 ubuntu as well. I will let you know if I get radiant working on my system.

---

### Post by tpf80 on 2009-01-18
well i followed the instructions on the urban terror forums, and got it to compile fine, now I just need to figure out how to make it work with Alien Arena. Perhaps you are missing a dependency?

---

### Post by maxol on 2009-01-18
[http://forums.urbanterror.net/index.php/topic,13504.0.html](http://forums.urbanterror.net/index.php/topic,13504.0.html)

Worked for me :)

---

### Post by tpf80 on 2009-01-18
I got it to compile fine, but now when I open it, it's asking me for a "project file". I am not sure what it is asking for exactly.

---

### Post by obsrv on 2009-01-18
Can anyone please make debs? :)

---

### Post by Allochtoon on 2009-01-31
if u tell me how, i can make debs from my laptop install

---

### Post by obsrv on 2009-02-08
> **Allochtoon said:**
> if u tell me how, i can make debs from my laptop install

Follow this link:

[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

---

### Post by Allochtoon on 2009-02-09
> **obsrv said:**
> Follow this link:

[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)


```
marco@lenovo:~/GtkRadiant/GtkRadiant$ dpkg-buildpackage -rfakeroot
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value:
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
tail: cannot open `debian/changelog' for reading: No such file or directory
dpkg-buildpackage: failure: tail of debian/changelog gave error exit status 1

```
can i just touch that file or?

---

### Post by obsrv on 2009-02-15
> **Allochtoon said:**
> ```
marco@lenovo:~/GtkRadiant/GtkRadiant$ dpkg-buildpackage -rfakeroot
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value:
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
tail: cannot open `debian/changelog' for reading: No such file or directory
dpkg-buildpackage: failure: tail of debian/changelog gave error exit status 1

```can i just touch that file or?

I think yes :) just touch it. No vital information for dpkg is in that file :)

---

