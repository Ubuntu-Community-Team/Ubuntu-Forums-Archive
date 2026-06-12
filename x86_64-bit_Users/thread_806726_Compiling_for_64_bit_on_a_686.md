---
title: "Compiling for 64 bit on a 686?"
date: 2008-05-25
forum: x86 64-bit Users
---

### Post by Schuttwegraeumer on 2008-05-25
I tried to compile a app for x86_64 on my 686 Prozessor and failed.

Which packages do I need to move my GCC into a crosscompiler?
A
```
./configure --disable-debug --enable-optimize --host=x86_64-unknown-linux-gnu
```
or a
```
./configure --disable-debug --enable-optimize --target=x86_64-unknown-linux-gnu
```
dont change the binary.

---

### Post by Julius on 2008-05-25
mmm a quick google search returned this as result:

[http://ubuntuforums.org/showthread.php?t=518979](http://ubuntuforums.org/showthread.php?t=518979)

---

### Post by Schuttwegraeumer on 2008-05-25
I have a problem with the wx libs:

> checking for wx-config... /usr/bin/wx-config
checking for wxWidgets version >= 2.8.0 (--unicode=yes)... no
configure: error: 
    The requested wxWidgets build couldn't be found.
    
    The configuration you asked for aMule requires a wxWidgets
    build with the following settings:
        --unicode=yes
    but such build is not available.

    To see the wxWidgets builds available on this system, please use
    'wx-config --list' command. To use the default build, returned by
    'wx-config --selected-config', use the options with their 'auto'
    default values.

    If you still get this error, then check that 'wx-config' is
    in path, the directory where wxWidgets libraries are installed
    (returned by 'wx-config --libs' command) is in LD_LIBRARY_PATH
    or equivalent variable and wxWidgets version is 2.8.0 or above.


With normale settings all is ok but all tries to crosscompile failed with this configure errors.

---

### Post by Kilz on 2008-05-25
> **Schuttwegraeumer said:**
> I have a problem with the wx libs:



With normale settings all is ok but all tries to crosscompile failed with this configure errors.

Just a question, why are you trying to compile amule, its in the repositories.

---

### Post by Schuttwegraeumer on 2008-05-26
> **Kilz said:**
> Just a question, why are you trying to compile amule, its in the repositories.
The Version in the REpositories is very old, yes the Version in the repository of 8.04 too.
I use my own build here.
News CVS versions can use the KAD2 with obfuscation.

---

