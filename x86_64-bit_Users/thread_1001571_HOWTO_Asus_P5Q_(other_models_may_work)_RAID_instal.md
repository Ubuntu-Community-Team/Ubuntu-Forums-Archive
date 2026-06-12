---
title: "HOWTO Asus P5Q (other models may work) RAID installation"
date: 2008-12-04
forum: x86 64-bit Users
---

### Post by vhozard on 2008-12-04
Vhozard's howto install ubuntu RAID on new Asus motherboards:

1. First of all you'll have to prepare your Hard Drives for RAID:
- Boot your computer and go in the BIOS, goto "Storage Configuration ---> Configure SATA as" and set it to RAID. Save changes and reboot.
- After you rebooted press "Control + I" during boot (maybe it's a different hotkey, but I doubt that), that will take you to the Intel Matrix Storage Manager
- Here you can create a RAID volume (I like gaming and I have two Samsung Spinpoint F1R 320GB harddrives, so I made one big volume of 640GB RAID0)

2. Then you need to download the Ubuntu Alternate cd-rom and burn it to a cd. (I have 4GB of memory, so I used 64 bit)

3. I assume you know how to setup your BIOS to use the dvd/cd-drive as first boot device.
Also you'll need to set your Storage Configuration to IDE in your BIOS (you're probably thinking: "What?!", but it has to be IDE). Save changes and reboot.

4. Boot from the ubuntu-cd and wait a LONG time, you really have to patient. Probably you will get a lot of errors, like:
"attempt to access beyond end of device
rw=0, want=139526045, limit=1723392"
Just ignore them and be patient.

5. When all the loading is done, just follow the instructions and install ubuntu.

6. After you installed ubuntu, go in your BIOS and set the Storage Configuration back to RAID. Save changes and reboot.

7. Have fun!

Feel free to email me at [email]vhozard@gmail.com[/email], if you get stuck.

Greets Vhozard,

PS If you're experiencing strange lock-ups you have to add "acpi=off" and/or "noapic nolapic" and/or "all-generic-ide"  to the kernel line when you boot from the cd-rom (see [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) for more information)

---

### Post by allanE on 2008-12-04
Many Thanks, It worked like a charm on my Asus DSEB-16 server board

---

