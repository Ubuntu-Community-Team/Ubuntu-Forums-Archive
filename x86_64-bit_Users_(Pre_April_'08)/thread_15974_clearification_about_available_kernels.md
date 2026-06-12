---
title: "clearification about available kernels"
date: 2005-02-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by rel on 2005-02-18
Hello, 

have to ask, cant find any information about it.

What are the differences about amd64-k8 and amd64-generic kernel images?

And what are these restricted modules and how do these work?
I see in synaptic that there are no matching restricted modules for 2.6.10 versions.

I use hoary on an AMD64, all works fine. But after creating a custom kernel I couldnt get
my nvidia card to work. I'am thinking of doing the kernel and nvidia outside apt.

greets, rel.

---

### Post by leech on 2005-02-18
Did you create the custom kernel the 'debian way'?  If so, basically what you'll need to get the modules, is to apt-get the 'nvidia-kernel-source' package and then go into /usr/src/linux and do the 'make-kpkg modules_image' and it should create the debian package for nvidia-kernel-2.6.10... etc.  Then you should be good to go.

Leech

---

### Post by rel on 2005-02-18
[QUOTE=leech]Did you create the custom kernel the 'debian way'?  If so, basically what you'll need to get the modules, is to apt-get the 'nvidia-kernel-source' package and then go into /usr/src/linux and do the 'make-kpkg modules_image' and it should create the debian package for nvidia-kernel-2.6.10... etc.  Then you should be good to go.

Leech[/QUOTE]

Hi leech,

that easy? I have done it the make-kpkg way and it almost went perfectly. 
Except that it didn't want to make an initrd kernel image for me 
(complaining about cramfs not found, altough I had the official sources whitch synaptic reported it had the unbuntu patches. In menuconfig there was no entry that
said cramfs - go figure). But the deb file was generated and I had compiled everything
needed at boot-time inkernel. This worked.

Now I'll try again. But, to understand it correctly:

After apt-getting the sources (2.6.11 for example) I need to apt-get nvidia-sources, and do make-kpkg *modules_image* inside the tree. Whitch will create the nvidia-glx deb?
Or restricted sources witch I need to install afterwards? I really want to understand this.

I come from gentoo, where everything is practically plain simple.

greets rel

---

