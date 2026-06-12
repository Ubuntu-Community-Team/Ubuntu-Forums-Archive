---
title: "mex compilation in Matlab"
date: 2009-03-03
forum: x86 64-bit Users
---

### Post by jaromir_jagr on 2009-03-03
Hi,

I'm running Ubuntu Linux in 64-bit mode.  Since there's no native 64 bit support for Linux, I've been running Matlab with 32 bit emulation in the following way

>> linux32 matlab

So far, this has worked fine.  But now, I'm trying to use a new package which requires me to compile a mex file and I can't get it to work.  

I get an error saying:

/usr/bin/ld: cannot open linker script file /usr/local/matlab/extern/lib/glnxa64/mexFunction.map: No such file or directory
collect2: ld returned 1 exit status

    mex: link of 'normxcorr2_mex.mexa64' failed.

make: *** [normxcorr2_mex] Error 1

My matlab/extern/lib directory only has glnx86, not glnxa64.  So I tried creating a symbolic link called glnxa64 and have this point to glnx86 but this didn't work. 

Does anyone know how I can compile this mex file to work under 32-bit emulation on a 64-bit system?

Thanks,

Andrew

---

### Post by mionescu on 2009-03-03
What do you mean by there is no native 64-bit support? I know there is because I am running the native 64-bit Matlab for Linux.

---

### Post by jaromir_jagr on 2009-03-04
I'm sorry, I was referring to the Academic version of Matlab.  As far as I know, there is only a 32 bit version of this available.

---

### Post by mionescu on 2009-03-04
Sorry, it seems that you are right. 
I am not sure then on how to compile the mex files. The problem is that you are trying to compile 32bits on a 64bits machine. Maybe you can set this up using "mex -setup" in the Matlab prompt, but it is just a wild guess.

---

### Post by Carlos_pe on 2009-07-22
hi every Matlab users,

I do use matlab Version 7.4.0.336 (R2007a).  I didn't resolve the problem of compiling .

the following error appears when emlmex is used:

>> emlmex emcrand
??? Compilation failed: emcrand_make.sh: line 33: gmake: command not found

Error in ==> emcrand Line: 1 Column: 1
C-MEX generation failed: C-MEX generation report at '/home/salim/work/embedded/emcprj/mexfcn/emcrand/html/emcrand_report.html'

any suggestion are welcome and very appreciated.

thanks,
Carlos

---

