---
title: "Is a C++ app i make and build, compatable on a 32bit system?"
date: 2008-06-28
forum: x86 64-bit Users
---

### Post by Mr.Useless on 2008-06-28
Firstly, i am using CodeBlocks 64bit on Ubuntu, and im fiding how it works fune, just when i send my friend the binary, or a.out file he cant run it, it makes the error:
 Cannot execute binary file,

he knows his linux so unless hes doing something absolutly obliviously wrong, i doubt he isnt.

Anyone got any answers on this, i could run his binary fine btw

Also, a noobish maybe, but, when i build the file, is it the binary that is my prgram that i release? its all confusing, in windows we all know thats its the .exe but in this a lot of new filetypes have come out ive never used before.

any help is appretiated

Mr.Useless

---

### Post by pytheas22 on 2008-06-28
A binary built on a 64-bit system can't run on 32-bit--but a 32-bit binary *can* run on 64-bit.  If your friend has a 32-bit system, the binary you send him is not going to work.
> 
is it the binary that is my prgram that i release? in windows we all know thats its the .exe but in this a lot of new filetypes have come out ive never used before.


Your executable can be named whatever you want in Linux--unlike Windows, it doesn't need to have a certain extension in order for the system to know how to handle it.  I'm not familiar with CodeBlocks or the kinds of output files that it gives, but basically any kind of executable file on Linux can be run with:
```

./[filename]
```

---

### Post by vishalrao on 2008-06-29
> **pytheas22 said:**
> A binary built on a 64-bit system can't run on 32-bit

it can if you provide compiler flags to build 32 bit and have 32 bit libraries installed.

for example "gcc -m32" and installed packages like ia32-libs, gcc-multilib (i forget what you need)...

---

### Post by Mr.Useless on 2008-06-29
If i used the 64bit software to create the course n whatever, but then copied the source into a 32bit compiler would this not work either?

Thanks

---

### Post by pytheas22 on 2008-06-29
> If i used the 64bit software to create the course n whatever, but then copied the source into a 32bit compiler would this not work either?


Yes.  As vishalrao says above, if you tell the compiler on your 64-bit system to build a 32-bit binary, then you'd get an executable that would be compatible with a 32-bit system (I should have been clearer; I didn't mean to imply that any binary built on a 64-bit system would not work on 32-bit or that it's not possible to build a 32-bit binary in a 64-bit compiler).

---

### Post by Mr.Useless on 2008-06-29
Ok thanks

helped a lot

---

### Post by stchman on 2008-06-30
> **Mr.Useless said:**
> Firstly, i am using CodeBlocks 64bit on Ubuntu, and im fiding how it works fune, just when i send my friend the binary, or a.out file he cant run it, it makes the error:
 Cannot execute binary file,

he knows his linux so unless hes doing something absolutly obliviously wrong, i doubt he isnt.

Anyone got any answers on this, i could run his binary fine btw

Also, a noobish maybe, but, when i build the file, is it the binary that is my prgram that i release? its all confusing, in windows we all know thats its the .exe but in this a lot of new filetypes have come out ive never used before.

any help is appretiated

Mr.Useless

Is he running 32 bit?

You can send him the source and a script to compile it on his system.

---

