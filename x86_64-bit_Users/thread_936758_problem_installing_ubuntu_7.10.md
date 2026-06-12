---
title: "problem installing ubuntu 7.10"
date: 2008-10-03
forum: x86 64-bit Users
---

### Post by Ricky1 on 2008-10-03
hello evryone.
 i was trying to in stall ubuntu 7.10 on my pc today but evrytime the cd boots and i choose (start/or install ubuntu now) the screen goes into power saving mode.any ideas on how to solve this?:confused:

i had a previous exp installing it on my older pc witch was half preformance of mu current my specs are:
Gigabyte motherboard Supports amd am2+phenom/am2 athlon 64 series
Ga-Ma770-Ds3/s3
Gigabyte graphics card Geforce 8500 512
2 gbs rams
amd phenom 9550 quad-core 2.21ghz


hope someone can help me with this...thanks

---

### Post by Idefix82 on 2008-10-03
I hope you don't mind me asking, but why are you installing 7.10 rather than 8.04?
If I were you I would burn a Ubuntu 8.04 Live CD at a low speed (say 8x or even 4x) and install that.

---

### Post by Kilz on 2008-10-03
even better would be to use the alternate install cd. It has a better record at installing the 64bit version.

---

### Post by Yellow Pasque on 2008-10-03
Actually, if I was a new user and had to download an .iso right now, I would probably go with Ubuntu 8.10 (especially with modern hardware).

---

### Post by Sef on 2008-10-03
> Actually, if I was a new user and had to download an .iso right now, I would probably go with Ubuntu 8.10 (especially with modern hardware).
That is a good idea.  Gutsy's upgrade support runs out in about 6 1/2 months.   Hardy Heron's, 8.04, support will run out in 2 1/2 years.

Intrepid Ibex is still in testing mode (beta now), if you do not want to be a tester, then go with Hardy Heron.   Ibex's support will run out in 18 months.

---

### Post by Ricky1 on 2008-10-04
Thank you all for replys,i was trying to install 7.10 cuz it was the only cd i had but now i downloaded a new iso image of ubuntu 8.0.4 and its working gr8..didn't have any problems with installing it but now am facing another problem that i didn't have on 7.10.
can't change screen resolution am stuck at a very big resolution..is it because am using a 64bit version that doesn't support my driver?
when i loged in it was asking me to download a batch of 124 files of updates maybe i need those for linux to detect my graphics card?
am fairly new to ubuntu don't flame pls:D
i found another thread explaining a app called envy that should fix the resolution thing looks kinda complicated but i won't giveup till i find a solution i really like ubuntu
so if anyone have any ideas would be happy to see it.
thanks

---

### Post by Idefix82 on 2008-10-04
You should definitely download all the updates that Ubuntu is offering you.
After that go to System->Administration->Hardware Drivers and see if Ubuntu offers you a proprietary driver for the graphics card.

Welcome to the world of Ubuntu by the way! Give it a month and you won't look back :)

---

### Post by Sef on 2008-10-04
What is your graphics card?

---

### Post by Ricky1 on 2008-10-04
ok i have more info on my problem hope its usefull.
i reinstalled a new copy of 8.0.4 cuz i think i messedup some stuff with this envy thingy.
so when i got into the fresh installation the resol was perfect 1280x778
and i was able to pick any diffrent resolution.
then i tried installing all secrurity updates all went fine but i coudn't use conpiz fusion and it kept telling me to enable Nvidia accelerated graphics driver so i clcked use then it downloaded a file then asks for restart.
after the restart the resolution went back to 640x3xx and i was able to use compiz fusion but stuck with very annoying resolution,so i disabled it for now.
oh and font is kinda broken too some letters r written in gray/white..so i guess i still need to install driver.
my card is Geforce 8500 GT Nvidia

---

### Post by xen-uno on 2008-10-04
I would suggest that you download latest driver here ...

[http://www.nvidia.com/object/linux_display_amd64_173.14.12.html](http://www.nvidia.com/object/linux_display_amd64_173.14.12.html)

... then follow the install guide here ...

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

I have a formatted printable doc of Starcannon's post here ...

[http://home.mchsi.com/~xen-uno/NvidiaDriverInstall.doc](http://home.mchsi.com/~xen-uno/NvidiaDriverInstall.doc)

---

