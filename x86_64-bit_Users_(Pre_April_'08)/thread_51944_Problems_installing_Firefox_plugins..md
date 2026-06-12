---
title: "Problems installing Firefox plugins."
date: 2005-07-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by St3althcAt on 2005-07-25
Hello all!
I'm a new user to Ubuntu. I've used other distributions before, like Mandrake and Foresight. Mandrake was the one I used for more time because it was the only one that supported my USB ADSL Modem. Now I've a router and the Internet problem is gone. Then I've installed Ubuntu. I like this distro, stable, fast, good, and it simply works... Except for one thing:

I've successfully managed to install, following the guide on [http://ubuntuguide.org](http://ubuntuguide.org) the mplayer plugins on Firefox to watch streaming TV broadcasts, but I can't install the Java and Macromedia flash plugins. When I do that, it gives me the following error:

For Java:

Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20amd64%20(20050407)_dists_hoary_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20amd64%20(20050407)_dists_hoary_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package sun-j2re1.5

For Macromedia Flash:

Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20amd64%20(20050407)_dists_hoary_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20amd64%20(20050407)_dists_hoary_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package flashplayer-mozilla.

I use Ubuntu 5.04 AMD 64 Version. I've an Athlon 64 3200+, Asus A8V Deluxe Motherboard, 1 Gb Ram. If you could help me, it would be nice. I need this plugins on Firefox working, they are almost essential to me. I'm a Windows fan, I admit, but I think Linux also has some good things.

Thank you!

---

### Post by joshuapurcell on 2005-07-25
Did you have the Hoary CD in the drive when you ran apt-get? That's the only thing I can think of... I have the same motherboard, processor, and mem size as you and everything works here. The only time I get that type of error is when I don't have the CD in the drive.

---

### Post by St3althcAt on 2005-07-25
The problem with the cdrom is now solved.
Now it gives me this:

For Java:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5

For Flash Player:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla

---

### Post by NeoChaosX on 2005-07-25
Um, there's no Flash or Java plugins for AMD64 Linux. That's why you can't install it.

(Nice avatar, btw)

---

### Post by St3althcAt on 2005-07-25
Damn. Don't tell me I have to download the 32-bit version... Now that I am out off traffic for my ADSL... Thank you for your answers!

---

### Post by Jet2k5 on 2005-07-25
[QUOTE=NeoChaosX]Um, there's no Flash or Java plugins for AMD64 Linux. That's why you can't install it.

(Nice avatar, btw)[/QUOTE]


I was wondering when someone was going to mention that :P


[QUOTE=St3althcAt]Damn. Don't tell me I have to download the 32-bit version... Now that I am out off traffic for my ADSL... Thank you for your answers![/QUOTE]


Don't know if you are talking about downloading the flash or java for 32-bit or downloading Ubuntu 32-bit.  because you can just run firefox, flash, and java from a 32-bit chroot mode.  I have never tried it so I don't know that much about it.  But the AMD64 UbuntuGuide should give you a starting point.

If you are at it, dont' forget to sign the thread that is floating around by telling macromedia to port their flash to 64-bit processors.  It might not work , but you can never know.

---

### Post by St3althcAt on 2005-07-26
I was talking about downloading Ubuntu 32-bit version :P. Already download, already installed, no plugin problems, no nothing. I've used many distros, but get fed up with them. I think I'm beggining to like this. At least, Linux is "obbeying" me, if you understand! :P

Note: For a Windows fan to say that he likes this, it's because Ubuntu is good! Congratulations for all developers and community too! :)

---

