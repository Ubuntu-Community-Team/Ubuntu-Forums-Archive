---
title: "amd vs intel 64bit"
date: 2007-10-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by bvbellomo on 2007-10-10
I currently have an older AMD64 CPU running Ubuntu.  I am thinking of running out and buying a quad core Intel CPU and continuing to run the 64 bit version of Ubuntu.  What issues can I expect?

Worst case, I have to backup my home directory, install a fresh Gibbon 64, and restore the contents of my home directory.  

Best case, I just swap boards, boot, and am good to go.

Any ideas what to expect?

---

### Post by John.Michael.Kane on 2007-10-10
> **bvbellomo said:**
> I currently have an older AMD64 CPU running Ubuntu.  I am thinking of running out and buying a quad core Intel CPU and continuing to run the 64 bit version of Ubuntu.  What issues can I expect?

Worst case, I have to backup my home directory, install a fresh Gibbon 64, and restore the contents of my home directory.  

Best case, I just swap boards, boot, and am good to go.

Any ideas what to expect?

Depends on the new hardware.Under most circumstances "best case" If every piece you buy has drivers/support in the kernel etc you should be able to simply install everything, and boot. The exception being the possibility of having to run sudo dpkg-reconfigure -phigh xserver-xorg to reset xorg.

IMHO to avoid any issues you are best off doing a clean install. Making sure to backup data deemed important. Unless of course you want to test the method above for knowledge purposes.

---

### Post by dabl on 2007-10-10
WRT the CPU and 64-bit architecture, I think the answer is "zero issues", at least that's my experience.  For Intel 64-bit chips, the term of art is "EM64T".  I've been running a Core 2 Extreme chip for a year now (Dapper, Edgy, Feisty, and Gutsy), and there's never been anything resembling a CPU-related problem.

I recall some issues around the P965 chipset -- you might want to check that out before selecting a motherboard.  My 975 is rock-solid.  :)

---

