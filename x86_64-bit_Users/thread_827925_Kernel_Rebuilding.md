---
title: "Kernel Rebuilding"
date: 2008-06-13
forum: x86 64-bit Users
---

### Post by chunkeydelight on 2008-06-13
Well, I installed Ubuntu 8.04 a few weeks ago and updated everything there was for me to update, but it seems that my Ubuntu runs at half the speed that Windows Vista does (which just isn't right) with my processor constently at 100%. Now, I'm not a complete n00b to Ubuntu but I'm nowhere near the novice level of the spectrum, and my friend (who helped me with some of my situations) had kept talking about rebuilding his kernel. So, I tried doing so and it wound up even slower than anyother system I knew (altho this was either Feisty or Gusty).

Could someone possible point me in the right direction for the information that is required for the building of a kernel? I would really like to be able to use my Ubuntu over Vista but as of right now it's to clunky or something. I'd be even more apreciative if someone could help me out and list what is absolutely neccessary for me to select when I do rebuild. If it helps at all my systems setup is in my signature.

---

### Post by Kilz on 2008-06-13
[This thread may help you.]("http://ubuntuforums.org/showthread.php?t=618563") Its the easiest way for a new user to compile a kernel.

---

### Post by zgornel on 2008-06-14
You might also try [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) , check the 'Old-Fashioned Debian Way' for building. Do not forget to remove any unnecessary options/modules otherwise it will be too big. Get informed on what hardware you use and search the net for other useful options to check or modify. If you get it right ubuntu speed should get a boost.

---

### Post by chunkeydelight on 2008-06-14
thanks soooo much for the links. as soon as i find some free time i definitely plan on rebuilding my kernel. now the main think i'm worried about now is which options don't i need. well... i guess i'll have to try it a few times. well. thanks once again

---

### Post by Washer on 2008-06-14
There are many reasons to recompile your kernel but speed isn't one of them. Something's using up your processor speed so look it up on system->admin->System Monitor & fix it or kill it.

---

### Post by chunkeydelight on 2008-06-15
> **Washer said:**
> There are many reasons to recompile your kernel but speed isn't one of them. Something's using up your processor speed so look it up on system->admin->System Monitor & fix it or kill it.

well. from the research that i've tried doing i've mostly heard that compiling the kernel does help because when you install linux (be it any kind) it installs with the default kernel so where it can be compatible on any system. where if you recompile the kernel, if you tell it what drivers you have, it will work only what is necessary to drive your computer. i'm not trying to argue, just explaining what i've heard/read about.

i do also see your point. i will look into what i have running and kill it and c about finding ways of killing it before it even starts the operation.

---

### Post by zgornel on 2008-06-16
Well, actually, when recompiling the kernel from source (ubuntu kernel source), with the .config file of the 'generic' kernel a 500MB monster is generated (I tried it and it lasted 2-3 hrs to compile). It is a good idea to remove unnecessary modules. Plus, a smaller kernel fits better in memory and the modules are compiled for a specific cpu resulting in increased speed.

---

