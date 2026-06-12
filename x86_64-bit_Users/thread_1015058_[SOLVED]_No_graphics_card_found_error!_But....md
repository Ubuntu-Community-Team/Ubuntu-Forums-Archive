---
title: "[SOLVED] No graphics card found error! But..."
date: 2008-12-18
forum: x86 64-bit Users
---

### Post by tngcritters on 2008-12-18
I can play movies etc.
Can't use Google Earth
Can't use Compiz Fusion
Both give me no graphics card installed.

specs:
HP Pavilion Slimline s7600n PC
AMD 64 Athlon
duel boot with:
Ubuntu Hardy 
Win. XP multi-media

I thought I installed the correct drivers for Nividia (my notes on my graphics card have been packed and in storage - moving soon)

I am sure Help with this would fix an on going battle with my graphics.  	](*,)

Sheila

---

### Post by cariboo on 2008-12-18
What graphics adapter does your computer use? You mention Nvidia, but not what model. If you could paste the output of:

```
sudo lshw -C video
```

We should be able to help install the proper drivers.

Jim

---

### Post by tngcritters on 2008-12-18
here is the output I got:

 *-display UNCLAIMED     
       description: VGA compatible controller
       product: C51 [GeForce 6150 LE]
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:05.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list
       configuration: latency=0


Thank you
Sheila

---

### Post by tngcritters on 2008-12-21
I did some checking around and it's fixed...just some tweaking on the fonts need to be done. I had forgotten about having/using EnvyNG!! Now to install some fun stuff for compiz fusion!!

---

