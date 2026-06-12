---
title: "g++ giving strange error messages"
date: 2006-09-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by donz on 2006-09-07
Hi!

I am having a problem with g++ [g++ (GCC) 4.0.3 (Ubuntu 4.0.3-1ubuntu5) ] On the 64-bit version of Dapper.

](*,) It is very hard to find typos and other errors with error messages like this:

	big_file_test.cpp: In function â:
	big_file_test.cpp:64: error: invalid conversion from â to â
	big_file_test.cpp:64: error:   initializing argument 1 of â
	big_file_test.cpp:64: error: â was not declared in this scope
	/usr/include/stdlib.h:640: error: too few arguments to function â
	big_file_test.cpp:69: error: at this point in file
	/usr/include/stdlib.h:640: error: too few arguments to function â
	big_file_test.cpp:74: error: at this point in file
	big_file_test.cpp:77: error: â was not declared in this scope
	/usr/include/stdlib.h:640: error: too few arguments to function â
	big_file_test.cpp:80: error: at this point in file


I have tried re-installing gcc, but that doesn't help.  

The problem only seems to occur with c++ code.  It works fine with straight c code.

Has anyone encountered this (and hopefully fixed it)?

Thanks

Donz

---

### Post by FluffyElmo on 2006-09-07
This is a guess. 

It may be due to a difference in data sizes? AMD64 uses 64 bit pointers, 64 bit resiters and 128 bit floating point registers. If your code assumes everything is 32bit and tries, for instance, to pass a 32bit pointer to a method expecting a 64bit pointer then you're going to have problems compiling it for 64bit. 

You should be able to compile 32bit code on a 64bit system which may solve your problem...or you could look at making your code 64bit compatible as well.

Just a guess, I'm a Java guy so don't usually worry about architecture differences but C++ is closer to the metal doesn't insulate you from them.

---

### Post by Mongoose on 2006-09-07
What locale are you using?  Is it actually outputting 'â'?  Try converting the file to ASCII or UTF-8 with proper symbol names.

---

### Post by donz on 2006-09-07
The locale is the default for US English.

The output is exactly as I showed (used copy/paste).  There really is an 'a-circumflex' in the error messages.

The actual errors were associated with 

exit() -- should have been exit(0),

and a call to rand_r() with a constant argument rather than a reference to an unsigned int.

This truly seems to be a bug in g++ as distributed with Dapper.

My thought is that it may be using a 32-bit library somewhere that it should be using a 64-bit library.

Unfortunately, I don't have the time to download the gcc source and re-build the compiler myself.:(

---

### Post by Mongoose on 2006-09-07
I don't know what to say.  I've been using the same compiler for quite a while now.  All I can say is double check your packages.  I assume you have all the matching cpp, g++, gcc, binutils, etc.  I would try to build with 'gcc -lstdc++ ' or whatever other extra options you need in place of g++ first.  I'm not able to legally operate heavy machinary at the moment, so I can't think of much else.  ;)

---

### Post by Sloth on 2006-09-08
This drove me nuts.  Add this to your environment:

LC_MESSAGES=en_US

---

### Post by Mongoose on 2006-09-09
So it was locale?  Thanks I'm not crazy.  ;)

---

