---
title: "Stupid Graphic Driver Problem"
date: 2007-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by blackstealth007 on 2007-03-04
Alright, i have installed Ubuntu x86_64 more than 4 times now becuase of driver problem. I am new at this having come from Windows. Anyways, I have the Ubuntu 6.10 x86_64 bit OS. And i have the Nvidia 6800gs, Every time after having installed, and updating everything, i run the Nvidia driver installation. After i am told to reboot, it gives me the blue screen saying error message about x server, and then drops me to the console command. No gui interface.. :(  I have tried tons of different guides for instaling a Nvidia 64 bit graphics driver, so if anyone can please tell me what to do. Or give me a script they know will work, i will be incredibly grateful. Remember i have the 64 bit os of Ubuntu.... Thanks already

BTW, my friend is having the same problems, and simliar hardware. No ATI

Also, i would like to install Beryl and Kiba Dock, so if you could also give me info about that and if it matters having the 64 bit OS and what i need to do then. I have already installed Beryl 2 times, and its definately worked and been incredible, but like i said, whenever i restart after installing the Nvidia driver, i am locked out of a gnome, and left to console becuase of some kernel problem with Nvidia and Xserver being different

---

### Post by ffxr on 2007-03-04
have you tried you using the prop drivers  from the NVIDIA site.. ?

get the 64bit package from [http://www.nvidia.com/object/linux_display_amd64_1.0-9746.html](http://www.nvidia.com/object/linux_display_amd64_1.0-9746.html)

then follow this guide: [http://doc.gwos.org/index.php/BerylOnEdgy#Option_2:](http://doc.gwos.org/index.php/BerylOnEdgy#Option_2:)

changing the part with 'NVIDIA-Linux-x86-1.0-9629-pkg1.run' to whatever the 64bit binary is called..

i have beryl working perfectly.. if you start seeing the NVIDIA/Beryl bugs post back and ll show u my fixes..

---

### Post by John Jason Jordan on 2007-03-04
> **blackstealth007 said:**
> Alright, i have installed Ubuntu x86_64 more than 4 times now becuase of driver problem. I am new at this having come from Windows. Anyways, I have the Ubuntu 6.10 x86_64 bit OS. And i have the Nvidia 6800gs, Every time after having installed, and updating everything, i run the Nvidia driver installation. After i am told to reboot, it gives me the blue screen saying error message about x server, and then drops me to the console command. No gui interface.. :(  I have tried tons of different guides for instaling a Nvidia 64 bit graphics driver, so if anyone can please tell me what to do. Or give me a script they know will work, i will be incredibly grateful. Remember i have the 64 bit os of Ubuntu.... Thanks already
When you're at that console, are there any error messages? What happens if you do "startx"? And another command that might be helpful would be "dmesg | tail," or "dmesg | less." The latter will display the results one screenful at a time and you have to hit the spacebar to move down a screenful.
I'm a noob with Linux also, so others may suggest other command line things for troubleshooting. 

I can't help at all with Beryl, as I have never tried it.

---

### Post by blackstealth007 on 2007-03-04
I get the message, "x server is not responding" or something like that, and then it says it shuts it down. I will try the things that you guys have said.

---

### Post by blackstealth007 on 2007-03-04
also, what do you mean when you say change it to the 64 bit binary? And is that guide you linked, supposed to help me setup the beryl in 64 bit, as well as graphic drivers? And , i am supposed to use everything they say to do i suppose?

---

### Post by blackstealth007 on 2007-03-04
YAAA!!!! thanks guys it worked beautifully!

---

