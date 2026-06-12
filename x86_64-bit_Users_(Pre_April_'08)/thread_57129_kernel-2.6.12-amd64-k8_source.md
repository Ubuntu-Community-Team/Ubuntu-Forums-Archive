---
title: "kernel-2.6.12-amd64-k8 source"
date: 2005-08-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by jewishj on 2005-08-15
Hi,

I have an acer ferrari 4005WLMi and I was following the steps as described at [http://pages.cpsc.ucalgary.ca/~weckerl/ferrari_ubuntu_64.html](http://pages.cpsc.ucalgary.ca/~weckerl/ferrari_ubuntu_64.html)

I used Tamir's repository to install the 2.6.12-amd64-k8 kernel from the image.  I'm now trying to install ndiswrapper and the only amd64 build I can find is one i need to make myself (I cannot find it in synaptic as described in the site above).  The problem is that the "make" command fails because it cannot find the kernel source.  I cannot find it either, anywhere, on the computer or online.  Where can i find this source, and once I do find it, what do I do with it.  I am a noob at this, so please be as specific as possible with commands/etc. included.

Thank you so much
-Jordan

---

### Post by tymek666 on 2005-08-16
Isn't better to compile kernel by yourself? I always had problems with kernel images...

---

### Post by jewishj on 2005-08-16
The only problem I am having is that ndiswrapper can't find the kernel source and errors out because of this when i try to run "make install".

And also, I'm not familiar enough with this stuff to compile my own kernel.  Wouldn't that require a knowledge of every driver I need and so forth to work with Ubuntu on my specific machine?

The actual error message I get is

"Can't find kernel sources in /lib/modules/2.6.12-amd64-k8/build;
give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check]: error 1"

---

### Post by tymek666 on 2005-08-16
Well, you have to download alsko kernel source, idon't know if they are present in Tamir reps, but you can alway download them from kernel.org...
Compiling kernel isn't very difficult, especially when you can use oldconfig.
You can find more information in this thread:
[http://www.ubuntuforums.org/showthread.php?t=43065](http://www.ubuntuforums.org/showthread.php?t=43065)

---

