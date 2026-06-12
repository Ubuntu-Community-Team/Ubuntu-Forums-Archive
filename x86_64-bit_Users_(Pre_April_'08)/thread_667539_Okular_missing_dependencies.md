---
title: "Okular missing dependencies"
date: 2008-01-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by John Jason Jordan on 2008-01-14
Gutsy x86_64

I recently heard about okular and decided to try it out. It is listed in Synaptic, but when I selected it to install Synaptic announced that the following dependencies could not be met:

libgs-esp8
libpoppler1 >=0.5.1
libpoppler1-qt4

Synaptic suggested that I enable all the repositories, but I did so months ago when I installed Gutsy. They are all still enabled. Evidently the above libraries are somewhere else. Does anyone know where I can get them?

---

### Post by John Jason Jordan on 2008-01-15
OK, I found the 64-bit dependencies, installed them, and okular then installed without incident via Synaptic. However, it failed to create a launch item in Applications >. I tried "okular" from the command line, but just got "command not found." Then I did "locate okular" from the command line and got nothing.

Does anyone know how to launch it?

---

### Post by Cappy on 2008-01-15
You should be able to run it with ```
/usr/lib/kde4/bin/okular
```

you can see the name of the binary file using 
```
dpkg -L okular
```

or looking up okular on [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by John Jason Jordan on 2008-01-15
> **Cappy said:**
> You should be able to run it with ```
/usr/lib/kde4/bin/okular
```

you can see the name of the binary file using 
```
dpkg -L okular
```

or looking up okular on [http://packages.ubuntu.com](http://packages.ubuntu.com)
Thanks!

However, I still can't get it to launch:

jjj@Devil7:/$ /usr/lib/kde4/bin/okular
/usr/lib/kde4/bin/okular: error while loading shared libraries: libkdefx.so.5: cannot open shared object file: No such file or directory

I searched Synaptic and can't find libkdefx. Then I googled and found this:

[https://bugs.launchpad.net/ubuntu/+source/koffice2/+bug/162667](https://bugs.launchpad.net/ubuntu/+source/koffice2/+bug/162667)

However, the above bug report did not reveal any solution and hasn't even been assigned to anyone. Anyone have any further ideas?

---

### Post by unrater on 2008-01-23
same problem here. any idea?

---

### Post by John Jason Jordan on 2008-01-24
> **unrater said:**
> same problem here. any idea?
I have it running! 

However, I regret that I did not document how I did it, nor do I remember. But at least I can confirm that it is possible to install it on Gutsy x86_64.

I note in Synaptic that I have installed:

okular-kde4
libokularcore1-kde4

I also note that I did NOT install:

okular
okular-dev-kde4
okular-extra-backends-kde4

I also recall that initially I tried to install the okular-extra-backends-kde4 package, but had a lot of problems with missing dependencies. 

And I think I found the following missing dependencies elsewhere on the net:

libgs-esp8
libpoppler1 >=0.5.1
libpoppler1-qt4

Having said all that it has only one feature that is worth anything - it can import a PS and convert it to PDF, then save it as a PDF. KPDF can import a PS as a PDF, but can't save it as a PDF. Personally I use this feature a lot.

Theoretically okular can open an editable PDF (like an income tax form) and fill it out (which until now could be done only in Adobe Reader 7.0 or later). In reality this feature needs a LOT of work. All the fields were messed up and some couldn't be edited at all. If you want to fill in editable PDF forms you still need Adobe Reader until the okular developers work on that feature some more.

It does seem stable and otherwise works reasonably well, although there is a problem with printing - I told it the paper size was US letter and when the printer finished imaging the file the printer's control panel said "load A4." It doesn't seem to be able to change the paper size in the dialog box from the default A4 size. Not a problem if you use A4 paper, but that size is hard to find and expensive in the US and a lot of other countries.

I hope the above helps people get it installed.

---

