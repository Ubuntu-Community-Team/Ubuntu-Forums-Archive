---
title: "Changing the ld from /usr/bin/ld to custom"
date: 2008-04-27
forum: x86 64-bit Users
---

### Post by Kapitan on 2008-04-27
Hi all ubuntu users :)

I've compiled a cross platform binutils
(32-bit) and now i want to make the system use
that version instead of the classical in 
/usr/bin/ld.

How can i do?

:popcorn:

---

### Post by Kapitan on 2008-04-27
I've found that /usr/bin/libtool is
a customizable script, so i've tried
to modify the LD line.

But it continues using /usr/bin/ld instead
of my custom ld...

I mean, when i launch gcc something -o someother.o
what is the config file i have to change to tell
gcc to use another linker?

---

### Post by Kapitan on 2008-04-27
And the /etc/ld.so.conf is an include.

It points to ld.so.conf.d that point to 
a few empty dirs...

What i have missed of library config?

---

### Post by Kapitan on 2008-05-02
I've found myself.

Gcc has an option that recalls
any library or tools (ld, ranlib..)
searching first the given prefix
(aka dir) and than the others.

This option is -B.

---

