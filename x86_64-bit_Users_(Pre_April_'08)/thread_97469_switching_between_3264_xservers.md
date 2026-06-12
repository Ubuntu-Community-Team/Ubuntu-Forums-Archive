---
title: "switching between 32/64 xservers?"
date: 2005-12-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by nalmeth on 2005-12-01
I have a Gigabyte Motherboard, with built in Intel Graphics card, and Intel pentium 4 processor with hyperthreading. Here are model names:
Motherboard: GA-81915ME-GL
Graphics: Intel 82915G express (915gl series)
NVIDIA and ATI drivers don't work.
this page has possibly working graphics drivers for linux:
[http://downloadfinder.intel.com/scri...9&submit=Go%21](http://downloadfinder.intel.com/scri...9&submit=Go%21)
The only installation types available are a tarball and an rpm. 
The packages on this site are in fact 3D-accelerated xservers aparently, and are only available for i386 architectures. 
As far as I know, there are no other easy solutions to getting this graphics driver.
I already have a 32-bit chroot environment set up, and my thinking is that I can install this xserver simply for the chroot environment, and keep my current amd64 xserver intact. 

If I set up this 32-bit chroot 3D-accelerated environment, could I run 3D apps in my AMD64 session by symlinking the app? Or would I have to change between servers entirely?
If so, is there an easy way to set up interchanging xservers?

Thanks for any suggestions

---

### Post by RAOF on 2005-12-01
Of course the ATI & nVidia drivers don't work - they're for ATI & nVidia cards, respectively ;)

I don't have an Intel card myself, but I believe they have the second-best open-source drivers available (behind old ATI cards).  You should be able to get everything working by just selecting the "intel" driver when you configure X (using "sudo dpkg-reconfigure xserver-xorg", if you need to).

I'm not sure how a 32bit X server would interact with the chroot environment, but my guess is that it would be a pain to set up.

---

