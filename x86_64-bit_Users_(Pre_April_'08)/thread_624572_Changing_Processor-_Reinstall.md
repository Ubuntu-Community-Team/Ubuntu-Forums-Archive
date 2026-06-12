---
title: "Changing Processor- Reinstall?"
date: 2007-11-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by SuperSack56 on 2007-11-27
I'm about to upgrade my machine. It's currently running 64-bit ubuntu, on an AMD Athlon64 3200+. I'm going to put in a Quad Core Intel Q6600, new motherboard, RAM, and video card. Since the new CPU is also 64-bit, will I have to reinstall ubuntu? I'm not sure what the increase in cores will do- I'd expect it to handle everything gracefully, but if I'm going to have to reinstall, I'd like to prepare in advance.

Thanks!

---

### Post by Kilz on 2007-11-27
> **SuperSack56 said:**
> I'm about to upgrade my machine. It's currently running 64-bit ubuntu, on an AMD Athlon64 3200+. I'm going to put in a Quad Core Intel Q6600, new motherboard, RAM, and video card. Since the new CPU is also 64-bit, will I have to reinstall ubuntu? I'm not sure what the increase in cores will do- I'd expect it to handle everything gracefully, but if I'm going to have to reinstall, I'd like to prepare in advance.

Thanks!

You shouldnt have to reinstall.

---

### Post by nzadLithium on 2007-11-27
kilz are u sure? processor modules are meant to be permanent doesnt that mean that they shouldnt be changed?

I'm not sure but to me it seems permanent means it doesnt change. Plz tell if im wrong though.

and id like to say thx for that flash install script makes it so easy to get flash on 64bit. :)

---

### Post by Kilz on 2007-11-27
I know from experience that you can upgrade a processor, as long as it is 64bit and it isnt necessary to reinstall. But rereading the original posters post, he should be ready to reinstall the video drivers. That is going to be the pain of the whole thing. Especially if switching from one made by ati to nvidia or vice versa.
But it never hurts to backup stuff just in case.

---

### Post by nzadLithium on 2007-11-27
ok so if the processor was 32bit and you upgrade it to another 32 bit or you processor was 64bit and you upgrade it to another 64bit you dont need to reinstall?

---

### Post by saru411 on 2007-11-27
from past experience if your installation wouldnt work if you moved your hdds to another type of mobo. im not sure how this works on ubuntu, but in my former experience installing xp i could change hdds from same type mobos, not different mobos. if you installed with a separate /home partition you should be able to reinstall without losing anything on that partition.

---

### Post by mystran on 2007-11-27
If the architecture stays the same, and the kernel you are using has all the necessary features/modules, then moving a linux-install from one system to another will work just fine.

I've moved installs from one system to another, often with no common hardware (not even HDs) and never had a failure other than some device driver issues with custom built kernels. Unless you've recompiled your own kernel, you should be safe. If you keep the same HD it's even easier as you don't need to move anything over.

Windows is a lot harder to move from a system another.. a linux system is really just a kernel and a bunch of files. :)

---

### Post by nzadLithium on 2007-11-27
awesome :D

---

### Post by mystran on 2007-11-27
> **nzadLithium said:**
> awesome :D

Oh and ... well... display driver trouble can still happen.. especially if switching from ati to nvidia or back, so might be good idea to print the "how to install <newvideo> drivers" stuff and/or keep the old video card nearby, if/when you end up with X not starting up.

---

### Post by magikx21 on 2007-11-28
I've fallen into the hell of doing similar things using Windows and learned to plan for a reinstall. If your transition works without a reinstall let's us know because I could understand maybe a CPU upgrade working without a problem but CPU, mobo and switching brands even...I can image how bad this would end up in Windows.

---

### Post by RAOF on 2007-11-28
Another thing to check for is the ordering of your hard drives.  Mounting your filesystems (/, /home, etc) will likely break if you've changed /etc/fstab at some point and are using device names (/dev/sda1, etc) to mount your various partitions/hard drives since the device naming will likely change.

If your /etc/fstab is using UUIDs or labels everywhere then you don't have to worry about this.

---

### Post by david_2001 on 2007-11-28
> **magikx21 said:**
> I've fallen into the hell of doing similar things using Windows and learned to plan for a reinstall. If your transition works without a reinstall let's us know because I could understand maybe a CPU upgrade working without a problem but CPU, mobo and switching brands even...I can image how bad this would end up in Windows.
Windows would blow all of its fuses if you tried this but GNU/Linux really is made of different stuff.  Do the swap in a considered way, e.g. by switching to a generic video driver before shutting down the old system for the last time, and there's no reason why the new system shouldn't boot up as if nothing happened.

---

### Post by mystran on 2007-11-28
> **magikx21 said:**
> I've fallen into the hell of doing similar things using Windows and learned to plan for a reinstall. If your transition works without a reinstall let's us know because I could understand maybe a CPU upgrade working without a problem but CPU, mobo and switching brands even...I can image how bad this would end up in Windows.

There's a simple difference between a typical Linux system, and a typical Windows system, that makes the Linux system not care of the mobo or a cpu, or the brand of network card, soundcard (and to a limited extend) even video cards are swapped.

You see.. it's the driver installation. You remember installing drivers for you cpu/mobo/networkcard when you installed Linux? I don't think so. Every time you start a Linux system, it'll check what hardware is present in the system, then tries to find the right drivers (if they aren't in the kernel already, which is also possible). The windows system on the other hand, has a database of installed drivers, which it then tries to load.

You can move a windows install from a box to another. You'll just need to tell it before hand that when it boots next time, you want it to do full hardware detection. I think the tool is called "sysprep" and ships on the install CD.

Anyway, Linux does full detection on every boot anyway. As long as it can find enough drivers to get the system up and running, it'll work. 

The only major exception to this rules is video drivers, 'cos they are handled by X, which wants a configuration file that says what driver you want to use.. and if the video card that X detects doesn't match the one specified in the configuration file (think it's /etc/X11/xorg.conf in modern Ubuntu) then you don't get a graphical login. You can almost always login on command line, edit the configuration file to suggest the right driver, then write "sudo /etc/init.d/gdm restart" or something similar to restart the graphical interface, and you're happily running in the graphics land again. Granted, not really that newbie friendly, but not exactly rocket science either.. alternatively I guess even just telling apt-get/aptitude to install the right nv/ati binary driver packages might fix the thing (not sure though).

---

### Post by SuperSack56 on 2007-11-29
Hey guys, thanks for all the responses.

I'm keeping all the same hard drives, etc- but adding two additional ones. I'll probably not even add them until the system is up and running with the new mobo/cpu/ram.

The old video card is an AGP Nvidia (i forget which model), and it's being replaced with a pci-e nvidia card. in theory, that should simplify things a little bit. thanks for the heads-up about that, though. that'll probably save me quite a bit of head-banging.

anyway, the hardware comes in the mail tomorrow (or so says UPS), so I'll post an update on how it goes when i get it all in there.

---

