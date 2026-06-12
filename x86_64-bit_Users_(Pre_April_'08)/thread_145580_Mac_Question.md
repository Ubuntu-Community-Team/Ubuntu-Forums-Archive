---
title: "Mac Question"
date: 2006-03-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by JDavid5381 on 2006-03-16
Alright, so Im new to Ubuntu, Linux and all that stuff.  I've went from being a Mac person to PC about two months ago.  I'm curious, and this probably comes across as a really dumb question to anyone who knows computers really well.  Is any software thats compatible with Ubuntu (Linux) on a PC, also always compatible with Ubuntu (Linux) thats running on a Mac?  OR does the whole machine level programming differences between the two interfere?  Just curious, as someone who's new to computers, no rush to answer the question. . .

Peace out,
James

---

### Post by ssam on 2006-03-16
i hope this goes some way towards explaining. feel free to ask more questions.

most linux programs (and the linux kernel itself) are written in a language called C. C source code must be compiled into a binary before it can be run. The binary is in a machine code with instructions specific to a processor type. intel and amd make processors the use the x86 instruction set, ibm make processors that use the powerpc instuction set (its a bit more complecated than this, but thats the basics). when you compile a C program you can do it for x86 or powerpc (or many other instuction sets). the compiled binary will then only run on that system.

with closed sourced software you only ever see the binary, so it will only work on one type of system. with open source you can always get hold of the source code and compile for you platform.

there are more issues in programming that means you have to change your source code to move between different operating systems (eg windows to linux). also you sometimes get bugs that happen only happen on powerpc but not x86.

the situation is also different for different programming languages. assembly code cannot be moved between systems. java gets compiled into a bytecode that runs on any system with a java virtual machine. intepreted languages (eg, perl python) just run on any system (in theory) with out any compiling.

so as a pratical example. firefox is writen mostly in C. if you just copy the files from ubuntu on a pc to ubuntu on a mac they will not work. but if you down load the source code and compile it for ubuntu on a mac then it will work. and the friendly ubuntu developers compile all the thousands of programs for ubuntu for x86, x86-64 and powerpc (and sparc i think), so we never need to worry about it.

---

### Post by engla on 2006-03-16
Ubuntu is really nice to us users with macs, mainly because of Debian is my guess.

Debian makes sure all software that go into the distribution compile for six different architectures. This is a pretty steep demand to even get accepted, but it makes sure it always works, and that the whole debian system is available for all those architectures.

Ubuntu takes its packages (software) from debian, [but has chosen to care only about three architectures; i386, amd64 and powerpc]. Basically, everything that's possible to put on all architectures, is there. And that's great for everyone.

---

### Post by rfruth on 2006-03-16
Are we going at this from a psysocial (sp?) point of view or from where the rubber meets the road cause if someone can compile C code ...

---

