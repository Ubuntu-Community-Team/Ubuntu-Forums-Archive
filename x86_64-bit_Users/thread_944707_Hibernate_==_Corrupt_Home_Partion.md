---
title: "Hibernate == Corrupt Home Partion?"
date: 2008-10-11
forum: x86 64-bit Users
---

### Post by Nikayah on 2008-10-11
First i would like to say that i am newish to Ubuntu. I used hibernate once and my computer "shut down". Afterwards when i went to boot it up again the splash screen came up as usual, with the bar moving side to side. Then it froze, but I noticed that the HDD was being read, so i didnt panic. Then the splash screen "moved" leaving green stripes and static at the top of my screen. A couple moments later it shifted to the left causing the part that got cut off to appear on the right-hand side of my screen. Serveral minutes later after nothing happened, i hard reset my computer. I then booted back in to ubuntu and it stopped halfway through the loading progress saying something about my disk, and giving me a root terminal. I pressed ctrl-D (It said to do so to return to the boot process)and got to the log in screen. I entered my username and password, and it said that my home directory didn't exist. I have yet to fix this problem, if anyone can help PLEASE do so. 


Here is some information about my setup.
I am triple booting with Ubuntu/Slax/XP.
My home folder is on a seperate partition.
my MB is Asus M3A
my proc is an AMD phenom
i have 4 gigs of ram
i'm using ubuntu 8.04 64bit

---

### Post by cariboo on 2008-10-11
When you get a message you don't understand, write it down and then look it up, this would have allowed you to fix your system without doing any extra damage. To repair the system now, get out your live cd boot to the desktop and in a Applictions-->Accessories-->Terminal type:

```
sudo fsck -r /dev/sdxx
```

where /dev/sdxx is you Ubuntu partition.

Jim

---

