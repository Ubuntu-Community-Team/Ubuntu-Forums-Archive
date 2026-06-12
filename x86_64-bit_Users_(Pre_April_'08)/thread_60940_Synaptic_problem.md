---
title: "Synaptic problem"
date: 2005-08-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by loafofbread34 on 2005-08-29
For some reason I cant download some packages (Actually they arn't even listen TO download...)

Like I added the wine repository, updated, but it cannot be found. Im not sure, but I think bison is a package that I should be able to download, but it cannot be found. Is somthing wrong?

I think I know what is up. I have a AMD64 system. There arn't packages for my system?

So I downloaded the source of wine and tried to ./configure, and got this error:

```
brent@brent:~/Downloads/Wine-20050725.tar.gz_FILES/wine-20050725$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
``` 

Know whats up?

---

### Post by DancingSun on 2005-08-29
Yes, it's most likely that the repositories you added do not have packages for the AMD64 architecture.  See [this thread](http://ubuntuforums.org/showthread.php?t=48905).  You'll also see that in the first post we have attempted to build WINE for AMD64 unsuccessfully.

---

### Post by loafofbread34 on 2005-08-30
Thats too bad. That means Ill have to go about and install windows and the such... :( I hate Windows. Do you know if the makers of wine are going to release a package that will work with AMD64?

---

