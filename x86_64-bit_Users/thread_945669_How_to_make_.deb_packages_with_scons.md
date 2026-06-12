---
title: "How to make .deb packages with scons"
date: 2008-10-12
forum: x86 64-bit Users
---

### Post by Nysomin on 2008-10-12
Does anyone know who to make a .deb package with SCons?

---

### Post by cariboo on 2008-10-12
I'm not sure about SCons, but all the  tools are already available in the repositories. If you haven't installed checkinstall, it is availabe in the repositories. to use it, use ,/configure as you normally would, then instead of running make, run checkinstall. If configure ran without any errors you should be on your way to creating a .deb

Jim

---

### Post by Nysomin on 2008-10-13
yeah, checkinstall is how I normally do it, but I'm trying to do Blender, and it's setup to use SCons already

---

