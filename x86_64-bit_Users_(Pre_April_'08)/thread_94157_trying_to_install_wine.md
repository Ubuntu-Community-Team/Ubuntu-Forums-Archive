---
title: "trying to install wine"
date: 2005-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by shomi on 2005-11-23
hello fellow ubuntu's ,

here is my query: i try to install wine from source and this is what i get :

shomi@ubuntu:~/wine-0.9.1$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc -m32
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.


why ??!!

thanks

---

### Post by Ribs on 2005-11-24
[QUOTE=shomi]See `config.log' for more details.[/QUOTE]

Not to sound rude, but I feel the next step is fairly obvious here... You've probably just forgotton to install a package it needs...

Or it's possible that wine flat out won't compile, I don't know if it compiles on 64-bit machines...

---

