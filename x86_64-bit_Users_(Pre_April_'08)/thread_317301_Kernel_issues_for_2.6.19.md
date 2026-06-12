---
title: "Kernel issues for 2.6.19"
date: 2006-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by kcallis on 2006-12-12
Last week while I was trying desperately to get fglrx working, I came upon a solution to build out a new kernel. Bottom line is that the fglrx is still not working, and now I have some other issues. 

I am running Edgy with a 2.6.19 kernel on a HP dv8040us which has a AMD64 ML34 process in place. Every since my changes, my lockup my machine, and if I happen to be looking at xconsole, before the lock up, there is either some reference to an error with the SMP register or I get errors about some issue with my hdc (cdrom drive).

I have not figured out what could be the problem, because it is not consistant. FIrst off, does anyone kow if there is an issue with adding SMP to the kernel? Secondly, I am wondering if there is a heat issue, but I can not get temp status to come up properly. Is there some trick that I am missing on getting the apci stuff to work to register the temperature? And lastly, I can get suspend to work, but there doesn't seem to anyway to get hibernation working... What is the trick to that? ](*,) 

Any pointers would be greaty appeciated!

K.

---

### Post by Kilz on 2006-12-12
> **kcallis said:**
> Last week while I was trying desperately to get fglrx working, I came upon a solution to build out a new kernel. Bottom line is that the fglrx is still not working, and now I have some other issues. 

I am running Edgy with a 2.6.19 kernel on a HP dv8040us which has a AMD64 ML34 process in place. Every since my changes, my lockup my machine, and if I happen to be looking at xconsole, before the lock up, there is either some reference to an error with the SMP register or I get errors about some issue with my hdc (cdrom drive).

I have not figured out what could be the problem, because it is not consistant. FIrst off, does anyone kow if there is an issue with adding SMP to the kernel? Secondly, I am wondering if there is a heat issue, but I can not get temp status to come up properly. Is there some trick that I am missing on getting the apci stuff to work to register the temperature? And lastly, I can get suspend to work, but there doesn't seem to anyway to get hibernation working... What is the trick to that? ](*,) 

Any pointers would be greaty appeciated!

K.

My suggestion is to boot back into the previous kernel and remove the one you created. [This howto]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Dapper_Manually") will then be good to get the video drivers working.

---

### Post by kleeman on 2006-12-12
I would echo kilz. Figuring out why a kernel is not working can be a very frustrating experience. Sometimes there are bugs in drivers in the latest kernel and they have not been filtered through the Ubuntu kernel developers and launchpad. Deciphering cryptic kernel messages is a recipe for madness unless you have a lot of experience.

---

