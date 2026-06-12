---
title: "New computer [Question]"
date: 2005-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Hack4ev3r on 2005-11-20
Hi I'm getting a new computer and i just wanted to know if anyone had/has problems with this motherboard "MSI K8n Neo4-F"
Also I'm getting a 250GB Western Digital S-ATA II 

Would i have problems with my Drive? how about the mobo anyone tried it? its nForce4 so i shouldn't have any problems right??
Thanks again,
Tommy.

---

### Post by RAOF on 2005-11-20
I'm running an NForce4 m/b and a sata h/d just fine.  It's not your **precise** m/b, so it's possible that some of the non-nforce bits (sound, firewire spring to mind) won't work, but I think that's unlikely.  You should have no problems.

---

### Post by nalmeth on 2005-11-20
I wouldn't expect any problems with your motherboard, but I am still having problems with my built-in graphics card. NVIDIA driver did nothing, and ATI driver operates maybe at 1/3 efficiency.

Good luck to ya

---

### Post by bonzodog on 2005-11-21
I have an MSI K8N Neo Platinum Nforce 3 mobo...it's ideal for linux. keep the gear all nvidia if poss, and it will 'Just Work'. The SATA drive will also work, as Ubuntu should install the SATA kernel at boot.
Mine also has the GBLan port on it and onboard Nvidia sound. I just mounted an NVidia GeForce6200 AGP 8x 250MB card on it.

---

### Post by Hack4ev3r on 2005-11-23
Thank you for your help everybody
i just got my computer today but my 10/100/1000 Ethernet card isn't working
i went to nvidia site and i found the drivers for athlon64 no problem downloaded put on disk-on-key load on the computer sh BLABLABLA and it says it doesn't find the kernel source and i can't do anything without my networking running.
is there a binary of nForce4 Drivers for ubuntu 64bit?

Thanks ahead,
Tommy.

---

### Post by trinaryouroboros on 2005-11-24
[QUOTE=Hack4ev3r]Hi I'm getting a new computer and i just wanted to know if anyone had/has problems with this motherboard "MSI K8n Neo4-F"
Also I'm getting a 250GB Western Digital S-ATA II 

Would i have problems with my Drive? how about the mobo anyone tried it? its nForce4 so i shouldn't have any problems right??
Thanks again,
Tommy.[/QUOTE]

Dude, firstly, I have that Sata drive. Installed it, never had anything so quick in my life in my computer. Awesome choice.

My Hoary 64-bit install went smoothly on it (I chose, ground-up install) - then Breezy updates went smoothly...then Dapper updates...smoothly. Then I noticed how smooth the hard drive sounds, and realized how noisy my fans are compared to it. Colt 45...smooooth.

Anycase, my scenerio does differ, for I have a DFI Lanparty nF4 Ultra-D mobo . My only qualm was eventually installing my XFX 6600 GT, which was really no problem. Don't forget to do the nvidia install outlined here:

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

  The qualm, case in point, was that I had to force nvidia-settings config to enable itself by default...was a weird issue though actually...just get the thing setup already, and start gaming the way it was meant to be.

*Edit: If, however, you get issues installing nVidia stuff and get like bloopy looking weird (but cool) ascii-looking patterns all over the place instead of what your Gnome login screen should look like, then just remember, CTRL+ALT+F1 (console) and ALT+F7 (Desktop) are your best friends...*

*Edit 2: ..and Lynx can be your friend too sometimes...good old text web browsing.*

---

### Post by trinaryouroboros on 2005-11-24
[QUOTE=Hack4ev3r]Thank you for your help everybody
i just got my computer today but my 10/100/1000 Ethernet card isn't working
i went to nvidia site and i found the drivers for athlon64 no problem downloaded put on disk-on-key load on the computer sh BLABLABLA and it says it doesn't find the kernel source and i can't do anything without my networking running.
is there a binary of nForce4 Drivers for ubuntu 64bit?

Thanks ahead,
Tommy.[/QUOTE]

Yes, and I'll be damned if I remember what they were. I would check the mobo site firstly. I got my onboard Marvell Yukon Gigabit card working by getting a linux driver for it from DFI, so I prolly can't help you anymore than a bit of searching on nVidia could.

---

### Post by Moobert on 2005-11-24
[QUOTE=Hack4ev3r]Hi I'm getting a new computer and i just wanted to know if anyone had/has problems with this motherboard "MSI K8n Neo4-F"
Also I'm getting a 250GB Western Digital S-ATA II 
[/QUOTE]

Hey,

Yup its works great. The onboard sound, onboard lan, pcie (with a 6600 GT), and ata all ran out of the box on a default install of breezy. I also tested it on a new verson of knoppix with the same results. Not tried the sata support, but i've heard that works as well too. Theres also a post about it on the debian lists:

[http://lists.debian.org/debian-amd64/2005/06/msg00290.html](http://lists.debian.org/debian-amd64/2005/06/msg00290.html)

sounds like hes using sata fine.

---

