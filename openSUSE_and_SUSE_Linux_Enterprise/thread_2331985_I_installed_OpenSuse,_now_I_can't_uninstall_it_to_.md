---
title: "I installed OpenSuse, now I can't uninstall it to install Ubuntu"
date: 2016-07-27
forum: openSUSE and SUSE Linux Enterprise
---

### Post by abdnormal on 2016-07-27
hello, so I wanted to try Opensuse 42.1 leap on my compaq labtop so I installed it and completely removed ubuntu, I don't like it at all and want to go back to ubuntu, but the problem is that now I can't boot from DVD nor USB stick. when I go to "boot options" in bios DVD/USB don't even appear and when startup normally it goes automatically to Grub and starts opensuse. I also tried changing the DVD and even a DVD of windows and it's the same thing, my dvd reader is just fine I tried it with other stuff and it's normal. I found that it's a thing with opensuse not just me, [this person for example had the same problem]("http://unix.stackexchange.com/questions/115336/installled-opensuse-and-now-cant-boot-from-usb-or-dvd"). can anyone help? thank you very much.

---

### Post by grahammechanical on 2016-07-27
I suggest that you enter the BIOS and go to the section for Boot and look at the sub-section for hard drives. The BIOS might now be seeing the DVD or USB stick as an external drive which you now need to select to boot from.

This is how I have to do things. Selecting Boot priority is find the first time but for every time after that I have to select the drive to boot from.

Regards.

---

### Post by Bucky Ball on 2016-07-27
*Thread moved to **openSUSE and SUSE Linux Enterprise***.

---

