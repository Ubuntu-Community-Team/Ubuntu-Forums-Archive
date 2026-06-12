---
title: "Creating kernel modules in Ubuntu on AMD64 arch"
date: 2008-06-20
forum: x86 64-bit Users
---

### Post by dsoftware on 2008-06-20
I am trying to build a kernel module on an AMD64 (K)Ubuntu system, but I am running into some problems getting the module to install on the system.  I am starting with the example from [http://tldp.org/HOWTO/Module-HOWTO/x839.html](http://tldp.org/HOWTO/Module-HOWTO/x839.html), which covers the basic hello world.  When i build the module, I get a few warnings (list below), but no errors.  Then when I try to install the module I get the following message:
```

$ sudo insmod  /home/apridgen/Programming/Kmodules/helloworld/hello.ko
insmod: error inserting '/home/apridgen/Programming/Kmodules/helloworld/hello.ko': -1 Invalid module format
```

Any help on this is greatly appreciated.  I have been searching around the net, and I have not been able to identify anything that relates to developing custom modules or creating the environment for AMD64, as shown in the Kernel Module How-to.  Below are the compile errors, my make file, and the modified source file to get the module to build.  Thanks in advance.

Compiler Warnings:
```
gcc -c -g -Wall -L/lib/modules/2.6.24-19-generic/build/include -I/lib/modules/2.6.24-19-generic/build/include -D__KERNEL__ -DMODULE -o hello.o hello.c
hello.c:12:1: warning: "__KERNEL__" redefined
<command-line>: warning: this is the location of the previous definition
hello.c:13:1: warning: "MODULE" redefined
<command-line>: warning: this is the location of the previous definition
ld -r -o hello.ko hello.o

```


Makefile:
```

KCFLAGS = -c -g -Wall -L/lib/modules/2.6.24-19-generic/build/include -I/lib/modules/2.6.24-19-generic/build/include -D__KERNEL__ -DMODULE
CC = gcc
M_OBJS = hello.o
M_TARGET = hello.ko

$(M_TARGET) : $(M_OBJS)
        ld -r -o $@ $(M_OBJS)

$(M_OBJS) : %.o : %.c
        $(CC) $(KCFLAGS) -o $@ $<
```

Source File:
```
/* hello.c
*
* "Hello, world" - the loadable kernel module version.
*
* Compile this with
*
*          gcc -c hello.c -Wall
*/

/* Declare what kind of code we want from the header files */

#define __KERNEL__         /* We're part of the kernel */
#define MODULE             /* Not a permanent part, though. */
#define CONFIG_X86_L1_CACHE_SHIFT 7
#define ARCH x86_64
/* Standard headers for LKMs */
#include <linux/module.h>
#include <linux/param.h>
#include <linux/module.h>
#include <linux/kernel.h>
//#include <linux/tty.h>
/* console_print() interface */

/* Initialize the LKM */
int init_module()
{
//  console_print("Hello, world - this is the kernel speaking\n");
  return 0;
}

void cleanup_module()
{
//  console_print("Short is the life of an LKM\n");
}
```

System Info:
```
$ uname -a
Linux supapwn 2.6.24-19-generic #1 SMP Wed Jun 4 15:10:52 UTC 2008 x86_64 GNU/Linux
```

---

