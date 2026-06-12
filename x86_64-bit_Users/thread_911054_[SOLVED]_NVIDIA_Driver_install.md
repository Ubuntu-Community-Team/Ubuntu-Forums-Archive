---
title: "[SOLVED] NVIDIA Driver install"
date: 2008-09-05
forum: x86 64-bit Users
---

### Post by Linux user 66 on 2008-09-05
I have NVIDIA Drivers installed for my GeForce 8800GTX, but the driver appears to be version 169.12 (according to Synaptic) and the one available on NVIDIA's download page is version 173.14.12 for Linux 64-bit. I downloaded the newest driver *NVIDIA-Linux-x86_64-173.14.12-pkg2.run*, but now I'm not sure how to proceed.

1. What should I uninstall before installing the new drivers and how?

2. How do I install the drivers?

(Detailed instruction, please :))

---

### Post by Lazy79 on 2008-09-05
173.14? i would use envyNG.. or have a look here:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_restricted_drivers](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_restricted_drivers)

or just

alt & f1 = console

then

sudo /etc/init.d/gdm stop 

sudo sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run

Do not download the kernel module, just say no if nvidia is asking..

after that install, configure your xorg.conf..(nv to nvidia)

And start gdm again

sudo /etc/init.d/gdm start 

but i rather would go with envyng because it makes your life easier.. i think.. ;)

and maybe someone is posting a detailed how to.. or a better link ;)

good luck

---

### Post by Crafty Kisses on 2008-09-05
Try Envy, it should work.

---

### Post by Linux user 66 on 2008-09-05
> **Lazy79 said:**
> 173.14? i would use envyNG.. or have a look here:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_restricted_drivers](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_restricted_drivers)

or just

alt & f1 = console

then

sudo /etc/init.d/gdm stop 

sudo sh NVIDIA-Linux-x86_64-173.14.12-pkg2.run

Do not download the kernel module, just say no if nvidia is asking..

after that install, configure your xorg.conf..(nv to nvidia)

And start gdm again

sudo /etc/init.d/gdm start 

but i rather would go with envyng because it makes your life easier.. i think.. ;)

and maybe someone is posting a detailed how to.. or a better link ;)

good luck

Thanks! Problem solved.

---

