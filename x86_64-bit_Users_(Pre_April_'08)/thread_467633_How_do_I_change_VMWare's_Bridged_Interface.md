---
title: "How do I change VMWare's Bridged Interface"
date: 2007-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by hiazle on 2007-06-07
I just installed VMWare server from the repos and the install went smooth. I noticed that a lot of the steps that would normally require user input were automated, which I believe brings me to my current problem. Every time I run an existing virtual machine, I get the following error:
> The network bridge on device /dev/vmnet0 is temporarily down because the bridged Ethernet interface is down.  The virtual machine may not be able to communicate with the host or with other machines on your network.

The virtual machine worked very well before reinstalling Feisty x64. If I remember correctly, the normal VMWare install script asks you which device you wish to bridge. Since that was automatically selected for me, how do I change that after-the-fact?

Thanx for your assistance in advance. ;)

EDIT: I have two NICs, a wired and broadcomm wireless (which I haven't tried to fix). My wireless nic is eth0, and the wired nic is eht1.

---

### Post by nxt on 2007-06-08
i would try running to try to reconfigure the vmvware server....

```
sudo vmware-config.pl
```

---

### Post by veloce on 2007-06-08
> **nxt said:**
> i would try running to try to reconfigure the vmvware server....

```
sudo vmware-config.pl
```

This has changed in the latest vmware to:

```
sudo vmware-config-network.pl
```

---

### Post by hiazle on 2007-06-08
> **veloce said:**
> This has changed in the latest vmware to:

```
sudo vmware-config-network.pl
```

THANK YOU VERY MUCH nxt and Veloce. That fixed it for me. I greatly appreciate your quick responses.

I LOVE UBUNTU, and especially the community!!! :D

---

### Post by tuesday20102001 on 2007-07-27
this topic is posted elsewhere,

---

