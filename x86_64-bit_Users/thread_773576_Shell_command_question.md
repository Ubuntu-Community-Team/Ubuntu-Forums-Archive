---
title: "Shell command question"
date: 2008-04-29
forum: x86 64-bit Users
---

### Post by stoneage on 2008-04-29
If I "sudo ln -s libgettextlib-0.17.so libgettextlib-0.16.1.so" will it tell my system to use libgettextlib-0.17.so when it wants to use libgettextlib-0.16.1.so ?

Using Ubuntu 8.04

---

### Post by Shootfast on 2008-04-29
No, it will do the opposite.

It will use libgettextlib-0.16.1.so every time something calls libgettextlib-0.17.so

It's link THIS to THAT

---

### Post by stoneage on 2008-04-29
Really? Hell. It appears to be working.
O.K. So I have libgettextlib-0.17.so and Blender won't run because I don't have libgettextlib-0.16.1.so. Did I do the right thing? It works having used it the way I posted.

---

