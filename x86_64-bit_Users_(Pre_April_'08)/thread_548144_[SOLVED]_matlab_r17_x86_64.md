---
title: "[SOLVED] matlab r17 x86_64"
date: 2007-09-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by o3rat on 2007-09-10
Im running 2.6.22-9-generic. I was able to install this 32bit version of matlab by passing '-glnx8x -nocp' arguments during the install, but now when I try to run it i get the following ```
~$ matlab 
---------------------------------------------------------------------------
Warning: Cannot locate Java Runtime Environment (JRE) . . .
 
         1. Either a correct JRE was not available for redistribution when
            this release was shipped, in which case you should refer to the
            Release Notes for additional information about how to get it.
 
         2. Or you have tried to use the MATLAB_JAVA environment variable
            to specify an alternate JRE, but MATLAB cannot find it.  Please
            run 'matlab -n' to determine what value you are using for
            MATLAB_JAVA and fix accordingly.
---------------------------------------------------------------------------

    matlab: No MATLAB bin directory for this machine architecture.


   ARCH = glnxa64

 
```my java is ```
~$java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0-b105, mixed mode)
 
```Any ideas on how to get around this , other than buying a new 64 bit version?

---

### Post by o3rat on 2007-09-11
Solved! Turn out if I run matlab with the '-glnx86' flag it runs no problem.

---

