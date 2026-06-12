---
title: "core2 duo and 8800GTS"
date: 2007-08-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by napster2500 on 2007-08-23
hello all!
i have purchased a new computer with an intel core2 duo proc and a 8800GTS video card... when i boot the ubuntu 64-bit cd it says that the gnome session cannot be loaded!
i mention that i have the original ubuntu cds! (3weeks waited to come but it worthed)...
anyone have an idea? please help! :D

---

### Post by napster2500 on 2007-08-24
no ideas? :(

---

### Post by kwunderlich on 2007-08-24
As soon as the live cd starts, hit the F6 key and try changing the argument from "splash" to become "nosplash".  Here is a link related to this: [http://ubuntuforums.org/showthread.php?t=421876&page=4](http://ubuntuforums.org/showthread.php?t=421876&page=4)

I have pretty much the same hardware that you do by the way.

Intel Core 2 Duo 6600
EVGA GeForce 8800 GTS
EVGA 68i motherboard

---

### Post by dabl on 2007-08-24
I like the "Alternate Install" CD better than the live CD.

Ubuntu 64-bit runs great on my Core 2 Extreme, with Nvidia 7900GS.  I think it will work great on your Core 2 Duo.  :popcorn:

---

### Post by napster2500 on 2007-08-25
yes but is the video card responsible by being so "young"? i mean that the vga is too new for ubuntu? i've heard that ubuntu has 100% support for nvidia but is this rule available for the newest vgas too?
in fact, where do i get the alternate cd?
thanks

---

### Post by bollix47 on 2007-08-25
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Near the bottom of the page there is a box you can check if you want the alternate.

---

### Post by napster2500 on 2007-08-25
ok but that cd uses the text based installer... i want to use the live cd so i can install ubuntu from the "user friendly" gnome interface...
any idea?... i forgot to say that the computer makes a couple of sounds when the "ubuntuuser" logges into ubuntu live cd... and then i recieve a message that says "the gnome interface cannot be loaded" or something like this!
thanks

---

### Post by saru411 on 2007-08-25
nvidia works just fine as soon as you have the drivers installed. the problem is that you must first get the o/s installed then install the graphics driver. have you tried installing in safe graphics mode?

---

### Post by TheAbyssDragon on 2007-08-25
I'm having similar problems with my laptop.

[http://ubuntuforums.org/showthread.php?p=3248514#post3248514](http://ubuntuforums.org/showthread.php?p=3248514#post3248514)

The issue hasn't been resolved yet, but I have determined that the problem is with 7.04, not 64 bit.

---

### Post by napster2500 on 2007-08-25
> **saru411 said:**
> nvidia works just fine as soon as you have the drivers installed. the problem is that you must first get the o/s installed then install the graphics driver. have you tried installing in safe graphics mode?

in the safe mode its no difference... the computer makes a couple of sounds and then crashes...

---

### Post by volksolwagen57 on 2007-08-27
a long time ago, when i downloaded ubuntu for the first time and burned it onto a cd, i had the same problem. i searched around and found that the best way to make a live cd is to burn it on the slowest possible speed. i don't know why this is so and why it works better this way, it just does. maybe you have a broken live cd?

---

### Post by napster2500 on 2007-08-27
i have the original ubuntu cds... i've ordered them....:-?

---

### Post by Mikey976 on 2007-08-28
i actually was having the same issue with my x1950 pro pci-e 

my setup is much like yours. or will be once my 8800 comes in.

however if u would like to install from the "User friendly GUI"

u can DL the edgy 6.10 live cd. run and install that. then update to most recent. 
then upgrade your dist to feisty 7.04. 

if you have a decent dsl/cable connection shouldnt take you more then 2hours. 

but my honest suggestion is if your "unsure" of the alternate cd. 
install vmware and run it from that. your not gonna beable to install any really visual goodies but it will familiarize u with the process. 

all my exp has been gained since this past friday night till now. 
between work and home i must have installed ubuntu well over 20 times

i have gotten to play with beryl with one of my work test bench pc's 
lil'ol am2 sempron 3000+
1gb ddr2 3200
and verto nvidia 7300le 256mb 

i have to say looks amazing and runs pretty fast

---

### Post by napster2500 on 2007-08-29
ok!
thanks for help!
i will try this method and post if it's working:)

---

### Post by Tanker Bob on 2007-08-29
I loaded 64-bit Kubuntu 7.04 from the live CD with no problems some months back. The screen looked bad when it came up because Kubuntu picked the VESA driver at 56 Hz. But that tells me that the basic load will run on the 8800GTS. As soon as I had the system installed, I installed Envy and used it to load the NVIDIA driver.

If the live CD runs from the CD itself, then it should work without significant problems when installed. That's the theory, anyway.

---

