---
title: "Bulding a kernel optimized for 64 bit, but running 32 bit programs?"
date: 2006-10-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by enigma_0Z on 2006-10-29
Will this work?

I'm building my kernel right now. I've simply changed the processor type in the kernel config. My questions are:

1. Does this make the kernel a 64-bit kernel (I changed it to "Opteron/Athlon64/Sempron"
2. Will this screw with the rest of my installation?
3. Are there any other programs that I should make 64-bit too?
4. Should I just change my arch completely over?

Finally, the reason that I'm trying this is because I've had some problems with the x86-64 version of ubuntu, mostly with some programs being really broken (synaptics touchpad driver, decss, ndiswrapper). If this won't work is there a way that I can keep my happy 32-bit system and then pick and choose which amd64 apps I want to be installed?

---

### Post by cocteau on 2006-10-29
1. No. It does however allows the kernel to take advantage of some of the instruction code unique to your processor, in effect making it run faster.

2. Probably not, although I can't say for sure, but I can't imagine how that would really be possible.

3. As much as possible really, but most packages are already build for 64 bit so there is no real need for compilation of programs specifically for your system.

4. From what to what? In my experience running 64bit with a few 32bit apps (firefox and wine) has posed very few problems so I would recommend doing that.

And finally. No theres is no way, none, to make 64bit programs run on a 32bit platform, even if your processor is 64bit. Backwards compatability only.

Hope that helps.

---

### Post by enigma_0Z on 2006-10-29
> **cocteau said:**
> 1. No. It does however allows the kernel to take advantage of some of the instruction code unique to your processor, in effect making it run faster.

Then what does make my platform a "64-bit" platform?

> **cocteau said:**
> 4. From what to what? In my experience running 64bit with a few 32bit apps (firefox and wine) has posed very few problems so I would recommend doing that.

From x86 (or 386?) to x86-64?. I've got an existing installation of ubuntu, but it's the x86 version. I guess my question is what constitutes a 64-bit installation and how can I switch over?

> **cocteau said:**
> And finally. No theres is no way, none, to make 64bit programs run on a 32bit platform, even if your processor is 64bit. Backwards compatability only.

Hope that helps.

Is there a way, however, to pick and choose which apps I move over to 64-bit? How would I do this if I changed my system over to 64-bit?

---

### Post by cocteau on 2006-10-29
It is the OS that determines if the platform is 64bit or not. If you install the amd64 (or x86_64) version of ubuntu you would have a 64bit platform. 

There's still a point to optimizing the kernel for your own processor though, as it will then take advantage of the instruction codes unique to your processor making some processes faster.

Unfortunately there is no way to 'upgrade' your system from 32 to 64bit. There is just the slow and painful format and reinstall, so if you want to make the switch that is what you have to do.

Finally, with regards to your programs I would do a bit of research first to see if a 64bit version exists and install that instead. I cannot imagine that config files and profile information wouldn't be stored the same on both 32 and 64bit versions.

Compilation shouldn't be nescessary since if the program can be compiled for 64bit somebody else has already done it and placed it in the repos.

If a program doesn't exist as native 64bit you can install the 32bit version with a bit of help. There are some very useful guides around here to help you with that. Another user called Kilz has made an install script for a 32bit firefox with flash and java that just works. Look for it in his signature.

The only issue I am having at the moment is getting my ATI card to display 3D graphics properly on the desktop but that's a problem with the ATI driver and not Ubuntu.

Is it worth it? In my experience definately but I also realise it is a lot of work especially if you haven't done it before. Try and search these forums for some of the many 32 vs. 64 bit debates that has been going on here.

---

### Post by RAOF on 2006-10-29
> **enigma_0Z said:**
> Then what does make my platform a "64-bit" platform?

A number of things.  First, the kernel has to run in x86-64 mode.  Just setting the architecture to "Athlon64" in the kernel config is **not** going to produce 64bit code.
Second, the instruction set of the system libraries.  Programs using the libraries **must** use the same instruction set, so x86-64 libraries can't be used by 32bit programs, and IA32 libraries can't be used by 64bit programs.

> **enigma_0Z said:**
> 
From x86 (or 386?) to x86-64?. I've got an existing installation of ubuntu, but it's the x86 version. I guess my question is what constitutes a 64-bit installation and how can I switch over?

You switch over by installing the AMD64 version from a CD.  The package manager (apt/dpkg) is just not capable of doing an "upgrade" from one architecture to another.

> **enigma_0Z said:**
> 
Is there a way, however, to pick and choose which apps I move over to 64-bit? How would I do this if I changed my system over to 64-bit?
[/quote]
No.  To change your system over to 64bit, you **reinstall**.  You can keep all your config (if you've got your /home on a separate partition), but all your programs and libraries get replaced.

---

