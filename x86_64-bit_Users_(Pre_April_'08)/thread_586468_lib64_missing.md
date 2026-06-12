---
title: "lib64 missing?"
date: 2007-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by carl.alv on 2007-10-22
Hi all!

I am kind of newb and I just upgraded my ubuntu feisty to gutsy in my asus laptop with core2duo. The thing is that in principle I had the 64-bit ubuntu version installed but when I look for lib64 libraries (in fact i was trying to compile a c++ program with the gcc 4.2 version and openmp) I cannot find them. I have the lib64 folder with some files in it, but I cannot find, for example, the lib64gomp1 library. When I search on the synaptics for the library it just gives me the option to install the  lib32gomp1 library, but the 64-bit one is nowhere to be found, so I'm beginning to think that I have the 32 version installed!!!

How can I verify this?

---

### Post by John.Michael.Kane on 2007-10-22
> **carl.alv said:**
> Hi all!

I am kind of newb and I just upgraded my ubuntu feisty to gutsy in my asus laptop with core2duo. The thing is that in principle I had the 64-bit ubuntu version installed but when I look for lib64 libraries (in fact i was trying to compile a c++ program with the gcc 4.2 version and openmp) I cannot find them. I have the lib64 folder with some files in it, but I cannot find, for example, the lib64gomp1 library. When I search on the synaptics for the library it just gives me the option to install the  lib32gomp1 library, but the 64-bit one is nowhere to be found, so I'm beginning to think that I have the 32 version installed!!!

How can I verify this?

Well if you are trying to verify that the system is running 64bit theres two ways to find out. Open the terminal
Type:
```
uname -a
```
Which will out put the below kernel info.
```
your kernel number-generic #2 SMP Wed Jan 31 19:04:30 UTC 2007 x86_64 GNU/Linux
```

or

Type:
```
arch
```
Which will out put arch type only.
```
x86_64
```

Anything other then x86_64 is shown then you are running a non 64bit OS. 

Also lib64gcc1, and openmpi-dev are in the gutsy64 repos.

---

### Post by carl.alv on 2007-10-22
Thank you! My arch is X86-64, so thats fine. But I dont know where to find the 64 bit repos, I have enabled main, universe, restricted and multiverse, put the synaptic does not find any lib64. Could you tell me where to find them?

---

### Post by Cappy on 2007-10-22
Those are the 64-bit repos. Most 32-bit libraries are stored in /usr/lib32 - most of which will only come from installing ia32-libs packages or packages such as lib32gomp1.

libgomp1 is the 64-bit package.
lib32gomp1 is the 32-bit package.

Anything without "lib32" ia "ia32" on the front is 64-bit.

---

### Post by carl.alv on 2007-10-22
Ohhh... ok :tongue: thank you all!!!!

---

