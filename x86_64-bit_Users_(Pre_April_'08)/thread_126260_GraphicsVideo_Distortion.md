---
title: "Graphics/Video Distortion"
date: 2006-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by aqwabawks on 2006-02-06
Hello,

I'm still fairly new to using Linux.  I just installed Kubuntu 5.10 (Breezy) today on my AMD X2 3800+ (with 250 GB Western Digital SATA HDD, NEC DVD+/-RW, Nvidia GeForce 6600GT PCI-Express, 1.0 GB Dual Channel RAM) and have encountered some problems.

Every so often areas of the screen turn purple-ish, sometimes encompassing the whole screen.  I figured this might be due to the fact that I didn't select my exact monitor model during setup (I had this option in previous Linux installs) and noticed that although my resolution was 1024x768 and the refresh rate was 60 Hz.  I thought this might incorrect so I found my monitor's (Viewsonic A75f) specifications and edited the setup file that contains the data for the monitor.

Initially, after I made the edits, the screen seemed to work fine but the purple stuff came back...  I was just wondering what I'm missing in trying to fix this error?  It's troublesome because each time it happens I have to either close the application or minimize and resize all the windows to get it to disappear.

Thanking you all for your time,

Aqwabawks

---

### Post by SleepyHollow on 2006-02-16
[QUOTE=aqwabawks]Hello,

I'm still fairly new to using Linux.  I just installed Kubuntu 5.10 (Breezy) today on my AMD X2 3800+ (with 250 GB Western Digital SATA HDD, NEC DVD+/-RW, Nvidia GeForce 6600GT PCI-Express, 1.0 GB Dual Channel RAM) and have encountered some problems.

Every so often areas of the screen turn purple-ish, sometimes encompassing the whole screen.  [/QUOTE]

Hi there,

no answer for this problem for a week? I got the same problem with breezy kubuntu live CD. It was just the same with i386 and Amd-64. Tried orginal ubuntu without "KDE" (live cds 32bit and 64bit) and it works out of the box. I'm now using AMD64Bit Ubuntu with Gnome installed on harddisk without problems.

My configuration:

motherboard: GA-K8-NF9
cpu: AMD64 3000+ Winchester
graphiccard: NV 6600GT Pcie

Seems to be a problem of the opensource driver in combination with KDE and the Nvidia card. Could be solved after installation of the original nvidia-driver. But i'm not sure of this, found some tipps in other posts but nothing serious. If you want to give it a try with the original nvidia-driver, please post your results.

---

### Post by KoldKay on 2006-02-16
I think I see a correlation, lads.  I also get it, especially on Konquerer and the menus.

And what am I running, I hear you cry?
AMD Athalon 64 3000+
**Geforce 6600 GT** AGP-8x

I think it's support for the Geforce 6600 GT.  I'm thinking about getting the drivers off Nvidia then running them from failsafe mode (which I have no problem running)

---

### Post by SleepyHollow on 2006-02-20
Hi there,

is the problem solved with the original nvidia-driver? I'm thinking about a new installation of 32-Bit-Ubuntu. 64-Bit being under slow development really sucks. Maybe I use Kubuntu this time, but only after one of you had posted sucess.

---

### Post by loafula on 2006-02-21
i had a different problem with the default nv video driver supplied with ubuntu i386/amd64 on my 6600 GT. my screen came up all garbled once X started. I switched to the generic vesa driver to solve the problem till I got nvidia's official driver installed. not sure if this helps to solve your problem, but from what ive experienced, the official driver from nvidia.com works much better than the default nv driver.

---

### Post by Daggett on 2006-02-22
The 6600 cards are funky, so I'm betting it is a driver problem.  Best to try the latest nvidia drivers.  If I were you, I'd compile the kernel and compile the drivers instead of installing the packaged version. 

This isn't likely to be YOUR problem, but I also got this kind of distortion under two conditions:

1. Cable is bad or loose
2. Using a KVM switch that isn't up to snuff

---

