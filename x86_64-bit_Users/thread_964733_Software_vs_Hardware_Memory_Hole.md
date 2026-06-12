---
title: "Software vs Hardware Memory Hole"
date: 2008-10-31
forum: x86 64-bit Users
---

### Post by forbjok on 2008-10-31
When I boot from the Ubuntu Server 8.10 install CD, it gives the following warning:
> Your BIOS doesn't leave a aperture memory hole
Please enable the IOMMU option in the BIOS setup
This costs you 64 MB of RAM

The system is:
MB: MSI K8N Diamond
CPU: AMD Athlon64 X2 4400
Memory: 4GB

I'm guessing this message is because I have memory hole remapping enabled in BIOS.

I don't believe there is an IOMMU setting in the BIOS - at least if there is, I've never been able to find it. However, there are a few other settings: (these are not exact quotes, as I don't have access to the machine at the moment to see the exact names)
* Hardware Memory Hole remapping (can be on/off)
* Software Memory Hole remapping (can be on/off)
* MTRR (can be Continuous/Discrete - set to Continuous)

If I enable either hardware or software memory hole remapping, the BIOS will see the full 4GB, but if I disable both it will only see just over 3GB.

When running Windows XP x64 on the same machine before, I've had to keep both hardware and software memory hole remapping enabled to see all 4GB of the memory, and for all hardware to work properly at the same time.

I know what the memory hole is, however I've never been able to find out what the difference between software and hardware remapping is.

This machine will now be running 24/7 as a server with Ubuntu Server, so Windows will not be an issue anymore - however, I need it to run stable in Ubuntu, and preferably be able to use the full 4GB memory.

To sum it up, my questions are basically:
1. What is the difference between hardware and software memory hole remapping?
2. Which should I use for Ubuntu 64-bit: Hardware or Software memory hole remapping? Or both?
3. Is it safe to just ignore the "warning" (will the system be stable)?

---

### Post by OlorinIWas on 2008-10-31
I'm getting this message aswell, and there is nothing to do in BIOS for me...doesn't seem to be a big deal, though I had to upgrade via text as a result...now I have some bs about kinit keeping be from booting to environment.

This has been a completely horrible upgrade.

---

### Post by bpl07 on 2008-10-31
If you don't like the message you can boot with the option iommu=noaperture.  I don't have a bios setting for iommu either so I've been doing this since gutsy with no issues.

I'm not sure why it's not picking up your bios setting though, maybe filing a bug would help.

---

### Post by randiroo76073 on 2008-10-31
Google:
Software memory hole:
[http://www.google.com/search?q=software+memory+hole&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=software+memory+hole&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Hardware memory hole:
[http://www.google.com/search?q=hardware+memory+hole&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=hardware+memory+hole&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Maybe you can find an answer in these.
HTH

---

