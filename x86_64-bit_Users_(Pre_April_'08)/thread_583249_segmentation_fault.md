---
title: "segmentation fault"
date: 2007-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2007-10-20
What is a segmentation fault?

---

### Post by John.Michael.Kane on 2007-10-20
> **go_beep_yourself said:**
> What is a segmentation fault?

I will try to answer your question. 


This from my limited reading on programing. I'm sure some of those more knowledgeable in programing etc can offer a better understanding.

A segmentation fault (sometimes shortened to segfault) is a particular error condition that can occur during the operation of computer software.

A segmentation fault occurs when a program attempts to access a memory location that it is not allowed to access, or attempts to access a memory location in a way that is not allowed (for example, attempting to write to a read-only location or during execution of a C program you freed memory and then within the scope of the same program try again to use the same memory,).Thus leading to a segfault. 

This is usually due to the fact that until the completion of the program the memory utilized is not returned to the operating system.

Segmentation faults may also occur in case of hardware errors, f.e. hard-disk or Memory failure. to find out, try running memtest and/or any hard-disk diagnostic tools from the manufacturer.

In the end this is usually caused by improper usage of pointers in the source code, dereferencing a null pointer, or "in C" mistakenly using a non-pointer variable as a pointer.

Hope this helps.

---

