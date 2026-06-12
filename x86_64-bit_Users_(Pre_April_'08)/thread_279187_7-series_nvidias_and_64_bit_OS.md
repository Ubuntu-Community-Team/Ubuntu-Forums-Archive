---
title: "7-series nvidias and 64 bit OS"
date: 2006-10-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dr_Freemanstein on 2006-10-17
I am in the process of upgrading my system and moving over to Ubuntu permanantly.  I am going upto an Athlon 64 sytem so will obviously need the 64 bit distro of Ubuntu.  My question however is about my motherboard/graphics card setup. I am buying a ASUS A8N-SLI SE motherboard and (for the moment) one 512MB XFX 7300GT PCI-E graphics card.  The problem is twofold...Firstly, there does'nt seem to be much in the way of info about running linux with a 7 series graphics card, and secondly, will (if I add another graphics-card) the SLi work with Ubuntu??

Has anyone already got a similar setup running? Or know any of the answers to my ponderings??  i have checked NVidia's site, but it's not much help!

---

### Post by John.Michael.Kane on 2006-10-17
Look here [http://www.nvidia.com/object/linux_display_amd64_1.0-8774.html](http://www.nvidia.com/object/linux_display_amd64_1.0-8774.html) which leads to this [http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html) 

As you can see 7series are supported.

As for sli the nVidia linux drivers support SLI so you should be fine.You may have to edit your xorg.conf for it to kick in though.

Also most sli based nvidia boards have no issues running linux. 

I'm not sure you will see any real gains from running it though.

---

### Post by rosbif on 2006-10-17
I have exactly this configuration on one of my machines - runs fine with AMD64-k8 kernel and the 8774 nvidia drivers.  Follow the link posted by the previous poster and it's all good, just alter "nv" to "nvidia" in the xorg.conf.  The reason I'm running nvidia is for the dual screen support, which still doesn't seem to work on the nv driver.

---

### Post by Dr_Freemanstein on 2006-10-17
Thank-you both for your replys.  You were both very helpful.

I had previously visited the first link you give, but regret that I totally missed the link to "Supported Products" Duh!!

Anyway, thanks-again and I look forward to chatting again one day hopefully on a dedicated Ubuntu machine!!

---

### Post by RAOF on 2006-10-17
> **Dr_Freemanstein said:**
> I am in the process of upgrading my system and moving over to Ubuntu permanantly.  I am going upto an Athlon 64 sytem so will obviously need the 64 bit distro of Ubuntu.  ...

That's not actually true.  AMD64 processors will run the 32bit version of Ubuntu just fine.  Also, since you're looking at such a high-end graphics card, you're presumably interested in games?  In which case, the 32bit version will make more sense for you; there really aren't many 64bit game binaries.  Also you'll probably be needing to use Wine to run Windows games, and it's substantially easier to use wine on the 32bit version.

---

### Post by patrickfromspain on 2006-10-18
hi-end card.. I would say that of a 7300, as any older 6600 beats this new 7300.. ;)

---

### Post by RAOF on 2006-10-18
> **patrickfromspain said:**
> hi-end card.. I would say that of a 7300, as any older 6600 beats this new 7300.. ;)

There's no reason to get anything but integrated video if you don't want to game :p.  **Any** non-integrated card is high-end.

Also, he talked about SLI.

---

### Post by thexaspect on 2006-11-25
fyi, sli does not have dual monitor support, so save yourself the trouble, and just run them as parallel cards =)

---

### Post by Pinoy915 on 2006-11-25
Mine works fine. I'm using an AMD X2 4200+ with Nvidia 7300GS on Ubuntu AMD64 Edgy. I'm not into games but I just didn't want my onboard to take up any of my ram.

---

