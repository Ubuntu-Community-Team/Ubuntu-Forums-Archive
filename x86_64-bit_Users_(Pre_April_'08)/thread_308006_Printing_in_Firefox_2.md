---
title: "Printing in Firefox 2"
date: 2006-11-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by jefrat72 on 2006-11-27
I just set up Firefox 2 on my 6.06 64bit machine, but I can not print.  I go to print and my only choice is "PostScript/default".  I am trying to print to a networked printer that all my other programs do currently print to.

Any help would be appreciated.

---

### Post by kleeman on 2006-11-27
cups problem not 64bit issue, my 64bit firefox sees all my printers. Ask in the General Help section

---

### Post by eurgain on 2006-11-30
I would bet the OP is having problems with a 32-bit Firefox on a 64-bit install.  I also have this problem with 32-bit Swiftfox and Acroread, but not with 64-bit Firefox.  I also have the same problem with xsane, which realli is odd...

Anyway, what we really need is 32-bit compatibility Cups libraries to install, but it seems that there are no .debs available.

I am going to do a lot of backing up then very carefully try manually installing the cups libraries from a 32-bit system into /usr as an experiment (something I have seen suggested elsewhere).  I have a 32-bit Edgy machine as well to use as a source.

I will let you know if I meet with any success (or failure).

Regards
A

PS: this is all a bit old-time stuff!

---

### Post by eurgain on 2006-12-05
Well, I have made some progress.

First, I tried copying all cups-related libraries from a 32-bit Edgy machine to /usr/lib32 in my 64-bit machine.  No change.

I then copied the entire contents (less symlinks) of /usr/lib from 32-bit Edgy to /usr/lib32 in my 64-bit machine.  Hay presto, 32-bit Swiftfox now shows all the printers :-) but acroread segfaults :-( with a problem related to Pango or Cairo.

I am going to try to copy libraries selectively until I get everything working. (I already have every 32-bit compatibility package installed.)

A

---

### Post by eurgain on 2006-12-30
> **eurgain said:**
> Well, I have made some progress.

First, I tried copying all cups-related libraries from a 32-bit Edgy machine to /usr/lib32 in my 64-bit machine.  No change.

I then copied the entire contents (less symlinks) of /usr/lib from 32-bit Edgy to /usr/lib32 in my 64-bit machine.  Hay presto, 32-bit Swiftfox now shows all the printers :-) but acroread segfaults :-( with a problem related to Pango or Cairo.

I am going to try to copy libraries selectively until I get everything working. (I already have every 32-bit compatibility package installed.)

A

I've given up!  Did anyone else have any success?

A

---

