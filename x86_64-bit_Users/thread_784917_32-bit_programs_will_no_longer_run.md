---
title: "32-bit programs will no longer run??"
date: 2008-05-06
forum: x86 64-bit Users
---

### Post by ZeroHimself on 2008-05-06
I can't get *ANY* 32-bit apps to run under my hardy amd64 installation....

I simply get```
zero@atlantis:~/src/zsnes/zsnes_1_51$ file zsnes 
zsnes: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.1, dynamically linked (uses shared libs), stripped
zero@atlantis:~/src/zsnes/zsnes_1_51$ ./zsnes
bash: ./zsnes: No such file or directory

```

????, it worked yesterday, all i did was install virtualbox

?? 

strace just reports No such file or directory

and yes it is -rwxrwxrwx

---

### Post by Cappy on 2008-05-07
Is ia32-libs still installed?

---

### Post by ZeroHimself on 2008-05-19
sorry, computer died, or i would have posted sooner, it turned out to be a missing library file...(i would post what lib, but i presently don't have a linux machine.......)

---

