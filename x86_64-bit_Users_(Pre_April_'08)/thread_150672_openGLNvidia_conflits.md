---
title: "openGL/Nvidia conflits?"
date: 2006-03-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hoffmann on 2006-03-26
Hello guys,

It seems like Ubuntu-amd64 presents conflits regarding either openGL or nvidia, or both?
Let me explain: There are some programs that need openGL. Moreover, I realized that I was able to run those programs just after installing nvidia-glx. The problem is:

(a) After open those programs [Ghemical or VMD ([http://www.ks.uiuc.edu/Research/vmd/)]](http://www.ks.uiuc.edu/Research/vmd/)]), I realized that the temperature of my box increases a lot. The fan goes crazy working with total power.
(b) I was not able to open pdf files anynore with programs such as kpdf.
(c) After "turning off" the program, the fan continues working hard:( 
(d) I was not able to shutdown the computer normally. It was necessary to push the botton.

Ok. After rebboting the system, I removed the nvidia-glx. Now, the system is working normally, and I can read pdf files. However I CAN'T run the other programs [Ghemical or VMD]. 

Could anyone, please, help me to solve this issue? I am starting thing that it was not a good idea to install the 64-bits of Ubuntu on my EM64T machine. Probably, I will be more satisfied with the 32-bits version? BTW, is there smp-kernels for the Ubuntu-32 bits in order to I use both of my CPUs (core dual)?

Thanks!
Hoffmann

---

### Post by hajk on 2006-03-26
Yes, openGL and NVidia don't go together. Edit /etc/X11/xorg.conf to change the "Module" section as follows
 
Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

This manual edit will cause some problems on the next upgrade, so neater is to make this change through "sudo dpkg-reconfigure xserver-xorg".

---

### Post by Hoffmann on 2006-03-26
[QUOTE=hajk]Yes, openGL and NVidia don't go together. Edit /etc/X11/xorg.conf to change the "Module" section as follows
 
Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

This manual edit will cause some problems on the next upgrade, so neater is to make this change through "sudo dpkg-reconfigure xserver-xorg".[/QUOTE]

Hi hajk,

Thanks for reply. I just didn't understand your last sentence very well> What do you mean by "...so neater is to make this change through "sudo dpkg-reconfigure xserver-xorg""?
In order to not have problem for the next upgrade, all I need to do is to enter the command:  "sudo dpkg-reconfigure xserver-xorg". Is that correct?

Hoffmann

---

### Post by hajk on 2006-03-26
Yes, the X installation remembers whether the /etc/X11/xorg.conf file has been "tampered with", so one way to avoid the consequences is to reconfigure the xserver-xorg package. You can pretty well accept all the suggested settings, except when choosing the modules you should only select the ones in my post. If you're not planning on upgrading xserver-xorg, then doing it manually is also OK. Don't worry, it's not a crucial issue either way -- FWIW, I just did it manually myself.

---

