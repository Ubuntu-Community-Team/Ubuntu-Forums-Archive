---
title: "hardware compatibility: the same with 32 and 64?"
date: 2008-04-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by LK_gandalf_ on 2008-04-12
Hi, i have a Dell xps m1530 (but it's not the point).
I'm using kubuntu 8.04 32bit now, but I'm thinking to install the 64bit version when the 8.04 will come out.

I know with the software I could have problem finding the packages for the 64bit. Ok.

But I've never understood the difference about the hardware drivers compatibility.
That is, for examples, if my webcam and bluetooth works out-of-the-box with Hardy at 32bit, will they work fine with the 64bit too?
it depends of the kernel? is the kernel the same?
i'm quite confused, please light me :)

---

### Post by Kilz on 2008-04-12
> **LK_gandalf_ said:**
> Hi, i have a Dell xps m1530 (but it's not the point).
I'm using kubuntu 8.04 32bit now, but I'm thinking to install the 64bit version when the 8.04 will come out.

I know with the software I could have problem finding the packages for the 64bit. Ok.
There are the exact same number of packages in the amd64 repository as in the i386. Can some old , rare, little known application not be available? Sure. But all the common applications in the 32bit version are available on the 64bit one.

> **LK_gandalf_ said:**
> But I've never understood the difference about the hardware drivers compatibility.
That is, for examples, if my webcam and bluetooth works out-of-the-box with Hardy at 32bit, will they work fine with the 64bit too?
it depends of the kernel? is the kernel the same?
i'm quite confused, please light me :)

It should work that way.

---

### Post by tamoneya on 2008-04-12
I have tried both 32 and 64 bit on both of my computers and have no driver related issues.  The only thing that is a pain in 64 bit is getting flash to work well.  It is difficult to get installed and when it is installed it doesn't quite work as well.

---

### Post by LK_gandalf_ on 2008-04-12
So the support out of the box is exactly the same for the 32 and 64bit? this is the main issue :)
I don't want to install the 64bit and then discover that, for example, my wi-fi card won't work with 64bit while there is the driver for the 32bit version.

---

### Post by Kilz on 2008-04-12
> **LK_gandalf_ said:**
> So the support out of the box is exactly the same for the 32 and 64bit? this is the main issue :)
I don't want to install the 64bit and then discover that, for example, my wi-fi card won't work with 64bit while there is the driver for the 32bit version.

Lets clarify that then, you asked about "out of the box" before.  If your wireless card works on the open source drivers that come standard in 32bit Ubuntu, yes it will. But if you have to go to a site and download proprietary drivers from the manufacturer, make sure they offer a 64bit version.

---

### Post by jespdj on 2008-04-14
I am running 64-bit Ubuntu 8.04 beta on a Lenovo T61 and installing Flash in 64-bit 8.04 is very easy - the necessary stuff like nspluginwrapper is installed automatically. So getting Flash to work is not difficult in 64-bit 8.04.

Your XPS M1530 most likely has the Intel 4965 WiFi card. That will most likely work automatically with 64-bit Ubuntu 8.04 - the Lenovo T61 has the same and it works without any problems.

(Note: I haven't got my XPS M1530 yet, I'm getting it today, so I can't really say anything about Ubuntu on the M1530 yet).

---

### Post by Clancy_s on 2008-04-16
> **jespdj said:**
>  the Intel 4965 WiFi card. That will most likely work automatically with 64-bit Ubuntu 8.04 - the Lenovo T61 has the same and it works without any problems.

I also have  Intel 4965 WiFi.  I need to use wicd with 64 bit GG but it works OOTB with the live CD of 64 bit HH on my system too. :)

eta: I have an ATI Mobility Radeon 2600 card.  With GG I needed to install the radeon HD drivers to get proper resolution (and use safe mode to get the live CD to boot), it looks as though that's working* OK in HH too.

*just the resolution and things like video playback.  I've not bothered with compiz.

---

### Post by LK_gandalf_ on 2008-04-17
thanks for the answer. 
So the only issue is to verify that, if the device doesn't work with the open source drivers, on the website is possible to find a 64bit version.
In some days I'll format and install a fresh kubuntu 8.04 64bit, I'll ask you if there are some problem :) thanks

---

