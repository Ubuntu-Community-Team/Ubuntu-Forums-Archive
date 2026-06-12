---
title: "Kernel update messed up vmware"
date: 2008-10-22
forum: x86 64-bit Users
---

### Post by slope on 2008-10-22
After the kernel update last week or so I can not start vmware anymore. I have read why on this thread here on the forum:

[Vmware stopped working]("http://ubuntuforums.org/showthread.php?t=949068")

I have the solution to the problem here I belive:
[Make changes to kernel, kernel headers, and restricted modules.]("http://ubuntuforums.org/showthread.php?p=6001912")

So my only problem now is to know what kernel I am running. How can I check what kernel I am currently running?

[B]
Do I run 386 kernel or 686 kernel?[/B]

---

### Post by jespdj on 2008-10-22
Type:
```
uname -m
```
Does this have anything to do with 64-bit? If you are running 64-bit Ubuntu, then you are using the **x86_64** kernel and not an i386 or i686 kernel.

But I'm not sure that the advice given in that other topic is good advice. I see in Synaptic that there are packages named, for example linux-amd64-generic, but the description of those packages says "Upgrade dummy package. Can be removed". So I don't know if it's a good idea to install it.

Try installing **build-essential** and **linux-headers-generic**, which will install the tools you need to compile software and the headers of the latest Linux kernel.

---

### Post by altonbr on 2008-10-22
You can try running my VMware Server 1.0x script or try using VirtualBox 2.0 (in Intrepid) as it is independent from kernel updates.

---

### Post by jespdj on 2008-10-22
It's not completely true that VirtualBox 2.0 is independent of kernel updates. VirtualBox also includes a kernel module, which won't work anymore if you update the kernel.

I just reinstall VirtualBox after a kernel update, that's not very hard and makes it work again (by compiling the kernel module for the updated kernel).

---

### Post by slope on 2008-10-22
> **jespdj said:**
> Type:
```
uname -m
```
Does this have anything to do with 64-bit? If you are running 64-bit Ubuntu, then you are using the **x86_64** kernel and not an i386 or i686 kernel.

But I'm not sure that the advice given in that other topic is good advice. I see in Synaptic that there are packages named, for example linux-amd64-generic, but the description of those packages says "Upgrade dummy package. Can be removed". So I don't know if it's a good idea to install it.

Try installing **build-essential** and **linux-headers-generic**, which will install the tools you need to compile software and the headers of the latest Linux kernel.

```
uname -m
```  Returns x86_64 .
So I run 64 bit. Is there a trick to make sure it all updates with a kernel-update without running things manually?    Or do I have to make room for manually updating everything in the future also?

---

