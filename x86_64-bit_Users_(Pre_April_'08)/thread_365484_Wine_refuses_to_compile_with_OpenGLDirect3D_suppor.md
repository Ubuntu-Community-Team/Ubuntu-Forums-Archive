---
title: "Wine refuses to compile with OpenGL/Direct3D support"
date: 2007-02-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by MysticAurora on 2007-02-19
Hi. I'm attempting to compile wine 0.9.31 so I can play Diablo II: Lord of Destruction with some of my friends. I followed the 64-bit user guide at [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit) , but at the very end of configuration, it spits the following error at me:

```
configure: WARNING: Wine will be build without OpenGL or Direct3D support
configure: WARNING: because something is wrong with the OpenGL setup:
configure: WARNING: No OpenGL library found on this system.
```

My configuring options are the same as the recommended ones at the above link. I'm using (X)Ubuntu 6.06 Dapper. I've ran 'glxgears' with no problems, and consulted #winehq on Freenode, but they can't seem to help me. This is pretty much my last resort. Any help I could receive to get OpenGL and/or Direct3D support with wine would be great.

---

### Post by RAOF on 2007-02-19
Welcome to the wonderful world of [my repository](ubuntu.moshen.de).  There are (or should be) Wine 0.9.31 debs in there, for AMD64.  

**Edit**: Edgy only, it seems, though.  They don't build right on Dapper.  Why don't you just download an i386 .deb from the Wine site, anyway?

---

### Post by dfreer on 2007-02-19
I just did this myself actually, and had the same problem.
What you need is some developer packages installed.

```
sudo aptitude install xlibs-dev xlibmesa-gl xlibmesa-dri xlibmesa-gl-dev libgl1-mesa-dri libgl1-mesa-glx libgl1-mesa-dev
```

I don't know if you need ALL of those installed, but it won't hurt anything.

In the end, though, I was able to compile wine 9.30 but after this last kernel update wine crashed on me. I figured it isn't worth it to compile the package when there is wine_0.9.31~winehq0~ubuntu~6.10-1_i386.deb out there that works just as well.

---

### Post by RAOF on 2007-02-19
The actual problem is you need to symlink a bunch of libraries in /usr/lib32.

But really, just download the deb from the wine site.  There's no reason to compile.

---

### Post by ryansinn on 2008-02-28
OpenGL & Direct3d support do not work correctly with the amd64 packages from Ubuntu Repositories or the WineHQ repositories...  So you do actually have to compile.

---

