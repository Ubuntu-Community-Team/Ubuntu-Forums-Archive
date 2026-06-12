---
title: "Compiling Kernel ... K8 ???"
date: 2006-05-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by pallaire on 2006-05-16
Hello,

I am recompiling the kernel to remove the most unused stuff as possible, and put the most important stuff into the kernel (not in module) I am not new to the kernel compiling, but I am new to the AMD64 world.

I **dont** want to use Ubuntu 64, because I dont want to mess with the chroot stuff for flash and codecs. 

So, currently I am running Ubuntu 32 bits, with one of their kernel : 2.16.12-10-**k7**

But now I am seeing **k8** in the xconfig of the kernel, is it going to work with a 32 bits installation ? or **k8** is reserved for the 64 bits version of Ubuntu ?

Thank you all for you inputs.

---

### Post by Sutekh on 2006-05-17
Hmm I tried this once when I was very new to Linux.  

I chose a K8 processor in the xconfig process, but was running the 32bit version of Ubuntu  The kernel compiled but I coudn't boot with it.  

I don't really know why it didn't work, but it *could* have been the reason you suggested.  It could have also been because I was a Linux nub.

Not really helpful I know.  You could just give it a shot.  Save your kernel config, and try the K8, if it doesn't work, then compile using the K7 option.

---

### Post by pallaire on 2006-05-17
So I tried it out last night, It works fine, we can select k8 with 32 bits versions of Ubuntu. So I guess it would be the best way to go to without going to the 64 bits side.

Now I just need to make my network card to work with the new kernel, I have downloaded the source from ASUS, should just be some patching recompiling ... I will try that from SSH (from work) right now ;)

---

### Post by Sutekh on 2006-05-17
Hey that's cool to know.  I'll definately try to compile my own kernel again soon.  I wonder if there is any benefit to compiling with the K8 option?

---

