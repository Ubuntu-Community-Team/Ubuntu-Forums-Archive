---
title: "Cross compile for 32 bit, missing libdbus-glib-1.so"
date: 2008-10-02
forum: x86 64-bit Users
---

### Post by shantzg001 on 2008-10-02
Hi 


I'm cross-compiling an application to 32 bit arch. My app uses dbus-glib bindings. My base system is Ubuntu Hardy 64, so I use the -m32 flag with gcc to compile but it gives me an error of missing libdbus-glib-1.so. All other libs are present as I've already installed gcc-multilib, ia32libs etc packages and am also able to cross compile other applications that don't depend on this particular library. Any suggestions which package to install to get this 32 bit lib onto my system?

My Compile command:
```
gcc -Wall -O `pkg-config --cflags dbus-1 glib-2.0 dbus-glib-1` `pkg-config --libs dbus-1 glib-2.0 dbus-glib-1` marshal.c main.c -o splert
```

Errors:
```
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libdbus-glib-1.so when searching for -ldbus-glib-1
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../libdbus-glib-1.a when searching for -ldbus-glib-1
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libdbus-glib-1.so when searching for -ldbus-glib-1
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libdbus-glib-1.a when searching for -ldbus-glib-1
/usr/bin/ld: skipping incompatible /usr/lib/libdbus-glib-1.so when searching for -ldbus-glib-1
/usr/bin/ld: skipping incompatible /usr/lib/libdbus-glib-1.a when searching for -ldbus-glib-1
/usr/bin/ld: cannot find -ldbus-glib-1
collect2: ld returned 1 exit status
```

---

### Post by Yellow Pasque on 2008-10-02
Use getlibs. [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by shantzg001 on 2008-10-03
@Temujin: Thanks a lot man (and to Cappy, getlibs author). It worked like a charm...

---

