---
title: "installing libs"
date: 2008-08-31
forum: x86 64-bit Users
---

### Post by ianellis on 2008-08-31
I am trying to install a server for a game but it keeps saying I need libmysqlclient.so.15

How do I install this so that I can get this working?

---

### Post by skunkTrader on 2008-08-31
Try installing libmysqlclient15off using apt

---

### Post by ianellis on 2008-08-31
ok I just did and I got this.

> ./spheresvr: error while loading shared libraries: libmysqlclient.so.15: cannot open shared object file: No such file or directory


---

### Post by Oldsoldier2003 on 2008-08-31
It would help if you told us what gameserver you are trying to install. Someone may have worked out this problem before and be able to provide help.

---

### Post by ianellis on 2008-08-31
I'm trying to install a server for Ultima Online, the name of the emu is SphereServer

---

### Post by Kilz on 2008-08-31
> **ianellis said:**
> I'm trying to install a server for Ultima Online, the name of the emu is SphereServer

Where did you get it? If it isnt from the repositories, and it doesnt specifically say its 64bit, its probably 32bit. If its 32bit, its looking for a 32bit library. [You can use Getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs") to install 32bit libraries, never ever ever force install libraries.
If it is 64bit, install  libmysqlclient15off

---

### Post by ianellis on 2008-08-31
ok thanks,

I'm trying something different, I installed Ubuntu server on another computer, all I have to do is figure out how to get the files from this computer to that one. Any ideas while I'm on the subject?

---

### Post by jpkotta on 2008-08-31
> **ianellis said:**
> ok thanks,

I'm trying something different, I installed Ubuntu server on another computer, all I have to do is figure out how to get the files from this computer to that one. Any ideas while I'm on the subject?

The two easiest methods are a flash drive (if you have one that is big enough) or ssh (if you have a network).  

If you use a flash drive, you should make a tarball of the files and put that on the drive, because that will preserve permissions and such.

If you use ssh:
```
scp -r /source/path/ user@remote:/destination/path/
```

---

