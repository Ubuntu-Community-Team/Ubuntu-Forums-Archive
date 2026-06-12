---
title: "symbol lookup error: &lt;libName64.so&gt;: undefined symbol"
date: 2009-08-13
forum: x86 64-bit Users
---

### Post by martelc on 2009-08-13
Hello,

I am porting a library to Ubuntu Server 64-bit.  I have built the library, loaded the library and called into the library.  However, when there is an attempt to construct one particular object, I get a symbol lookup error with details about the undefined symbol.  When I "ldd -d" the shared object, there are no undefined symbols.  When I "nm -a | grep <undefined_symbol>", the symbol is defined.

Are there any other utilities available for use to help diagnose this issue?  Do you have any other hints?

Thanks,

martelc

---

