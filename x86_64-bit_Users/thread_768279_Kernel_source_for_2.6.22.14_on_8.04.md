---
title: "Kernel source for 2.6.22.14 on 8.04"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by Helskov on 2008-04-26
Hey

I need the kernel source for kernel 2.6.22-14-generic
on hardy 8.04
I need it for the Nvidia driver. 
I cant seem to find it in the repository.
I need to use the above kernel to get my Creative X-fi beta driver to work.

Anyone know how to get it?

---

### Post by FredB on 2008-04-26
Nvidia driver ? What about using restricted driver manager in system menu ?

---

### Post by Helskov on 2008-04-26
Because it doesnt work. 
It install a etc nvidia-glx-new version for kernel 2.6.24-16.
It doesnt work for 2.6.22-14

Thats why i need to install manually. 

I dont want 2.6.24-16 bacause the X-fi Beta driver doenst work with that kernel version.

---

### Post by Helskov on 2008-04-26
Tried to use Envy. But it broke it all. No graphics accell and no X-fi sound.

---

### Post by GeekGirl1 on 2008-04-26
You can get anything you need at [http://packages.ubuntu.com](http://packages.ubuntu.com)

I did a quick search for Hardy kernel-source and came up with this: [http://packages.ubuntu.com/hardy/nvidia-legacy-kernel-source](http://packages.ubuntu.com/hardy/nvidia-legacy-kernel-source)

---

### Post by ptn107 on 2008-04-26
Just so you know you don't want the entire kernel source.  You can just use 'ubuntu-restricted-modules-$VERSION-generic'.  If you plan to compile from source (which is not the easy way to go) you need your headers installed 'linux-headers-$VERSION-generic' and you also need then 'nvidia-kernel-source'.

---

### Post by FredB on 2008-04-26
2.6.22 ? It is Gutsy kernel. Why don't you stay with gutsy ? Someone put a rocket launcher on you and force you to install Hardy ?

---

### Post by Helskov on 2008-04-26
> **FredB said:**
> 2.6.22 ? It is Gutsy kernel. Why don't you stay with gutsy ? Someone put a rocket launcher on you and force you to install Hardy ?

It's not a Gutsy kernel or Ubuntu kernel. Its a kernel! 
And i want it for Hardy. 
And i got i for Hardy. A recompiling and problems solved.

---

