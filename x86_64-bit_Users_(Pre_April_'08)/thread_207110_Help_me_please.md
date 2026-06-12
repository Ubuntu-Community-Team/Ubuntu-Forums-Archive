---
title: "Help me please"
date: 2006-07-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by rurik on 2006-07-01
Im new to linux and i want to learn how to use linux/unix so i got ubuntu because i really liked how Ubuntu looked.

Im having lots of problems and so if u could point me in the right direction or give me instrutions of how to fix some of my problems, it would be awesome.

I installed the 64 bit version on an IDE drive. Now ive been trying to use a method to dual boot my system where I copy the first 512 bytes of the boot partion and then transfer that file to Windows XP but all i get is an empty file that way. I dont know if its possible to set the IDE drive as my master becuse XP is on 2 SATA drives that are set to raid 0. but if anybody got suggestion, im willing to try them.

it also seems that my video card is not detected by ubuntu. when i open the xorg.conf file when i was updating my video drives to stop ubuntu from crashing, the entry there stated it was a generic NVIDIA card and the drivier was nvidia but all the other data was missing. im using NVIDIA GEFORCE 7800GT in a PCIe slot.

Also my sound doesnt work, does ubuntu support drives for the creative X-Fi series cards?

im running a amd 64 3800+ on a K8N NEO4-F NF4 motherboard.

if u need more information please ask and ill post that. Thanks alot for the help. I really want to get linux up and running as its important for my work and i just want to learn how to use linux better.

---

### Post by JoshHendo on 2006-07-01
Im not sure about all your problems, but as for the graphics card it may help to install the nvidia drivers following the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=139264&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=139264&highlight=nvidia) .

That should help. Please ask me if you have any problems with that :).

- Josh

---

### Post by rurik on 2006-07-01
ive tried method 1 before and that is what helped me stop ubuntu from freezing up on me, but when i open my xorg.conf file this is the output for my video card

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

is it possible that the card is not being recongnized becuase its in a PCI Express slot?

also how can I change the resolution for my monitor? Thanks for the help.

---

### Post by eldaria on 2006-07-01
it says 

> 
Driver "nvidia"


That is the Nvidia driver, so if you are able to boot up and you have a display, then your card is working with the Nvidia driver.

The standard open source driver is only called 'nv'

Just try and launch a open GL screensaver, and you will see. :-)

---

### Post by zonerr on 2006-07-01
As far as the raid files you should be able to set up the boot sequence in bios for the drive you want to boot from. Depending on the bios all of them have a boot sequence setting. 
Pci e is supported in ubuntu so that's not the problem.
Id follow the other link and check again to see if it worked.

---

