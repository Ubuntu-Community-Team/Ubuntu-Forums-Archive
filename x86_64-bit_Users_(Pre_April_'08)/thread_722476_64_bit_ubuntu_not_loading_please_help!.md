---
title: "64 bit ubuntu not loading please help?!"
date: 2008-03-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cew27 on 2008-03-12
hey i have an nvidia 8800 ultra graphics card and im trying to install ubuntu 64 bit (gutsy) but i get loading kernel then some text and a black screen, can i fix this im sick of vista already i only use it for games?!

---

### Post by sandysandy on 2008-03-12
> **Cew27 said:**
> hey i have an nvidia 8800 ultra graphics card and im trying to install ubuntu 64 bit (gutsy) but i get loading kernel then some text and a black screen, can i fix this im sick of vista already i only use it for games?!

what r ur full system specs. 

do u have 64 bit machine.

r u using live Cd or alternate CD.

regards

---

### Post by Jouke74 on 2008-03-12
A search for Black Screen Nvidia and Install would have shown some results I guess. Use the Alternate install CD. Afterwards, at first boot from HD, start the Kernel after you have edited the kernel line with grub and have changed the "splash" into "nosplash".

---

### Post by Maelgwyn on 2008-03-12
I run x64 Hardy Heron Alpha 6 and when I boot, I get text, and then a black screen (the monitor even pops up saying there's no input), but after a little while, I get my GDM screen :) Just see what happens if you leave it for a little while :)

---

### Post by felker2 on 2008-03-12
> **Cew27 said:**
> hey i have an nvidia 8800 ultra graphics card and im trying to install ubuntu 64 bit (gutsy) but i get loading kernel then some text and a black screen, can i fix this im sick of vista already i only use it for games?!

Have you tried booting in safe mode from the live cd? It's the second boot option.

---

### Post by Cew27 on 2008-03-12
i havent tried the alternate cd, i have tried safe graphics and full system specs are 
intel core 2 duo q6600
nvidia evga 8800 ultra ko silent
evga 780i motherboard
2 gig of ocz sli ready 1066mhz ram 
750 gig seagate barracuda hdd 
2 dvd writers 
cheers

---

### Post by Jedimaniac on 2008-03-12
I had a problem very similar to this. In the end i found that disabling the splash screen in the grub boot loader seemed to fix it. When ever the Splash tries to load it hangs the machine. (at least with an 8800 series card anyway)

Assuming you use the Grub bootloader, try editing the boot command by highlighting your kernel and pressing 'E' (I think). If I remember rightly you have to remove the "-splash" command.

If that fixes your problem you will have to edit your menu.lst file located at /boot/grub and remove the command permenently.

Unfortuantely I am still a bit of a noob so my instructions may not be terribly accurate.

---

### Post by Cew27 on 2008-03-12
ok can any post step by step how to of this ?

---

### Post by Jedimaniac on 2008-03-12
Will try a guide:
[list]

[*]Restart machine
[*]At the dos based menu (Grub bootloader) highlight the required kernel by using the arrow keys (dont press enter)
[*]Press 'e'
[*]A new screen should appear. Highlight the option starting with 'kernel' using the arrow keys and press 'e' again
[*]A new screen will open with a flashing prompt and some text. If i remember rightly the text will end with "ro quiet splash"
[*]Delete "splash" using backspace key
[*]Press enter
[*]Press 'b'
[*]If all goes well the kernel should boot. Report back,
[/LIST]

---

### Post by Cew27 on 2008-03-13
ok done as above it worked thanks, im now creating a new partition to dual boot vista bit it says please wait resizing partiton and has so for the last 5 mins its at 0%

---

### Post by Maelgwyn on 2008-03-13
When you say you're resizing the partition, where are you doing that from?

Best way to do this is download a GPart cd and boot from that so that you're not actually trying to resize a disk that's currently mounted :)

---

### Post by Cew27 on 2008-03-15
ok i installed it but i messed up the dual boot grub is there anyway to re-configure it

---

### Post by fjgaude on 2008-03-15
> **Cew27 said:**
> ok done as above it worked thanks, im now creating a new partition to dual boot vista bit it says please wait resizing partiton and has so for the last 5 mins its at 0%

Depending on the size of your disk, it could take a long time resizing, like 30 minutes. Hang in there, you'll love the results... trust me! <smile>

---

### Post by Cew27 on 2008-03-15
i used ubuntu before but this is my new uber pc, the graphics card whent t!ts up today so i need to rma that but i cant boot windows i messed up the menu.lst

---

### Post by Lintel on 2008-03-17
When I installed Ubuntu x64 a week ago the partition resizing was stuck at 0% for 15 min and then was instantly done, is there any reason why the progress bar does not work?

---

### Post by Cew27 on 2008-03-17
ok graphics card sent away :)

---

