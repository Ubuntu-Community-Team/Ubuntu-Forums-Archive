---
title: "loading opensc module with 32bit firefox on 64bit ubuntu"
date: 2007-12-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by kristian64 on 2007-12-20
I wish to use my SCR3310 smartcard reader with firefox on my 64 bit Ubuntu(7.04). I haven't gotten java to work well with 64 bit Firefox, so I installed 32 bit one instead and java works great with it, but when trying to load opensc security module (/usr/lib/opensc-pkcs11.so) Firefox gives me an error message claiming that the module was not found. Trying the same thing with 64 bit Firefox worked.

Opensc by itself does work and recognizes the reader, when using opensc-tool --list-readers for example.

Does anybody know what could be the problem? I am quite new to linux and very new to 32/64 bit architecture problems.

---

### Post by Cappy on 2007-12-20
Install getlibs from here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

and try
```
sudo getlibs -32 opensc-pkcs11.so
```

32-bit programs need the 32-bit version of the libraries they require

---

### Post by kristian64 on 2007-12-21
I tried that before and now again and unless the libaries are copied somewhere else than /usr/lib32 or /usr/lib, which I both tried, it didn't work.

---

### Post by Cappy on 2007-12-21
```
ls -la /usr/lib32/opensc*
```
should return 
```
-rw-r--r-- 1 root root  1005 2007-12-21 11:26 /usr/lib32/opensc-pkcs11.la
-rw-r--r-- 1 root root 83120 2007-12-21 11:26 /usr/lib32/opensc-pkcs11.so

/usr/lib32/opensc:
total 32
drwxr-xr-x  2 root root  4096 2007-12-21 11:26 .
drwxr-xr-x 36 root root 28672 2007-12-21 11:26 ..
lrwxrwxrwx  1 root root    19 2007-12-21 11:26 opensc-pkcs11.so -> ../opensc-pkcs11.so
```

but those libraries are not there on your computer?

If they aren't can you run ```
sudo sh -x /usr/bin/getlibs -32 opensc-pkcs11.so
```
and post the output in the CODE tags please =)

---

### Post by kristian64 on 2007-12-21
```
s -la /usr/lib32/opensc*
```

```

-rw-r--r-- 1 root root  1005 2007-12-21 12:51 /usr/lib32/opensc-pkcs11.la
-rw-r--r-- 1 root root 78704 2007-12-21 12:51 /usr/lib32/opensc-pkcs11.so

/usr/lib32/opensc:
total 16
drwxr-xr-x  2 root root  4096 2007-12-21 12:51 .
drwxr-xr-x 21 root root 12288 2007-12-21 12:51 ..
lrwxrwxrwx  1 root root    19 2007-12-21 12:51 opensc-pkcs11.so -> ../opensc-pkcs11.so

```

Trying to load those still results in an error however.

Tried removing those files and then using getlibs to get them back:

```
sudo sh -x getlibs -32 opensc-pkcs11.so
```
resulted in:
```
sh: Can't open getlibs
```
and
```
sudo getlibs -32 opensc-pkcs11.so
```
resulted in:
```

Matched library opensc-pkcs11.so to /feisty/libs/libopensc2
The following i386 libraries will be installed:
/feisty/libs/libopensc2
Continue? (y/n) y
Downloading. Installing libraries ...
ldconfig: /usr/lib32/libdrm.so.1 is not a symbolic link
```

Files are now back, but loading them still results in an error.

---

### Post by Cappy on 2007-12-21
Okay, it isn't a problem with getlibs then, it's firefox. Normally a program will search for the correct library but firefox seems to have the path stored instead.

I don't know much about this but it seems that the file 
```
~/.mozilla/firefox/pluginreg.dat
```
may have a line where "/usr/lib/opensc-pkcs11.so" needs to be changed to "/usr/lib32/opensc-pkcs11.so".

You could link usr/lib/opensc-pkcs11.so to usr/lib32/opensc-pkcs11.so but that would break 64-bit opensc-tool. You could uninstall the 64-bit opensc-tool and install the 32-bit opensc-tool but then it probably wouldn't work with any 64-bit program.

Someone who knows more about firefox and firefox plugins will be able to help you more.

---

