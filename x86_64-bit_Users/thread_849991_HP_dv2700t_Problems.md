---
title: "HP dv2700t Problems"
date: 2008-07-05
forum: x86 64-bit Users
---

### Post by Dorotheos on 2008-07-05
OK, my gf tells me that after a week of ignoring her while trying to get Ubuntu to work properly on my new laptop if i dont just ask for help and fix the things she will leave me ](*,) So im asking for help.

I just brought this new "special edition" Hp dv2700t laptop. After three days i finally figured out how to use ndiswrapper and install my driver bcmwl6.inf. So now when i type ndiswrapper -l i get
bcmwl6 : driver installed
        device (14E4:4315) present
\\:D/

However, when i use the GUI "Windows Wireless Drivers" it says Hardware present: No.

](*,)

Also, iwconfig says

lo no wireless extensions.
eth0 no wireless extensions.

](*,)

So needless to say my laptop won't acess the internet.

PLus, my Nvidia 128MB DDR video card... is worthless!!!!!!! When i go into the Hardware Drivers GUI i see

nvidia_new        [checked] o Not in use

I have gone the NVIDIA website and installed the new linux 64bit driver for the card, but it won't install. It first wanted root, then after i got pass that it want's the server turned off! 

Guys im totally Lost in the cool computer world and about to lose my gf :-({|= if i dont fix this. Cause she's right, i do care about my new laptop more than her \\:D/

Thanks,
DT

---

### Post by Melk79 on 2008-07-05
I just finished setting up my dad's DV2700 with Ubuntu (32-bit though).  He had a Broadcom wireless chip and I followed this [link]("http://www.akyl.net/Network+Manager+problem+in+Ubuntu+8.04") to correct.  Wicd seemed to work better than Network Manager for his setup.

I've got Nvidia's to work on my laptop and my dad's just by checking and unchecking the Nvidia box in Hardware Drivers.  It took once or twice, but then the driver was installed automatically. This was in one of the sticky links for this forum.

---

### Post by Yellow Pasque on 2008-07-05
Here's what worked for me with my wireless card:
```
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```
Then, add ndiswrapper to the list of modules to load at boot:
```
gksudo gedit /etc/modules
```
Restart the system.
Finally, go give your girlfriend some affection.

---

### Post by Dorotheos on 2008-07-06
Temujin,
I really appreciater your help, but that didn't work for me I did everything as you typed and it's still not working. Thanks though

---

### Post by Dorotheos on 2008-07-06
Melk79,

That's probably exactly what i need to fix the display, but since my wireless isn't working i can't acces the internet through that laptop. Any other suggestions?

---

### Post by phidia on 2008-07-06
You might want to look at [this thread]("http://ubuntuforums.org/showthread.php?t=811732&highlight=broadcom+64+bit+driver"). There's a link in post #5 that might be useful too.

---

