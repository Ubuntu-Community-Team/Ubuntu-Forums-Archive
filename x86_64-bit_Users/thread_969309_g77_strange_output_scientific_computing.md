---
title: "g77 strange output scientific computing"
date: 2008-11-03
forum: x86 64-bit Users
---

### Post by 0101 on 2008-11-03
Hi all,

I am currently using g77 to compile a small program that I wrote for a calculation. The problem is that when I compile and execute the code on my Intel i386 based laptop I get the result I should get. When I compile the same code on my x86-64 AMD machine in my office I get strange results. The code will compile with no errors but the output is incorrect.

Here is the question: Assuming that the code compiles on the 64bit arch.,  is there some flag I need to set to tell the compiler that I would like the same result as on the 32 bit arch.?

thanks for the help.

---

### Post by chrisdeckard on 2008-11-03
I'd say you're asking in the wrong place.  I'd hit up the g77 mailing lists.  My assumption is it has something to do with the "size" of integers and other things.  Your code probably depends on sizes of specific things and they are different between 32bit and 64bit.

-Chris

---

### Post by swf22 on 2008-11-10
Have you tried using gfortran rather than g77? gfortran works fine for me with 64-bit Intrepid. I haven't installed or tried g77.

---

### Post by 0101 on 2008-11-14
Hey thanks for the replies. I will definitely check out the mailing list for g77. Also, I have tried gfortran and the same thing happens. I am guessing that it is related(as said previously) to how 64 bit treats arithmetic operations and the size of "things" like integers. In the gfortran man page you can set a flag that will change the size of real, integers etc to 8 bytes, if you haven't done so in the code, which is what some people say should work for 64 bit operations when the code is executed, but still no luck for me setting when those are flags. 

I have tried  also setting the "-m64" and "march=native" flags with no luck.

Well off to the mailing list.

Thanks again. Any further ideas/comments will be appreciated.

---

