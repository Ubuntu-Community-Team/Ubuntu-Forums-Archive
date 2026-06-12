---
title: "Wine and OpenGL problem."
date: 2007-11-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Unnicknamed on 2007-11-24
Hi there I'm having trouble running OpenGL apps with Wine, I get this message error:

err:module:load_builtin_dll failed to load .so lib for builtin L"Opengl32.dll": libGL.so.1: cannot open shared object file: No such file or directory

I'm on AMD64 Ubuntu. I'm using Compiz Fusion and using the ATI drivers from AMD site.

Is it possible to fix this? Thanks in advance,

The same things happens with Google Earth

 error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

This what I get when trying to run it.

---

### Post by Unnicknamed on 2007-11-24
OK guys I follow this guide.
[http://bbs.keyhole.com/ubb/showflat.php?Cat=0&Board=SupportGELinux&Number=620003&page=2&fpart=2](http://bbs.keyhole.com/ubb/showflat.php?Cat=0&Board=SupportGELinux&Number=620003&page=2&fpart=2)
I get the file libGL.so.1 so I can now run Google Earth.

But how about the wine problem? Where I should put this file?

---

### Post by Kilz on 2007-11-25
> **Unnicknamed said:**
> Hi there I'm having trouble running OpenGL apps with Wine, I get this message error:

err:module:load_builtin_dll failed to load .so lib for builtin L"Opengl32.dll": libGL.so.1: cannot open shared object file: No such file or directory

I'm on AMD64 Ubuntu. I'm using Compiz Fusion and using the ATI drivers from AMD site.

Is it possible to fix this? Thanks in advance,

The same things happens with Google Earth

 error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

This what I get when trying to run it.

What happens to your problems when you disable Compiz Fusion?

---

