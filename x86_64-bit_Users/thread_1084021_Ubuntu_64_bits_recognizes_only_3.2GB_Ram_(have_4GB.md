---
title: "Ubuntu 64 bits recognizes only 3.2GB Ram (have 4GB)"
date: 2009-03-01
forum: x86 64-bit Users
---

### Post by Shoeman on 2009-03-01
Hey folks,

One of the main reasons for I've installed the 64 bits version is that my computer has 4GB RAM but for my surprise Ubuntu Intrepid 8.10 64 bits only recognizes 3.2GB. Have I missed any configuration I should have done?

---

### Post by howefield on 2009-03-01
> **Shoeman said:**
> Hey folks,

One of the main reasons for I've installed the 64 bits version is that my computer has 4GB RAM but for my surprise Ubuntu Intrepid 8.10 64 bits only recognizes 3.2GB. Have I missed any configuration I should have done?

I'll ask the silly question, I suppose you have double checked that you have installed the 64 bit version and not the 32 bit ?

Typing uname -m in terminal does return x86_64 ?

---

### Post by Svensk023 on 2009-03-01
I also have 4GB of RAM and it only recognizes 3GB. also on my AMD 64-bit Atholon x2 laptop, it only recognizes 1.7GB of RAM out of 2GB. So yes I would aslo like to know why this is happening

EDIT:
I ran the above code and it returned this:
i686

---

### Post by pparks1 on 2009-03-01
Are you using a computer with integrated video and it's the video card using that system RAM?

---

### Post by whoop on 2009-03-01
This got something to do with it?
[https://lists.ubuntu.com/archives/kernel-team/2008-December/003834.html](https://lists.ubuntu.com/archives/kernel-team/2008-December/003834.html)

---

### Post by Svensk023 on 2009-03-01
> **pparks1 said:**
> Are you using a computer with integrated video and it's the video card using that system RAM?

My desktop uses two independent video cards both with 512MB of memory. My laptop however has integrated video I believe. but I'm still not sure why 1 whole GB of memory goes missing on from my desktop

---

### Post by Svensk023 on 2009-03-01
> **whoop said:**
> This got something to do with it?
[https://lists.ubuntu.com/archives/kernel-team/2008-December/003834.html](https://lists.ubuntu.com/archives/kernel-team/2008-December/003834.html)

thank you whoop! that brings me some clarity, but does the same apply for 64-bit? because that's what I am running

---

### Post by boof1988 on 2009-03-01
> **Svensk023 said:**
> I also have 4GB of RAM and it only recognizes 3GB. also on my AMD 64-bit Atholon x2 laptop, it only recognizes 1.7GB of RAM out of 2GB. So yes I would aslo like to know why this is happening

EDIT:
I ran the above code and it returned this:
i686

> **Svensk023 said:**
> thank you whoop! that brings me some clarity, but does the same apply for 64-bit? because that's what I am running

@Svensk023,

Are you *sure* that the "i686" is a 64-bit OS?

---

### Post by Cracauer on 2009-03-01
Almost all BIOSes reserve close to a gigabyte for the PCI address space, even if no actual devices with memory are present there or if the devices only use a couple dozen megabytes.

You need to activate the BIOS option to remap the memory from 3.2-4.0 GB to 4.0-4.8 GB.

Up there you will be able to use it with a 64 bit kernel or with a 32 bit kernel with PAE for a total of 4 GB.

---

### Post by Svensk023 on 2009-03-01
the dvd I used to install Ubuntu is an official 64-bit dvd that came from a magazine I bought awhile ago.

---

### Post by boof1988 on 2009-03-01
> **Svensk023 said:**
> the dvd I used to install Ubuntu is an official 64-bit dvd that came from a magazine I bought awhile ago.

Is it a possibility that the installer DVD includes both the 32-bit and 64-bit OS's?

---

### Post by Svensk023 on 2009-03-01
the 32-bit OS was on the reverse side of the disk. i looked up i686 and got this
[http://linux.about.com/cs/linux101/g/i686.htm](http://linux.about.com/cs/linux101/g/i686.htm)

---

### Post by Yellow Pasque on 2009-03-01
> **Svensk023 said:**
> the 32-bit OS was on the reverse side of the disk. i looked up i686 and got this
[http://linux.about.com/cs/linux101/g/i686.htm](http://linux.about.com/cs/linux101/g/i686.htm)
You installed the 32-bit version. At this point, you can either try to reinstall with the 64-bit version, or you can use the linux-server kernel, which has PAE and can recognize up to 64GB of RAM IIRC.

---

### Post by Svensk023 on 2009-03-01
yup, I was usuing the wrong side of the dvd >.< wow I feel stupid. Well I'm currently re-installing Ubuntu 64-bit version on my desktop, then I will put it on this laptop. Thanks for all the help!

---

### Post by Shoeman on 2009-03-02
> **howefield said:**
> I'll ask the silly question, I suppose you have double checked that you have installed the 64 bit version and not the 32 bit ?

Typing uname -m in terminal does return x86_64 ?

Yeah, I'm pretty sure I'm running the 64 bits version. Have already faced a lot of problems because of this :)

$ uname -m
x86_64

---

### Post by Shoeman on 2009-03-02
> **pparks1 said:**
> Are you using a computer with integrated video and it's the video card using that system RAM?

Yep, but it's configured to use 128MB, so there is still about 670MB missing anyway

---

### Post by Shoeman on 2009-03-02
> **whoop said:**
> This got something to do with it?
[https://lists.ubuntu.com/archives/kernel-team/2008-December/003834.html](https://lists.ubuntu.com/archives/kernel-team/2008-December/003834.html)

Well, I don't think so. Not running i386 kernel.

---

### Post by Cracauer on 2009-03-02
> **Shoeman said:**
> Yep, but it's configured to use 128MB, so there is still about 670MB missing anyway

See my previous post.

Most BIOS just grab a gigabyte or close to it, whether they need it or not.

See my previous post.

---

### Post by Ianto_unite on 2009-03-02
> **Cracauer said:**
> Almost all BIOSes reserve close to a gigabyte for the PCI address space, even if no actual devices with memory are present there or if the devices only use a couple dozen megabytes.

You need to activate the BIOS option to remap the memory from 3.2-4.0 GB to 4.0-4.8 GB.

Up there you will be able to use it with a 64 bit kernel or with a 32 bit kernel with PAE for a total of 4 GB.
I'm a relative newbie to Ubuntu. how do I do this?

---

### Post by Shoeman on 2009-03-02
> **Cracauer said:**
> Almost all BIOSes reserve close to a gigabyte for the PCI address space, even if no actual devices with memory are present there or if the devices only use a couple dozen megabytes.

You need to activate the BIOS option to remap the memory from 3.2-4.0 GB to 4.0-4.8 GB.

Up there you will be able to use it with a 64 bit kernel or with a 32 bit kernel with PAE for a total of 4 GB.


Well I didn't find this option on my BIOS setup. I'll do a further research about this, thanks.

---

### Post by Cracauer on 2009-03-02
> **Shoeman said:**
> Well I didn't find this option on my BIOS setup. I'll do a further research about this, thanks.

The option always has an obscure name. There seems to be a competition going on in hiding it. Which is not surprising, it is hard to get right and many BIOSes have the option but it fails. It's better to pretend this capability doesn't exist and blame "the 32 bit OS".

What brand mainboard?

---

### Post by Shoeman on 2009-03-03
> **Cracauer said:**
> The option always has an obscure name. There seems to be a competition going on in hiding it. Which is not surprising, it is hard to get right and many BIOSes have the option but it fails. It's better to pretend this capability doesn't exist and blame "the 32 bit OS".

What brand mainboard?

It's a PCWARE PW-945GCX. Tried to google "PCWARE PW-945GCX" remp memory, no great success. I'll try to play with some BIOs parameters.

---

### Post by reiki on 2009-03-03
There are motherboards out there that claim to support 4GB of RAM and which in fact do not (Asus P5LD2 comes to mind... since that what I have). There is nothing in BIOS to remap and lots of folks complaining about the fact that this motherboard claimed to support 4GB. Apparently a chipset limitation (945P) prevents it actually doing so. I found this information elsewhere, but it might prove helpful for some:

In order to access the full 4GB, you must meet the following criteria:

One of the following chipsets (and any later with greater than 4GB support):
• Intel 975X
• Intel P965
• Intel 955X on Socket 775
• Chipsets that support AMD processors that use socket F, socket 940, socket 939, or socket AM2. These chipsets include any AMD socket and CPU combination in which the memory controller resides in the CPU.

The CPU must support the x64 instruction set. The AMD64 CPU and the Intel EM64T CPU support this instruction set.

The BIOS must support the memory remapping feature. The memory remapping feature allows for the segment of system memory that was previously overwritten by the Peripheral Component Interconnect (PCI) configuration space to be remapped above the 4 GB address line. This feature must be enabled in the BIOS.

You must be running an x86_64 (64-bit) OS.

---

### Post by zika on 2009-03-03
```
gksudo gedit /boot/grub/menu.lst
```
change the following line to have this option at the end, beginning might be different:
```
# defoptions=... iommu=noaperture
```
then do in Terminal:
```
sudo update-grub
```reboot.
now You should have all the problems with memory hole gone ... ;)

to undo simply remove added option and do *update-grub* again.

---

### Post by Cracauer on 2009-03-03
Oh yes. I forgot.

The Intel 945 chipset is indeed crippled and does not support the remapping. It is limited to 4 GB straight, with no ability to remap parts from below 4 GB to above 4 GB.

This is a chipset/Intel problem, for a change you can't beat up the mainboard/BIOS makers.

Don't buy junk hardware, in particular not mainboards.

---

### Post by Shoeman on 2009-03-03
> **Cracauer said:**
> Oh yes. I forgot.

The Intel 945 chipset is indeed crippled and does not support the remapping. It is limited to 4 GB straight, with no ability to remap parts from below 4 GB to above 4 GB.

This is a chipset/Intel problem, for a change you can't beat up the mainboard/BIOS makers.

Don't buy junk hardware, in particular not mainboards.

The manufacture specs says that the motherboard support up top 4GB. So are they lying? Yes, the computer was really cheap once it was a core 2 duo 4GB RAM SATA 500GB, but I would never guess someone yould sell a 4GB computer with a motherboard that doesn't support that amount of memory. So there is nothing I can do to get the 4GB recognized?

---

### Post by Cracauer on 2009-03-03
> **Shoeman said:**
> The manufacture specs says that the motherboard support up top 4GB. So are they lying? Yes, the computer was really cheap once it was a core 2 duo 4GB RAM SATA 500GB, but I would never guess someone yould sell a 4GB computer with a motherboard that doesn't support that amount of memory. So there is nothing I can do to get the 4GB recognized?

You can put 4 GB of RAM in all right. It's just that the BIOS makes ca. 0.8 GB of it invisible. That the usual way to make the invisible RAM visible again is disabled is "easily" accessible in Intel's chipset programming documentation :)

Don't feel too bad, there are plenty of mainboards that have a chipset capable of remapping (or AMD CPUs which always do it) and they screw it up in the BIOS.

There might be a way to trick the BIOS into only taking what it needs. Did you play with the AGP aperture size?

---

### Post by Shoeman on 2009-03-03
> **Cracauer said:**
> You can put 4 GB of RAM in all right. It's just that the BIOS makes ca. 0.8 GB of it invisible. That the usual way to make the invisible RAM visible again is disabled is "easily" accessible in Intel's chipset programming documentation :)

Don't feel too bad, there are plenty of mainboards that have a chipset capable of remapping (or AMD CPUs which always do it) and they screw it up in the BIOS.

There might be a way to trick the BIOS into only taking what it needs. Did you play with the AGP aperture size?

Yeah, I've tried Zika's sugestion, no succes. Sent an e-mail to the manufacturer but I don't think it will ever be replied.

---

### Post by Cracauer on 2009-03-03
> **Shoeman said:**
> Yeah, I've tried Zika's sugestion, no succes. Sent an e-mail to the manufacturer but I don't think it will ever be replied.

No, you need to play with the aperture size in the BIOS. By the time the kernel comes up the battle for the missing memory is long over.

---

### Post by TheSamurai on 2009-03-03
> **Svensk023 said:**
> I also have 4GB of RAM and it only recognizes 3GB. also on my AMD 64-bit Atholon x2 laptop, it only recognizes 1.7GB of RAM out of 2GB. So yes I would aslo like to know why this is happening

EDIT:
I ran the above code and it returned this:
i686

i686 is 32 bit.

Oops, just realized this was already answered.

---

