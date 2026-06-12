---
title: "T4200 processor - 64 bit or 32 bit version?"
date: 2009-04-26
forum: x86 64-bit Users
---

### Post by gtosco on 2009-04-26
Hi!
I have just bought an Acer Aspire 5735z laptop provided with an Intel T4200 dual core processor and 4GB of RAM (shared with the graphics card). I would like to wipe out Vista and to install Kubuntu Jaunty. I wondered whether to install a 32 bit version or a 64 bit one. What do you suggest to install? Thanks in advance.

---

### Post by xxalejoxx on 2009-04-26
I have 5738 and i have 64 bits ubuntu, its the best, works fine ;)

---

### Post by jespdj on 2009-04-27
This is a job for Intel's [processorfinder](http://processorfinder.intel.com/).

Hmmm... strange, the processorfinder says it doesn't know the T4200. Are you sure it's a T4200? Or maybe it's a very new model and it's not in the processorfinder yet.

If the T4200 is a **Core 2 Duo**, then it is certainly 64-bit.

Do you have Windows on the laptop? Then you can download [CPU-Z](http://www.cpuid.com/cpuz.php) to find out information about the CPU. If it says that your CPU supports "EM64T" or "Intel 64" then it has the 64-bit extensions.

About choosing the 32-bit or 64-bit version of Kubuntu: Since you have 4 GB RAM, it would be better to go for the 64-bit version. The 32-bit version will not be able to see all your RAM.

---

### Post by sanderj on 2009-04-27
> **gtosco said:**
> Hi!
I have just bought an Acer Aspire 5735z laptop provided with an Intel T4200 dual core processor and 4GB of RAM (shared with the graphics card). I would like to wipe out Vista and to install Kubuntu Jaunty. I wondered whether to install a 32 bit version or a 64 bit one. What do you suggest to install? Thanks in advance.

According to [http://en.wikipedia.org/wiki/List_of_Intel_Pentium_Dual-Core_microprocessors#.22Penryn-3M.22_.2845_nm.29](http://en.wikipedia.org/wiki/List_of_Intel_Pentium_Dual-Core_microprocessors#.22Penryn-3M.22_.2845_nm.29) , the Pentium Dual Core T4200 is 64-bit. 

So, you *can* run 64-bit, and 32-bit Ubuntu. 

Which version is best for you, is a FAQ and handled in the sticky [http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by gtosco on 2009-04-28
OK.Thank you very much guys! I am very happy to install the 64 bit version of Kubuntu! I have just another question. Should I modify something in the BIOS before installing the 64 bit version?

---

### Post by 3Miro on 2009-04-28
> **gtosco said:**
> OK.Thank you very much guys! I am very happy to install the 64 bit version of Kubuntu! I have just another question. Should I modify something in the BIOS before installing the 64 bit version?

It depends on the BIOS. You should be able to install with out trouble, now if the system doesn't automatically detect the 4GB of RAM, then you might have to change the BIOS settings.

---

