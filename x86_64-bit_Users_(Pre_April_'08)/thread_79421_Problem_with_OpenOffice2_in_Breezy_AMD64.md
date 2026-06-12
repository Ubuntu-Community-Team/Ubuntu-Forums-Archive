---
title: "Problem with OpenOffice2 in Breezy AMD64"
date: 2005-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by vicmanmo on 2005-10-20
Hi

When execute OpenOffice, I see this error message:

/usr/lib/openoffice2/program/javaldx: error while loading shared libraries: libz.so.1: cannot open shared object file: No such file or directory
/usr/lib/openoffice2/program/soffice.bin.real: error while loading shared libraries: libz.so.1: cannot open shared object file: No such file or directory

I remove OpenOffice and then I install the OpenOffice1.1.5 and OpenOffice2, and these programs show the same error message.

Help you,

Thank you.

---

### Post by mthaddon on 2005-10-20
I'm getting the same problem - see this bugzilla entry:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=17934](http://bugzilla.ubuntu.com/show_bug.cgi?id=17934)

Hopefully we can get it resolved soon....

Tom

---

### Post by R2-Bert on 2005-11-01
[QUOTE=mthaddon]I'm getting the same problem - see this bugzilla entry:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=17934](http://bugzilla.ubuntu.com/show_bug.cgi?id=17934)

Hopefully we can get it resolved soon....

Tom[/QUOTE]

I was having the same problem in Breezy on an AMD64. As Tollef Fog Heen suggested in the last comment on that bug, I re-installed lib32z1, ia32-libs-openoffice.org and ia32-libs-gtk.

```
sudo apt-get --reinstall install lib32z1 ia32-libs-openoffice.org ia32-libs-gtk
```

I'm not sure which one solved the problem, but now OpenOffice.org 2 works fine for me.

Thanks for the link to that bug report!

-Keith

---

