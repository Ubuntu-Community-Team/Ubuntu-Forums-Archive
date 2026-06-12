---
title: "I Could Cry!"
date: 2006-09-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by backinblack on 2006-09-21
](*,) ](*,) And its true!!
This is a Ubuntu kernel 2.6.15 AMD generic with and ASUS 8N-VM CSM motherboard, AMD Athlon Socket 939, and NVidia GeForce 6150 GPU chipset.
Where is the appropriate driver needed to get this thing connected to the internet?
The NVidia site has 120 pages to look through, and it is very confusing.
For now I'm dual booting with this and WindowsXP64-bit trial version.
Assuming the driver is ever located, what commands are needed to get Synaptic to install the driver.
I am not a computer tech, so please do not assume that I know what you know.

---

### Post by colo on 2006-09-21
I've set this board up with Gentoo back in the days of 2.6.13 I believe. You don't need any of the proprietary drivers provided by NVIDIA to get the NIC working. Try loading the "forcedeth"-module ( `sudo modprobe forcedeth` ). If that does not work, post the output of `lspci` here.

---

### Post by Aquila62 on 2006-09-21
Your Motherboard has NVIDIA Gigabit LAN with NVIDIA ActiveArmor Firewall driven by the nForce chipset.

Quote from nVidia >

NVIDIA nForce Drivers 

Open source drivers for NVIDIA nForce hardware are included in the standard Linux kernel and leading Linux distributions. 

End Quote

---

### Post by ajgreeny on 2006-09-21
How do you connect to the internet (or how are you trying to connect)?  Modem or ethernet card or wireless.  A network card wired to a router/modem is probably easiest, usb modems can be a big problem for linux in general, not just ubuntu.

---

### Post by tseliot on 2006-09-21
I think that you should install Ubuntu 32bit since you're new to Ubuntu. And yes, you can use a 32bit Operative System even if you have a 64bit CPU

---

### Post by tymek666 on 2006-09-21
> **tseliot said:**
> I think that you should install Ubuntu 32bit since you're new to Ubuntu. And yes, you can use a 32bit Operative System even if you have a 64bit CPU

Well, i think that in this case 32bit version won't help...

---

### Post by Kilz on 2006-09-21
> **tseliot said:**
> I think that you should install Ubuntu 32bit since you're new to Ubuntu. And yes, you can use a 32bit Operative System even if you have a 64bit CPU

Network problems tend to be just as hard to solve no matter what version you are running.

---

### Post by acefreely on 2006-09-22
Open a terminal, run "ifconfig -a" and paste the output here.  Also run "lsmod" and paste the output here.

If you are not a "computer tech" this could be a difficult challenge for you.  That said, the best way to learn is by searching the internet and trial and error.  Keep at it, persistence is key.  And use the forum search features.

---

### Post by backinblack on 2006-09-23
Acefreely(love that screen name!) you are right. That is how I have learned what little I do know about computers.
kilZ, you might be right. This system is very different from any that I have come across, but I still want to hang in there with it.
Its different, and a little frustrating, but it is also very exciting as well!!!
The following might be useful for some. I came across this in the ASUS CD. [email]linux-nvidia-bugs@nvidia.com[/email]
The address is valid, and I sent an e-mail to them with all the info, so maybe I'll get an answer soon.:D

---

