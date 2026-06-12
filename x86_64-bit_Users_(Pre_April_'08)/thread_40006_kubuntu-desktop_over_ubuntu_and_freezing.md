---
title: "kubuntu-desktop over ubuntu and freezing"
date: 2005-06-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by jyp on 2005-06-07
Freezing ... freezing... freezing...

I first installed Kubuntu (AMD64) ; freezing occured as soon as I tried to resize a window in kde.

Then I installed kubuntu-destop over Ubuntu; the freezing behavior was not cured at all.

Then I installed kubuntu-desktop over Ubuntu (i386) with the kdm display manager: instant freezing.

Then I changed from kdm to gdm: the freezing is much less frequent but still occurs mainly using Firefox. Sometimes, it does not freeze but every window goes blank (white).

I need a stable system for my work and it does not look good for now.

BTW, is there a i686 version that I could install on my machine (amd64)? I have given up for now on 64bits!

---

### Post by FluffyElmo on 2005-06-07
Could you give more information on your machine? Motherboard model or chipset, video card installed, amount of RAM, etc. would help narrow things down.

There is an i686 (and k7) kernel available in Synaptic if you are running the i386 install. There is also a k8 kernel if you are running the amd64 install.

---

### Post by jyp on 2005-06-07
Will, in your opinion, changing kernel to K7 or K8 increase the instability of the system? It seems that the i386 is the basis on which Ubuntu is built.

Of course, I would like to take full advantage of my machine and this has not been the case up to now; I worked with Debian for quite a while and had a lot of problems. So I hoped that Ubuntu (Kubuntu) could help me; it is not the case yet but I am more than willing to stick with the Ubuntu community if there is hope coming out of the tunnel.

In short, my system is built as follows :

motherboard : MSI K8N Neo2 Platinum
chipset : nVidia nForce3 Ultra
cpu : AMD Atholon64 S939 3500
memory : Corsair 400 MHz, DDR, PC3200C2, 2GB (2x TwinX(2x 512MB)
video card: Asus AGP GF6 V9999/GT/TD 128 DDR3 nVidia 6800
hard disks: Western Digital Sata Raptor 36GB + 2 Sata Caviar 200GB
dvdrom: LG
dvr: Pioneer 108

If useful, I could post outputs of lspci, dmeg, /proc.

Thank you

---

### Post by FluffyElmo on 2005-06-07
I'd recommend the processor specific kernels, you should get a bit of a performance increase and I've had no problems to speak of. Also the generic kernel has (had?) problems with more than 900mb of ram, the processor specific kernels generally don't. 

Try disabling RenderAccel in xorg.conf (Option "RenderAccel" "false"), as mentioned in this thread:
[http://ubuntuforums.org/showthread.php?t=24703&page=2&pp=10&highlight=freeze](http://ubuntuforums.org/showthread.php?t=24703&page=2&pp=10&highlight=freeze) 

You can also try installing the latest Nvidia drivers, or if it is a kernel issue you can try the development kernel from the Breezy repositories.

---

### Post by jyp on 2005-06-07
Thank you FluffyElmo

[QUOTE=FluffyElmo]
Try disabling RenderAccel in xorg.conf (Option "RenderAccel" "false"), as mentioned in this thread:
[http://ubuntuforums.org/showthread.php?t=24703&page=2&pp=10&highlight=freeze](http://ubuntuforums.org/showthread.php?t=24703&page=2&pp=10&highlight=freeze) 
.[/QUOTE]

There is no (Option "RenderAccel" "false") in my /etc/X11/xorg.conf file maybe because I did not yet upgraded the nvidia driver.

As for the kernel, I suppose that I could get it using apt-get instead of Synaptic. Being a newbie, I try to avoid the front end stuff in order to train myself on the shell level.

---

### Post by FluffyElmo on 2005-06-07
Try disabling USB2 in your BIOS, I think I remember reading that some people have had problems with it and the nforce3? If it doesn't help you can just re-enable it.

You should be able to install the latest Nvidia driver using the link below:
[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver) 

I like Synaptic for the easy search and browsing, but you should be able to find and update the kernel from the command line using the commands below...
```
sudo apt-get update
apt-cache search linux-image
//Choose the kernel and install ie, for the k7 processor...
sudo apt-get install linux-image-k7 

```

If you still have problems with the latest Nvidia driver installed we can start looking at dmesg and lspci. Good Luck!

---

