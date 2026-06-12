---
title: "mathmap plugin for GIMP x86 64"
date: 2007-08-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by pearlie on 2007-08-08
Has anyone managed to get the mathmap plugin installed on 64-bit GIMP 2.2?  If so, I'd appreciate some guidance on how you did it.  I've tried installing the 64-bit .rpm - no dice - and compiling from source code,-  which gives me this:

pearlie@laptop:~/Desktop/mathmap-1.0.1$ make install
gcc -I. -DCGEN_CC="\"gcc -O2 -c -fPIC -o\"" -DCGEN_LD="\"gcc -shared -o\"" -g -Wall `gimptool-2.0 --cflags` -DGIMP2 -DGIMP22 -DGIMP -DLOCALEDIR=\"/usr/local/share/locale\" -DENABLE_NLS -DMATHMAP_VERSION=\"1.0.1\" -c builtins.c
builtins.c:29:28: error: gsl/gsl_vector.h: No such file or directory
builtins.c:30:28: error: gsl/gsl_matrix.h: No such file or directory
builtins.c:31:28: error: gsl/gsl_linalg.h: No such file or directory
builtins.c: In function ‘solve_linear_equations’:
builtins.c:206: error: ‘gsl_matrix’ undeclared (first use in this function)
builtins.c:206: error: (Each undeclared identifier is reported only once
builtins.c:206: error: for each function it appears in.)
builtins.c:206: error: ‘m’ undeclared (first use in this function)
builtins.c:207: error: ‘gsl_vector’ undeclared (first use in this function)
builtins.c:207: error: ‘b’ undeclared (first use in this function)
builtins.c:207: error: ‘r’ undeclared (first use in this function)
builtins.c:207: warning: left-hand operand of comma expression has no effect
builtins.c:210: warning: implicit declaration of function ‘gsl_matrix_alloc’
builtins.c:211: warning: implicit declaration of function ‘gsl_vector_alloc’
builtins.c:216: warning: implicit declaration of function ‘gsl_matrix_set’
builtins.c:219: warning: implicit declaration of function ‘gsl_vector_set’
builtins.c:221: warning: implicit declaration of function ‘gsl_linalg_HH_solve’
builtins.c:224: warning: implicit declaration of function ‘gsl_vector_get’
builtins.c:226: warning: implicit declaration of function ‘gsl_vector_free’
builtins.c:228: warning: implicit declaration of function ‘gsl_matrix_free’
make: *** [builtins.o] Error 1


Boo hoo.  Obviously I'm missing something.  

thanks for any suggestions.

---

### Post by Kilz on 2007-08-08
> **pearlie said:**
> Has anyone managed to get the mathmap plugin installed on 64-bit GIMP 2.2?  If so, I'd appreciate some guidance on how you did it.  I've tried installing the 64-bit .rpm - no dice - and compiling from source code,-  which gives me this:

pearlie@laptop:~/Desktop/mathmap-1.0.1$ make install
gcc -I. -DCGEN_CC="\"gcc -O2 -c -fPIC -o\"" -DCGEN_LD="\"gcc -shared -o\"" -g -Wall `gimptool-2.0 --cflags` -DGIMP2 -DGIMP22 -DGIMP -DLOCALEDIR=\"/usr/local/share/locale\" -DENABLE_NLS -DMATHMAP_VERSION=\"1.0.1\" -c builtins.c
builtins.c:29:28: error: gsl/gsl_vector.h: No such file or directory
builtins.c:30:28: error: gsl/gsl_matrix.h: No such file or directory
builtins.c:31:28: error: gsl/gsl_linalg.h: No such file or directory
builtins.c: In function ‘solve_linear_equations’:
builtins.c:206: error: ‘gsl_matrix’ undeclared (first use in this function)
builtins.c:206: error: (Each undeclared identifier is reported only once
builtins.c:206: error: for each function it appears in.)
builtins.c:206: error: ‘m’ undeclared (first use in this function)
builtins.c:207: error: ‘gsl_vector’ undeclared (first use in this function)
builtins.c:207: error: ‘b’ undeclared (first use in this function)
builtins.c:207: error: ‘r’ undeclared (first use in this function)
builtins.c:207: warning: left-hand operand of comma expression has no effect
builtins.c:210: warning: implicit declaration of function ‘gsl_matrix_alloc’
builtins.c:211: warning: implicit declaration of function ‘gsl_vector_alloc’
builtins.c:216: warning: implicit declaration of function ‘gsl_matrix_set’
builtins.c:219: warning: implicit declaration of function ‘gsl_vector_set’
builtins.c:221: warning: implicit declaration of function ‘gsl_linalg_HH_solve’
builtins.c:224: warning: implicit declaration of function ‘gsl_vector_get’
builtins.c:226: warning: implicit declaration of function ‘gsl_vector_free’
builtins.c:228: warning: implicit declaration of function ‘gsl_matrix_free’
make: *** [builtins.o] Error 1


Boo hoo.  Obviously I'm missing something.  

thanks for any suggestions.

A search of the [Ubuntu package site]("http://packages.ubuntu.com/") says [This Package]("http://packages.ubuntu.com/feisty/libdevel/libgsl0-dev") contains the gsl files.

---

### Post by pearlie on 2007-08-08
Woo hoo!  thanks Kilz, you put me on the right track.  I also had to hunt down and install bison and flex.  But I think that's got it - at least I have the plugin in the menu now, I'll have to try out a photo and see if it works.

:guitar:  you rock.  Thanks for taking the time.

---

