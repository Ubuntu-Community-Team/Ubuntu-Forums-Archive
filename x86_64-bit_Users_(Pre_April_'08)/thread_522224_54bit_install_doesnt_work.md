---
title: "54bit install doesnt work"
date: 2007-08-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by jbseven on 2007-08-10
Hello all,

Ive been ttying out the linux platform and the 32bit ubuntu 7.04 and it works marvellously.
My cpu is 64bit so i decided to install the amd64 version of ubuntu.

When i boot from cd and "Start or install ubuntu" or "start or install ubuntu with safe graphics"
i get a few lines saying "kernel alive" etc. but then my monitor shuts off and my capslock/scrlock indicators keep flashing and my system stops reading from the cd.

My pc is:
amd athlon 64 3400+
asrock k8nf4g-sata2
2GB DDR400
256MB X800GT PCI-Ex
2 SATA-II drives, 3 IDE drives, 1 DVDRW
550W Power Supply

Also, i tried the same install on a friends 
amd 64 X2 6000/ asus m2n32sli/ 2GB DDR2-800/ 640MB-8800GTS,
after the "kernel alive" line, the screen remains blank and the cd drive stops reading from cd.

can anyone help me install this os?

---

### Post by jbseven on 2007-08-10
sorry for the typo(s)

---

### Post by PinkBullets9 on 2007-08-10
You could try making another CD because it sounds like something messed up when you were burning it. I have a 64bit ready PC as well but I didn't find that 64bit was much better since most applications don't run on 64bit only 32bit, so I use 32bit. You could try installing it from virtualbox/vmware before you try installing it on your PC to make sure the CD works.

---

### Post by John.Michael.Kane on 2007-08-10
> **jbseven said:**
> Hello all,

Ive been ttying out the linux platform and the 32bit ubuntu 7.04 and it works marvellously.
My cpu is 64bit so i decided to install the amd64 version of ubuntu.

When i boot from cd and "Start or install ubuntu" or "start or install ubuntu with safe graphics"
i get a few lines saying "kernel alive" etc. but then my monitor shuts off and my capslock/scrlock indicators keep flashing and my system stops reading from the cd.

My pc is:
amd athlon 64 3400+
asrock k8nf4g-sata2
2GB DDR400
256MB X800GT PCI-Ex
2 SATA-II drives, 3 IDE drives, 1 DVDRW
550W Power Supply

Also, i tried the same install on a friends 
amd 64 X2 6000/ asus m2n32sli/ 2GB DDR2-800/ 640MB-8800GTS,
after the "kernel alive" line, the screen remains blank and the cd drive stops reading from cd.

can anyone help me install this os?

Reboot the machine. At the boot/install prompt (make sure to hit F6 first), and add the command below to the boot parameter.
```
nosplash noapic nolapic
```  
note: do not remove any of the commands already shown in the boot line. just add the above commands to it.

---

### Post by jbseven on 2007-08-10
Thanks! That worked like a charm, although not without some editing.
I had to edit the line 
"Boot Options :casper initrd=/casper/initrd.gz quiet splash --" and change it to
"Boot Options :casper initrd=/casper/initrd.gz quiet -- add nosplash noapic nolapic"

and then after the install, edit the boot options in GRUB and change the same parameters
and finally within the os, edit the grub config file with 
"sudo gedit /boot/grub/menu.lst" and change the same parameters.

Thanks for the assistance!!

---

