---
title: "Compiling with 64 bit compiler"
date: 2009-01-16
forum: x86 64-bit Users
---

### Post by sasanpad on 2009-01-16
Hi All,

I've just installed 64 bit Ubuntu on my laptop and I have a few questions about it.

1. Can I still compile c++ code with the 64 bit version and run them on 32 bit systems?
2. Do I have to change the way i program with c++ integers and floats , etc?
3. Can I run 32 bit versions of old C++ correctly on 64 bit?
4. Is it possible to have 32 bit compilers on 64 bit OS?

Thanks in advance

Sassan

---

### Post by jespdj on 2009-01-16
> 1. Can I still compile c++ code with the 64 bit version and run them on 32 bit systems?
Yes, but you'll have to setup the compiler correctly so that it produces 32-bit binaries, and you need 32-bit development versions of the libraries that you're using. Sorry, I don't know the details.

> 2. Do I have to change the way i program with c++ integers and floats , etc?
Not really. With the GNU C++ compiler (g++), an int is still 32 bits. There are some other issues; pointers are 64 bits instead of 32 bits, for example.

> 3. Can I run 32 bit versions of old C++ correctly on 64 bit?
I don't know what you mean by this. You can run 32-bit programs on 64-bit Ubuntu. Some source code is badly written and won't work correctly if compiled for 64-bit without modifications.

> 4. Is it possible to have 32 bit compilers on 64 bit OS?
Yes, but you don't need the compiler itself to be 32-bit; you just need to set it up to produce 32-bit code.

---

### Post by sonofusion82 on 2009-01-16
1 & 4. a quick google shows leads me to [http://www.cyberciti.biz/tips/compile-32bit-application-using-gcc-64-bit-linux.html](http://www.cyberciti.biz/tips/compile-32bit-application-using-gcc-64-bit-linux.html)
use gcc -m32 option to compile for 32-bit binaries


2. linux uses the LP64 programming model, which mean integer remains 32-bit while long and pointers are 64-bit. see this for a 64-bit porting guide: [http://www.ibm.com/developerworks/library/l-port64.html](http://www.ibm.com/developerworks/library/l-port64.html)

3. yes, if you have the 32-bit libraries installed, you can run 32-bit executable on 64-bit linux.

---

### Post by sasanpad on 2009-01-19
thanks for the replies.

---

