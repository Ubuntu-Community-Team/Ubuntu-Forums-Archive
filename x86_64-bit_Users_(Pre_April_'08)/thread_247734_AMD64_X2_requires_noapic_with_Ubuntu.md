---
title: "AMD64 X2 requires noapic with Ubuntu"
date: 2006-08-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by daou on 2006-08-31
I put together a new comp for a friend.

During the installation of Ubuntu it always froze after loading the kernel, once with the i386 LiveCD it suggested turning off APIC with the noapic command.

It always froze with the i386 and amd64 installations as well.

After giving the noapic command for the kernel, it starte installing (i386 failed at the kernel installation) and we finally got a working Ubuntu with amd64 kernel installed. However, it only boots with the noapic command.

How important is the APIC module? A read at wikipedia says it is used (by Intel) for multiprocessor interrupts. I would guess it's important for an AMD X2 4200+ as well, being a dualprocessor core.

Has anyone had experience with this or a possible fix other than disabling the APIC module? The Ubuntu is currently running a amd64-generic kernel.

---

### Post by ser1alsn1per on 2006-08-31
what are the serious advantages of using ubuntu 64bit could you not just install the 32 bit ubuntu with k7 kernel or what ever it is?

---

### Post by daou on 2006-08-31
The i386 installation failed during the kernel configuration/installation. So there was no other option than to put an amd64 kernel.

---

### Post by Kilz on 2006-08-31
> **daou said:**
> The i386 installation failed during the kernel configuration/installation. So there was no other option than to put an amd64 kernel.

Thanks for that post, some people still do not believe that there are problems installing a 32bit OS on a 64bit system. Mine doesn't see the CD drive in 32bit. Besides there are work around for everything. If nothing else there is a chroot setup script if you must have some piece of software that absolutely wont run on 64bit.
Have you tried the alternate install disk? Sometimes it works when other disks need options.

---

### Post by Kilz on 2006-08-31
> **ser1alsn1per said:**
> what are the serious advantages of using ubuntu 64bit could you not just install the 32 bit ubuntu with k7 kernel or what ever it is?

One serious advanatge is the os is noticably faster. Also some programs can have a 30% increese in speed. You are using yout processor to its best advantages.

---

### Post by daou on 2006-08-31
Yes, I tried the alternate and desktop cd of i386. No cigar. Possibly changing the kernel from amd64-generic to amd64-k8 or some other would help.

---

### Post by alexandermimix on 2006-08-31
I am unable to install 32bit ubuntu on to my AMD64 x2 machine either. Lan problems or soemthing... im not too sure however apt-get wont work and for someone running a ATI x800GT no internet means no graphical interface.

64bit works great however and the few 32bit programs that I need to keep it all running seem to also run fine (32 bit firefox, wine, etc.) Mainly thanks to Kilz and his top notch tutorials. :)

---

### Post by tymek666 on 2006-09-01
I've always use noapic option on ati chipset based boards. That's why i'm using nf4 now ;)

---

### Post by daou on 2006-09-03
Kernel update from generic to K8 SMP didn't help. But there doesn't seem to be any adverse effects from using the noapic option, so it probably doesn't matter.

---

### Post by digitalice on 2006-10-03
same problem!!!
with many linux distos too... :mad: 
im going MAD!!!

so, amd64 x2 is unsoported??  :confused: 

regards:neutral:

---

### Post by kuja on 2006-10-03
I don't know if you've done so yet, but you could try installing the proprietary ATI graphics drivers, and reconfigure X accordingly. This may help with graphics issues, but I can't test it to know if it'd work on your system... seeing as I'm using a socket 939 board with an Nvidia video card. (which, of course, works flawlessly)

---

### Post by Ausus on 2006-10-04
Hi All,

I'm using ASUS A8N32 SLI Deluxe motherboard with +3800 AMD dual core CPU. I don't have any problems. Also using Nvidia GPU.
Mobo is using NF4 chipset.

I saw in one of the forums someone had a problem with "noapic" with the new AMD-AM2 motherboard.This problem relates to the mobo manufacture.They have to set up Bios correctly, that is where the problem lies.


Regards

---

### Post by sir4taye on 2008-02-20
I run:
amd64 athlonX2
nVidia chipset
nVidia 6100 (shared ram)
broadcom 4311 mini-pci wlan
compaq presario f730us notebook

I have installed Ubuntu onto a variety of machines. This being the first 64-bit. Only one machine have I got to install without using noapic nolapic as a boot parameter with the live-CD. 

I have finally gotten my wireless to work. I'd like to experiment with the b43, but haven't gotten that far yet. I got the card working with ndiswrapper. I posted the simple step by step walk through here: http://ubuntuforums.org/showthread.php?t=694171

I also would like to know what effect the noapic parameter is having on the way Ubuntu uses my hardware. And, is there a way to work around it. 

Is there a walk-through for using the alternate install disk?

Please explain the noapic commands functions and if possible how to get around using it?


Thank you ubuntu for making a viable alternative to M$ spyware Os's

---

### Post by Cappy on 2008-02-20
This explains it thoroughly:
[http://osdev.berlios.de/pic.html](http://osdev.berlios.de/pic.html)

Basically helps your processors be more efficient under heavy loads by managing priority.

I'm 95.55555555% (repeating, of course) sure there isn't anyway around it because it is simply because the APIC of your motherboard isn't supported in the kernel yet.

---

### Post by NullHead on 2008-02-20
I have this problem when I set some settings wrong in my bios. Such as when I turn a feature on for my processor it kills linux's acpi ... also it will cause windows to fail booting ... I think it's my flaky bios. I would play around with the settings dealing with the processor.

---

### Post by sir4taye on 2008-02-21
Thank you cappy, that link was very informative. Though, he seems to be able to use his lapic very agressively. I don't see the need for the tweaking but I do see it as being vital to stop high-load hangups which is a problem I seem to be having upon startup since installing awn and configuring compiz fusion. I think that I need to back off these settings, awn all together and compiz lesser, but I am also going to try leaving out the nolapic, using the noapic solo to see if I get less hang ups. Not only am I dealing with a amd64 (fussy), but a dual core which by the articles saying needs the lapic functionality. Am I making sense?

---

