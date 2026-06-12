---
title: "x86_64 stability and memory issues"
date: 2009-10-12
forum: x86 64-bit Users
---

### Post by ternarybit on 2009-10-12
I am interested in 64-bit computing, but stability matters more to me at this point than addressable memory. I rely heavily on a rock-solid machine, so would I be unwise to run x86_64? What are your experiences with stability in x86_64 vs. x86?

Also, when I have installed the amd64 version before, I noticed that system monitor recognizes 3.8GB RAM. All 4096MB are detected in BIOS (I have memory remap feature on). Is there any reason I would miss out on the final ~200MB? somewhat anal of me, but I just want to make sure it's not indicative of a problem.

If it matters, I have 4GB OCZ 2x2GB PC2-6400 w/ Core2Quad Q9500 on Asus P5W DH Deluxe. Thank you!

---

### Post by SoftwareExplorer on 2009-10-12
I have a Asus P5VM SE motherboard, so my motherboard is probably pretty close. I usually only see about 3G of ram on my machine, but I think that is because some of it is used for graphics. Maybe your graphics card is using 256 MB of ram?
As far as stability, I have used both x386 and 64 bit and they seem equally stable to me.

---

### Post by ternarybit on 2009-10-12
> **SoftwareExplorer said:**
> I have a Asus P5VM SE motherboard, so my motherboard is probably pretty close. I usually only see about 3G of ram on my machine, but I think that is because some of it is used for graphics. Maybe your graphics card is using 256 MB of ram?
As far as stability, I have used both x386 and 64 bit and they seem equally stable to me.

Thanks for the info.

I have a 1GB video card (radeon hd 4890). Either way, since I'm running x86_64 it should be able to address all 5GB (4 system, 1 video) with no problems. If you don't know of any problems then it's OK, I just want to be sure.

---

### Post by 3rdalbum on 2009-10-13
64-bit is just 32-bit, recompiled.

All my 64-bit-capable machines (not only the ones I own - the ones I support too) are now running 64-bit Ubuntu.

I'm missing 200 megs too but it doesn't seem to be causing any problems. It might be some sort of BIOS "feature" so you can run Windows 98 or something...

You're right, the video card's memory gets taken out of the address space, not out of the real RAM; so all 5 GiB should be able to be addressed.

---

### Post by bedtime_with_the_bear on 2009-10-13
> **3rdalbum said:**
> 64-bit is just 32-bit, recompiled.

All my 64-bit-capable machines (not only the ones I own - the ones I support too) are now running 64-bit Ubuntu.

I'm missing 200 megs too but it doesn't seem to be causing any problems. It might be some sort of BIOS "feature" so you can run Windows 98 or something...

You're right, the video card's memory gets taken out of the address space, not out of the real RAM; so all 5 GiB should be able to be addressed.

That's not entirely the case - especially for the kernel. The kernel must be true, 100% 64bit native. *User* programs, can usually just be recompiled for 64bit and become 64bit. An obvious example, is that without being true 64bit native, the kernel would be unable to correctly address the full 64bits worth of memory addresses, since the size of pointers in code that assumes 32bits will be wrong. In practice, the use command to rebuild the kernel is the same regardless, but that's because there are certain tricks that cause the 64bit version of the source to be compiled for a 64bit kernel, and the 32bit code path to be compiled for a 32bit kernel.

That 200MB you're missing is probably due to the memory usage of the kernel itself. There are certain kernel data structures that cannot be paged out to virtual memory so will constantly take up memory. The 4GB in the BIOS is just telling you what hardware was detected, not what will be usable once your OS is running.

As far as stability is concerned, I've been running 64bit Ubuntu for a couple of years, and have noticed no problems due to 64bit.

---

### Post by Slim Odds on 2009-10-13
> **bedtime_with_the_bear said:**
> That 200MB you're missing is probably due to the memory usage of the kernel itself. There are certain kernel data structures that cannot be paged out to virtual memory so will constantly take up memory. The 4GB in the BIOS is just telling you what hardware was detected, not what will be usable once your OS is running.

As far as stability is concerned, I've been running 64bit Ubuntu for a couple of years, and have noticed no problems due to 64bit.

Let me address stability first. My personal experience is that the 64 bit version seems **more** stable that the 32 bit version. I don't have any hard data to back this up, it's just my opinion.

As far as the missing 200MB, there is some space reserved below 4G. This is for legacy 32 bit hardware devices that cannot be mapped into space above 4G. Some older video cards, network adapters, etc. might need this.

Most modern motherboards know about this and provide a "memory hole" feature (sometimes under different names) to keep this space open without giving up RAM.

---

### Post by mad_max0204 on 2009-10-14
Turn off memory remap

I've got 8gb working

---

### Post by tuxxy on 2009-10-14
64-bit is very stable! I have to agree slimodds with the native 64-bit packages and plugins its fast and stable, you should have no worries about using 64-bit Ubuntu everyone one will soon :D

You wont see the memory as its allocated to specific pc components for example video cards.

---

### Post by RoboNuggie on 2009-10-16
Just to backup everyone else's opinion, that 64-bit is stable... I am running 64-bit on my server, HTPC (Mythbuntu) and desktop....  if you have a 64-bit machine, you might as well run 64-bit...

---

### Post by Arup on 2009-10-16
Been using x64 since the day Ubuntu launched it. Earlier on there were few apps here and there that would give some minor glitches but by Hardy, everything was AOK.

---

