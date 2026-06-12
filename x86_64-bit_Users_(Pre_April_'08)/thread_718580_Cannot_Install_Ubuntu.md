---
title: "Cannot Install Ubuntu"
date: 2008-03-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dahiasj on 2008-03-08
i normally have Windows Vista on my Labtop, but i want to try something other, so i found Ubuntu, i have now downloaded ubuntu for 64bit Amd... 
i have burned the img. file to a cd using ImGBurn. 
now i have tried to restart the computer and the ubuntu screen opens up, i press Start or install ubuntu, there comes som text, and a black screen, then there comes a box message that says that it cant find my graphic card and my monitor. and it need to start on low graphic mode, i press continue and there comes a black screen, and nothing happens. after waiting 15 minutes still nothing happens. i have tried to find my card and so on, but i cant get i work ? i'm new to linux and have allways used windows. Please i really need som help!:confused:

---

### Post by crjackson on 2008-03-08
Hit the F6 key and take out the word splash (but nothing else) from the parameters.

Also please post your computer specs. so others can/will help.  I'm no expert here...

If that doesn't work, then remove the word splash, but also add ```
irqpoll pci=noacpi noapic nolapic acpi=off

``` to the boot parameters

---

### Post by Dahiasj on 2008-03-08
thx i works perfect now :D

---

### Post by crjackson on 2008-03-08
> **Dahiasj said:**
> thx i works perfect now :D

Your welcome.  Don't forget to mark the thread as solved, and click the little gold star next to the quote button on your way out the door..  :)

---

