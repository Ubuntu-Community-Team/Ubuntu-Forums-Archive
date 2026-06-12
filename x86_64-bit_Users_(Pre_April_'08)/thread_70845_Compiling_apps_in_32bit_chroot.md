---
title: "Compiling apps in 32bit chroot"
date: 2005-10-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by mthaddon on 2005-10-01
Anyone know how to install an app from source in the 32bit chroot if I need to use the linux-headers as part of the compilation?

As an example, my uname -a from within the chroot shows:

Linux ubuntu 2.6.10-5-amd64-k8 #1 Fri Sep 23 14:14:36 UTC 2005 x86_64 GNU/Linux

But I can't install the linux-headers-2.6.10-5-amd64-k8_2.6.10-34.6_amd64.deb package because it gives me an error. 

Alternatively, can I somehow fool my source compilation into using other headers (such as k7 rather than k8 )?

Thanks, Tom

---

### Post by rplantz on 2005-10-01
Tom,

I'm new to the chroot stuff, but I don't know why you would want to do this. Are you trying to create a 32-bit application?

When I first moved to the amd64, I had a bunch of assembly language programs that needed to be built in the 32-bit mode. Some include C/C++ functions, so I needed to also compile in 32-bit. Basically, I needed to create 32-bit applications.

First, I installed ia32-libs and ia32-libs-dev using Synaptic.

Then the compiler needs the -m32 switch.

For the sake of completeness, the assembler (gas) needs the --32 switch. When I have a mixture of assembly language and C/C++ files, I first create object files (-c switch to compiler) for each source file. Then I use gcc with the -m32 switch to link them. Since I am linking object files, gcc goes directly to ld. The advantage of using gcc for linking is that it automatically links in the required C/C++ libraries. If you explicitly use ld, you need to explicitly specify all the libraries.

Bob

---

### Post by mthaddon on 2005-10-02
Thanks, that sounds good.

Tom

---

