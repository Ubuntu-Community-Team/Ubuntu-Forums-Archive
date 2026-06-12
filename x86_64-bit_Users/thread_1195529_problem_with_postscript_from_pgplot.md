---
title: "problem with postscript from pgplot"
date: 2009-06-23
forum: x86 64-bit Users
---

### Post by rvenable on 2009-06-23
I've recently switched from CentOS to Ubuntu for my desktop box; most things work well, but I've some trouble with my PGPLOT Fortran programs when I build with the libpgplot5 from Ubuntu.  The PostScript driver doesn't seem to work; the file produced has just the header defining the PostScript commands that the driver will use.  The same programs were able to produce PostScript output when I had linked against a libpgplot I built myself, but as I'd linked against a 32-bit X11 lib, I cannot run them on an x86_64 Ubuntu machine.  (CentOS has better 32-bit compatibility support).

Has anyone else observed this problem?  How can I report this as a possible bug?

---

