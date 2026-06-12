---
title: "Problems with Yaboot (For the millionth time)"
date: 2006-02-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by andydude117 on 2006-02-19
Aight, so after having so much trouble trying to install ubuntu on my external HD because of some bug in yaboot, I decided to partition my internal.  I didn't know how many partitions I needed, so I chunked it up into 4 partitions:  OS X, Ubuntu, Swap, Boot.  I'm not sure if I needed the swap or boot partitions :confused: .

I went off to go install ubuntu on one of the partitions, and I got to the end and it said it failed the yaboot installation step.  This is the same thing that happened when I tried on my external HD, and it's really pissing me off.  How can I get this to work, and what partitions do I need to have?

Thanks,
Andy

---

### Post by linear on 2006-02-19
The easiest thing to do is set up two partitions: first partition as free space and second for OS X. Then at the partitioning step in the installer, tell it to use largest free space.

---

### Post by Ptero-4 on 2006-02-20
You don't need a boot partition, it's a bootstrap one you need. You make a 1MB partition and select "newworld boot partition" (or something similar) in the partitioner. And about yaboot. It sucks. I would like to see a fully graphical bootloader (with graphical menus and menus screen background images) for PowerPC Macs like what grub is on PC's.

---

### Post by Huck500 on 2006-02-22
Try installing without the external HD connected, if it still is. That caused a Yaboot failure for me. As soon as I disconnected my firewire HD, it worked like a charm.

I like Yaboot, graphical interface not necessary as far as I'm concerned.

---

### Post by Ptero-4 on 2006-02-23
I do like a GUI boot menu b/c I'm used to the fully eye-candy graphical from boot to shutdown look from SuSE and Fedora on x86 PC's and In the PPC platform I never saw a GUI bootloader (I have splashy to make the GUI boot and shutdown splash screens, but the text-based boot menu is quite odd in my setup and comes out like a sore thumb).

P.D: I heard that M$ paid big money to Apple on the condition that Apple had to first make their Open Firmware unable to allow GUI bootloaders. It seems to be that M$ was planning it to make hardcore Linux thinkerers bore out and get x86 PC's which have TCPA embedded.

---

### Post by jdp on 2006-02-24
Where'd you read that?  AFAIK, Apple use has boot-logo support in OF.  When you boot OS X, it's all graphical... so is Classic Mac OS.  Even using EFI in the new Macs should have a graphical boot too.

---

### Post by Ptero-4 on 2006-02-24
What do you mean by boot-logo support?
Also the OSX and OS9 bootloaders aren't multiboot capable so they aren't in the list. A good GUI bootloader should be multiboot capable so that if the user installs two OS's (Classic and OSX, Classic and Linux, OSX and Linux, etc) he won't have to peck through awfull small text menus, instead he gets a nice menu that can be activated via mouse or keyboard and behind it he gets a nice graphical splash screen to fit the graphical boot, login and shutdown logos (and yes ubuntu supports then through splashy and no, it doesn't require kernel modding/recompilation).

---

### Post by jdp on 2006-02-24
So, the Option key boot menu doesn't count in your book? ;)  I've never used it, but the boot-logo thing is used to show a graphic when powered up.  I had an RS/6000 PPC that did that, and it also had a graphical setup menu.  I haven't seen a Mc configured to do that, though.

---

### Post by Ptero-4 on 2006-02-25
It does. But I would like it to have something like the grub "hidenmenu" setting in which it shows a minimal splash screen for some seconds and then disapears and boots the default OS unless the user press a specified key b4 the timer reaches 0 (like grub does). In fact what I would like is to use grub but it's impossible b/c it's x86 only and the grub dev team says that although grub2 will be compatible with ppc and x86, the grubsplash support will only be available on x86 PC's, not in PPC Macs or the new EFI x86 Macs b/c Apple "intentionally" removed the necesary hooks of the OF and won't put them in the EFI (elilo ppl says it'll never gain the GUI capalities the old lilo had b/c of that too).

---

