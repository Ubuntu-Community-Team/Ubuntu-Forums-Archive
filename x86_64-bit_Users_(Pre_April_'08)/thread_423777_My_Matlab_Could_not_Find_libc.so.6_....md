---
title: "My Matlab Could not Find libc.so.6 ..."
date: 2007-04-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by dsdsdds on 2007-04-26
Hello, everyone.
:-/ I ran matlab then I got this.
My OS is Ubuntu 7.04 x86_64, Matlab is R14.

$ matlab
awk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
/bin/pwd: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
expr: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Internal error 2: Could not determine the path of the
MATLAB root directory.

original command path = /usr/local/bin/matlab
current command path = /usr/local/bin/matlab

Please contact:

MathWorks Technical Support

for further assistance.

What should I do then??

---

### Post by Miss_Piggy on 2007-04-27
Hello,

I think I got the solution... 


If you read all the posts about this topic, you will realize that
at the end of the installation you should manually edit the 
script $(MATLAB)/bin/.matlab7rc.sh 

1) 1st SOLUTION

you should add 

"
export LD_ASSUME_KERNEL=2.4.1
                                                               "

--> From Mathworks 
[http://www.mathworks.com/support/solutions/data/1-QVND8.html?solution=1-QVND8](http://www.mathworks.com/support/solutions/data/1-QVND8.html?solution=1-QVND8) 

but this can even not work because of the different location of the shared libraries, in this case the libc.so.6 

and below there is the nicest message that you can get from the shell 

# expr: error while loading shared libraries: libc.so.6: cannot open shared object file: No such #file or directory
#/bin/uname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

#Sorry! We could not determine the machine architecture for your
#host. Please contact:

#MathWorks Technical Support

#for further assistance.

---> it&#347; better having a look on this LD_ASSUME_KERNEL
[http://people.redhat.com/drepper/assumekernel.html](http://people.redhat.com/drepper/assumekernel.html) 
It gives hints where to look for shared libraries...and of course this is 
strongly dependent by the architecture.... uhmmmm  :-k 


ok 

2)2nd solution  

adding at the beginning of the same file 

"
export MALLOC_CHECK_=1 
                                                 "

any heap problem will be detected and a message will be printed, but the program will not be
aborted.
---> [http://www.die.net/doc/linux/man/man3/malloc.3.html](http://www.die.net/doc/linux/man/man3/malloc.3.html) 


ok, and then relax, have a beer
and run matlab with no problems! 

Bye Bye

Susy

---

