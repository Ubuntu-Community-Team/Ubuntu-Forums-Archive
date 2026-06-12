---
title: "Couldn't find Xaw library"
date: 2008-10-18
forum: x86 64-bit Users
---

### Post by rehin on 2008-10-18
There is a similar post but there is no solution in it. When I try to configure ngspice rework 17 package, I get the following problem:
```

checking for main in -lXaw... no
configure: error: Couldn't find Xaw library
```

However when I look for libXaw, it exists and already installed:
```

> sudo ldconfig -v | grep libXaw
        libXaw3d.so.8 -> libXaw3d.so.8.0
	libXaw8.so.8 -> libXaw8.so.8.0.0
	libXaw3d.so.6 -> libXaw3d.so.6.1
	libXaw7.so.7 -> libXaw7.so.7.0.0
	libXaw6.so.6 -> libXaw6.so.6.0.1
	libXaw8.so.8 -> libXaw8.so.8.0.0
	libXaw7.so.7 -> libXaw7.so.7.0.0
	libXaw6.so.6 -> libXaw6.so.6.0.1
```

What should I do? It is very important and vital for my research. So please help. :( (By the way I use opensuse 11)

---

### Post by Yellow Pasque on 2008-10-18
You have the shared libraries, but you probably need the X development package (i.e. the '.h' files)

Look for a package whose name begins with xorg-x11-devel in your package managment system.

---

### Post by turbodog on 2008-12-16
> **rehin said:**
> There is a similar post but there is no solution in it. When I try to configure ngspice rework 17 package, I get the following problem:
```

checking for main in -lXaw... no
configure: error: Couldn't find Xaw library
```

However when I look for libXaw, it exists and already installed:
```

> sudo ldconfig -v | grep libXaw
        libXaw3d.so.8 -> libXaw3d.so.8.0
	libXaw8.so.8 -> libXaw8.so.8.0.0
	libXaw3d.so.6 -> libXaw3d.so.6.1
	libXaw7.so.7 -> libXaw7.so.7.0.0
	libXaw6.so.6 -> libXaw6.so.6.0.1
	libXaw8.so.8 -> libXaw8.so.8.0.0
	libXaw7.so.7 -> libXaw7.so.7.0.0
	libXaw6.so.6 -> libXaw6.so.6.0.1
```

What should I do? It is very important and vital for my research. So please help. :( (By the way I use opensuse 11)


I am using 8.10 and was able to fix this by installing libxaw7-dev

---

### Post by physeetcosmo on 2009-01-22
> **turbodog said:**
> I am using 8.10 and was able to fix this by installing libxaw7-dev

Great! This works for those of you installing ngspice. The package names aren't always straight forward, at least for a newbie such as myself ;)

---

