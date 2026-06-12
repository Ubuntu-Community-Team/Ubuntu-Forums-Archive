---
title: "AMD Turion64 installation help"
date: 2006-07-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by The Shadow on 2006-07-30
when I try to "boot from CD or Install" UBUNTU 6.06 AMD 64 version on my HP Pavilion dv8000 laptop I get the following message:

"Kernel Panic - notsyncing: Attemot to kill init!" any ideas how i can correct this problem? I tried running the x86 memory test and it found no problems.

Robert

---

### Post by x64Jimbo on 2006-07-30
Try some of the boot options. It's possible that the kernel is having trouble grappling with some of your low-level system configurations like BIOS, acpi, etc.

---

### Post by The Shadow on 2006-07-30
I'm a nubi so I'm not familiar with the boot options; any suggestions? Where can I go to find information on boot options?

---

### Post by x64Jimbo on 2006-07-30
Press F2 or F3 when the boot screen comes up. It will list them. I'd recommend turning off acpi for starters.

---

### Post by The Shadow on 2006-07-30
OK. I used the apci=off option and got the live CD to boot. I assume that if I do the permanent install i will be able to edit he boot file and add that option. Thanks for the help.

I now have a problem that the network/internet does not work. 
Any further suggestions for solving that problem?

---

### Post by x64Jimbo on 2006-07-30
Need more info. Model number of network card? Driver you're trying to use? Wireless? Wired?

---

### Post by The Shadow on 2006-07-30
I have wireless internet built in to my HP Pavilion dv8000. Device manager says it is a Broadcom 802.11b/g WLAN card. I have not attempted to install a Ubuntu driver for the wireless (not sure how yet) somaybe that is the problem.

---

### Post by x64Jimbo on 2006-07-30
This oughta get you started:
[http://ubuntuforums.org/search.php?searchid=7106235](http://ubuntuforums.org/search.php?searchid=7106235)

---

### Post by The Shadow on 2006-07-30
Thanks for the help. I didn't understand much of what I read; guess  I will have to do some additional research to help my understanding of Linux. At this point i have managed to get Ubuntu installed and working (without network access) so I am making some progress.

---

