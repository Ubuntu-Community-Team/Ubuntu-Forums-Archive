---
title: "Nvidia drivers on 9.10"
date: 2009-10-25
forum: x86 64-bit Users
---

### Post by VampyrByte on 2009-10-25
I installed 9.10 today on my laptop and there is no way to install the Nvidia drivers from the Hardware Drivers menu, under System > Administration. I downloaded the driver from the Nvidia website, but being a complete beginner when it comes to Linux i have no idea what to do with it!
If its the case that the drivers wont be avaliable until the release of 9.10, is there a way i can set the screen resoloution properly in the mean time. only Ubuntu sticks it at 1280x720 which i am afraid to say is close, but no cigar. I need to change this to 1280x800.

I also find it odd that the LiveCD wanted me to load the drivers. But now i have installed Ubuntu, there is no mention of them.

Thanks for your help =D

---

### Post by VampyrByte on 2009-10-25
dont know what happend, but the Hardware Drivers menu suddenly decided it would show me the money!. i didnt change anything, all ive done is browse forums and reboot 1 or 2 times.

---

### Post by JDShu on 2009-10-27
> **VampyrByte said:**
> I installed 9.10 today on my laptop and there is no way to install the Nvidia drivers from the Hardware Drivers menu, under System > Administration. I downloaded the driver from the Nvidia website, but being a complete beginner when it comes to Linux i have no idea what to do with it!
If its the case that the drivers wont be avaliable until the release of 9.10, is there a way i can set the screen resoloution properly in the mean time. only Ubuntu sticks it at 1280x720 which i am afraid to say is close, but no cigar. I need to change this to 1280x800.

I also find it odd that the LiveCD wanted me to load the drivers. But now i have installed Ubuntu, there is no mention of them.

Thanks for your help =D

Heres how to install the driver from the nvidia website (you might want to write this down before doing it, also if you don't know how to locate your file in the command prompt, move the file to your home folder):

1. press CTRL-ALT-F1
2. You will be in a login screen, login with your username and password.
3. type in without the quotes "sudo gdm stop", press enter and type in your password
4. type in without quotes "sudo apt-get purge nvidia*" and press enter. Answer yes to the confirmation.
5. type in without quotes "sudo sh <your file that you downloaded>" and press enter
6. Follow the instructions on the screen.
7. When finished, type in without the quotes "startx"

The nvidia driver should be installed, if you have any questions feel free to ask!

---

