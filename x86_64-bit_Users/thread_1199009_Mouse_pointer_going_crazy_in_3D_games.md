---
title: "Mouse pointer going crazy in 3D games"
date: 2009-06-28
forum: x86 64-bit Users
---

### Post by DPJ93 on 2009-06-28
I have this very strange problem.. Whenever I run a 3D game in my Ubuntu 9.04 64 bit, the mouse pointer moves by itself completely randomly. It happens in Super Tux Kart 0.6.1, sometimes in Extreme Tux Racer, and in many 3D shooter games.

I'm not sure if this happens because I'm using he 64 bit edition or not, so feel free to move this topic if the same happens in the 32 bit version. :)

And I don't know if this happens because of Ubuntu or bad coding in the games.

Anyway, is there a way I can solve this?

---

### Post by DPJ93 on 2009-06-28
The same thing happens in Secret Maryo Chronicles too. Maybe some typical SDL game problem?

Help is very appreciated. This is the only problem I have with Ubuntu 64 bit.

---

### Post by DPJ93 on 2009-06-29
*Bump* Nobody else has got this problem?

---

### Post by fricot on 2009-06-30
Hi,
I'm experiencing a similar problem. On many of my games the mouse pointer moves itself independently in the menu. But also while playing it seems like the mouse resets constantly its position, making impossible to play.

any ideas?

cya

---

### Post by DPJ93 on 2009-08-18
Come on! This is a serious issue! Also, it's not always the mouse pointer, but also, the up, down, left, and right buttons are being pressed all the time visually it seems like.. So I have no way to over-control it! It's impossible to play a game with that issue.

And in Neverball, the mouse pointer seems to sticky it self to the middle of the screen so I can't really move the floor sideways or forwards..

Please help, somone.

---

### Post by dagrump on 2009-08-18
Do you have the effects enabled? try disabling compiz and see if it works.
Do you have the proper drivers for your video card installed, you have offered very little to work with. How do you expect any one to help?
I'm sorry if I sounding like a grump but the more info the better chance some one will have an answer.

---

### Post by DPJ93 on 2009-08-19
> **dagrump said:**
> Do you have the effects enabled? try disabling compiz and see if it works.
Do you have the proper drivers for your video card installed, you have offered very little to work with. How do you expect any one to help?
I'm sorry if I sounding like a grump but the more info the better chance some one will have an answer.

Oh, sorry.. I'm not really used to write down the most obvious things I have done to try make it work.. :P I'm a hardcore googler and haven't found any help.

Anyway, I do turn off compiz fusion every time I play a game (to prevent lag), and I do have functional Ati Radeon HD 3400 drivers. This sure might be problems with the game's programming though and just not being compatible with 64 bit Ubuntu. I've heard that nVidia drivers are much more supported when it comes to Linux drivers. But hey.. I don't really think this has got anything to do with the graphic..

It all reacts like.. it's like an un-calibrated keyboard and mouse.. Like the game can't calibrate the controls when it starts.. somehow..

The reason I didn't write too much info was because I was expecting that someone else maybe also had this problem and had already solved it...

---

### Post by lyricalpapa on 2009-08-19
I had a similar problem with my mouse. It was resolved by disconnecting my joystick.

Just a thought.

---

### Post by lyricalpapa on 2009-08-19
Another thought on this. Ran across while tracking down my problem with the joystick.

Some keyboards (eg Microsoft) can also interfere with mice.

---

### Post by DPJ93 on 2009-08-22
This is a VERY strange problem.. And pretty random too. I have never used a joystick in ubuntu.. Never connected one at all. I have an HP Pavilion dv5 laptop.

---

### Post by DPJ93 on 2009-08-26
I wonder if this topic would get some more attention if it was named something else...

---

### Post by DPJ93 on 2009-09-01
Bump

Is this problem so hardware specific that almost nobody else has got it? I'm getting kinda pissed at Ati now..

---

### Post by DPJ93 on 2009-09-15
For the last time; BUMP!

---

### Post by Tiede on 2009-09-19
Well, it's not an ATi only problem, I'm afraid...
I have an HP ProBook 4510s, and the same thing happens to me...
A little lspci for those who may like it...

```

tiede@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
85:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 436c (rev 10)

```
Disabling compiz doesn't do squat...
My uname -api...
```

tiede@yubuntu:~$ uname -api
Linux machine-name 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux
```

---

### Post by DPJ93 on 2009-09-20
Heh. The strange thing is that I seemed to have less problems in Ubuntu 8.10.. Lets just hope this will be fixed in 9.10.. By the way, my graphic card is Ati Mobility Radeon HD 3450 (I believe I wrote HD 3400 before, but that was incorrect).

---

### Post by Artemis3 on 2009-09-20
You should try with a completely different mouse, just to discard hardware issues.

---

