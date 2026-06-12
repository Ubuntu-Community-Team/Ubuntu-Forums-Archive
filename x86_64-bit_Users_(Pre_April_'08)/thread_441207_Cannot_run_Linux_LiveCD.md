---
title: "Cannot run Linux LiveCD"
date: 2007-05-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Elliot.strumlauf on 2007-05-12
Hey, I just bought a new laptop (AMDX2 64) and I tried to install a downloaded copy of Feisty 64 and it will not boot. It gets to a point where it says loading ... OK and then my CD player shuts off and the screen goes blank. I then proceeded in trying 6.10 32-bit and it did the same. Even 6.06lts 32 didn't work, it said some error "cat: /var/lib/acpi bios error" or something to that affect. I really want to try Feisty on my laptop, half the reason i bought it was to run Beryl and 64 Feisty. Any help would be greatly appreciated!

---

### Post by DaRush on 2007-05-12
Alright having the same exact issue, live CD didn't work, screen when blank...

I believe the problem is related to your display driver.  I'm running an Athlon X2 3800+, Ati Radeon X800.

The live cd works if I decrease the resolution when I am given the list of boot options (press F4, and reduce the visual settings).

I've installed feisty doing this,  but the same problem happens when i try to boot the system in graphical mode (command line works).  I think i have to edit the xorg.conf file, and I'm trying to figure that out now...

---

### Post by Elliot.strumlauf on 2007-05-13
So to run it i have to hit f4 and then install it, but when i use 7.04, can i reset my resolution? I have a Nvidia Geforce Go 6150, if that helps?

---

### Post by Elliot.strumlauf on 2007-05-13
Ok, need some help...i have an hp dv6355us with geforce 6150 card, im tired of using windows and could use some help?

---

### Post by koshari on 2007-05-13
try booting with some extra switches , 

there is a post in these forums with a heap of options, 

what i did on a problemsome system was booted with the splash screen NOT in quiet mode, then you can see the stage it stalls at, and try a few swtches regarding that area,

---

### Post by Cappy on 2007-05-13
Try booting with "acpi=off" or turn acpi off in your bios. Googling your laptop + " linux" will generally tell you if there is something extra you need to do to get it to work.

---

### Post by Elliot.strumlauf on 2007-05-13
What is an ACPI and how do I turn it off? And how do I edit my bios?

---

### Post by jerrylamos on 2007-05-13
Well, on CD Live, when it gives the boot options, push F6 then add noapic acpi=off at the end of the line like so:

quiet splash noapic acpi=off

Which worked for me for one Linux distro on one computer - the others didn't need it.  Note, if you do an install of the same level on the same computer, you may need the options as well.  Then booting CD Live again after the install you could do a:
Applications Accessories Terminal
sudo fdisk -l
look for Linux.  Mine's on /dev/sda3 I'm sure yours will vary.
sudo mkdir /media/C your choice of directory name, I chose C
sudo mount /dev/sda3 /media/C
sudo gedit /media/C/boot/grub/menu.lst
where the l is a lower case L
Then look for the first line that starts kernel and add the same incantation:
kernel...............bunch of other stuff................quiet splash noapic acpi=off
note the kernel line is all one line, and will likely wrap around to the next displayed line.

Cheers, Jerry

---

### Post by bluetracer on 2007-05-14
I had a similar issue with a configuration very similar to yours (Athlon 64 3700, Radeon X850XT).

What worked for me was to edit the boot parameters (F6 at startup for the LiveCD, edit /boot/grub/menu.lst for a full install) so that 'splash' becomes 'nosplash'.  All was then well.

---

### Post by Elliot.strumlauf on 2007-05-14
I got it running using the no ACPI under f6. Now I need help with wireless? Can anyone adivse me on what to do?

---

### Post by bluetracer on 2007-05-15
> **Elliot.strumlauf said:**
> I got it running using the no ACPI under f6. Now I need help with wireless? Can anyone adivse me on what to do?

What is your wireless card?

---

### Post by Elliot.strumlauf on 2007-05-19
I have no clue. It came with my dc6355us hp laptop. And for the record, I cannot even install the darn system because it keeps saying I cannot resize this partition. I give up on Linux

---

