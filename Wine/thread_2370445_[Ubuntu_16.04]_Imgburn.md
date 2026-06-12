---
title: "[Ubuntu 16.04] Imgburn"
date: 2017-09-03
forum: Wine
---

### Post by mapomme1108 on 2017-09-03
Hello,

I use Ubuntu 16.04 on a Qnap NAS with a USB Blu-ray burner.
I have installed Wine Stable and Imgburn.

The burner is not mounted in Ubuntu's usual directory but in /nas_share/external/OpticalDisc2
I have added the burner as drive D: with WineCFG but it is not detected by Imgburn.

How can I fix this?
Is there a ubuntu software like Imgburn?

Thank you in advance for your help.

---

### Post by ajgreeny on 2017-09-03
Plenty of available packages for burning CDs and DVDs but I don't know about blu-ray disks.
Try xfburn, brasero, k3b, or search using ubuntu-software or synaptic for any other alternatives.
They will all burn an image to disk, eg an .iso of a Linux distro.

---

### Post by mapomme1108 on 2017-09-04
Hello,


I have read about all these softwares but they do not seem to work with blu-ray disks.


It works with the Windows software Anyburn, with Wine.

Thanks anyway

---

### Post by ajgreeny on 2017-09-04
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by mastablasta on 2017-09-05
apparently k3B : [https://userbase.kde.org/K3b](https://userbase.kde.org/K3b)
and brasero: [https://help.ubuntu.com/community/CdDvd/Burning#Blu-Ray_Burning](https://help.ubuntu.com/community/CdDvd/Burning#Blu-Ray_Burning)

can burn blu ray.

CDRTools:
> [COLOR=#333333][FONT=monospace]As of 3.01a21, with the help of Jorg Schilling and Clement Lefebvre, the packaging includes scripts that mimic Genisoimage, Readom, and Wodim, so that Brasero should function with all features enabled. Other apps should as well. [/FONT][/COLOR]

still if you found somehting that works well in wine, then i see no reason not to use it.

---

