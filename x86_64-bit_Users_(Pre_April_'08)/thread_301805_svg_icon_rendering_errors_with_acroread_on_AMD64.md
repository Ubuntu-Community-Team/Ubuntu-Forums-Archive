---
title: "svg icon rendering errors with acroread on AMD64"
date: 2006-11-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by redsoxred on 2006-11-17
Dear 64bit Dapper Users,

I pretty much followed Debian AMD64 FAQ to install 32-bit acroread on my AMD64 Unbuntu 6.06 from this URL
[http://wiki.debian.org/DebianAMD64Faq]("http://wiki.debian.org/DebianAMD64Faq")

Everything works as mentioned, except that when I click "File--> Open", I get the following errors:
```
(acroread:14140): Gtk-WARNING **: Error loading theme icon for stock: Unable to load image-loading module: /usr/lib32/gtk-2.0/2.4.0/loaders/svg_loader.so: /usr/lib32/gtk-2.0/2.4.0/loaders/svg_loader.so: cannot open shared object file: No such file or directory

```

The problem is pretty straight forward, there is no 32-bit svg_loader.so in the lib32 gtk-2.0 directory.

Is there a way to over come the type of svg rendering problem?  Thanks.

---

### Post by salbma on 2006-11-29
remove the lines referencing the library from /etc/gtk-2.0/gdk-pixbuf.loaders32

and it works.


good luck

---

