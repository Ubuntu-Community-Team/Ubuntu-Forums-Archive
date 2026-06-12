---
title: "Orange Box Issues"
date: 2008-09-19
forum: Wine
---

### Post by Teddy Picker on 2008-09-19
I installed the Orange Box using WINE, but when trying to play a game, the screen goes white at the main menu of the game (the ad for valve works fine though). I tried everything I saw online, then tried installing windows on another hard disk to boot between the two (using windows for my games). Then I tried to partition the drive I have running now so that I could run windows on one of the partitions, but none of these methods have been able to work. If anyone could help me out I would greatly appreciate it.

---

### Post by aoanla on 2008-09-19
Have you successfully installed other games in Wine?

What is your graphics card, and what drivers are you using?

When you say that "none of the methods" worked, including some examples of trying to run games in Windows, apparently, what do you mean? At the moment, your description doesn't tell us what didn't work in those cases...

---

### Post by Teddy Picker on 2008-09-19
by saying I tried everything I saw online, I meant that I googled every tutorial about how to run the Orange Box, but non of their methods worked......

---

### Post by aoanla on 2008-09-19
You still haven't answered my question about your video card and drivers.

Also, what I was referring to was that you said you tried dual booting with Windows, and that didn't work. Did you mean "you couldn't get it to dual boot" (which is a separate issue), or "you couldn't get the Orange Box to work in Windows, once you dual booted"? 
Being precise and detailed in describing your problem helps us to help you.

---

### Post by Teddy Picker on 2008-09-20
I have an Nvidia GeForce FX 5900 and as far as drivers in Wine go, I am clueless you would have to tell me how to find those. With the dual boot, What I wanted to do was partition a little bit of my drive to install Windows on, but I am not sure how. I have been unable to install Windows on either of my extra drives (one IDE and one SATA) and do not know what to do. So when I said I can't dual boot, I meant that I have been unable to successfully install Windows to attempt a dual boot. Hope this helps; thanks.

---

### Post by aoanla on 2008-09-20
Not drivers in Wine (Wine doesn't use separate device drivers) - drivers in Ubuntu!

Did you tick the box to use the nVidia drivers in the "Hardware Drivers" menu item? If you didn't, you're using the free nv driver, which almost certainly won't work.
I suggest that you install EnvyNG with Synaptic and use it to install up-to-date drivers for your card, and see if games work then.

---

### Post by Teddy Picker on 2008-09-21
I have the box checked in the hardware drivers to use the actual Nvidia drivers, should I still try to run EnvyNG or is there something else I should try?

---

### Post by aoanla on 2008-09-21
Definitely use EnvyNG. The Ubuntu copies of nVidia drivers are usually rather old.

---

