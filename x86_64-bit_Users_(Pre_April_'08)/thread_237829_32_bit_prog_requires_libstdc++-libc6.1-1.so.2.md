---
title: "32 bit prog requires libstdc++-libc6.1-1.so.2"
date: 2006-08-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by LazyBoy on 2006-08-16
I need to run JDK 1.3.1 from sun.  The javac is complaining about not finding libstdc++-libc6.1-1.so.2.

I tried
```
sudo ln -s libstdc++.so.6.0.7 libstdc++-libc6.1-1.so.2
```
and
```
sudo ln -s libstdc++.so.5.0.7 libstdc++-libc6.1-1.so.2
```

in /usr/lib32, as javac is a 32bit proggy.  But javac seg faults with either one, unsuprisingly.

Any suggestions?

Thanks,
LB

---

### Post by LazyBoy on 2006-08-17
FYI,

OK.  I figured out that this is a form that is not found in debian/ubuntu repositories.  Here's what I ended up doing:
```

mkdir tmp
cd tmp
wget ftp://fr2.rpmfind.net/linux/fedora/core/5/x86_64/os/Fedora/RPMS/compat-libstdc++-296-2.96-135.i386.rpm
sudo alien --to-tgz compat*rpm
tar zxf compat*tgz
cd usr/lib
cp sudo cp libstdc++-2-libc6.1-1-2.9.0.so /usr/lib32/libstdc++-libc6.1-1.so.2

```

LB

---

### Post by cpudney on 2006-08-24
G'day,

I tried a different approach that involved [installing libstdc++2.10-glibc2.2 and then symlinking to libstdc++-3-libc6.2-2-2.10.0.so]("http://ubuntu-linux-dell-inspiron-9400.blogspot.com/2006/08/sun-jdk131.html")

YMMV,
Chris.

---

### Post by mobile01 on 2007-04-06
> **LazyBoy said:**
> FYI,

OK.  I figured out that this is a form that is not found in debian/ubuntu repositories.  Here's what I ended up doing:
```

mkdir tmp
cd tmp
wget ftp://fr2.rpmfind.net/linux/fedora/core/5/x86_64/os/Fedora/RPMS/compat-libstdc++-296-2.96-135.i386.rpm
sudo alien --to-tgz compat*rpm
tar zxf compat*tgz
cd usr/lib
cp sudo cp libstdc++-2-libc6.1-1-2.9.0.so /usr/lib32/libstdc++-libc6.1-1.so.2

```

LB
I am not able to find out the command alien

sudo alien --to-tgz compat*rpm

could you please help me with that

---

### Post by oboontoo on 2007-04-10
> **mobile01 said:**
> I am not able to find out the command alien

sudo alien --to-tgz compat*rpm

could you please help me with that

You need to install alien.

```
sudo apt-get install alien
```
Make sure the universe repository is enabled.

---

### Post by JMensing on 2007-09-14
> riginally Posted by LazyBoy  View Post
FYI,

OK. I figured out that this is a form that is not found in debian/ubuntu repositories. Here's what I ended up doing:
Code:

mkdir tmp
cd tmp
wget [ftp://fr2.rpmfind.net/linux/fedora/core/5/x86_64/os/Fedora/RPMS/compat-libstdc++-296-2.96-135.i386.rpm](ftp://fr2.rpmfind.net/linux/fedora/core/5/x86_64/os/Fedora/RPMS/compat-libstdc++-296-2.96-135.i386.rpm)
sudo alien --to-tgz compat*rpm
tar zxf compat*tgz
cd usr/lib
cp sudo cp libstdc++-2-libc6.1-1-2.9.0.so /usr/lib32/libstdc++-libc6.1-1.so.2

LB


The above link for the RPM package changed to:

[ftp://fr2.rpmfind.net/linux/fedora/core/6/i386/os/Fedora/RPMS/compat-libstdc++-296-2.96-138.i386.rpm](ftp://fr2.rpmfind.net/linux/fedora/core/6/i386/os/Fedora/RPMS/compat-libstdc++-296-2.96-138.i386.rpm)

---

