---
title: "libncurses not found"
date: 2006-08-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by sd_rich on 2006-08-24
i have a program that is library dependent on libncurses.so.5
$ ldd /opt/storix/bin/stinstmenu
        linux-gate.so.1 =>  (0xffffe000)
        libncurses.so.5 => not found
        libc.so.6 => /lib32/libc.so.6 (0x55577000)
        /lib/ld-lsb.so.1 (0x55555000)

but as you can see, ldd cant find the shared library.

it is installed on the system
$ ls -l /lib/libncurses*
lrwxrwxrwx 1 root root     15 2006-08-24 17:47 /lib/libncurses.so.4 -> libncurses.so.5
lrwxrwxrwx 1 root root     17 2006-08-23 16:16 /lib/libncurses.so.5 -> libncurses.so.5.5
-rw-r--r-- 1 root root 373480 2006-01-13 12:54 /lib/libncurses.so.5.5
lrwxrwxrwx 1 root root     18 2006-08-23 16:16 /lib/libncursesw.so.5 -> libncursesw.so.5.5
-rw-r--r-- 1 root root 414856 2006-01-13 12:54 /lib/libncursesw.so.5.5

and ldconfig can find it
$ ldconfig -p | grep libncurses*
        libncursesw.so.5 (libc6,x86-64) => /lib/libncursesw.so.5
        libncurses.so.5 (libc6,x86-64) => /lib/libncurses.so.5

any ideas as to why ldd does not see it or how i can get the system to use it when i launch this program?

---

### Post by Kilz on 2006-08-25
> **sd_rich said:**
> i have a program that is library dependent on libncurses.so.5
$ ldd /opt/storix/bin/stinstmenu
        linux-gate.so.1 =>  (0xffffe000)
        libncurses.so.5 => not found
        libc.so.6 => /lib32/libc.so.6 (0x55577000)
        /lib/ld-lsb.so.1 (0x55555000)

but as you can see, ldd cant find the shared library.

it is installed on the system
$ ls -l /lib/libncurses*
lrwxrwxrwx 1 root root     15 2006-08-24 17:47 /lib/libncurses.so.4 -> libncurses.so.5
lrwxrwxrwx 1 root root     17 2006-08-23 16:16 /lib/libncurses.so.5 -> libncurses.so.5.5
-rw-r--r-- 1 root root 373480 2006-01-13 12:54 /lib/libncurses.so.5.5
lrwxrwxrwx 1 root root     18 2006-08-23 16:16 /lib/libncursesw.so.5 -> libncursesw.so.5.5
-rw-r--r-- 1 root root 414856 2006-01-13 12:54 /lib/libncursesw.so.5.5

and ldconfig can find it
$ ldconfig -p | grep libncurses*
        libncursesw.so.5 (libc6,x86-64) => /lib/libncursesw.so.5
        libncurses.so.5 (libc6,x86-64) => /lib/libncurses.so.5

any ideas as to why ldd does not see it or how i can get the system to use it when i launch this program?

Its possible that the applications is 32bit and looking for the 32bit version. There is a [package that supplies it]("http://packages.ubuntu.com/dapper/libs/lib32ncurses5") in the Universe repository.

---

### Post by sd_rich on 2006-08-25
that was it. thanks.

---

