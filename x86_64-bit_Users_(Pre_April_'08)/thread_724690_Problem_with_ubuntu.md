---
title: "Problem with ubuntu"
date: 2008-03-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Jc61990 on 2008-03-14
ok.. so for the past 2 days ive been doing a lot, just moved my gaming pc from Windows Vista Ultimate x64 to Ubuntu 7.04 Feisty Fawn x64 edition, had no problems till i installed my video card drivers, i had no screen, well the people over at maximumpc.com helped me alot at got that problem fixed, but now about 30 min ago, i downloaded the Gusty iso for x64 and booted into my normal ubuntu 7.04 and the software update said that i can upgrade to Gusty so i did, the install went through and finished with no errors, but when it said i need to restart, i did, and now im back at square 1 like i have been since i started installing ubuntu. I have no display... the light on my monitor just keeps blinking, i think ive tryed everything i did when i got this problem with feisty. i really dont want to reformat, i had a lot of information, and games installed. is there any way i can fix this so i can use my computer again?

Mobo: Striker Extreme (latest bios)
CPU: Core 2 Quad Q6600 (2.4GHz)
RAM: 2x Crucial Ballistix Tracer 800Mhz Ram (2GB Total)
PSU: Tagan BZ Series 700 Watt
Video Card: EVGA GeForce 8800GT KO 512MB with latest drivers (169.12 for x64)


please help, thanks

---

### Post by whoop on 2008-03-15
A lot of people are experiencing similar problems. I had the problem too. what worked for me was editing /boot/grub/menu.lst.

I removed " quiet splash" from my kernel line and made it something like so:
"kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx ro"

I don't get the splash screen but I don't want that. If you want a splash screen you can try adding one of the splash resolutions by adding a vga value:
```

Colours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
--------+--------------------------------------------------------------
 4 bits |    ?       ?     0x302      ?        ?        ?         ?
 8 bits |  0x300   0x301   0x303    0x305    0x161    0x307     0x31C
15 bits |    ?     0x310   0x313    0x316    0x162    0x319     0x31D
16 bits |    ?     0x311   0x314    0x317    0x163    0x31A     0x31E
24 bits |    ?     0x312   0x315    0x318      ?      0x31B     0x31F
32 bits |    ?       ?       ?        ?      0x164      ?

```

---

