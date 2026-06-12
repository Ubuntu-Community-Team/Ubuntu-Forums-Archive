---
title: "[SOLVED] Ubuntu, kernel 2.6.20-16-lowlatency - GENERAL QUESTION"
date: 2007-06-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-06-15
What is the Ubuntu, kernel 2.6.20-16-lowlatency ?  Is this different than the kernel that is loaded on my system that I assume is update (I check for daily updates)?

If it's different, what would I gain or lose by installing it, and where do I get it from?

Sorry for being an uninformed newbie...;)

---

### Post by Kilz on 2007-06-16
> **crjackson said:**
> What is the Ubuntu, kernel 2.6.20-16-lowlatency ?  Is this different than the kernel that is loaded on my system that I assume is update (I check for daily updates)?

If it's different, what would I gain or lose by installing it, and where do I get it from?

Sorry for being an uninformed newbie...;)

You can search in synaptic for linux-image for a list of kernels. You can install multiple kernels and they will be added to the grub boot list. Then try them to see if they improve the speed. As long as you keep the working one, if one doesnt load its only a reboot and an uninstall to remove it.
I think the kernel is for machines used in sound processing, at least thats what a google search shows.

---

