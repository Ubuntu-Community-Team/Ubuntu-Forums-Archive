---
title: "upgrade 8.10 to 9.04, ati mobility radeon hd 3870 drivers no good"
date: 2009-07-02
forum: x86 64-bit Users
---

### Post by jewfromdahood on 2009-07-02
I'm fairly new, but quickly learning linux, (I have Doom 3 and Doom 3 RoE as well as ETQW on my laptop at highest quality 1920 X 1200 running smoothly) I have tried upgrading on several occasions to jaunty jackalope. I run a laptop I built myself, and it works beautifully in 8.10 but I want to upgrade. But my issue is for some reason ATI restricted drivers won't work, tried every method when it came out. But I stayed with jaunty because I was tired of reinstalling 8.10. I've tried installing ATI Catalyst 9.4, 9.5, and 9.6 on 8.10 as I just want to make sure they work at all.
I need 3D rendering as I have mentioned above, I play Doom 3, Doom 3: Resurrection of Evil, and Enemy Territory: Quake Wars all natively under Ubuntu intrepid. I currently use fglrx 8.543, Ubuntu 8.10 2.6.27-14 kernel customized to trim the fat (shed drivers that are ancient that I don't use), as well as optimize it for my Core 2 duo.
My laptop is an OCZDIY17A2-DM88XT Barebones
1 X ATI Mobility Radeon HD 3870 512MB GDDR3 512MB
Intel Core 2 Duo P9500 2.53Ghz
4GB DDR3 RAM

At login screen I get a black screen always. And I have to restore via recovery mode.

Also I was wondering about how can I get my avermedia a312 card I installed to work?

---

### Post by Pabloo0o0 on 2009-07-03
UP

I have the same problem, on my dell laptop 1555 @  ATI HD4500 Series

---

### Post by tenmoi on 2009-07-04
> **jewfromdahood said:**
> I'm fairly new, but quickly learning linux, (I have Doom 3 and Doom 3 RoE as well as ETQW on my laptop at highest quality 1920 X 1200 running smoothly) I have tried upgrading on several occasions to jaunty jackalope. I run a laptop I built myself, and it works beautifully in 8.10 but I want to upgrade. But my issue is for some reason ATI restricted drivers won't work, tried every method when it came out. But I stayed with jaunty because I was tired of reinstalling 8.10. I've tried installing ATI Catalyst 9.4, 9.5, and 9.6 on 8.10 as I just want to make sure they work at all.
I need 3D rendering as I have mentioned above, I play Doom 3, Doom 3: Resurrection of Evil, and Enemy Territory: Quake Wars all natively under Ubuntu intrepid. I currently use fglrx 8.543, Ubuntu 8.10 2.6.27-14 kernel customized to trim the fat (shed drivers that are ancient that I don't use), as well as optimize it for my Core 2 duo.
My laptop is an OCZDIY17A2-DM88XT Barebones
1 X ATI Mobility Radeon HD 3870 512MB GDDR3 512MB
Intel Core 2 Duo P9500 2.53Ghz
4GB DDR3 RAM

At login screen I get a black screen always. And I have to restore via recovery mode.

Also I was wondering about how can I get my avermedia a312 card I installed to work?


Here you go: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Ubuntu_way_to_install_the_Proprietary_Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Ubuntu_way_to_install_the_Proprietary_Drivers)

Next time do a google search for how to install ati on ubuntu and you wont have to wait.

---

### Post by jewfromdahood on 2009-07-06
> **tenmoi said:**
> Here you go: [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Ubuntu_way_to_install_the_Proprietary_Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#The_Ubuntu_way_to_install_the_Proprietary_Drivers)

Next time do a google search for how to install ati on ubuntu and you wont have to wait.

Actually.... Here's the sad thing. Did it, tried every approach they had for intrepid ibex, same result everytime... Black Screen. so I have to boot into recovery mode and restore to generic video and then reinstall original fglrx.

Other than that Enemy Territory: Quake Wars, and Doom 3 as well as Doom 3: RoE run flawlessly on my OCZ DIY17A2 I built, even with just a single gpu, I get max quality max AA, max AF, all at a beautiful crisp 1920 X 1200.

---

### Post by jewfromdahood on 2009-07-06
Basically right now, if I could find a method to get it working with the latest drivers on just intrepid ibex. It would be awesome if there was someone out there with the same barebones I have so they would know what to do.

I need a sure-fire way for intrepid ibex and jaunty. As I can not completely reinstall ubuntu 8.10 after wiping out 9.04 so I can use fglrx rendering.

PS... Everything else on this laptop works, even things i installed after I purchased it, with exception to my Avermedia a312 TV tuner, Intel wireless 5300, the analog volume dial, optical toslink sound, it just ran perfect with exception to tv tuner and gpu driver after 9.3. AMD really screwed up ATI. I have been an ATI man since I was a little boy at 8 or 9 playing Tribes 2 with the ATI Rage 128 I still have, and later a Radeon Pro 9600. Though its a coaster now... I always loved how ATI still supported GPUs very very old. But AMD read my lips... "I NEVER USED YOUR CPUS OTHER THAN OPTERON, YOUR DRIVER PHILOSOPHY SUCKS! BRING THE OLD ATI BACK THAT WE ALL KNOW AND LOVE! FOR GOD SAKE THEY SUPPORTED MY 9600 PRO LONGER THAN YOU GUYS SUPPORTED MY X1800XT IN MY DESKTOPS"

---

### Post by tenmoi on 2009-07-07
> **jewfromdahood said:**
> Actually.... Here's the sad thing. Did it, tried every approach they had for intrepid ibex, same result everytime... Black Screen. so I have to boot into recovery mode and restore to generic video and then reinstall original fglrx.

Other than that Enemy Territory: Quake Wars, and Doom 3 as well as Doom 3: RoE run flawlessly on my OCZ DIY17A2 I built, even with just a single gpu, I get max quality max AA, max AF, all at a beautiful crisp 1920 X 1200.

Hmm. So that's as far as I can help. 
I was reading somewhere that AMD was releasing its source code and would open this and that and I decided to by a DESKTOP 3870 and now I regret my decision. Whenever I think about being deceived into this open source trap I just get so angry I come to curse AMD.

THey suck. So next time buy Intel or NVIDIA, which is the bad guy not the devil AMD is.

---

### Post by jewfromdahood on 2009-07-08
I have never actually owned anything using Nvidia (other than my old Xbox). But also the laptop I built OCZDIY17A2, had everything I needed and more. See when I built this I had intended it for dual-boot windows (just to use it with my iPhone), 2 hard drives, optical toslink audio, powerful upgradeable GPU, capable of powerful CPU (I balanced power and performance with my P9500), DDR3 at 1066Mhz (for a 1:1 ratio with the FSB), eSATA, HDMI, firewire, full keyboard that is backlit (can change red, green, blue that was a perk), great speakers (these are loud, clear, great quality, even with mini subwoofer), large screen (17"), and great webcam (2.0 MP and can rotate up and down) analog rotary volume control (Make it easier to set to exactly how loud I want it, and it shows the volume bar everytime I adjust it similar to a Mac, Thanks Ubuntu!), not to mention Blu-Ray, and gigabit ethernet. And the this was the barebones that fit the bill, and it only came in an Intel version with Crossfire capability, or a similar version, only with AMD CPU.

FYI this is the same or similar barebones as the Alienware m17. it's known as the Flextronics Arima W840-DI.

---

### Post by Yellow Pasque on 2009-07-09
I kept getting the black screen issue when I tried (the Ubuntu version of) fglrx on a spare install of Kubuntu 9.04. I hadn't tried fglrx in a while, and I wanted to confirm it still sucked (it does). I ended up doing something else with that disk space, but I think using this in the Device section of xorg.conf might have solved it though:
```
Option "EnableRandr12" "false"
```

---

### Post by jewfromdahood on 2009-08-21
Unfortunately I tried that as well just now, and no dice! Tried it with 9.8 and 9.7

---

### Post by markbuntu on 2009-08-23
What you need to do is completely remove fglrx before upgrading or the driver will fail and you will end up with a black screen, guaranteed. If you are using the generic VESA driver when you upgrade everything should go smoothly/

After you upgrade successfully do not use the driver offered in hardware drivers (9.3) but get the latest 9.8 from ati.  The 9.3 driver does not support many of the mobility x3xxx series and many of the newer 4xxx cards. Make sure you have all the updates before trying to install the driver.

---

