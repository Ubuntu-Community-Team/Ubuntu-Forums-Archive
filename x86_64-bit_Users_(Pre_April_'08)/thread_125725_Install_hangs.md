---
title: "Install hangs"
date: 2006-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by gzander on 2006-02-04
I am trying to install Ubuntu but it stops with the folloing message:
"unlink after no-IRQ? Controller is probaly using the wrong IRQ"
Can any body help?

---

### Post by gzander on 2006-02-06
Looks like nobody has knows.
Guess Ubuntu is not ready for Prime Time!

---

### Post by newuser111 on 2006-02-06
try booting with linux acpi=off

---

### Post by Sentor on 2006-02-09
I have a simular problem. I also got the message: controller is probably using the wrong controller.

I started the innstallation with: linux pci=biosirq irqpoll
This made the installation start(I choose language keyboard etc.)and everything is fine until it starts reading the information on the cdroom. It freezes at 22%, or sometimes at 6%

I have a HP pavilion with an AMD64 processor.

Does anyone have an Idea how to solve this?

---

### Post by meenfreem on 2006-02-13
I'm having problems too... i haven't even gotten to where you got to yet :(

the install either won't start or end up with a black screen.

---

### Post by friends on 2006-02-14
I dont think this will solve anyones problems, but I had a fairly similar problem with my plain install, where everything went fine until it got up to copying files to my hard drive, when it would hang.

I got around it by using a CDR instead of a CDRW.

Hope this helps, but i doubt it will..

---

### Post by Raevn on 2007-06-01
Running Ubuntu Feisty AMD64 on HP Pavilion dv6338se laptop (dv6000 series) 

Research showed that I need to add the following to the the initial CD boot command: "noapic irqpoll noirqdebug" . 

Results: 
Ubuntu Feisty installed with minimal problems and dual-booted itself with WinXP with no initial problems. :KS

Then I had trouble getting drivers for WinXP to run the webcam and some other hardware on the former Vista machine. So it was back to Vista which blotted the whole SATA drive and I was back to square one. On the reinstall of Feisty, the boot commands worked as before. I had to wait forever for the partition manager to crunch down the Vista NTFS partition but the install went OK. :p

On the reboot for Feisty's initial login, the Ubuntu progress strip froze at about 12%. Vista ran fine except that it objected to having its partition "adjusted" but its chkdsk app pronounced the drive usable. Other reboot attempts into Ubuntu froze the progress strip froze at 12% and 50%.  :confused: 

](*,) Gonna try the Edgy AMD64 disk and then the i386 install next. Client is not that expert but he's forced to live as close to the edge as possible due to his work. He's also taking it to Ecuador for the next few years and it needs to be as stable and rebuild-able as possible. Talk about conflicted requirements. 

Raevn

---

### Post by transactionlogfiller on 2007-06-02
Raevn, you can use Vista to resize NTFS partitions - you should do that to create some free space before installing Ubuntu.

I'm happily dual booting with Feisty and Vista now on my HP Pavilion ts 1000.

Thanks for the tip about the kernel params :)

Edit:

One more thing: If you use the live CD and enter the noapic stuff to make it boot, you have to do it again after installation because it seems to install with just the default options. That's probably why it's hanging at 12%.

---

### Post by Circus-Killer on 2007-06-13
> **Raevn said:**
> Running Ubuntu Feisty AMD64 on HP Pavilion dv6338se laptop (dv6000 series) 

Research showed that I need to add the following to the the initial CD boot command: "noapic irqpoll noirqdebug" . 

Results: 
Ubuntu Feisty installed with minimal problems and dual-booted itself with WinXP with no initial problems. :KS

Then I had trouble getting drivers for WinXP to run the webcam and some other hardware on the former Vista machine. So it was back to Vista which blotted the whole SATA drive and I was back to square one. On the reinstall of Feisty, the boot commands worked as before. I had to wait forever for the partition manager to crunch down the Vista NTFS partition but the install went OK. :p

On the reboot for Feisty's initial login, the Ubuntu progress strip froze at about 12%. Vista ran fine except that it objected to having its partition "adjusted" but its chkdsk app pronounced the drive usable. Other reboot attempts into Ubuntu froze the progress strip froze at 12% and 50%.  :confused: 

](*,) Gonna try the Edgy AMD64 disk and then the i386 install next. Client is not that expert but he's forced to live as close to the edge as possible due to his work. He's also taking it to Ecuador for the next few years and it needs to be as stable and rebuild-able as possible. Talk about conflicted requirements. 

Raevn

one quick question, Raevn, does your pavilion laptop have a wireless card, and did you manage to get it working?

---

### Post by Ayuthia on 2007-06-14
I am also running an HP dv6338se and have Vista, Ubuntu Feisty 64-bit, and Ubuntu Feisty 32-bit installed.  I installed the DVD that came with the Linux Magazine because it contained other desktop managers and I was too lazy to try to install them myself.  Instead of using Raevn's kernel parameters, I used noapic and nolapic.  The main issue that I have right now is that the webcam does not run out of the box with the 64-bit version, but works fine in the 32-bit version.

As for wireless, I ended up using bcm43xx-fwcutter instead of ndiswrapper.  I have not verified if it will connect at any speeds faster than 11Mb though.  ndiswrapper appears to connect at the higher speeds, but I can't seem to get it to work with network manager.

---

### Post by spodhajecki on 2007-07-09
I have a HP dv9310 AMD64 Turion with vista.  I had the same problem with the web cam. I installed the r5u870 drivers and kernel module but would get a garbled picture in ekiga. I would always get the dreaded irq #7 disabled message.  Changing the kernel params to "noapic irqpoll noirqdebug"  seemed to fix the issue.  (I had just "noapic nolapic").  The wifi works with ndiswrapper.  nVidia installed with envy.  Sound works (headphone jacks too.)  LCD dimmer works.

It is interesting to note that "noapic noirqdebug" also seems to work.  

Good luck,

Steve

---

### Post by Cuppa-Chino on 2007-07-09
> **spodhajecki said:**
> I have a HP dv9310 AMD64 Turion with vista.  I had the same problem with the web cam. I installed the r5u870 drivers and kernel module but would get a garbled picture in ekiga. I would always get the dreaded irq #7 disabled message.  Changing the kernel params to "noapic irqpoll noirqdebug"  seemed to fix the issue.  (I had just "noapic nolapic").  The wifi works with ndiswrapper.  nVidia installed with envy.  Sound works (headphone jacks too.)  LCD dimmer works.

It is interesting to note that "noapic noirqdebug" also seems to work.  

Good luck,

Steve

oh gonna try that boot option, I have an HP TX1000 based model - what chipset does the dv9310 have?

---

