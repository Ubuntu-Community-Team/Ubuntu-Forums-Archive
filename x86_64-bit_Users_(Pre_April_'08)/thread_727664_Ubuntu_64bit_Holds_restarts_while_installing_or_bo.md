---
title: "Ubuntu 64bit Holds restarts while installing or booting"
date: 2008-03-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Serdar on 2008-03-18
Ubuntu 64bit Holds restarts while installing or booting

The Ubuntu 64bit desktop install cd loads up - I select the first option, 'start or install Ubuntu' - the splash screen appears with the nice little logo and loading bar - then the computer restarts.:confused:

I have also tried Windows xp64 Professional, but that seems to keep restarting the computer and I can not get a full install to happen. It will boot up the windows splash screen, and then try and continue the install, but it always restarts.:confused:

Although I took one of the memory out from my laptop which is 2GB, than I did install the 64bit ubuntu successfully. After I installed the ubuntu 64bit, I put the 2gb memory back(Total 4GB). Now it’s restarting again. 

I've already had a problem with my Intel® GMA X3100 graphics driver that I was searching for answers. I realized my graphic card (Intel® GMA X3100) is blacklisted. 
Now the restarts problems too, I can not take it anymore. :(

Should I use Ubuntu 64bit? Or keep it with 32bit? Please help me? I do not want to use damn xp either vista.
Thanks for your help...

PS: 32bit Ubuntu works fine. But I can see total 3GB Memory and I can not use Ubuntu desktop effects because of intel GMA X3100 drivers.

Laptop Configuration
Jetta 930S
Intel® 965GM Express
Intel® GMA X3100 !!!!!!!!!!!!!!!!!"Also Blacklisted :( :("
Dual-Core Intel® Core™ 2 Duo T7500 2.20GHz 800FSB 4MB Cache
2 x2GB PC26400 800MHz DDR2 SODIMM
200GB 7200RPM Serial ATA Notebook Drive
Intel® PRO/Wireless 4965AGN Network Adapter
Marvell 99E8055 10/100/1000 Gigabit
Bluetooth 2.0

Thanks Again...

---

### Post by Yellow Pasque on 2008-03-18
Tips for Desktop Effects
[http://ubuntuforums.org/showpost.php?p=4202892&postcount=6](http://ubuntuforums.org/showpost.php?p=4202892&postcount=6)

---

### Post by Serdar on 2008-03-18
Thank you Temüjin , I will give it a try, when I install 32bit Ubuntu.

---

### Post by malathion on 2008-03-18
I had this problem, disabling USB Keyboard in the BIOS fixed it. AFAIK this is a known bug but it does not get much attention.

---

### Post by Rogers on 2008-03-20
> **Serdar said:**
> Ubuntu 64bit Holds restarts while installing or booting

The Ubuntu 64bit desktop install cd loads up - I select the first option, 'start or install Ubuntu' - the splash screen appears with the nice little logo and loading bar - then the computer restarts.:confused:

I have also tried Windows xp64 Professional, but that seems to keep restarting the computer and I can not get a full install to happen. It will boot up the windows splash screen, and then try and continue the install, but it always restarts.:confused:

Although I took one of the memory out from my laptop which is 2GB, than I did install the 64bit ubuntu successfully. After I installed the ubuntu 64bit, I put the 2gb memory back(Total 4GB). Now it’s restarting again. 

I've already had a problem with my Intel® GMA X3100 graphics driver that I was searching for answers. I realized my graphic card (Intel® GMA X3100) is blacklisted. 
Now the restarts problems too, I can not take it anymore. :(

Should I use Ubuntu 64bit? Or keep it with 32bit? Please help me? I do not want to use damn xp either vista.
Thanks for your help...

PS: 32bit Ubuntu works fine. But I can see total 3GB Memory and I can not use Ubuntu desktop effects because of intel GMA X3100 drivers.

Laptop Configuration
Jetta 930S
Intel® 965GM Express
Intel® GMA X3100 !!!!!!!!!!!!!!!!!"Also Blacklisted :( :("
Dual-Core Intel® Core™ 2 Duo T7500 2.20GHz 800FSB 4MB Cache
2 x2GB PC26400 800MHz DDR2 SODIMM
200GB 7200RPM Serial ATA Notebook Drive
Intel® PRO/Wireless 4965AGN Network Adapter
Marvell 99E8055 10/100/1000 Gigabit
Bluetooth 2.0

Thanks Again...

Bad ram.  Hardware issue.

---

### Post by Serdar on 2008-03-20
Thank you Temüjin. With 32 bit ubuntu I am able to use desktop effects now. the only problem is that if i wanna watch a movie or something I have to disable it. But it's okay.

In my bios I tried to disable the USB support but it did not work, either. Also my bios does not let me change anything except time and booting...

I did run memtest86+ 3 times  and could not find any problems...

Thank you guys for responding to my problem...I will try to find out a solution and share it here with you...

---

### Post by lH)4~mK0e on 2008-03-22
Certain systems only allow you to install a certain amount of memory if you are using a 64 bit operating system because of the way the processor and system bus handle the memory.  I had this experience with my desktop, so I chose to stick with 1 GB of memory.  If you want to use all 2 gigs you will need a 32 bit system.

---

