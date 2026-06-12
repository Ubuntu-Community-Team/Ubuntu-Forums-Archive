---
title: "64 Bit GRUB"
date: 2008-02-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by bloodhound23 on 2008-02-12
How does Grub load a 64 bit OS? From what I've seen it only does powerPC and x86.

---

### Post by prince_niceguy on 2008-02-12
Can you be more specific? I am using ubuntu 7.10 64bit with vista 64bit ultimate and everything is working fine. So, it is booting the 64 bit OS. Earlier I had xp 32 bit too with 64bit ubuntu without any issue. So, there is no issue in 64bit. 

Hope that clears your doubt.

---

### Post by bloodhound23 on 2008-02-12
If I wrote a 64 bit kernel, would I have problems loading it with GRUB and how would I setup the multiboot header?

---

### Post by mrsteveman1 on 2008-02-12
Since grub runs on the processor under real mode (just like the bios) it doesn't really matter what kernel it is loading as long as grub can pass control onto the kernel after loading it from the disk.

The kernel is what eventually puts the processor into 32-bit or 64-bit mode after it loads (at least thats my understanding of the process).

The multiboot spec is [here]("http://www.gnu.org/software/grub/manual/multiboot/multiboot.html")

---

