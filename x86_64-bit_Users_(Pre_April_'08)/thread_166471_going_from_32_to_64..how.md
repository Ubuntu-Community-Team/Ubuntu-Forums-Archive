---
title: "going from 32 to 64..how?"
date: 2006-04-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by s_spiff on 2006-04-26
guys, I was using i86 version of Ubuntu BB [ asus X series motherboard, amb 2400+ 32 bit ], when my motherboard concked off.. now I have a new motherboard, and a new 64 bit processor [ Gigabyte motherboard and 64bit 3500+ processor ]. Now when I tried to boot into linux [ which was intsalled on a 80 gb hdd ] It is not able to load the GDM, citing some error that it couldn't be generated something, with loads of grabled characaters. Is there a way to boot in? cuz I don wanna lose all the data, and the customizations! It would take me a months effort and research to get all my stuff back. Please help!

---

### Post by RAOF on 2006-04-26
[QUOTE=s_spiff]guys, I was using i86 version of Ubuntu BB [ asus X series motherboard, amb 2400+ 32 bit ], when my motherboard concked off.. now I have a new motherboard, and a new 64 bit processor [ Gigabyte motherboard and 64bit 3500+ processor ]. Now when I tried to boot into linux [ which was intsalled on a 80 gb hdd ] It is not able to load the GDM, citing some error that it couldn't be generated something, with loads of grabled characaters. Is there a way to boot in? cuz I don wanna lose all the data, and the customizations! It would take me a months effort and research to get all my stuff back. Please help![/QUOTE]
Well, you can still get to the command line by booting into "recovery mode".  And is the motherboard the only thing you changed?  Were you using the on-board graphics?  If so, you may need to run **sudo dpkg-reconfigure xserver-xorg** to select the driver for the new graphics chip.

Interesting/useful pieces of information:  the output of **lspci**, and the contents of the files /etc/X11/xorg.conf and /var/log/Xorg.0.log

---

### Post by s_spiff on 2006-04-30
well the recovery mode was quite confusing... so I did a fresh install... but even after that , ubuntu cannot detect the new graphic card or something, and cannot render the graphical interface... what to do?
... i have a Gigabyte motherboard [ iDNA series ] with GeForce gpu onboard graphics 64 mb..extendable to 128, and support for pci express graphic card [ tho I havent put on anythign there yet, and using the on board one ]. someone help!!!

---

### Post by RAOF on 2006-04-30
[QUOTE=s_spiff]well the recovery mode was quite confusing... so I did a fresh install... but even after that , ubuntu cannot detect the new graphic card or something, and cannot render the graphical interface... what to do?
... i have a Gigabyte motherboard [ iDNA series ] with GeForce gpu onboard graphics 64 mb..extendable to 128, and support for pci express graphic card [ tho I havent put on anythign there yet, and using the on board one ]. someone help!!![/QUOTE]
Well, it looks like you'll need to get the binary nVidia drivers.  The new integrated video chips aren't (well) supported by the free nv drivers.

```

sudo /etc/init.d/gdm stop
sudo apt-get nvidia-glx
sudo nvidia-xconfig
sudo /etc/init.d/gdm start

```

Incidentally, if you'd posted the relevant pieces of information, I could've saved you a reinstall ;)

---

### Post by s_spiff on 2006-05-01
well chuck it...i installed dapper drake...but now i don have the damn drivers...and without drivers i cant connect to net! i have to come to winxp just to post my query man! painful! i'm thinking of goin back to ubuntu32 bit...i know on a 64 its a lil wierd..but i'm havin doubt wether it'll work or not..

---

### Post by RAOF on 2006-05-01
[QUOTE=s_spiff]well chuck it...i installed dapper drake...but now i don have the damn drivers...and without drivers i cant connect to net! i have to come to winxp just to post my query man! painful! i'm thinking of goin back to ubuntu32 bit...i know on a 64 its a lil wierd..but i'm havin doubt wether it'll work or not..[/QUOTE]
Which drivers?  How do you connect to the net?  Your network card **should** be detected by default.

32bit Ubuntu will work just fine on an 64bit processor.  But you'll probably have the same problems with it - you'll still need to get the graphics drivers.

---

### Post by s_spiff on 2006-05-02
well ...yeah the 32 bit has probl;ems with the drivers....but i think its not only with the graphics [ on board one ] ..but also the ethernet card. Cuz i had this how-to [ [http://www.ubuntuforums.org/showthread.php?t=87643](http://www.ubuntuforums.org/showthread.php?t=87643) ] on this forum that asked me to run lsmod | grep mii and if i didnt get the response it meant that i dont have the drivers installed. I havent quite understood it and it wud be great if u cud help me with what exactly do i need to run..cuz he's given like 5 pages of stuff to try.. anyways i got the drivers on a cd now.. but when i try to install it it says : check that you have binutils package installed and if so, please see that 'ld' is in the PATH [ something of this sort ].

---

### Post by RAOF on 2006-05-02
I'm not sure of the exact steps, my ethernet card has always worked.  But I'll try.
Run, and post the output here: 
```
dmesg | grep -i eth
```
That should give some line like: 
```
[   50.864533] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.53.
```
If it doesn't, run **sudo modprobe -v forcedeth**, then run the dmesg again.

---

### Post by s_spiff on 2006-05-02
well installing the damn drivers for my chipset..then will check out if it still doesnt work.. if it begins working. ...I wont have to go thru that tedious how-to... will update u guys abt it...time to get back to ubuntu :P

---

