---
title: "32 bits mysql client"
date: 2009-03-05
forum: x86 64-bit Users
---

### Post by MasterOfQuebec on 2009-03-05
Hello,
I want to compile a program as a 32 bit program under ubuntu 64. This program must be compiled with the mysql client libs.

When I try to compile the program I get these errors:
```
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/../../../libmysqlclient.so when searching for -lmysqlclient
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/../../../libmysqlclient.a when searching for -lmysqlclient
/usr/bin/ld: skipping incompatible /usr/lib/libmysqlclient.so when searching for -lmysqlclient
/usr/bin/ld: skipping incompatible /usr/lib/libmysqlclient.a when searching for -lmysqlclient
/usr/bin/ld: cannot find -lmysqlclient
```
I think I must install the 32 bit mysql libs. How may I install these librairies (I do not want to remove/remplace the x64 mysql client libs)?

Thanks in advance.

---

### Post by Cappy on 2009-03-05
Install getlibs from [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
and run
```
sudo getlibs -p libmysqlclient15-dev
```
or
```
sudo getlibs -l libmysqlclient.so
```

---

### Post by MasterOfQuebec on 2009-03-05
Thanks for your help, I do not have errors anymore.

---

