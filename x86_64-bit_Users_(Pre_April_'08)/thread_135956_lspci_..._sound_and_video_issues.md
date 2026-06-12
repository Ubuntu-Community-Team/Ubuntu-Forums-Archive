---
title: "lspci ... sound and video issues"
date: 2006-02-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by dbee on 2006-02-24
I have no sound on my ubuntu64. Also the screen tends to just blot out every now and again. I have nvidia geforce 6 graphics card and an msi neo4 card which comes with a powerful DigiCell set-up, monitoring and diagnostic tool which msi 'spent many years developing' ... although they never got around to finishing from the looks of - since it only works with windows.
Anyway here's my lspci
> 
root@ubuntu64:/home/babo# lspci
0000:00:00.0 Memory controller: nVidia Corporation: Unknown device 005e (rev a3)0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0050 (rev a3)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0052 (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 005a (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 005b (rev a3)
0000:00:04.0 Multimedia audio controller: nVidia Corporation: Unknown device 0059 (rev a2)
0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 0053 (rev f2)
0000:00:07.0 IDE interface: nVidia Corporation: Unknown device 0054 (rev f3)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 0055 (rev f3)
0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 005c (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation: Unknown device 0057 (rev a3)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:05:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0161 (rev a1)


... there's alot of unknow devices in there. I followed an nvidia driver tutorial on this site before but it didn't fix anything permanently I'm afraid. Any suggestions anyone ?

These are the libraries I have from synaptic 

linux-restricted-modules-2.61
nvidia-glx
nvidia-kernel-common
nvidia-settings

---

### Post by roderikk on 2006-02-28
Hi,

I've got exactly the same LSPCI output only with the 32 bit version. I also tried to install the nvidia driver but the uknown devices won't go away. I've tried now for days to get my sound to work and searched everywhere to my knowledge. 

I've checked the alsamixer, turned off IEC, tried turning off the external amplifier, checked in groups whether I had the right to play sound card none of it worked for me. I guess the problem is that those devices show up as unknown even though when I type

cat /proc/asound/oss/sndstat it does state my card configuration as NVidia CK804 with ALC850 as it should.

Does anyone know? Thanks!

---

### Post by dbee on 2006-03-02
Hi rodderik,

I've got mine working (or almost working) by now. The sound issue was an IEC issue (I think). There are also two places that has volume control in ubuntu, the alsa mixer (assuming your using the alsa drivers) and the desktop sound controller thingy. Check both of them.

The nvidia driver issue was a matter of breezy not natively supporting the nvidia card and PCI express connector. I downloaded the nvidia installer from their website. It downloaded and installed the linux kernel module needed, plus it compiled the drivers as well. I think that you need the linux headers package from the repository as well. You should ask on irc #ubuntu

The only problem I have now is that I have to recompile the nvidia kernel module on ever reboot. I think it's a gcc problem, where the kernel doesn't recognize the fact that the nvidia driver is complied using a gcc-3.4 version. Not too sure about that one though. I'll have a look at it later on.

Anyway good luck and I hope this helped

---

### Post by roderikk on 2006-03-02
Hi dbee,

I am glad you got your sound (almost) working :-). As I am relatively new to Linux I am not exactly sure what you mean by IEC.

Thanks, Roderik

---

