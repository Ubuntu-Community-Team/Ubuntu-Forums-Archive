---
title: "32bit libraries"
date: 2007-07-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Sockerdrickan on 2007-07-10
Hi

./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory


Where do I get the 32bit package?

---

### Post by Cappy on 2007-07-10
I would say getlibs:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
;)

Once installed:
```

getlibs -32 libgtkglext-x11-1.0.so.0

```
or you can point it to whereever pSX is insalled to
```

getlibs pSX

```
(If you know where it is)

---

### Post by Sockerdrickan on 2007-07-10
getlibs -32 =INSTANT win ;)

---

### Post by Sockerdrickan on 2007-07-11
Oh dang, zsnes won't do it!

robin@PC:~$ cd Emulatorer/SNES && getlibs -32 zsnes
No match found for 32-bit zsnes

I need libslang !

---

### Post by Cappy on 2007-07-11
Usage: getlibs /path/to/binary
Usage: getlibs -64 amd64librarytoinstall.so
Usage: getlibs -32 i386librarytoinstall.so

```

getlibs Emulatorer/SNES/zsnes
```
if that's the right path

---

### Post by Sockerdrickan on 2007-07-11
Usage: getlibs -64 amd64librarytoinstall.so

So I can use my 64 bit .so's? :D

Only libslang left

---

### Post by Cappy on 2007-07-11
Yes.
All this and more is documented on the getlibs page:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by Sockerdrickan on 2007-07-11
robin@PC:~/Emulatorer/SNES$ ./zsnes
./zsnes: error while loading shared libraries: libslang.so.2: cannot open shared object file: No such file or directory
robin@PC:~/Emulatorer/SNES$ getlibs -64 libslang.so.2
No match found for libslang.so.2

? :S

---

### Post by Cappy on 2007-07-11
Ah I know why, that library is in /lib and not /usr/lib
It's a 64-bit so you can just
```
sudo apt-get install libslang2
```
I've encountered this problem before, I'll fix it soon.

---

### Post by Sockerdrickan on 2007-07-11
Already got it man :S Doesn't help starting zSnes... :(

---

### Post by Cappy on 2007-07-11
So you do need a 32-bit one.

I HATE doing this manually:
```

wget http://mirrors.kernel.org/ubuntu/pool/main/s/slang2/libslang2_2.0.6-4build1_i386.deb
dpkg -x libslang2_2.0.6-4build1_i386.deb libslang
sudo mv -R libslang/lib/* /lib32

```

Edit:
Fixed this in getlibs, new release isn't done yet though

---

### Post by Sockerdrickan on 2007-07-12
Thanks and thanks. Yes this is more complicated than getlibs, really! ;)

---

### Post by Cappy on 2007-07-12
just wow..

---

### Post by Sockerdrickan on 2007-07-12
Wow what?

---

