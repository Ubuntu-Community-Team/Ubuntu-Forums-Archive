---
title: "New PCs 4800+ X2 AMDs, and nvidia chipset. no LAN?"
date: 2007-07-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by Maggoo on 2007-07-30
Hi

I've recently purchased two new desktops, which I intend to make into servers.

I want to run Ubuntu 6.06 LTS amd64 on them.

I managed to get it to install by adding the following kernel params:

noapic
nolapic
acpi=off
pci=noacpi

Ubuntu now boots ok when 'noapic' is added to the kernel params.

However, the sound and onboard LAN are not recognised.

The motherboard is a nForce 405 (MCP61S) chipset. This suggests it would need the forcedeth module, but 'modprobe forcedeth' doesn't do anything. nothing is returned, and ifconfig still only lists the loopback.

Can anyone shed any light on this?

Cheers

Miles

---

### Post by praxis22 on 2007-07-30
Might help:

[http://ubuntuforums.org/showthread.php?p=1772285](http://ubuntuforums.org/showthread.php?p=1772285)

Open a terminal window and type:

**lspci**

what does it say?

---

### Post by Maggoo on 2007-07-31
```

0000:00:00.0 RAM memory: nVidia Corporation: Unknown device 03ea (rev a1)

0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 03e0 (rev a2)

0000:00:01.1 SMBus: nVidia Corporation: Unknown device 03eb (rev a2)

0000:00:01.2 RAM memory: nVidia Corporation: Unknown device 03f5 (rev a2)

0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 03f1 (rev a2)

0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 03f2 (rev a2)

0000:00:04.0 PCI bridge: nVidia Corporation: Unknown device 03f3 (rev a1)

0000:00:05.0 0403: nVidia Corporation: Unknown device 03f0 (rev a2)

0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 03ec (rev a2)

0000:00:07.0 Bridge: nVidia Corporation: Unknown device 03ef (rev a2)

0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 03f6 (rev a2)

0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 03e8 (rev a2)

0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 03e9 (rev a2)

0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 03e9 (rev a2)

0000:00:0d.0 VGA compatible controller: nVidia Corporation: Unknown device 03d1 (rev a2)

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

0000:01:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)

```

How would I go about updating the kernel, without an ethernet card? is that possible?

Thanks

Miles

---

### Post by praxis22 on 2007-07-31
Well, that's pretty terminal. In your case the only way to update the Kernel is to burn a CD-ROM with all the tools you'll need and a new kernel. might be easier to download the .deb's than to try to compile from source, at least for the build environment. Search for the "master kernel thread" for a FAQ on how to build a ubuntu kernel.

---

### Post by Maggoo on 2007-07-31
joy :D

Is the newer kernel included in a later version of ubuntu that I could install instead?

If not, is there another debian based distro that uses it?
I think more time would be saved downloading another distro, and installing that, than burning countless CDs because i've forgotten certain files.

Thanks for your help.

Miles

---

### Post by praxis22 on 2007-07-31
Hi,

Depends on your level of technical competence. Ubuntu is for noobs, as such it's easy to use, easy to configure. You could install a base Debian distro, sidux64 for example, is cutting edge and available now. But then you'd have to do a lot more typing, and know a lot more.

Ubuntu "just works" (most of the time) :P everything else needs more or less work to achieve the same level of functionality.

Seriously, check the master kernel thread look at the initial **apt-get** line and pull all thos packages down as .deb's then download the lastest kernel and the latest patch. Burn to CD, then install the .deb's and compile away.

Might be an idea to check if your Mobo is supported by the latest kernel, what is it? Model number etc.

---

### Post by Maggoo on 2007-07-31
[http://usa.asus.com/products4.aspx?modelmenu=2&model=1547&l1=1&l2=1&l3=380&l4=0](http://usa.asus.com/products4.aspx?modelmenu=2&model=1547&l1=1&l2=1&l3=380&l4=0)

Thats the most that I can tell about my PCs, have sent an email to ambros asking for the motherboard details.

Cheers

Miles

---

### Post by praxis22 on 2007-07-31
Hi,

It's likely a noname-asus box. Mass produced, like dell motherboards, etc. 

Have you had a look here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Modems_.2F_Network](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Modems_.2F_Network)

ndiswrapper may be of some use to you, as it will allow you to use PC drivers to run your network card. so you should be able to download and expand the official drivers for XP say, and then use them with ndiswrapper.

Worth a shot.

---

