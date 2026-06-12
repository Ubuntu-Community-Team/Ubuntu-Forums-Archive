---
title: "Ubunut 8.10 wont work"
date: 2008-12-20
forum: x86 64-bit Users
---

### Post by myriadmagus on 2008-12-20
ok i recently got ubuntu 8.10 shipped !!well i am currently using 8.04 !
well when i try to run it as live cd (8.10) nothing appears except for startup screen the welcome startup music aint working .. the tollbars aint there !! is it because i dont have a gfx card..
i have an AMDX64 K8V-MX SERIES 
WITH VIAK8M800 chipset !! well i dont get driver for this chipset for 8.04 itself !! and so i cant even use 3d effects on 8.04 !! 
can any one tell me what the problem is and is there a possibility for me to run 3d effects with this chipset on 8.04 ??
Thank you !!

:edit: i have 640gb hdd and 1.5gb ram !!! :) and processor speed is 2ghz :.

---

### Post by Sef on 2008-12-20
Instead of booting into the live cd, go down to check disk for errors and click enter.  Make sure that the disk is good.

---

### Post by myriadmagus on 2008-12-20
well i had it shipped from the official site so i doubt that cos it worked perfectly fine in my cousin's laptop :)

---

### Post by DeMus on 2008-12-20
> **myriadmagus said:**
> ok i recently got ubuntu 8.10 shipped !!well i am currently using 8.04 !
well when i try to run it as live cd (8.10) nothing appears except for startup screen the welcome startup music aint working .. the tollbars aint there !! is it because i dont have a gfx card..
i have an AMDX64 K8V-MX SERIES 
WITH VIAK8M800 chipset !! well i dont get driver for this chipset for 8.04 itself !! and so i cant even use 3d effects on 8.04 !! 
can any one tell me what the problem is and is there a possibility for me to run 3d effects with this chipset on 8.04 ??
Thank you !!

:edit: i have 640gb hdd and 1.5gb ram !!! :) and processor speed is 2ghz :.

I have also tried to start the 8.10 live CD and all I notice is the start-up music, but absolutely no picture, nothing.
The same happened when I tried to install the new O.S. The monitor gets signal, I see the blue led burning at the front side of the monitor, but the screen itself stays absolutely black.

I have aP5K motherboard with a Q6600 processor running at 3.0GHz, 4GB ram, 2 times 500GB harddisk and an nVidia 8500GT graphics card.

I use a downloaded and home burned CD with the 64 bits version.

What could be wrong here?

---

### Post by myriadmagus on 2008-12-21
i dont see anything wrong with your config ;P for it not to work 
well the only reason why i thought it didnt work in mine was cos the fact probably it couldnt render the required gfx !!but your config seems pretty good enough
try installing it through wubi.. and then after installing restart and there are chances it **mite** work

---

### Post by DeMus on 2008-12-21
> **myriadmagus said:**
> i dont see anything wrong with your config ;P for it not to work 
well the only reason why i thought it didnt work in mine was cos the fact probably it couldnt render the required gfx !!but your config seems pretty good enough
try installing it through wubi.. and then after installing restart and there are chances it **mite** work


Thanks for your answer. I also see no reason why 8.10 should not work since 8.04 works as a charm. As always we want more, we want the newest so I want to upgrade.
Using Wubi sounds nice but is impractical. I have read the info on the Wubi page and although it is not a virtual machine, the whole installation is done in a file in a Windows folder, meaning I still depend on Windows. Once I need to re-install that, I loose the complete 8.10 installation. I also want to get rid of Windows completely and work on Ubuntu since I like that very much.

Any other ideas what could be wrong, why I can't install 8.10 on my machine?

---

### Post by 2hot6ft2 on 2008-12-21
Have you tried adding noacpi to the kernel at the boot screen? Right after selecting the language. I believe it's the F6 key and just add that to the end and hit Enter.

---

### Post by DeMus on 2008-12-21
> **2hot6ft2 said:**
> Have you tried adding noacpi to the kernel at the boot screen? Right after selecting the language. I believe it's the F6 key and just add that to the end and hit Enter.

No, I didn't do that. The first time i used a Linux distro I did use that to be able to install it, but the machine became so slow that I didn't use the installation anymore and returned to Windows. Now I am using Ubuntu for about a year and I do not want to return to Windows, but I also don't like to have a slow machine.
What does noacpi do btw?

---

### Post by DeMus on 2008-12-21
In the meantime I found out what went wrong:
My lcd monitor has 2 cables, one with a blue VGA connector and one with a white digital connector.
I only use the digital connection on my 8500GT nVidia card. 
When the VGA connector is plugged in at boot, I do see the desktop but it is set at a wrong resolution. Changing it to the right one doesn't help much. I have to re-start and since I do this using the live CD I would think I will loose the new settings completely, right?

Why doesn't the program use the digital connection to my lcd and also uses the right resolution like 8.04 does?

Anyone?

---

### Post by myriadmagus on 2008-12-22
thats probably cos the graphics driver hasnt been installed .. so if you go to hardware setting it mite show you your gfx card driver to be installed once u install it ,it shud work :)

---

