---
title: "[SOLVED] Need advice 32 vs. 64 bit"
date: 2008-10-20
forum: x86 64-bit Users
---

### Post by Arrowx7 on 2008-10-20
Hi Everyone,
I wanted to get some advice on installing 64 vs. 32 bit ubuntu.

This machine has 4gb of ram (potentially more later if we decide 64bit) with nvidia card.  

This will be used for a lot of mathematical processing - solving biochemical structures.  However, the linux software used to do this isn't too ubuntu-friendly.  We already set up a 32-bit system, but had some issues with finding libraries.

Our software builds upon Python, the Boost.Python Library, and C++ to provide an environment for automation and scientific computing.  Another piece of software is built on tcl/tk.

I know 64bit is probably better for high-end computing, but I was wondering how much trouble I'll run into installing C++/python/tcl/tk + dependent libraries to run the software.  I guess we can't run any 32-bit libraries on a 64-bit machine?

If anyone share some experiences, comments, or give suggestions, it would be much appreciated!

Thanks so much!

---

### Post by Sef on 2008-10-20
> I know 64bit is probably better for high-end computing, but I was wondering how much trouble I'll run into installing C++/python/tcl/tk + dependent libraries to run the software. I guess we can't run any 32-bit libraries on a 64-bit machine?


It can.   Also so a search.  This question is asked a lot here.

---

### Post by Robstarusa on 2008-10-20
Arrowx>  Post here if you have problems with libraries.  I have resolved some issues myself without too much trouble.

---

### Post by insane_alien on 2008-10-20
64-bit in linux is actually more compatable than 32-bit. its only really windows that has problems with 64-bit.

---

### Post by wangmaster on 2008-10-20
> **insane_alien said:**
> 64-bit in linux is actually more compatable than 32-bit. its only really windows that has problems with 64-bit.

Yes and no.  I'd argue Windows has less problems than Ubuntu has.  The problem with Windows Vista x64 and 32-bit compatibility primarily lies in driver support.  This same compatibility problem technically exists with Linux.  You can't link 32-bit modules into a 64-bit kernel.  However, on Linux, since most drivers are in source format this is less of an issue.  Additionally, windows applications seem to enjoy sticking things into the kernel rings much more than things do in the linux world which makes this compatibility issue much more noticeable on Windows.

However, Windows WoW64 architecture, ruling out kernel level drivers/modules, is FAR FAR FAR more complete than ubuntu's sorely lacking ia32 library availability.  getlibs helps, but to me, the lack of a distribution provided complete 32-bit runtime ends up resulting in a frankenstein OS hackjob.

Ubuntu really needs a more complete 32-bit/64-bit multiarch linux enviroment.  Hell, it's not just ubuntu, linux distributions in general are sorely lacking.  Unfortunately it's a drawback of the linux opensource momentum where applications that are non-free or binary only are treated as second class citizens (there's both good and bad to this mentality).

---

### Post by mad_max0204 on 2008-10-20
@Arrowx7

Anyone who ever tried to setup on a 64bit os would tell you to go for it.
Almost everything can be installed without any hustle. I'm using my computer for some hardcore procesing and I'm happy with 64bit os.
Go for it and dont think about it.

---

### Post by sethvath on 2008-10-20
If you have plans to upgrade your ram to 8/16gb go with x86_64. It will be a hassle reformating 32bit ubuntu for 64bit when you decide to upgrade. 

As you mentioned, the machine is probably a dedicated work station running your custom academic software and most system libraries are already well supported on the 64 bit version. To be certain, test out the software on a spare computer and see which libs are required. 

If your custom software is not top secret material, post it here and I'm sure anyone here can help to figure out what to do to get it working on 64bit.

---

### Post by Arrowx7 on 2008-10-20
Thanks a lot guys,
I really appreciate your confidence and support.

I'll give it a shot!

---

