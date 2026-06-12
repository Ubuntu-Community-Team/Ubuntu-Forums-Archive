---
title: "[SOLVED] c source includes and gcc"
date: 2008-05-15
forum: x86 64-bit Users
---

### Post by Superkuh on 2008-05-15
I'm on Ubuntu 8.04 64bit compiling some C code and trying to use the generic kernel headers', but every time I do the header mentioned is not found. I checked in /usr/src/linux-headers-2.6.24-16/include/asm-x86/ . It is there. I even recursively copied io.h and it's includes to one flat directory while substituting the flat paths in the copied includes; this obviously failed. I do not know what I am doing wrong. 

gcc lptstuff.c = error: asm/io.h: No such file or directory

I ask here because it is not exactly a c related question and more related to distribution.

It doesn't have to be the below code, of course. It's the <asm/io.h> that matters.```
#include <stdio.h>
#include <unistd.h>
#include <asm/io.h>

#define BASEPORT 0x378 /* lp1 */

int main()
{
  /* Get access to the ports */
  if (ioperm(BASEPORT, 3, 1)) {perror("ioperm"); exit(1);}
  
  /* Set the data signals (D0-7) of the port to all low (0) */
  outb(0, BASEPORT);
  
  /* Sleep for a while (100 ms) */
  usleep(100000);
  
  /* Read from the status port (BASE+1) and display the result */
  printf("status: %d\n", inb(BASEPORT + 1));

  /* We don't need the ports anymore */
  if (ioperm(BASEPORT, 3, 0)) {perror("ioperm"); exit(1);}

  exit(0);
}
```

---

### Post by hoarycripple on 2008-05-15
You may want to take a look at this documentation:

[http://www.debian.org/doc/manuals/reference/ch-kernel.en.html](http://www.debian.org/doc/manuals/reference/ch-kernel.en.html)

Specifically, section 7.1.1 "Kernel Headers"

---

### Post by Superkuh on 2008-05-15
Ah, the full path (#include </usr/src/linux-headers-2.6.24-16/include/asm-x86/io.h>) works. Thanks. I feel silly now.

---

