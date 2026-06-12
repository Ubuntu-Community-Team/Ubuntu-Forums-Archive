---
title: "want to link against /usr/lib32/....."
date: 2007-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by glangollor on 2007-11-03
When I  try to install FST ([http://www.joebutton.co.uk/fst/](http://www.joebutton.co.uk/fst/)) the compiling seems to work up to linking a file.
When I did this step by myself I saw that I looks for its librarys in /usr/lib and /usr/lib64 .
It should look for them in /usr/lib32, but although I specified -L/usr/lib32 on the command line it still just looks in the 64bit directorys.
When I specify a library with -l:/usr/lib32/libTHENAME.so.(WHATWEVER VERSION) I get no error. 
But thats not really a solution, since that are quite many librarys.

Can anyone see what goes wrong here??
Thanks for your help in advance!  

(I run Gutsy on amd64)

---

