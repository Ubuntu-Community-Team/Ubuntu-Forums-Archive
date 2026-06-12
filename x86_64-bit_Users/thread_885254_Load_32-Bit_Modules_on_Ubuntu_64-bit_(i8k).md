---
title: "Load 32-Bit Modules on Ubuntu 64-bit (i8k)"
date: 2008-08-09
forum: x86 64-bit Users
---

### Post by eugenio_vb on 2008-08-09
Hi,

I'm having troubles with Ubuntu Hardy 64-Bit because I need to control my laptop's fans to keep it cool, however, I can't because I8K module isn't present on 64-Bit Kernel, but it does on the 32-Bit Kernel.

¿Is there any way to load a 32-Bit module on the 64-Bit Kernel?
¿Is there a port of I8K x86?
¿Is there an alternative to control dell laptop fans on Ubuntu 64?

Thank you.

---

### Post by C. Wizard on 2008-08-10
Thanks for posting this question.  I've been
trying to load a 32 bit driver for the Agere
PCI soft modem and have the same problem.

Does anyone know if there is a line command to force the installation of a 32 bit module?

---

### Post by Yellow Pasque on 2008-08-10
> Does anyone know if there is a line command to force the installation of a 32 bit module?
If you have a 64-bit system, you'll need 64-bit drivers. Is the source code available?

> I8K module isn't present on 64-Bit Kernel
Let me see if I can build it and pack it into a .deb

---

### Post by Yellow Pasque on 2008-08-10
I'm sorry, the kernel module won't compile. I get assembler errors :(

Maybe this utility will work better?
[http://ubuntuforums.org/showthread.php?p=3350647](http://ubuntuforums.org/showthread.php?p=3350647)

---

