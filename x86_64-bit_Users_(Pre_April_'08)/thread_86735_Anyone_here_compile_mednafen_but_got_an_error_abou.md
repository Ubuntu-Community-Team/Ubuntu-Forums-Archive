---
title: "Anyone here compile mednafen but got an error about  libintl.so.3?"
date: 2005-11-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by BoyOfDestiny on 2005-11-06
mednafen
mednafen: error while loading shared libraries: libintl.so.3: cannot open shared object file: No such file or directory

It compiled just fine... Any ideas what could be causing this during runtime?

[http://mednafen.com/](http://mednafen.com/)

(It compiled/works fine on ubuntu 32-bit)

---

### Post by Mednafen on 2005-11-10
Search for AM_GNU_GETTEXT(blahblahblah) in configure.ac, remove everything in the parenthesis and the parenthesis, and run ./autogen.sh(make sure you have aclocal-1.6, automake-1.6, autoconf, and libtool installed.

Then rerun the configure script and compile.

Does that solve the problem?

---

### Post by BoyOfDestiny on 2005-11-10
[QUOTE=Mednafen]Search for AM_GNU_GETTEXT(blahblahblah) in configure.ac, remove everything in the parenthesis and the parenthesis, and run ./autogen.sh(make sure you have aclocal-1.6, automake-1.6, autoconf, and libtool installed.

Then rerun the configure script and compile.

Does that solve the problem?[/QUOTE]

Nope, same problem. I notice though in the configure.ac right below the gettext stuff:

AM_GNU_GETTEXT

AC_SUBST(LIBINTL)

The error I'm getting is in regard to libintl?

P.S You aren't the project maintainer for mednafen are you? :)

---

