---
title: "32/64 lib confusion"
date: 2008-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Goliath! on 2008-01-01
I'm trying to run an application called xmind.  I get the following messages:
```
j@xan:~$ ./xmind 
Gtk-Message: Failed to load module "gail": libart_lgpl_2.so.2: cannot open shared object file: No such file or directory

** ERROR **: file accessible.c: line 550 (spi_accessible_construct): assertion failed: (o)
aborting...
Aborted (core dumped)
```

I am running 64-bit 7.04 on AMD64.  I've had this exact same problem with other applications (Acroreader for one) and I never got it resolved.

That so is in /usr/lib:
```
j@xan:/usr/lib$ ls -l | grep libart_
lrwxrwxrwx  1 root root       23 Jul  5 14:53 libart_lgpl_2.so.2 -> libart_lgpl_2.so.2.3.17
-rwxrwxrwx  1 root root    93208 Jan 27  2005 libart_lgpl_2.so.2.3.17
```

I've done a lot of searching on this and can't find an answer.  I've tried a lot of things to resolve it.  Most recently I tried reinstalling ia32-libs-gtk.  No joy.

Any ideas would be very much appreciated.

Thanks!

---

### Post by Cappy on 2008-01-01
Install getlibs from here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
and run ```
getlibs -32 libart_lgpl_2.so.2
```

---

### Post by Goliath! on 2008-01-01
Really wonderful script Cappy.  Thanks!

That seems to have solved my first problem.  Now I've got an application error, so now I'm back to xmind.org :(

Thanks!

---

