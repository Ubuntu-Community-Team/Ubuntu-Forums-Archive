---
title: "Compiling Clearlooks 0.6.2 for AMD64"
date: 2005-08-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by pailhead on 2005-08-01
I'm trying to compile and make Clearlooks for the 64 bit system.  Well I've run ./configure and I've ended up with the following statment:

```
checking for ANSI C header files... (cached) yes
./configure: line 22489: --variable=gtk_binary_version: command not found
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
configure: error: GTK+-2.0 is required to compile clearlooks-engine
pailhead@ubuntu:~/packages/clearlooks/clearlooks-0.6.2$
```

Do I need to install something or is the 64bit Ubuntu release not compatable with this version of Clearlooks?

Thanks...

---

### Post by varunus on 2005-08-02
Install libgtk2.0-dev from synaptic, then try to compile again.  It should work now.

---

