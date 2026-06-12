---
title: "Some problems"
date: 2005-12-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by yilez on 2005-12-04
Ok. My system is an AMD 64 Dual Core 4400. I have a PCI-E Graphics card, and my only network card is a Netgear WG111 v2, which is a usb wireless G card.

Here are my problems. X crashes when I log in to gnome. People have suggested that I download the driver from nvidia and that I also need the kernel header files and binuntils in order to compile it.

Now, I was told to use apt-get to get the kernel header files and binutils. But theres a problem. I have a wireless G network card, so I need ndis wrapper. I had a look for the source code, and that says that I need the kernel header files.

So I'm in a bit of a pickle.

To even get to a desktop, I need to download stuff, but can't due to lack of network.

I find that on many distros they don't like it when you don't install stuff using their package manager.

So. Should I download the source for the various packages that I need, or is there another way of installing the packages of the things that I need, or should I just use another distro?

---

### Post by Iandefor on 2005-12-04
I'm certain that a computer new enough so as to support AMD64 and PCI-E also has at least one traditional ethernet interface. What motherboard are you using? 

If you plan on finding a different distro, may I suggest SUSE? I've heard good things about it.

---

### Post by yilez on 2005-12-05
[QUOTE=Iandefor]I'm certain that a computer new enough so as to support AMD64 and PCI-E also has at least one traditional ethernet interface. What motherboard are you using?[/quote]

Yes, it does, but I don't want to spend £20+ on a ethernet cable (my router is a good 15-20 meters from my computer in terms of wiring) when after running 5 commands I won't be needing it again. We also only have one phone line in our house, so moving the router closer isn't an option.

[QUOTE=Iandefor]If you plan on finding a different distro, may I suggest SUSE? I've heard good things about it.[/QUOTE]

I've heard different ;)

I'm thinking of Vidalinux (if their website ever comes back). I used to use Gentoo, and thoroughly like it, but it just relys upon internet connections too much and doesn't ship with ndiswrapper.

Does anyone know of a genuine reason why so many distros don't ship with ndis support? it just seems crazy that so many people have wireless g networks, and the only distro that ships with ndis is Mandriva (that I've found so far), but it doesn't recognise my USB card.

---

### Post by RAOF on 2005-12-05
You can manually download all the package files (.deb) from an Ubuntu repository, and then install them with:

sudo dpkg -i packagename.deb

---

### Post by yilez on 2005-12-05
Ok, thanks.

If anyone wants to know, I used this repository

[http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/)

I'll try everything in a couple of days.

---

### Post by grsing on 2005-12-06
This is the low tech solution, but couldn't you just move your computer closer to your router and buy the cheapest ethernet cord you can get (shouldn't be more than about $5 or the equivalent, and it might come in handy just to have around), then move your computer back to where it is when you download what you need?  Kind of a pain, but ought to work without having to fight any software problems.

---

