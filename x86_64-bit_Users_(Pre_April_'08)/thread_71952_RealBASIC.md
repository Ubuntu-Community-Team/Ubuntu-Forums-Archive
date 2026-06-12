---
title: "RealBASIC"
date: 2005-10-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by arlie on 2005-10-04
Did this

./REALbasic2005

and got this

./REALbasic2005: error while loading shared libraries: libcups.so.2: cannot open shared object file: No such file or directory

****

I did not have any problem with hoary only until I ran RealBASIC on breezy amd64. What files do I need to get? Please help.

---

### Post by DancingSun on 2005-10-04
[QUOTE=arlie]Did this
./REALbasic2005
and got this
./REALbasic2005: error while loading shared libraries: libcups.so.2: cannot open shared object file: No such file or directory
****
I did not have any problem with hoary only until I ran RealBASIC on breezy amd64. What files do I need to get? Please help.[/QUOTE]
Is this Real Basic for AMD64?

---

### Post by arlie on 2005-10-05
[QUOTE=DancingSun]Is this Real Basic for AMD64?[/QUOTE]
I'm not sure. But I don't think so. 

I think a 32-bit program may still run  on a 64-bit OS. Can I not just download the missing files?

---

### Post by DancingSun on 2005-10-05
[QUOTE=arlie]I'm not sure. But I don't think so. 
I think a 32-bit program may still run  on a 64-bit OS. Can I not just download the missing files?[/QUOTE]
In theory, you could.  But of course, you'll need the 32-bit version of those files.  If you can find the 32-bit version of those files, try putting the .so files in /lib32/, and see if they work or not.  I don't know where to get those files though, but I'm sure doing a web search will yield some clues.

I don't know which files you need as well, as that depends on the program's dependencies, so you'll have to hunt them down one-by-one.  If a certain package is required, I'll be more careful, since that may entail the installation of more than just the library files.

---

