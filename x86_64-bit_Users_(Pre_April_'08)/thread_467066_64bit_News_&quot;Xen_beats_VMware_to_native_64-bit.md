---
title: "64bit News: &quot;Xen beats VMware to native 64-bit punch&quot;"
date: 2007-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by octoberdan on 2007-06-07
Noticed an interesting article on Linux Today that I thought my ubuntu brothers and sisters would find interesting. Apparently Xen now has a native 64-bit build, beating VMWare to the 64bit punch. Checkout the story at [http://searchservervirtualization.techtarget.com/originalContent/0,289142,sid94_gci1255875,00.html](http://searchservervirtualization.techtarget.com/originalContent/0,289142,sid94_gci1255875,00.html)

> 
Version 3.1 of the open-source Xen hypervisor, official word of which is imminently expected, now runs natively in 64-bit, making it possible to run any supported operating system in 64-bit or 32-bit mode


> 
At 32-bit, Xen was limited to 16 GB of RAM per physical host, Crosby said. In contrast, 64-bit environments can address up to 16 TB of memory. So with previous versions of Xen, running "up to ten virtual machines per host is no problem," Simon said, but depending on how much memory you allocate to a VM (virtual machine), 16 GB of RAM can be quickly consumed by more VMs. 


And a note on VMWare
> 
VMware officially added 64-bit guest support to ESX this fall with the launch of version 3.0.1, even though the hypervisor itself runs as a 32-bit application.
...
ESX's ability to run 64-bit guests is "a remarkable hack, really," said Simon Crosby, CTO at XenSource, the leader of the Xen virtualization project. "I'm amazed that it works."


---

### Post by frankabel on 2007-09-07
Hi,

What mean "now runs natively in 64-bit"? I saw a 3.0 package named ubuntu-xen-desktop-amd64, that don't mean 64bit support? Can you help me with my doubt? Pls, take a look at [http://ubuntuforums.org/showthread.php?t=545495](http://ubuntuforums.org/showthread.php?t=545495)

Salute
Frank Abel

---

### Post by stmiller on 2007-09-07
> What mean "now runs natively in 64-bit"?

Frank: you are replying to a slightly dated post. But that article does imply 64bit goodness was added in that version of Xen.

---

### Post by frankabel on 2007-09-08
Thanks for your reply, but what about the 3.0 package named ubuntu-xen-desktop-amd64, I mean, before the Xen 3.1 was released exist a 64bit package, what feature was added really in the 3.1?

Salute
Frank Abel

---

