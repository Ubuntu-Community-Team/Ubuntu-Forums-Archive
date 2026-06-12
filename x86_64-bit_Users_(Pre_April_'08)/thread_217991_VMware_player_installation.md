---
title: "VMware player installation"
date: 2006-07-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by catalin on 2006-07-17
I am new to linux and I am having a hard time installing VMWare player but it fails to install ... a script fails during installation ... it's about Drapper on a AMD64 box ... the player is the one in the update channels.

Anyone have any ideeas ?

---

### Post by tuxcantfly on 2006-07-18
what do you mean it fails during startup? error messages please? by the way, I hope you have properly added the repositories [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) and done a sudo apt-get update. perhaps updating your kernel and the vmware player kernel modules might help

---

### Post by Kilz on 2006-07-18
> **tuxcantfly said:**
> what do you mean it fails during startup? error messages please? by the way, I hope you have properly added the repositories [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) and done a sudo apt-get update. perhaps updating your kernel and the vmware player kernel modules might help

From reading the orignal posters comments, about the script failing. Its possible they do not know vmware player is in the repositories and can be installed with Synaptic.

---

### Post by catalin on 2006-07-18
Sorry, I fogot to specify ... it's when I install it with Synaptic that fails ... the instllation start and I am opening the terminal window just for fun to see what it is doing and when one of the scripts it is executed it fails and the whole installation fails ... you can retry another time but that's it.
The error I get is 

E: vmware-player: subprocess post-installation script return error exit status 1

Sorry for not being more precise before.

---

### Post by Hallavej on 2006-07-18
I think someone forgot to update vmware kernel modules with the latest kernel upgrade. Therefore vmware is completely broken. It sucks, but you need to get it from [http://www.vmware.com](http://www.vmware.com) instead.

---

### Post by tuxcantfly on 2006-07-18
just purge everything related to vmware and reinstall it all

---

### Post by tuxcantfly on 2006-07-18
also, I hope you don't have any broken stuff on your system that might be screwing up synaptic; try

sudo apt-get -f install

---

### Post by tuxcantfly on 2006-07-19
if the issue is with the kernel modules, though, you can just use the older kernel until they build a module for the new one

---

### Post by catalin on 2006-07-20
Works !
I just uninstalled the VMware Player with the add/remove utility,
and then installed again the plyer and works like  charm.

Being a Windows programmer (for a life now) I am very nice surprised by Ubuntu ... I still have to fight with a couple of thing to install but for a first time on Linux/Unix installation not bad at all ... thx for everybody for the help.

Thx tuxcantfly

---

