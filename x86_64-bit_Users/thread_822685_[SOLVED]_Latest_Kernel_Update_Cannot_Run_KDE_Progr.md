---
title: "[SOLVED] Latest Kernel Update Cannot Run KDE Programs"
date: 2008-06-08
forum: x86 64-bit Users
---

### Post by Didjit on 2008-06-08
Sine the last kernel update, I cannot run KDE program any more. I get:

Inconsistency detected by ld.so: ../sysdeps/x86_64/dl-machine.h: 416: elf_machine_rela_relative: Assertion `((reloc->r_info) & 0xffffffff) == 8' failed!

Anyone know of a fix?

Tx

Didjit

---

### Post by Sef on 2008-06-08
What *butnu and version are you running?

---

### Post by Didjit on 2008-06-08
> **Sef said:**
> What *butnu and version are you running?

Sorry Ubuntu (gnome) Hardy 64

Didjit

---

### Post by prestomation on 2008-06-08
You specified KDE programs, so I'm assuming your default Gnome desktop works?  Is it just KDE apps?

---

### Post by Sef on 2008-06-09
> You specified KDE programs, so I'm assuming your default Gnome desktop works? Is it just KDE apps?

What apps have you tried to install and haven't worked?

---

### Post by Didjit on 2008-06-09
> **Sef said:**
> What apps have you tried to install and haven't worked?

So far:

konsole
konqueror
amrok

They have always been installed and worked fine before the update.

Didjit

Edit: After another reboot, the problem went away. Strange....

---

### Post by Sef on 2008-06-09
> Edit: After another reboot, the problem went away. Strange....

Sometimes, that is what is needed.  Glad your problem got cleared up.

---

### Post by iivanov on 2009-03-29
I have the exact same error message with firefox on intrepid x64. Can anyone help me? :confused:

---

### Post by Paintrick on 2009-06-06
I have the same issue
with Apache on ubuntu server.

---

