---
title: "chroot question"
date: 2006-08-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrw on 2006-08-31
My Perfection 3170 Epson scanner works on the 32-bit version of Ubuntu but not the 64-bit version. Is it possible to install the scanner with chroot? If so, how is it done?

---

### Post by zxee on 2006-08-31
> **mrw said:**
> My Perfection 3170 Epson scanner works on the 32-bit version of Ubuntu but not the 64-bit version. Is it possible to install the scanner with chroot? If so, how is it done?

chroot is used mostly to go into another install different from one you're running and perform administrative tasks, ect. So I don't see, myself, how that will help you get your scanner working in in your situation. Have you looked at the notes for the backend for your scanner at sane?

[http://www.sane-project.org/sane-supported-devices.html](http://www.sane-project.org/sane-supported-devices.html)

---

### Post by Kilz on 2006-08-31
I dont know if its possible, but it may be worth a shot if nothing else works. [Here is a link to a script]("http://www.ubuntuforums.org/showthread.php?t=157412") that automaticly sets one up.

---

### Post by mrw on 2006-08-31
I already have chroot up and running and have installed xsane but I don't know how to install the latest sane backends. When I run ./configure under the chroot prompts I get the error  "onfigure: error: C compiler cannot create executables"

---

### Post by Kilz on 2006-08-31
> **mrw said:**
> I already have chroot up and running and have installed xsane but I don't know how to install the latest sane backends. When I run ./configure under the chroot prompts I get the error  "onfigure: error: C compiler cannot create executables"

./configure is used to create a make file so the command make works. Are you compiling source code?

---

### Post by mrw on 2006-08-31
Yes, I downloaded the latest sane backends and need to compile it. From what I understand chroot is a 32-bit environment within and indendent of the 64-bit Ubuntu. It is a 32 bit version of snyaptic from which I installed gcc (the c compiler). I wonder if I need another component to compile. This installed without a problem on my 32-bit Ubuntu (a different partition) where the Epson scanner works with xsane.

---

### Post by Kilz on 2006-08-31
> **mrw said:**
> Yes, I downloaded the latest sane backends and need to compile it. From what I understand chroot is a 32-bit environment within and indendent of the 64-bit Ubuntu. It is a 32 bit version of snyaptic from which I installed gcc (the c compiler). I wonder if I need another component to compile. This installed without a problem on my 32-bit Ubuntu (a different partition) where the Epson scanner works with xsane.

probibly the build-essensial package

---

