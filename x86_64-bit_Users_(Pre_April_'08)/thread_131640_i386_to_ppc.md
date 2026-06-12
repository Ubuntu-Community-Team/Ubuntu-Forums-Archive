---
title: "i386 to ppc?"
date: 2006-02-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by SectionThree on 2006-02-16
Does anybody know of a (preferably easy) way to make a .deb package created for i386 work with the ppc architecture?

---

### Post by engla on 2006-02-16
Umm..

Generally, it's not possible at all in any way. Deb packages for i386 are compiled binaries that are tailor-made (so to speak) by a compiler for that exact processor type.

To get a deb that works for PPC, you need to make one from the source code.

---

### Post by CameronCalver on 2006-04-18
what exactly is i386 is it just normal pc  and ppc mac ?

---

### Post by Lanrond on 2006-04-19
[QUOTE=CameronCalver]what exactly is i386 is it just normal pc  and ppc mac ?[/QUOTE]

*i386* means that the package is compiled for the Intel processor architecture. To make the program work on ppc architecture, you need to find the source code and re-compile it for ppc.
By the way, (as far as I know) the new iMac Intel based should need i386 packages.

---

### Post by hentaidan on 2006-04-20
[QUOTE=CameronCalver]what exactly is i386 is it just normal pc  and ppc mac ?[/QUOTE]

i386 is a type of processor (found in "beige" personal computers), PPC are those found in Macs (bar the new Intel Macs), and AMD64 are found in some computers.

They all differ so much that each program has to built for i386. PPC and AMD64, hence the 3 versions of Ubuntu that are distributed, and you have to make sure you download the right version of a program depending on your processor (or download the source and build the program yourself).

---

