---
title: "black screen after splash screen"
date: 2008-03-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by trisscross on 2008-03-17
i installed ubuntu 7.10 and installed nvidia driver rebooted and i get black screen after the splash screen. i have spent all day trying diffrent things with no luck apart from installing the nv driver 
can someone please help me get the nvidia driver working 
my video card is a 6800gt (agp)
many thanks tris

---

### Post by Auric_Falc0n on 2008-03-18
I've got a PCI-e 8400 GS that has the same problem - my monitor isn't getting a signal at all. I used the NVIDIA driver from the restricted drivers installer.

I finally just let it be once I realized that the machine was still starting. I wouldn't mind fixing it if someone has a fix, though.

---

### Post by Stom on 2008-03-18
You can try removing spalsh and quiet from the boot command, it worked for me, although that was using an ati card. Only suggestion i have :)

---

### Post by Tomatz on 2008-03-18
Uninstall the packaged (restricted) nvidia drivers and use this little app instead:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

It will download and install the latest nvidia/ati drivers in a few clicks :)

---

### Post by trisscross on 2008-03-18
thankyou for thhe replys 
Tomatz i tryed envy but same result 
Stom i am going to try this again because i did it by pressing e on the grub menu.
i have also been trying to edit my xorg.conf but nano cant find it is this a problem ??

---

### Post by trisscross on 2008-03-19
little update i have gone back to 32bit ubuntu and all is fine. i am going to stay there till i get a better at this 

thankyou for your help :)

---

### Post by gluko on 2008-04-03
i've got the same problem. sadly i'm not very skilled with linux yet.
i uploaded some screens (with the whole dmesg), maybe someone is able to help me. 

after i installed hardy with wubi (i don't think it's a wubi bug), i always get a black screen after the splash screen. after booting in safe mode, i also get errors saying the system would be "read only" (no screens of that though).

it would be nice if some one could look the screens through. maybe i will try to install the 32bit version again. the first time wubi installed the amd64 one, although i added the --32bit argument and even placed a 32bit version iso of ubuntu 7.10 in the same folder -> maybe THAT's  a wubi bug? (i know, they have their own forum)

sorry for my bad english- i'm german... and it's pretty late (at least in germany :) )

uploaded it on rapidshare (7,76 mb): [download]("http://rapidshare.com/files/104666641/boot_8.04.zip.html")

---

