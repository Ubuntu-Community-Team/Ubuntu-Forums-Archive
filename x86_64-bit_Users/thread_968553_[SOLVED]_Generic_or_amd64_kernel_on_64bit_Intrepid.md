---
title: "[SOLVED] Generic or amd64 kernel on 64bit Intrepid?"
date: 2008-11-02
forum: x86 64-bit Users
---

### Post by PinkFloyd102489 on 2008-11-02
Ive got 64bit Intrepid installed, which was upgraded from 64bit Hardy. My current kernel is 2.6.27-7-generic. Im just wondering how installing the amd64 kernel would fair on my system.

Specs:

Intel Core 2 Duo 2.4Ghz 800Mhz FSB
Nvidia GeForce 8600M GT 256MB
320GB SATA HD
SoundBlaster Audigy SE
Dell 1505 Wireless N mini PCI card


The main part Im worried about is the wireless card. It has the bcm4328 chipset and is currently using the "wl" driver.


Opinions?

---

### Post by cariboo on 2008-11-02
If you got a 64bit distribution installed you already have a 64bit kernel installed, the reason it is called a generic kernel it is designed to run on all 64bit capable computers, whether it is a single core or a quad core, they all use the same kernel.

To create a kernel specific to your computer you would have to compile a custom kernel. Here is a howto:

[http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)

Jim

---

### Post by Yellow Pasque on 2008-11-03
Don't be confused by "amd64". That's just the name of the architecture (AMD invented it, Intel copied it and named it EMT64 for their CPU's). Both AMD and Intel processors are supported by the generic kernel.

The other available kernels are: server, virtual, and rt (real-time)

---

### Post by roelpeeters on 2008-11-03
To make absolutely sure you can always try the following command in the terminal:

```

uname -a

```

The output of this command shows your kernel version and build date. If you are running 64 bit, you should see the string 'x86_64' in the output of the command.

Roel

---

### Post by PinkFloyd102489 on 2008-11-03
Ah ok, thanks. I just thought there were different ones since the Nvidia drivers have three different builds for IA32, x86_64, and IA64.

---

