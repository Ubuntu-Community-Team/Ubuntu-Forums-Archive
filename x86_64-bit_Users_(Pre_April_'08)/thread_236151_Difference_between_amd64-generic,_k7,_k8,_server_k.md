---
title: "Difference between amd64-generic, k7, k8, server kernels?"
date: 2006-08-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by harisund on 2006-08-14
Hello

I am used to installing a server version of Ubuntu on my 32 bit machines and then installing ubuntu-desktop. Along the way, I also install the linux-restricted-modules-$(uname -r) as well. 

I did the same on my laptop (turion 64) with an AMD64 Ubuntu and tried to install the linux-restricted-modules-$(uname -r) but it wasn't found. 

Searching for it, I found tha the kernel I have is 2.6.15-26-amd64-server and this in particular has no restricted modules section. However, I find plenty of other kernel images, such as amd64-generic, k8 and k7.
 
Which one should I install for AMD64 Ubuntu on Turion 64 processor? If I recall correctly, Turion64 was basically a rework of Athlon 64 for laptops.

Thanks for your help. 

PS: If I were to install 32bit Ubuntu on my Turion64, which would be the ideal kernel? linux-686? or something else?

---

### Post by Kilz on 2006-08-14
> **harisund said:**
> Hello

I am used to installing a server version of Ubuntu on my 32 bit machines and then installing ubuntu-desktop. Along the way, I also install the linux-restricted-modules-$(uname -r) as well. 

I did the same on my laptop (turion 64) with an AMD64 Ubuntu and tried to install the linux-restricted-modules-$(uname -r) but it wasn't found. 

Searching for it, I found tha the kernel I have is 2.6.15-26-amd64-server and this in particular has no restricted modules section. However, I find plenty of other kernel images, such as amd64-generic, k8 and k7.
 
Which one should I install for AMD64 Ubuntu on Turion 64 processor? If I recall correctly, Turion64 was basically a rework of Athlon 64 for laptops.

Thanks for your help. 

PS: If I were to install 32bit Ubuntu on my Turion64, which would be the ideal kernel? linux-686? or something else?

The difference from what I understand is
Generic - Should work with any 64bit chip from intel or amd
k8 - should work with any 64bit athlon chip
k7 - Should work with any 32bit athlon chip

imho The ideal would not be putting any 32bit kernel or os on a 64bit system. In an idea world everything would work in 64bit and there would be no need to ever use anything but a 64bit os. Sadly there are some rare situations where it may be better to use 32bit. 
Those rare instances would include
1) rare unique hardware that dose not have a 64bit driver or is incompatible.
2) need to run a proprietary application that the 64bit version is not available or the 32bit version is not installable. Those applications are rare.

---

### Post by harisund on 2006-08-14
Awesome. Thanks for that. 

So assuming Turion64 is just a rebuilt Athlon64 for laptops, I am good to go with the 64 bit k8 kernel right?

---

### Post by Kilz on 2006-08-14
> **harisund said:**
> Awesome. Thanks for that. 

So assuming Turion64 is just a rebuilt Athlon64 for laptops, I am good to go with the 64 bit k8 kernel right?

From what I understand thats correct, but dont remove the generic kernel untill you have tested it. If nothing else you are a reboot away from going back to a working setup.

---

