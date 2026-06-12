---
title: "cannot mount .bin"
date: 2008-07-08
forum: x86 64-bit Users
---

### Post by obsrv on 2008-07-08
I'm trying to mount .bin image, bet I get his error:

```
root@ubuntu:/home/adomas# mount Documents/Age_Of_Empires_III/rld-aoea.bin -o loop /mnt/ -t fuse
/bin/sh: /dev/loop2: Permission denied

```

---

### Post by Cappy on 2008-07-08
Install gmountiso - it makes it easy.

Anyway, it's complaining because you need sudo. It would also be good to use a new folder, such as /media/iso or /media/image or something.

---

### Post by obsrv on 2008-07-08
Is there such thing as kmountiso? because I use KDE

---

### Post by obsrv on 2008-07-08
I get this error :(
[IMG]http://img67.imageshack.us/img67/3084/erroroccuredpj2.png[/IMG]

---

### Post by Kilz on 2008-07-08
> **Cappy said:**
> Install gmountiso - it makes it easy.

Anyway, it's complaining because you need sudo. It would also be good to use a new folder, such as /media/iso or /media/image or something.

I dont think so Cappy, he's running as root ( A Very BAD idea by the way). I am not sure how one would mount a .bin file. The question I would like to ask, is where did the orignal poster get the rld-aoea.bin from?

---

