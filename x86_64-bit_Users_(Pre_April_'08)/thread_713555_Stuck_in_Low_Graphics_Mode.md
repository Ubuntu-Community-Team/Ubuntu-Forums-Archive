---
title: "Stuck in Low Graphics Mode"
date: 2008-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by ombpro on 2008-03-02
Hello,
I am looking for help.  I am totally new to linux.  I am a 3d artist looking to experiment with some linux software.  However, after creating an extra partition on my windows machine and successfully installing ubuntu I am now having problems.  The problems first occured when I enabled the ati propietary graphics driver.  When I rebooted I got stuck in low graphics mode and any amount of configuration would not take me out of it.  I attempted to download drivers from ati and it did not fix the problem.  I then deleted the parition and reinstalled ubuntu, thinking I must have messed something up.  This time I had learned about Envy, so I downloaded it and gave it a try.  It seemed to work great, however, when I rebooted, same exact problem:

could not detect video card, running in low graphics mode

options of continuing or configuring

of course, configuring gets me no where becaue you have to reboot for the changes to take effect, and rebooting puts me back to low graphics mode.

I then learned about reconfiguring xserver with a command in terminal.
of course it looked like it worked out just fine, I restarted from the terminal, and I'm back to low graphics mode again.

I am about to conclude that linux just won't work for me and will be forced to stay with windows.  If anyone can suggest something that might work, I would love any help at all.  Thanks very much for the time.

my hardware:
asus p5b-vm do
intel 2.4 ghz core 2 quad
his radeon hd2600pro
500 gb w.d. hard drive

again, the solutions I have tried are

using proprietary ati drivers = failed
using Envy to configure =  failed
reconfiguring xserver = failed

stuck in low graphics mode, 800x600

Thanks very much again!!:)

---

### Post by loserboy on 2008-03-02
i dont personally know the answer but i'm sure someone has got it working and posted a howto, could you tell me if its an agp or pci-e card and i'll start lookin around

i havent used an ati card in a while but i recall needing to setup fglrx and such

---

### Post by ombpro on 2008-03-02
Hi, thanks for the help

it is pci-e

actually, i am wondering if I did something wrong in configuring xserver
when it asks for the slot number or something for your video card, I was unsure of what to put, and it said you could probably use the default answer so I went with that.  Anyway, thanks, greatly appreciate it:)

---

### Post by loserboy on 2008-03-02
well ive never had the default go wrong on me, but ive seen where somtimes it does, i think its pretty rare though... also i think if that particular question was answered wrong you would get no video at all.

I found this page [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Pre-Installation_Checks](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Pre-Installation_Checks)
try going through the steps right from the beginning, it takes a little knowledge of command line but u can mostly copy and paste, lemme know if you have any questions.

---

### Post by ombpro on 2008-03-02
well, I tried the stuff on that page, the first method seemed to be working, but I just ended up with the same result again

the second method got me kind of confused, but I think I sorted through it though.  Yet, I still can't get it to work.

Thanks for the help though, I must be off to bed, will check back tomorrow after work.

Thanks again!!:)

---

### Post by felker2 on 2008-03-03
Which architecture version of Ubuntu are you using: the i386 or the AMD64/x86-64? This forum is especially for the AMD64/x86-64 stuff.

And which version number: 7.10 (or an alpha version of 8.04)?

Have you tried the second option "... safe graphics" from the live-CD boot menu? That should give you at least 1024x...

BTW: I would not dive into envy nor amd/ati-stuff to get things working; Ubuntu's tools should do.

---

### Post by loserboy on 2008-03-03
sorry none of it worked, if you are using 7.04 I would suggest trying 7.10 or vice versa.

I know it gets frustratiing, but don't give up, it feels really good when you get everything going and I remain confident that you will, i'm at work atm but i'll keep looking for more info when i get a chance.

---

### Post by ombpro on 2008-03-05
thanks for the advice, I am still working on it days later, been pretty busy so I have not had a chance to mess with it.  I have yet to get it working yet, but I am going to keep trying and will post something when I get it fixed.  I am using the laster 64 bit version, btw.

Thanks again!!:)

---

### Post by caver1 on 2008-03-05
I had the same problem with a Nvidia Geforce8 card. Gutsy 64bit. Finally narrowed it down to compiz.
Asxlong as I don't try to use it I'm fine. As soon as I try to enable the effects I go back to low graphics.
So until I find an answer I'm avoiding compiz. Asus m2n-e motherboard.:(
caver1

---

### Post by loserboy on 2008-03-06
I looked around more, but everywhere i look usually points me back to that same page and people seem to be getting it to work, i really don't know.... maybe someone with more knowledge will jump in and help ya.

---

