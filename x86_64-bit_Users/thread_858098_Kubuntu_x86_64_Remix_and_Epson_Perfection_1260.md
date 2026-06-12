---
title: "Kubuntu x86_64 Remix and Epson Perfection 1260"
date: 2008-07-13
forum: x86 64-bit Users
---

### Post by Renato_A on 2008-07-13
Hello all:

I have a good old Epson Perfection 1260 which functioned perfecly in previous Kubuntu versions. All of them were IA32.
I decided then to try Kubuntu Hardy x86_64 Remix, as my system is an IA64 and the software support to these systems improved a lot.
The problem is that my scanner is now scanning color images with two stripes in it: one yellow in the left and one red in right side (see attachment). Grayscale images have the same kind of distortion, with two gray stripes across the image.
I tested the scanner in a winxp box and it functioned perfectly. Also,I have tried Kooka, Xsane and Quiteinsane to no avail.:confused:

Any help ?

---

### Post by gabolander on 2009-02-08
> **Renato_A said:**
> Hello all:

I have a good old Epson Perfection 1260 which functioned perfecly in previous Kubuntu versions. All of them were IA32.
I decided then to try Kubuntu Hardy x86_64 Remix, as my system is an IA64 and the software support to these systems improved a lot.
The problem is that my scanner is now scanning color images with two stripes in it: one yellow in the left and one red in right side (see attachment). Grayscale images have the same kind of distortion, with two gray stripes across the image.
I tested the scanner in a winxp box and it functioned perfectly. Also,I have tried Kooka, Xsane and Quiteinsane to no avail.:confused:

Any help ?

Same problem here using Kubuntu Intrepid on a X86_64 architecture and same model/type of scanner.
I solved using a different application that doesn't seem to have the same bug..
I suggest you to use application "**quiteinsane**". It's a very good frontend of sane. It works flawlessly and doesn't have the yellow-red problem of xsane ;)

It has many useful options even for scanner's lamp and ocr.

[INDENT][I]
sudo apt-get install quiteinsane[/I][/INDENT]

Hope this help.
:popcorn:

---

