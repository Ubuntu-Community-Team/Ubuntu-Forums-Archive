---
title: "Unable to boot after installing in safe graphics mode in aspire 4520"
date: 2007-12-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by s.jesudasan on 2007-12-30
Hi 
i installed ubuntu 64 bit in safe graphics mode in aspire 4520
after instllation when i try to boot it boots into 
busybox so sudo is not working there

i get 4 options in boot menu
1.generic boot
2.recovery mode
3.memory test
4.win xp

there is no option for booting in safe graphics mode
is there a way i can get that prompt.
or can i edit the boot menu
i dont know how to do that 
im new to ubuntu

kindly help

---

### Post by overdrank on 2007-12-31
> **s.jesudasan said:**
> Hi 
i installed ubuntu 64 bit in safe graphics mode in aspire 4520
after instllation when i try to boot it boots into 
busybox so sudo is not working there

i get 4 options in boot menu
1.generic boot
2.recovery mode
3.memory test
4.win xp

there is no option for booting in safe graphics mode
is there a way i can get that prompt.
or can i edit the boot menu
i dont know how to do that 
im new to ubuntu

kindly help

Hi and You can try and press esp key at the grub line, this will allow you to edit  the kernel line by pressing e and you can remove the quiet splash and add vga=771 and then hit enter and then  b to boot. What is the model of the graphics card on the system? Hope this helps.  Good luck!

---

### Post by s.jesudasan on 2007-12-31
First of all thanks for ur reply
im going to try out what u said
my lappy has nvidia g 7000 chipset
and ubuntu doesnt detect it

---

### Post by s.jesudasan on 2007-12-31
> **overdrank said:**
> Hi and You can try and press esp key at the grub line, this will allow you to edit  the kernel line by pressing e and you can remove the quiet splash and add vga=771 and then hit enter and then  b to boot. What is the model of the graphics card on the system? Hope this helps.  Good luck!

hi that didnt work
i just had quiet at the grub line
so i deleted it and added a new line as vga=771
but when i boot it just restarts
any idea to boot in safegraphics mode

---

### Post by overdrank on 2007-12-31
> **s.jesudasan said:**
> hi that didnt work
i just had quiet at the grub line
so i deleted it and added a new line as vga=771
but when i boot it just restarts
any idea to boot in safegraphics mode

Ok you can try to boot into recovery mode and enter the command startx. But before you do please see if you can install some driver with this command ```
apt-get install nvidia-glx-new
``` Then if it does install try and reconfigure you xorg with ```
dpkg-reconfigure -phig xserver-xorg 
``` if all this works then hopefully the startx command will bring you to a GUI.

---

### Post by s.jesudasan on 2007-12-31
when i try to boot in recovery mode 
i get stuck in the first screen 
and i just get a blinking cursor
thanks

---

### Post by overdrank on 2007-12-31
> **s.jesudasan said:**
> when i try to boot in recovery mode 
i get stuck in the first screen 
and i just get a blinking cursor
thanks

Ok this is the last thing that I have to offer and I hope it will be of some help
[http://ubuntuforums.org/showthread.php?t=510352](http://ubuntuforums.org/showthread.php?t=510352)
Good luck!

---

### Post by s.jesudasan on 2008-01-01
hi i downloaded ubuntu 6.06 64bit and
installed it in safemode and now im able to boot my 
aspire 4250 but i dont have any sound,my network card
is not detected.so i got connected to internet using usb
connection.I tried to install nvidia driver using envy but that 
didnt work.i tried to install the driver i downloaded from nvidia website
that too didnt work.So im thinking of downloading ubuntu 6.06 32 bit 
and install that.If u have any idea to install drivers.Kindly help me.

my config is
amd 64x2 1.7ghz
1 gb ram
nvidia ge force 7000M
160 gb HDD
gigabit lan

---

