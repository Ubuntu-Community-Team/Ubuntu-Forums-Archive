---
title: "How do I know it is 64 bit"
date: 2007-06-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by j_dog on 2007-06-23
Once you install the 64 bit version. Does it state it somewhere ?

---

### Post by Cappy on 2007-06-23
```
arch
```

---

### Post by j_dog on 2007-06-23
I'm sorry.       You lost me .  What is Arch and what do I do with it ?

---

### Post by Cappy on 2007-06-23
Goto Applications-->Accessories-->Terminal and type (or copy and paste)
```
arch
```
If you are running 64-bit it will echo back "x86_64", otherwise it will echo back something else

---

### Post by Enverex on 2007-06-23
Type it in a terminal.

---

### Post by j_dog on 2007-06-23
Oh !    I see !  it says i686 . Would that be 64 bit.   ?

Thanks !

---

### Post by Cappy on 2007-06-23
You're running 32-bit.

---

### Post by fakie_flip on 2007-06-25
Here's a few commands to show you that you are using 64 bit software.

uname -a

sudo find / -name '*.deb' -exec bash -c "dpkg -I {} | grep 'Package\|Architecture'" \;

file $(which firefox)

---

### Post by mandar-seo on 2007-06-25
Thanks but is there any PDF available or any program which will have all such commands recorded at one place.

With regards,
Mandar Thosar

---

### Post by fakie_flip on 2007-06-26
PDF, yeah linux books from torrent websites, but im not telling to get those. Google has plenty too. Here's one link.

[http://en.wikipedia.org/wiki/List_of_Unix_programs](http://en.wikipedia.org/wiki/List_of_Unix_programs)

---

