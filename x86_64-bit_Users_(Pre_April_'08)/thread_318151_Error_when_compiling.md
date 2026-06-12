---
title: "Error when compiling"
date: 2006-12-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by amanita on 2006-12-13
I would like to install Epson Perfection V 100 scanner on my 64bit Edgy, but provided packages are in i386rpm and in source code only.

So I tried to compile and then make from the source according to readme file with this output: 

In file included from imgstream.cc:31:
imgstream.hh:46:18: error: ltdl.h: No such file or directory
imgstream.hh:115: error: 'lt_dlhandle' does not name a type
imgstream.hh:116: error: 'lt_ptr' does not name a type
imgstream.hh:118: error: 'dl_handle' does not name a type
imgstream.hh:120: error: 'dl_ptr' does not name a type
imgstream.hh:121: error: 'dl_handle' has not been declared
imgstream.hh:124: error: 'dl_handle' does not name a type
imgstream.cc:155: error: 'dl_handle' in class 'iscan::imgstream' does not name a type
imgstream.cc:174: error: 'dl_ptr' in class 'iscan::imgstream' does not name a type
imgstream.cc:181: error: 'int iscan::imgstream::dlclose' is not a static member of 'class iscan::imgstream'
imgstream.cc:181: error: 'dl_handle' was not declared in this scope
imgstream.cc:182: error: expected ',' or ';' before '{' token
imgstream.cc:211: error: 'dl_handle' in class 'iscan::imgstream' does not name a type
make[2]: *** [libimage_stream_la-imgstream.lo] Error 1

I suppose it need imgstream library, but cannot find nothing similar to it. 
Could anyone help?

---

### Post by coren_ita on 2007-02-12
I've got the same error on dapper 32 bit. Someone has a clue? :(

---

### Post by amanita on 2007-02-13
Looks like you don't have libltdl3-dev installed. But try to convert rpm packages to deb - that worked for me.

---

