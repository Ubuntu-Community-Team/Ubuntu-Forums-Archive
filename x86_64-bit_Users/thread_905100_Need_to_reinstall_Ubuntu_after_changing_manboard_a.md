---
title: "Need to reinstall Ubuntu after changing manboard and chipset?"
date: 2008-08-30
forum: x86 64-bit Users
---

### Post by Milleman on 2008-08-30
Hi!

I recently upgraded my computer case with a new CPU, mainboard and graphic card. Migrated from following setup:

CPU: AMD Athlon X2 4200
Mainboard: NVIDIA Nforce
Graphics: NVIDIA 8600 GT

To this:

CPU: AMD Phenom X4 9850
Mainboard: AMD/ATI Chipset 780G
Graphics: NVIDIA 8800 GT

In reality: The harddisk were changed from one system to another, even if the case were the same. The old Ubuntu installation booted fine under the new hardware though.

Anyway... After the hardware upgrade, I noticed that my Ubuntu system began to lock and sometimes hang while doing heavy graphic or running WMVare with a couple of virtual computers running simultaneous.

My question: -Do I have to reinstall Ubuntu from scratch, or do the existing installation readjust itself to the new hardware without any problems?

(Using Ubuntu Hardy 8.04 64 bit)

---

### Post by DemonBob on 2008-08-30
It should readjust itself. I would consider uninstalling, and reinstalling the nvidia drivers though.

---

### Post by Milleman on 2008-08-30
DemonBob,
Do I uninstall with the Synaptic Package Manager?

I haven't done this before. Ubuntu installed the NVIDIA driver by itself, when I installed it for the first time on the original hardware configuration.

---

### Post by cariboo on 2008-08-30
Use synaptic and select complete removal, then reboot. It will then ask you to install the restricted drivers once the desktop has loaded.

Jim

---

### Post by Milleman on 2008-08-31
Jim, thanks for the reply!

Just to make sure I don't do anything regretful, I just want to confirm what modules to delete in the Synaptic.

Searching on "NVIDIA" i Synaptic, gives the following installed hits:

linux-restricted-modules-2.6.24-18-generic ==== Non-free Linux 2.6.24 modules on x86/x86_64
linux-restricted-modules-2.6.24-19-generic ==== Non-free Linux 2.6.24 modules on x86/x86_64
nvidia-glx-new ==== NVIDIA binary XFree86 4.x/X.Org 'new' driver
nvidia-kernel-common ==== NVIDIA binary kernel module common files
nvidia-settings ==== Tool of configuring the NVIDIA graphics driver
xserver-xorg-video-nv ==== X.Org X server -- NV display driver

Which of those should I select and make "Complete Removal" on?

---

### Post by oldrocker99 on 2008-09-01
I had to replace my motherboard with a completely different chipset, and I only had to reboot twice and reinstall the Nvidia drivers.

Another reason to love Linux!

:guitar:

---

### Post by Milleman on 2008-09-01
Sounds fine, but...

How did you uninstall the NVIDIA drivers? Which files?

The reason I'm asking, is that I don't want to end up with a system that can't start the XWindows.

---

### Post by Elfy on 2008-09-01
I've removed all except  xserver-xorg-video-nv ==== X.Org X server -- NV display driver in the past, one of them stopped the hardware driver tool working until it was reinstalled and rebooted.

Just remove the nvidia-glx-new it should take nvidia-kernel-common and nvidia-settings with it if you do a complet removal in synaptic I think.

You might alos need to remove linux-restricted-modules as well , but it's only an extra reboot to be sure.

---

### Post by Jouke74 on 2008-09-02
Are your virtual machines based on the "standard hardware PC" from vmware? Did you install the vmware tools? That might be a reason for crashes of that program. I think the vmware kernels are CPU specific. Don't know how it handles a Virtual Windows XP machine. Also vmware tools are much more sensitive to hardware + kernel changes which might result in the crashes.

---

### Post by Milleman on 2008-09-02
It was not the the VMWare that crashed. It was the whole Ubuntu. I mentioned VMWare as this can make the host system to take heavy workloads, just like graphic intense programs.

I have not yet uninstall / reinstall the NVIDIA drivers, as I'm currently working on a project and wait with the uninstall reboot until I'm finished.

When I'm finished, I'll post a comment here on how the NVIDIA driver trick helped killing the symptoms.

---

### Post by Milleman on 2008-09-02
It was not the the VMWare that crashed. It was the whole Ubuntu. I mentioned VMWare as this can make the host system to take heavy workloads, just like graphic intense programs.

I have not yet uninstall / reinstall the NVIDIA drivers, as I'm currently working on a project and wait with the uninstall reboot until I'm finished.

When I'm finished, I'll post a comment here on how the NVIDIA driver trick helped killing the symptoms.

---

### Post by Milleman on 2008-09-04
Worked fine!
Removing and then reinstalling the NVIDIA drivers seems to be the solution! A role of thumb when switching mainbord on a Linux system then! :)
Have not yet had any kind of hanging or freezing.

Thanks for the help guys!

---

