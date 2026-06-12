---
title: "gcc compiler problem (no include path)"
date: 2008-05-11
forum: x86 64-bit Users
---

### Post by captain_hideous on 2008-05-11
I am unable to compile simple c program. I have installed gcc, g++, libc6-dev and build-essential without success. 

the program:

#include <stdio.h>

main()
{
    printf ("Hello World!\n");
}

the error:

gcc main.c
main.c:1:19: error: no include path in which to search for stdio.h

---

### Post by hoarycripple on 2008-05-15
Try installing libstdc++6-4.2-dev if it is not already installed.

---

### Post by amingv on 2008-05-15
Or better:

```
sudo apt-get install build-essential
```

---

### Post by captain_hideous on 2008-05-29
I have installed build-essential and libstdc++6-4.2-dev. I still get the same error message.

---

