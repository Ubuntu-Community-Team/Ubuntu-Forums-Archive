---
title: "C++ Graphic Library Wanted"
date: 2008-08-28
forum: x86 64-bit Users
---

### Post by elmoosecapitan on 2008-08-28
I am looking for a c++ library, other than root ([http://root.cern.ch](http://root.cern.ch)), that will output basic geometric shapes. I want to be able to make a rectangle that is filled with a color of my choice. Any suggestions?


cheers

---

### Post by Sockerdrickan on 2008-08-28
SDL or perhaps OpenGL

---

### Post by jespdj on 2008-08-29
Have a look at the [Cairo](http://www.cairographics.org/) graphics library, which is used by a lot of programs on Ubuntu. The C++ interface to this library is called [cairomm](http://www.cairographics.org/documentation/cairomm/reference/).

OpenGL is mainly meant for 3D graphics and is very low-level (and doesn't have a native, object oriented C++ interface).

---

