---
title: "Compiling Rhythmbox 0.9.0 question"
date: 2005-08-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by pailhead on 2005-08-14
I'm trying to compile the latest Rhythmbox on my AMD64 machine and I get the following error:

```
./configure: line 21672: PKG_PROG_PKG_CONFIG: command not found
checking for pkg-config... /usr/bin/pkg-config
checking for              gtk+-2.0 >= 2.5.4  libgnomeui-2.0                                   libglade-2.0  gnome-vfs-2.0 >= 2.6                     gnome-vfs-module-2.0  totem-plparser >= 1.1.3                  ... Package libgnomeui-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgnomeui-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgnomeui-2.0' found

configure: error: Library requirements (                  gtk+-2.0 >= 2.5.4  libgnomeui-2.0                                   libglade-2.0  gnome-vfs-2.0 >= 2.6                     gnome-vfs-module-2.0  totem-plparser >= 1.1.3                  ) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
pailhead@ubuntu:~/packages/rhythmbox/rhythmbox-0.9.0$
```

Any ideas.  I've checked and I have libgnomeui-2.0+...

---

### Post by clparker on 2005-08-14
Is that the only version of Rythmbox you have tried? Maybe you might have better luck with another version?

---

### Post by pailhead on 2005-08-14
Well I've got 0.8.8 from the repo's and that's installed. I wanted to get 0.9.0 to compile and create a 64bit package.

---

### Post by dori on 2005-08-14
You need libgnomeui-2.0-dev and other gtk dev packages

---

### Post by Tamir on 2005-08-14
[QUOTE=pailhead]Well I've got 0.8.8 from the repo's and that's installed. I wanted to get 0.9.0 to compile and create a 64bit package.[/QUOTE]
 Please don't do that, I already started to. I don't want  double jobs :) thanks very much. try to make packages of other requests.

---

### Post by pailhead on 2005-08-14
[QUOTE=Tamir]Please don't do that, I already started to. I don't want  double jobs :) thanks very much. try to make packages of other requests.[/QUOTE]
 Ok sorry.. didn't know it was already being done.

---

