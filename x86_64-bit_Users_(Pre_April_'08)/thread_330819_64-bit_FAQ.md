---
title: "64-bit FAQ"
date: 2007-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by kuja on 2007-01-03
I realised we need something like this, and got bored, then wrote it.

Q: Is there any difference in performance between 32-bit and 64-bit Linux/Ubuntu? 
A: Yes, and the areas in which it shines brightest are when it does things such as precise math, rendering(things like blender), and things like audio/video encoding.

Q: I have installed 32-bit Ubuntu, can I upgrade to 64-bit? 
A: No, you'll have to do a clean install with the amd64 CD.

Q: I have installed 64-bit Ubuntu, can I downgroud to 32-bit?
A: No, you'll have to do a clean install with the i386 CD.

Q: How can I tell if I have installed 64-bit Ubuntu (as opposed to 32-bit Ubuntu)?
A: Open a terminal, and type in "uname -m".

Q: Can I install 32-bit Ubuntu on my 64-bit machine?
A: In most cases yes, but it doesn't work so well on some hardware.
Q: I have heard there are far less applications available for 64-bit, is this true?
A: No, the differnece in the number of applications is actually quite small; however, some things, most of which proprietary, are not available for 64-bit. For many of these you will be able to install and use the 32-bit program. For more information on this see the sticky thread about getting 32-bit apps to work on 64-bit.

Q: What processors have 64-bit support?
A: AMD Processors that have support: Any socket 754, 939, 940, AM2, or S1 as far as I know. Processor. This includes Athlon 64/FX/X2, Turion 64/X2, some Opterons, and some Semprons.
Intel Processors: Some Pentium 4s, Some Celeron Ds, Some Xeons (including all Core 2 Xeons) , All Pentium D's, and all Core 2 processors, have 64-bit support.

Q: How do I install a 32-bit deb in 64-bit Ubuntu?
A: dpkg --install --force-architecture package.deb

Q: I've heard to use 32-bit applications in 64-bit Ubuntu that I need to use a chroot, is this true?
A: It used to be true, but no longer is. See the installing 32-bit apps in 64-bit Ubuntu sticky thread for more information.

---

