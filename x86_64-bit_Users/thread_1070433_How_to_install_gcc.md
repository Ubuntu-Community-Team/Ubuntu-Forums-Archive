---
title: "How to install gcc??"
date: 2009-02-15
forum: x86 64-bit Users
---

### Post by Electricalkhukuma on 2009-02-15
How can i install "gcc" to compile 'c' programmes??

---

### Post by uidb4056 on 2009-02-15
It should be installed by default, if you start a terminal and type gcc you should have an output like this:

robert@nox810x64:~$ gcc
gcc: no input files
robert@nox810x64:~$

That means gcc is installed.

---

### Post by binbash on 2009-02-15
sudo apt-get install build-essential

---

### Post by jespdj on 2009-02-15
Indeed, you need the package **build-essential**. Besides the compiler it installs the standard C library header files and some other stuff that you need to compile C and C++ programs.

---

