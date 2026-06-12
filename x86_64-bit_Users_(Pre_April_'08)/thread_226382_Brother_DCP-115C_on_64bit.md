---
title: "Brother DCP-115C on 64bit"
date: 2006-07-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by fredricsolstad on 2006-07-31
Hi everyone!

I'm wondering if there is anyone that has gotten a Brother MFC210 or a DCP115 to work in Ubuntu 6.06 64bit. 

I've found a great guide, but I cannot get the deb packages to install on my system (they complain about me running a 64 bit one and the packages are for 32 bit systems)

any suggestions or tips are really appriciated. 

cheers
Fredric

---

### Post by hefelump on 2007-10-14
Hi, I am quite new to Ubuntu and recently installed Feisty 64-bit on my computer.
I followed the instruction for the brother DCP-115C installation. I've got the same error message ... something like incompatible architecture....
However there is a solution to the problem. I found it under the FAQ section on the brother side. [http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html)
there they state:
    * I'm using an AMD64 bit version of Linux. Can I use the Brother Linux printer drivers?

      Yes, but please note the following conditions:

      For RPM package users:
      If you cannot print, install lib32stdc++6 or ia32-libs.

      For DPKG package users:
      Install the driver using the command option "--force-architecture".
      If you cannot print, install lib32stdc++6 or ia32-libs.

      Also, try copying the file which name starts with "brlpdwrapper" in the
      " /usr/lib/cups/filter" to the "/usr/lib64/cups/filter".

.... and it worked for me!!!

good Luck

---

