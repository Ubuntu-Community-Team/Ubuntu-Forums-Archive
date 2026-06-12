---
title: "total problems from start to install"
date: 2007-06-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by diacronic on 2007-06-13
I have the following motherboard:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813138074](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138074)

two sata hdds hooked up, 1gb of memory (2x512), and one pci wifi card. that is all.
first when i start up i have to:
sudo dpkg-reconfigure xserver-xorg
and switch to vesa 

then once i finally get the installer running it gets to step 5. 
And just sits there, like it sees no hdds.
The motherboard and bios sees them , but not linux. 

I'd really like to get this all to work but don't even know where to start.

---

### Post by Cappy on 2007-06-13
So, it seems you need to switch to vesa because linux isn't detecting your integrated video card.
Starting points:
Does
```
sudo fdisk -l
```
show your HD?

Does ```
sudo gparted
```
give any errors when you run it in the terminal?

Look in
```
dmesg | less
```
and see if you  see anything mentioning your HD or HD drivers.

You are using your hard drive as a raid 0? (non parity)

---

### Post by diacronic on 2007-06-13
To simplify the whole thing I unhooked one HDD, so now instead of two Sata HDDs, there is only one. 


> fdisk -l

does nothing


> gparted

terminate called after throwing an instance of 'Glib: :OptionError'
Aborted

> dmesg | less

Only things that seem out of place are:

Nvidia board detected. Ignoring ACPI timer override.
ACPI: bIOS IRQ0 pin2 override ignored.


it gives hdb to the cd/dvd drive , why would it skip hda ?

one other thing i noticed is the sound card isnt working either. 


Seems like all the chipsets this motherboard has are not supported ATM. 
Sigh. Even if I have to bypass some of this stuff for now until it is supported I don't mind. 

Thanks for the help.

---

### Post by diacronic on 2007-06-14
Would like to get the computer running, anyone ?

---

### Post by Cappy on 2007-06-14
you did run ```
sudo fdisk -l
``` with sudo, correct?

I googled and the only thing I found was that the bios setting for SATA may need to be "Linux AHCI" or maybe something else. There's about 1 results in English for your motherboard and Linux.

---

### Post by diacronic on 2007-06-14
Got a copy of Gutsy Gibbon and Used that Install CD, that seemed to work. still had the video card problems but that was expected. at least this saw the hdds. about to restart now and see how it turns out.


well that is a flop too. wireless card doesnt work. sound doesnt work. i wish i could at least run a wire to it for updates and hopefully the wifi would work after.

---

### Post by diacronic on 2007-06-14
seems gutsy is the only one that will install. all the rest fail to find the hdds, which I don't understand at all. 
I can't really keep using this version as nothing seems to really work. At this point I even tried to get 32 bit versions working, same problems.

---

### Post by diacronic on 2007-06-15
Well I have to do it but I guess I'll have to install Windows back onto the computer. I was fine using Linux until now when I upgraded the computer , seems linux has a while before it will be caught up. Maybe I'll be back then someday.

---

