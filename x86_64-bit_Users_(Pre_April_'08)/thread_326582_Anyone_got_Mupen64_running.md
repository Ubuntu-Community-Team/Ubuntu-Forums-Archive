---
title: "Anyone got Mupen64 running?"
date: 2006-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by ghoster on 2006-12-27
Can anyone give me some rough instructions for compiling mupen64 in edgy 64?
At the moment i get this:

```

~/Desktop/mupen64_src-0.5$ make
gcc -DX86 -O3 -fexpensive-optimizations -fomit-frame-pointer -funroll-loops -ffast-math -fno-strict-aliasing -mcpu=athlon -Wall -pipe   -c -o main/rom.o main/rom.c
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
main/rom.c:1: error: CPU you selected does not support x86-64 instruction set
make: *** [main/rom.o] Error 1


```

---

### Post by Jason_25 on 2006-12-27
Is there any reason your compiling it?  Have you tried running the 32-bit version?  It runs fine on my 64-bit kubuntu and ubuntu pcs, aside from the occasional sound problem.

---

### Post by ghoster on 2006-12-27
When I try to run the 32-bit version I get this:
```

./mupen64: error while loading shared libraries: libgtk-x11-2.0.so.0: wrong ELF class: ELFCLASS64

```

---

### Post by Jason_25 on 2006-12-27
Do you have ia32-libs and ia32-libs-gtk installed?

---

### Post by ghoster on 2006-12-27
Yep, but i'd forgotten i32-libs-sdl. 32 bit works now, thanks.

Still interested in knowing if anyone has successfully compile for 64 bit.

---

### Post by StandardBlueCaboose on 2007-05-09
Just thought I'd mention that I was also unable to get mupen64 to compile in a 64-bit environment.

> 	Yep, but i'd forgotten i32-libs-sdl. 32 bit works now, thanks.

That should be ia32-libs-sdl, I do believe.

I'd also like to say that mupen64 would not run if I had the CPU Core set to "Dynamic Recompiler," which is the default setting. I had to set it to either "Interpreter" or "Pure Interpreter."

I have some questions as well.

None of the "Test" buttons yield any results other than the audio plugin. I assume the others are supposed to at least do *something*. I am unable to configure the input plugin, which is my only real problem. I can configure blight's plugin but that does not work.

Any ideas?

Edit: Fixed my problem within seconds of posting, nevermind... The "Test" buttons still do nothing, however.

---

### Post by Baldwin on 2007-05-10
> **ghoster said:**
> Can anyone give me some rough instructions for compiling mupen64 in edgy 64?
At the moment i get this:

```

~/Desktop/mupen64_src-0.5$ make
gcc -DX86 -O3 -fexpensive-optimizations -fomit-frame-pointer -funroll-loops -ffast-math -fno-strict-aliasing -mcpu=athlon -Wall -pipe   -c -o main/rom.o main/rom.c
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
main/rom.c:1: error: CPU you selected does not support x86-64 instruction set
make: *** [main/rom.o] Error 1


```


You "-mcpu=athlon" is confusing it, since athlon's don't support 64-bit. Not sure of the correct setting to use, possibly "-march=x86_64"

---

### Post by kuja on 2007-05-10
Remove -mcpu, try using 
"-march=k8"

---

### Post by Crube on 2007-06-18
I tried everything and tested things for hours... then I accidently run mupen64 in sudo and evrything workder perfectly

---

### Post by Mochino on 2007-06-18
i was not able to compile it, instead i got a direct file which i had to run, from the website.

---

### Post by Bachstelze on 2007-06-18
Yes, I have it running very well here on Gentoo. Not tried it in Ubuntu, though...

---

