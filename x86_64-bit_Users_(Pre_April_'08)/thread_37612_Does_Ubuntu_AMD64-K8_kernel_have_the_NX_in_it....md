---
title: "Does Ubuntu AMD64-K8 kernel have the NX in it..."
date: 2005-05-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by Optimal Aurora on 2005-05-27
I have been using windows alot for a while because of this feature of the amd64 processor that stops viruses (something about enhanced virus protection)...

You can find more info on the it here... [http://www.amd.com/us-en/Weblets/0,,7832_11104_11105,00.html](http://www.amd.com/us-en/Weblets/0,,7832_11104_11105,00.html)

Thanks...

---

### Post by ::DoGG:: on 2005-05-28
Well i don`t know very much but i think that in Linux You have WAY BATTER protection against viruses that in Windows. Viruses is most a Windows problem, cause all the windows environment is pretty the same (depends from ver.) Since in Linux You have so many differences ( different libraries versions, different kernels and so on) in linux , viruses even when they exists they don`t have much space to duplicate on another machines because of that. For me is an obvious that on Linux, even without antivirus i`m more protected then in Windows (with service pack or without). I just wouldn`t botter so much abut that "Virus protection " thing. For me it`s just another marketing tip :D

---

### Post by Optimal Aurora on 2005-05-28
Yah that is a fact although you do have to still be careful of what you use because even though the code is open, it still could have malicious strings attacted...

---

### Post by ::DoGG:: on 2005-05-28
Sure thing... But to be ohnest.. most of the people that even touch linux know how to recognize the virus and kill that damn thing :D ( last time i had virus on my machine was like 1,5 year ago).

---

### Post by Optimal Aurora on 2005-05-29
Yah you have a point... Otherwise, they wouldn't be using linux (heck that also applies to Mac OSX). They would be sitting there at their workstation (excuss me personal computer and calling tech support because they encounter an error or some problem they don't know how to fix...

---

### Post by ::DoGG:: on 2005-05-29
Yeah, exactly... Asking tehc supprt guy  a question like "How do i check which browser do i use" :D :D

---

### Post by sir4taye on 2008-02-27
but seriously, can we find out about the Enhanced Virus Protection capabilities. I'd like all the ammo I can get in propigating. Someone shed some light on this.

---

### Post by Yellow Pasque on 2008-02-27
From wikipedia ([http://en.wikipedia.org/wiki/NX_bit](http://en.wikipedia.org/wiki/NX_bit))
> Linux kernel currently supports standard hardware NX on CPUs that support it, such as the current 64-bit CPUs of AMD, Intel, Transmeta and VIA.

The support for this feature in the 64-bit mode on x86_64 CPUs was added in 2004 by Andi Kleen, and later the same year, Ingo Molnar added support for the NX bit in 32-bit mode on 64-bit CPUs. These features have been in the stable Linux kernel since release 2.6.8 in August 2004.

The availability of the NX bit on 32-bit x86 kernels, which may run on both 32-bit x86 CPUs and 64-bit x86 compatible CPUs, is significant because a 32-bit x86 kernel would not normally expect the NX bit that an AMD64 or IA-64 supplies; the NX enabler patch assures that these kernels will attempt to use the NX bit if present.

Some desktop Linux distributions such as Fedora Core 6, Ubuntu and openSUSE do not enable the HIGHMEM64 option, which is required to gain access to the NX bit in 32-bit mode, in their default kernel; this is because the PAE mode that is required to use the NX bit causes pre-Pentium Pro (including Pentium MMX) and Celeron M and Pentium M processors without NX support to fail to boot. Other processors that do not support PAE are AMD K6 and earlier, Transmeta Crusoe, VIA C3 and earlier, and Geode GX and LX. Older versions of VMware, and even current versions of Microsoft Virtual PC and Parallels does not support PAE on the guest. Fedora Core 6 does provide a kernel-PAE package which supports PAE and NX though.

Non-execute functionality has also been present for other non-x86 processors supporting this functionality for many releases.

So, if you're running an amd64 or an i686 optimized kernel, everything's gravy. Note that Ubuntu chose backward-compatibility with 386-class hardware over the features and optimization for their x86 distro. However, one could still compile their own kernel and enable the i686 features if so inclined.

---

