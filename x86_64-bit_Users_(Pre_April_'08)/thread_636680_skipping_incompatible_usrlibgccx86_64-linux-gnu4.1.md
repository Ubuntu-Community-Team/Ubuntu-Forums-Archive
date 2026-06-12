---
title: "skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libstdc++.a when searching"
date: 2007-12-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by svadimr on 2007-12-10
Hello,

This question probably was asked a lot but I still didn't found any suitable answer.

I have number of applications as source code. I need to compile them on my ubuntu 64bit machine. As a result of make I get this kind of error:

 /usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.1.3/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status

on some different source I got:/usr/bin/ld: skipping incompatible /usr/bin/../lib/libz.a when searching for -lz
/usr/bin/ld: skipping incompatible /usr/lib/libz.a when searching for -lz
/usr/bin/ld: cannot find -lz
collect2: ld returned 1 exit status

I really don't know what to do next and it's important to me to build those applications.

Thanks.

Vadim.

---

