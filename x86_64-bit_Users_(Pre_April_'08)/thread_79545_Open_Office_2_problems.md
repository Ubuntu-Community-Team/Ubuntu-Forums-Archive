---
title: "Open Office 2 problems"
date: 2005-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by mthaddon on 2005-10-20
I have a problem which I've reported in bugzilla [http://bugzilla.ubuntu.com/show_bug.cgi?id=17934](http://bugzilla.ubuntu.com/show_bug.cgi?id=17934), but the trail seems to have gone cold on that one. I upgraded from hoary and something seems broken in my openoffice installation. If I try to start up oowriter2 from the command line I get:

/usr/lib/openoffice2/program/soffice: line 152:
/usr/lib/openoffice2/program/javaldx: No such file or directory
/usr/lib/openoffice2/program/soffice: line 213:
/usr/lib/openoffice2/program/pagein: No such file or directory
/usr/lib/openoffice2/program/soffice.bin: line 3:
/usr/lib/openoffice2/program/soffice.bin.real: No such file or directory
/usr/lib/openoffice2/program/soffice.bin: line 3:
/usr/lib/openoffice2/program/soffice.bin.real: Success

All of the files it's saying don't exist do exist.

Any ideas?

Thanks, Tom

---

### Post by queenorych on 2005-10-21
Dumb question, have you tried reinstalling openoffice?


sudo aptitude
'/openoffice' return
I think it was 'L' for reinstall.

---

### Post by exp(x) on 2005-10-21
I'm getting this message: 

/usr/lib/openoffice2/program/javaldx: error while loading shared libraries: libz.so.1: cannot open shared object file: No such file or directory
/usr/lib/openoffice2/program/soffice.bin.real: error while loading shared libraries: libz.so.1: cannot open shared object file: No such file or directory

I have zlib1g installed, though, and libz.so.1 is in /usr/lib/. I am confused as to why it is not seeing it.

Edit: nevermind, I figured it out.

---

