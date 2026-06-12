---
title: "Ubuntu 7.10 Move from IDE -&gt; SATA = Grub Error 21"
date: 2008-04-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by devzero on 2008-04-17
Hi,

As you can see in the Thread title, i want (must) move my Ubuntu to another Hard drive because the current one is about to fail very soon (Media sense error, switching ATA modes and so on)

I did the following:
booted from the live-CD made a cp -a /mnt/sdg2/* /mnt/sdc1/
It copied the system sucessfully without errors, as the hard disk is yet working.

Then i mounted the /dev and the /proc directory from the CD in /mnt/sdc1/dev and ../proc
chrooted altered the fstab, did a grub-install /dev/sdc1 and an update-grub.
I changed the drive in the bios as first drive and tried to boot.

Before the menu entries appears, the grub greeted me with a Stage 1.5 Error 21 error and halted.

Unfortunately I am currently at work, so I can post the menu.lst and the drivemap on evening, but my systen didn't get that far to use them.

My Hardware is a Asus P5K with the P35 Chipset
the new HD is connected to a Silicon 3112 but the Bios regonizes it so I can select the boot order.

The Old HD is connected with IDE to the mainboard.

the Ubuntu on my IDE Hard drive detected the HDs on the Silicon Controller natively without needing to install any driver, so I wonder that grub didn't like it.
I have no raid or so on.

I reinstalled Gub 2 or 3 times did a recheck during install, and updated it too.

Another weird thing is, that the new HD is sometimes on /dev/sda1 and sometimes on /dev/sdc1 I tried to reinstall grub at both constellations but it didnt help.

Has anyone an answer about this?
The Forum search told me no one had this error ever here, and google told me to change the boot order, but as the old HD is yet in the system I have a Problem with that (Maybe I want to install Windows on another HD too)

Thanks for help in advance
greets Martin

---

### Post by Marabu on 2008-04-17
Hi Martin

What exactly is the problem in changing the boot order in your bios? There is still the possibility to add an entry in your grub for a windows residing on another HD. 
The problem i guess is that you installed grub only on your new harddisk but your system still boots from the old one. 
So try to change your boot order. Alternatively you might try to re-install grub on your old HD too.

cheers 
Marabu

---

### Post by devzero on 2008-04-18
Hi,

thanks for the answer,
its just was a simple human error of unknowledge of grub

after I did:
grub
>root (hd0,0)
>setup (hd0)
>quit

surprise surprise it works now :D

But I cant login in the ubuntuforum with Firefox an opera
If I am logging in, i am logged out again.

IE4Linux works, thats weird

---

