---
title: "Library files..."
date: 2006-09-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by EternalChild on 2006-09-04
Hi all

I've got Kubuntu 64bit on my PC, and I'm having some trouble with certain programs and their required shared libraries.

So far I've had the same problem with two software packages... one being google earth and the other being a game called Uplink.

What happens is that when I run the binaries it says it can't find certain library files, but I've checked and they are there...

I've tried updating /etc/ld.so.conf and running ldconfig, but its not helping... any ideas?

Thanks and regards
Bradly

---

### Post by Kilz on 2006-09-04
> **EternalChild said:**
> Hi all

I've got Kubuntu 64bit on my PC, and I'm having some trouble with certain programs and their required shared libraries.

So far I've had the same problem with two software packages... one being google earth and the other being a game called Uplink.

What happens is that when I run the binaries it says it can't find certain library files, but I've checked and they are there...

I've tried updating /etc/ld.so.conf and running ldconfig, but its not helping... any ideas?

Thanks and regards
Bradly

I can safely bet that the applications are 32bit. Libraries in /lib are 64bit and cant be used by 32bit applications. If in fact they are 32bit applications you will need to manualy install 32bit libraries for them. [I have a page on my site that may be of help to you.]("http://www.tghc.org/staticpages/index.php/32bitapplications")

---

