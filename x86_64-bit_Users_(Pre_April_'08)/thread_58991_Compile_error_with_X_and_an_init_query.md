---
title: "Compile error with X and an init query"
date: 2005-08-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by hack_benjamin on 2005-08-22
A nice simple one for you:

when i do any ./configure for a program requiring X i get the following error:
```
checking for X... configure: error: 
Can't find X includes. 
Please check your installation and add the correct paths!
```

As I'm new to ubuntu (been using Gentoo for about 2 years) I'm not really used to compiling my own because emerge dealt with it (I know how to but don't know what parameters to pass), so anyone tell me what I pass to ./configure to get it to find the correct X libs/headers?

Also, is there a useful tool similar to rc-update for ubuntu?
rc-update is what Gentoo uses to control what programs are in what runlevel, for example if I wanted to add shorewall to my default runlevel it'd be rc-update add shorewall default.

Cheers

---

### Post by zarathustra on 2005-08-22
I've had this problem too since I often try to compile to get the latest software instead of being patient and wait for them in the repository. You need to install the development files that provide headers, at least that's what I did.

---

