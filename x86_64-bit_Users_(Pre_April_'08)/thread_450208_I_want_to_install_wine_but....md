---
title: "I want to install wine but..."
date: 2007-05-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by madhu542 on 2007-05-21
hai, I want to install some windows utils so,I tried to install wine in ubuntu dapper drake, but it is not installing...could u please help me...

thanks...

---

### Post by renzokuken on 2007-05-21
how are you trying to install wine?

which windows appa are you looking to install?

---

### Post by madhu542 on 2007-05-21
hai,

     I want to install the applications like internet explorer, windows media player etc, in ubuntu dapper for that  i tried to install wine first but it is not installing and giving this error when i tried...

root@madhu-desktop:/home/madhu/shell_script# sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

---

### Post by abrar-ahmed on 2007-05-21
do a
sudo gedit  /etc/apt/sources.list

find the backports universe repository and enable it

then do a
sudo  apt-get update 

that should do it.

---

### Post by Kilz on 2007-05-21
Wine is not available For Dapper in the AMD64 bit version with apt.  I just double checked as I use Dapper. It just became available with Feisty for AMD64.
You can find a few 64bit debs on the forum, but they are mostly compiles from other users. You can also install the version from the wine website with the install script linked in my signature.

---

