---
title: "Java installation problems..."
date: 2005-11-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by grizzly451 on 2005-11-29
I've been having a lot of problems trying to get any version of Java to run with ubuntu or kubuntu.  I followed the directions of wiki.ubuntu.com/JavaPPC in downloading the package from IBM and the installation procedure.   Everything works fine until the end when I get a message different from what you are suppose to get and from the error messages listed online.

You are suppose to get this:

$ java -showversion 
java version "1.5.0"
Java(TM) 2 Runtime Environment, Standard Edition (build pxp32dev-20050923b)
IBM J9SE VM (build 2.3, J2RE 1.5.0 IBM J9 2.3 Linux ppc-32 j9vmxp3223-20050915a (JIT enabled)
J9VM - 20050914_03248_bHdSMR
JIT  - 20050914_1758_r8
GC   - 20050907_AB)
JCL  - 20050915

If you see this output, java has been successfully installed. 

But I get this:

Using '/installation directory of where java' went for java

and thats it, java isn't installed and each time I run the package I get that same result.  I've tried as root and as myself.

So I'm pretty confused...

---

### Post by robotgeek on 2005-11-29
is that the exact message you get?

---

### Post by tijs on 2005-11-30
I have a similar problem, that is everything seems to go OK, but when I want to verify which version of Java I am using, by issuing this command:

java -showversion

it says the command cannot be found.

Openoffice still doesn't work because of some Java dependencies I suppose:

> /usr/lib/openoffice2/program/javaldx: error while loading shared libraries: libuno_sal.so.3: cannot open shared object file: No such file or directory
/usr/lib/openoffice2/program/soffice.bin: error while loading shared libraries: libvcl680lp.so: cannot open shared object file: No such file or directory


---

