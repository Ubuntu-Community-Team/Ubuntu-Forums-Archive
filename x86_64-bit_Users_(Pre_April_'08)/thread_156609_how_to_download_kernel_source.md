---
title: "how to download kernel source"
date: 2006-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by eleach on 2006-04-07
I'm trying to install the nvidia driver:

   NFORCE-Linux-x86_64-1.0-8178-pkg2.run.

It is giving me the error:

   Unable to find kernel source tree

My kernel is:

   2.6.12-9-amd64-generic

How do I download this kernel source?

Thanks,

Ed

---

### Post by skylark on 2006-04-07
Hi eleach,

Normally you can find these with synaptic (or apt-get/aptitude in a terminal).

I like the termal, so here's how you might find them. Open a terminal (under Applications->Accessories) and type in:```
 apt-cache search 2.6.12-9
``` This shows you all the packages available to you that match that kernel version. You should be able to see the source package in the list (it is called "linux-tree-2.6.12") however in this case I think you mightly only need "linux-headers-2.6.12-9-amd64-generic" which are just the kernel header files. Packages "linux-restricted-modules-2.6.12-9-amd64-generic" and "linux-restricted-modules-2.6.12-9-amd64-generic-nvidia-legacy" look interesting, I don't know if you need these (I don't have an NVIDIA card so haven't looked at what the drivers need). Anyway to install any of these just type: ```
sudo aptitude install <package name>
``` where <package name> is linux-headers-2.6.12-9-amd64-generic or linux-tree-2.6.12 etc.

Good luck installing those drivers!

Edit:
You might find following a howto like: [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia) more helpful. Or even [https://wiki.ubuntu.com/NvidiaManual](https://wiki.ubuntu.com/NvidiaManual) which describes what you want to do I think (be careful of the exact kernel versions used in those wiki pages, you will have to update those numbers to 2.6.12-9 and AMD64).

---

### Post by eleach on 2006-04-07
Thanks, skylark. Will try what you suggest.

I'm not even sure I have the right driver. What is the difference between Graphics Drivers and nForce drivers?

Ed

---

### Post by skylark on 2006-04-07
I believe nForce is to do with a chipset on your motherboard (interfaces with things like ethernet/sound card various buses etc) while the graphics drivers are limited only to your graphics card :-) You shouldn't need the nForce stuff - Linux already has drivers built in to handle that side of things and they work okay.

If you just want to get video drivers that work well for your Nvidia card, I recommend you look at [http://www.ubuntuforums.org/showthread.php?t=75074&highlight=8178](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=8178) and try method 1 (it should still work I think). 

Or maybe instead carefully follow that first wiki page: [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)
Where it mentions that you have to install "linux-restricted-modules-386" you would intead install "linux-restricted-modules-amd64-generic" etc. So don't follow these guides word by word everywhere.

PS: I can't test any of this since I don't have an Nvidia card. Maybe someone who has gone through all this can help you further.

---

### Post by eleach on 2006-04-09
Skylark,

Got with the BinaryHowTo.

Next I need to set up TwinView for dual monitors, but I don't have time to get to it today.

THANKS again,

Ed

---

