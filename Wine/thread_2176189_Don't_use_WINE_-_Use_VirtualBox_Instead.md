---
title: "Don't use WINE - Use VirtualBox Instead"
date: 2013-09-23
forum: Wine
---

### Post by Dave_Reeves on 2013-09-23
vBox is open source, and you can install windows 7 or 8 with a KMS to make them activate as Genuine

---

### Post by santosh83 on 2013-09-23
Virtualisation generally sucks for games. I don't get the kind of framerates for Morrowind in VirtualBox like I do on WINE.

---

### Post by sudodus on 2013-09-23
I have installed a virtual machine using ***KVM***, ***qemu***, and ***virt-manager*** according to this wiki page

[https://help.ubuntu.com/community/KVM/VirtManager](https://help.ubuntu.com/community/KVM/VirtManager)

It works very well, for example it is easy to use ***USB pendrives***, also to boot from them, and to use ***image files*** (dd-cloned images) as virtual disks. Select [FONT=comic sans ms][SIZE=4]**i**[/SIZE][/FONT], the tab with the setup information about the virtual machine. Right-click in the window for specifications and select 'Add Hardware'. Select managed or other existing storage, and click the button 'Browse local'.

- Select the block device for the USB pendrive, for example **[FONT=courier new]/dev/sdb[/FONT]**, and
- Select the file for the dd-cloned image, for example [FONT=courier new][B]dd_lubuntu-13.04-obi-sept1_4GB.img
[/B][/FONT]
The host machine must use either Intel VT or AMD-V chipsets that support hardware-assisted virtualization, and it must be activated or possible to activate in the BIOS, otherwise KVM will work but very slowly (qemu software virtualization), and VirtualBox might be be faster. See this link
[URL="http://pic.dhe.ibm.com/infocenter/lnxinfo/v3r0m0/topic/liaai.kvminstall/liaaikvminstallenable.htm"]
http://pic.dhe.ibm.com/infocenter/lnxinfo/v3r0m0/topic/liaai.kvminstall/liaaikvminstallenable.htm[/URL]

and this overview link [URL="http://www.linux-kvm.org/page/Main_Page"]http://www.linux-kvm.org/page/Main_Page
[/URL]

---

### Post by santosh83 on 2013-09-23
> **sudodus said:**
> I have installed a virtual machine using ***KVM***, ***qemu***, and ***virt-manager*** according to this wiki page

[https://help.ubuntu.com/community/KVM/VirtManager](https://help.ubuntu.com/community/KVM/VirtManager)

The host machine must use either Intel VT or AMD-V chipsets that support hardware-assisted virtualization, and it must be activated or possible to activate in the BIOS, otherwise KVM will work but very slowly (qemu software virtualization), and VirtualBox might be be faster. See this link
[URL="http://pic.dhe.ibm.com/infocenter/lnxinfo/v3r0m0/topic/liaai.kvminstall/liaaikvminstallenable.htm"]
http://pic.dhe.ibm.com/infocenter/lnxinfo/v3r0m0/topic/liaai.kvminstall/liaaikvminstallenable.htm[/URL]

and this overview link [URL="http://www.linux-kvm.org/page/Main_Page"]http://www.linux-kvm.org/page/Main_Page
[/URL]

My processor is Intel Pentium (formerly Dual-Core) E2140 (Allendale core) and I don't think it supports either Vandepool or Pacifica technologies. :-(

But I'm told games are slow even with hardware virtualization since the virtual machine usually has no hardware graphics acceleration. So when a game works under WINE I happily use run it under Linux otherwise I just dual-boot. 

But I do plan to use VirtualBox for testing various Linux distros, other Ubuntu flavours and even alternatives like FreeBSD, just to get a feel for what's out there. :-) I suppose since my processor doesn't support hardware virtualization KVM would offer no real benefits over VirtualBox...

---

### Post by vasa1 on 2013-09-23
> **santosh83 said:**
> ... I suppose **since my processor doesn't support hardware virtualization** KVM would offer no real benefits over VirtualBox...
I'm not sure you'd get KVM to work at all then. I didn't try KVM at all when I learned my processor didn't support hardware virtualization.

---

### Post by patrick19 on 2013-09-23
I used to try this method on supported hardware for a few applications that would not run in wine at the time. Personally IMHO, if you're going to the extent to even touch a Windows installation, no point in not just doing a dual-boot.

---

### Post by bapoumba on 2013-09-23
Please remember we do not allow illegal activities on the forums.

---

### Post by Dave_Reeves on 2013-09-24
I use Steam, windows 7 guest in VirtualBox (Ubuntu host), to play many multi-user games without any problems

---

