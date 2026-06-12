---
title: "Cannot compile (warning: implicit declaration of function ‘fork’)"
date: 2009-02-11
forum: x86 64-bit Users
---

### Post by Izkata on 2009-02-11
So, fork() does not work:
```

#include <stdlib.h>
#include <stdio.h>

int main(char *args[]) {
   fork();
   return 0;
}

```
```
izkata@Izein:~/C$ gcc -o Forktest Forktest.c 
Forktest.c: In function ‘main’:
Forktest.c:5: warning: implicit declaration of function ‘fork’

```

Yes, build-essential is installed.  Anyone have any ideas?

---

### Post by movieman on 2009-02-11
Fork is defined in unistd.h, I believe.

BTW, that's only a warning, the program would probably still work.

---

### Post by Izkata on 2009-02-11
Well, it got rid of the warning.  I was sure I had it before with just stdlib (and included stdio to make sure).

Thanks!

---

