---
title: "Detecting 64-bit Ubuntu"
date: 2008-05-09
forum: x86 64-bit Users
---

### Post by altonbr on 2008-05-09
How do I detect a 64-bit Ubuntu in a BASH script?

Such as:
```
ARCH=`` # detect here
if [ $ARCH == 'x86' ]; then
# x86 code here
else
# x64 code here
fi

```

---

### Post by tamoneya on 2008-05-09
for detection you should just parse through ```
uname -m
```

---

### Post by altonbr on 2008-05-09
What's the output for a 64-bit box?

My 32-bit box returns
> i686

---

### Post by tamoneya on 2008-05-09
here is what 64 bit looks like
```
tamoneya@ubuntu1:~$ uname -m
x86_64

```

---

### Post by altonbr on 2008-05-09
> **tamoneya said:**
> here is what 64 bit looks like
```
tamoneya@ubuntu1:~$ uname -m
x86_64

```

Perfect, thank you!

---

### Post by millie95 on 2008-05-09
uname -m

x86_64

---

### Post by Cappy on 2008-05-09
Here's what my detection looks like in getlibs:
```
architecture=`uname -m`
if [ "$architecture" != "x86_64" ] && [ "$architecture" != "ia64" ]; then
    architecture="x86"
else
    architecture="x86_64"
fi
```

I doubt ia64 is used often but it is one of the architectures supported by debian.

---

### Post by jespdj on 2008-05-10
Cappy, [ia64]("http://en.wikipedia.org/wiki/Itanium") is a non-x86-compatible 64-bit CPU architecture, so it's not really correct to say architecture = "x86_64" if it's really ia64.

---

### Post by Cappy on 2008-05-10
ia64 32-bit libraries goto the same place as they do in amd64. For my purposes it is the same. It's just a variable; I'm not saying they are the same architecture.

ia64 is x86 compatible. That's where the name ia32-libs came from.

---

### Post by altonbr on 2008-05-10
Thanks everyone.

If you want to see the script this was used for, check it out here: [http://ubuntuforums.org/showthread.php?p=4920233](http://ubuntuforums.org/showthread.php?p=4920233) (VMware Server for 8.04)

---

