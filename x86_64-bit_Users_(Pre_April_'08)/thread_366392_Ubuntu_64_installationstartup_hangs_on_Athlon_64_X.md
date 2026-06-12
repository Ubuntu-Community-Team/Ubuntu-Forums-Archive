---
title: "Ubuntu 64 installation/startup hangs on Athlon 64 X2 4200+"
date: 2007-02-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by ms12345 on 2007-02-20
I am installing Ubuntu server on a brand new Dell Optiplex 740 AMD Athlon 64 X2 4200+ and both the 64-bit server and 64-bit desktop Edgy installations hang.  

I've tried running the regular x86 Edgy CD and it seems to work just fine, but I want to take full advantage of the processor.  Does anyone know how to get the 64-bit Edgy installation to work, or am I using the wrong image?

Thanks,
Mike

---

### Post by Eigenwert on 2007-02-21
At what point in the installation process do they hang?

EW

---

### Post by workaholicbe on 2007-03-13
I've got almost the same problem. I can't install another system but the ****ing Windows XP (pre-installed) ...
At startup  he's giving me the following problem

Ubuntu stops his installation(at startup) procedure every time after those lines:   

libata version 1.20 loaded
parport : PnPBIOS parport detected                            
parport0:PC-style at 0x378, irq 7 (PCSPP, Tristate, EPP)

Looks to me that there is a problem with SATA recognition...in combination with USB ports 
or am i totally wrong?

I even committed a 'sin' .... i've tried to install Fedora Core 5 on the same machine...but that's even worse ... that OS doesn't give me further information

So afterwards... i tried the System Rescue CD... That one passes but when i enter the startx (graphical environment) after some movements of my mouse it freezes. After a while also the keyboard behaves the same way.

On those Optiplex machines you don't have an internal CD/DVD reader... so i have to use an external. Is that perhaps the problem?

My config :

Optiplex 740
AMD 64 X2 4600+
BIOS (1.0.5)
no internal devices 

thx in advance

---

### Post by randara on 2007-03-13
Same problem here, I even have tried with the option NOAPIC IRQPOLL PCI=ROUTEIRQ, mouse and keyboard works but there is a problem with the nic, I think its a bios problem.

Dell Optiplex 740
BIOS 1.0.5
Ubuntu 6.10 AMD64

PS: No response from dell linux forum.

---

### Post by firecat53 on 2007-03-14
Maybe try noapic noacpi nosmp?  All three at the end of "kernel" line in /boot/grub/menu.lst

Scott

---

### Post by randara on 2007-03-14
It works, thanks firecat53.

Adding those options fixed the problem. I'll inform of the stability of the system the next week.

---

### Post by alek66 on 2007-03-15
have tried to install it with out nothing attached to usb?
mi laptop used to crash on installations when I had everything plugged in.

---

### Post by Jose Consuervo on 2007-03-17
> **firecat53 said:**
> Maybe try noapic noacpi nosmp?  All three at the end of "kernel" line in /boot/grub/menu.lst


That worked for me, thanks dude.

---

### Post by mandible on 2007-03-18
I'm getting further now, using the alternate cd I saw that the boot process was freezing on usb initialization. 
I had my USB devices plugged into the ports on the case. 
Moved the devices to the motherboard directly and did get further will continue to plug away at things.

---

### Post by cobray on 2007-03-18
Try running the memtest from the CD.
I was having random trouble installing and I found out I had a bad memory stick. Everything good now
I had the same problem the 32-bit one went on but random crashes and the 64-bit failed to install.
Now running amd64 life is sweet.

---

### Post by qhartman on 2007-04-24
Do you guys have any more thoughts on these machines now that you've had them awhile? I'm considering picking some of these up for my business, and would love to hear more of your experiences before I take the plunge.

---

