---
title: "Cross Compile Kernel from x86_64 to x86 - How in Ubuntu?"
date: 2007-11-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by ilikenwf on 2007-11-25
I have a killer custom kernel team that I've been working with over at the gentoo forums, and I was named the Debian/Ubuntu maintainer. Unless you want to take 3.5gb of space up on your hard drive for cloning the git tree, you should help me so that you can try this (superfast, bleeding edge, stable) kernel. I have to build these every so often, and I have two questions.

1. Most Imporatantly, could someone tell me what packages I need to cross-compile, and furthermore, could you tell me how to cross-compile the kernel for x86 with make-kpkg? (I run a 64 bit kernel)

2. Secondly, how is it that the ubuntu generic kernel is so small, and the one I built is 150mb larger? I used the same config file. Any ideas on that one?

---

### Post by Yellow Pasque on 2007-11-25
I won't claim to be an expert, but I have compiled a sound support library for the 32-bit flash plugin. I used synaptic to get the corresponding multilib package for the version of gcc I was using and then used the -m32 flag in the compilation step.

I hope that helps :neutral:

> 2. Secondly, how is it that the ubuntu generic kernel is so small, and the one I built is 150mb larger? I used the same config file. Any ideas on that one?
Are you using the new 2.6.24 kernel? If so, it's probably because they added A LOT of features and drivers to it. Ubuntu is still using the 2.6.22 kernel.

---

### Post by ilikenwf on 2007-11-25
It would probably be easiest if I'd just install gutsy32 on a qemu machine...Although that takes more time and space...

Thanks for attempting to help me ;).

So far, I don't know if I need wrappers or not, and I don't think that making my config file with ARCH=x86 is a good idea, as I would have to choose a specific processor. That said, can someone here who is wiser and more skilled at these things advise me as to what package(s)/code I need to build, and the string needed to compile a 32 bit deb kernel package on a 64bit machine (I am running gutsy 64).

---

### Post by ilikenwf on 2007-11-25
Anybody know why the compiler isn't stripping the debugging symbols out of anything, even though I have told it to? Help please...I need to figure out how to cross compile using make-kpkg on my 64bit install to compile for a 32bit kernel. I don't have any experience with cross compiling. Any and all help would be appreciated.

---

### Post by ilikenwf on 2007-11-26
I got the kernel small enough....the deb is 18.5mb for x64. I just need help cross compiling so I don't have to do a qemu install.

Somebody, please help me.

---

### Post by Yellow Pasque on 2007-11-26
I take it my earlier suggestion didn't work :(

Instead of cross compiling, why not just set up a 32-bit chroot/kernel on your current install. Google around for it. It's pretty easy to use, though it does require a decent bit of hard disk space.

---

### Post by ilikenwf on 2007-11-26
> **Temüjin said:**
> I take it my earlier suggestion didn't work :(

Instead of cross compiling, why not just set up a 32-bit chroot/kernel on your current install. Google around for it. It's pretty easy to use, though it does require a decent bit of hard disk space.

I'm trying to avoid huge disk usage...

---

