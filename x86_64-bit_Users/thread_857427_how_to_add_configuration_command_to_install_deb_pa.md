---
title: "how to add configuration command to install deb package using apt-get"
date: 2008-07-12
forum: x86 64-bit Users
---

### Post by pegasusmd on 2008-07-12
Hi all, 

I need to configure a deb package with some options(eg. -fPIC)
I can use apt-get install to install directly but dont know where to add this options. 

how can I use apt-get to configure like this? 

or are there other ways to do this and then install. 

Thanks, 

Dan

---

### Post by Cappy on 2008-07-13
Debian packages are precompiled. To add those options you need to compile the program yourself. You can get the newest source by googling your package.

If the package is already in the ubuntu repos use
```
sudo apt-get build-dep package_name
```
to get all the dependencies before compiling the source yourself.

If you want to use the source (which may be old, but probably not) from the ubuntu repos use ```
sudo apt-build source package_name
```

Compiling programs is usually as easy as ```
./configure
make
sudo make install
```

---

